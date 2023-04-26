# Generative - Adversarial networks for generation and compression of thermography data
 
### Short description of the project
This project was made for my engineering thesis' purpose. I studied at a Polish university, AGH University of Science and Technology, and that is the reason for the Polish language in comments and labels in `Wojciech Orzeł Projekt dyplomowy.ipynb` file. That file shows the main case of my project, which was an attempt to find the hidden representation of thermographic images obtained from the examination of composite materials by laser thermography. The hidden representation is in fact the input vector to the StyleGAN3 network (link to the StyleGAN3 project: https://nvlabs.github.io/stylegan3/). The sense of doing that comes from the fact that thermographic data needs a lot of computer memory. It is better to store only a file with a trained network `network-snapshot-000050.pkl` and small input vectors (3KB) for example `tensor.pt`. If you want to get the original image, you only need to pass a selected vector through the network to get the original image.

### Solution explanation
My solution is based on a custom-trained StyleGAN3 network that generates the artificially random thermographic images.
The second part of the process is fitting a real thermographic image to an artificial image from a generator. For this purpose, I use genetic algorithm, which work in iteration. Each iteration (poulation) is the set of images (individuals) in which the algorithm chooses the most similar image to the real image. In the next iteration, that image will be the base for generating a new set. This process continues till the case of reaching zero difference between a real image and a generated one or reaching the limit of iteration.
The function that is responsible for checking image diffrence is based on several factors obtained after calculating the perason criteria for those images and the diffrence between them.

### Results interpretation
The results are at the bottom of `Wojciech Orzeł Projekt dyplomowy.ipynb` file. You should see that they are not perfect, but that is because the generator network training was not completed as it should have been because of hardware and time limitation. Traing took me about 2 days on my laptop, which is not the best tool for making such a large number of computations.
Even if training could be done perfectly, there is still a chance that the genetic algorithm is not enough for this purpose. In that case, there is a need to change the fitting algorithm. (e.g., gradient algorithm, CNN).
