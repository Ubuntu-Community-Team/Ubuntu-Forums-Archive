---
title: "Camera  - a movie player and a portable map"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by protinginys on 2010-12-19
Hello everybody. I have a Canon camera with a big screen. Im travelling a lot and I could really get much more out of my camera than just taking photos with it. For example, watch movies on it (when you have to spend a night in the airport, its quite a nice way to entertain yourself), or view certain maps of the area I am going in. Now the problem is that most of cameras do not recognize neither images nor video files you transfer to them. I googled a bit and I found out that if I changed file's encoding to the one of my camera, it would be possible to view both images and video files on my camera. I just dont know how to do it :) What programs or command lines should I used in ubuntu to change encoding system of files I want to read on camera?
Thanks in advance.

---

### Post by orange2k on 2010-12-19
If I understand you correctly you want to be able to see in Ubuntu what you have recorded on your camera.

To do that you will probably need to prepare your ubuntu system by a couple of commands because you will need different codecs for video and audio so your recording will be recognized correctly. I recommend you read here: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by protinginys on 2010-12-19
No, I have no problems watching my recorded videos on ubuntu. This is what I want: I have a movie file (just ordinary movie, for example "Redemption" with M. Freeman), transfer it to my camera and try to watch it (make my camera a movie player), but I cant because my camera doesnt recognize the file. So I want to find out if there is a way 1) I can edit the movie (or image) file on ubuntu and 2) make it readable on canon camera. Its quite difficult to explain :)

---

### Post by migs73 on 2010-12-19
> **protinginys said:**
> No, I have no problems watching my recorded videos on ubuntu. This is what I want: I have a movie file (just ordinary movie, for example "Redemption" with M. Freeman), transfer it to my camera and try to watch it (make my camera a movie player), but I cant because my camera doesnt recognize the file. So I want to find out if there is a way 1) I can edit the movie (or image) file on ubuntu and 2) make it readable on canon camera. Its quite difficult to explain :)

Welcome to the forums :)

I think is see what you are getting at, I don't know what video format is used by canon, (my Konica uses .MOV files)but to change the file format is relatively easy, if a little time consuming.

There are a few video conversions tools in the Ubuntu Software Centre, one of the ones with most conversion options is Avidemux.

Right click on one of the video files FROM YOUR camera (this will let you see what format it uses), and select properties,first note the file extension used (ie 'filename'.MOV with.MOV being the file extension) the  then click on the Audio/Video tab. This tells you the Audio and video 'codecs' used to 'make' the film. Note these down as they are what you require to have avidemux convert your film to.

Open Avidemux and then select the film you want to convert (clck 'Open' and browse to the film), in the left hand columns set the Audio and video codecs as per you camera file and then set the file type under Format.

Once this is done click on save, at this point it will ask for a new file name (NB you will have to add the file extension {.MOV for example} onto the end of the filename as Linux does not do this automatically and your camera would not recognise the file without it) then when you click save again the encoding will begin.

Depending on what you are encoding from/to, how fast your processor is , how much RAM you have and how long the film is will vary in how long it takes to encode. As you are probably going from a high quality to lower quality format it shouldn't take too long, but a few hours is likely.

I really hope this is what you wanted 'cause it took a while to write all that down!!!! 


Mike :D


EDIT; I am assuming you know how to install Avidemux from the software centre

---

