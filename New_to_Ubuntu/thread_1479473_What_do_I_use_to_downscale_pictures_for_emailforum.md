---
title: "What do I use to downscale pictures for email/forums/social networking sites."
date: 2010-05-10
forum: New to Ubuntu
---

### Post by Phosphorror on 2010-05-10
Greetings,

Hopefully, this is a simple question:

Back when i was on Windows (all of last week!) :) I used to use a program called Pixresizer.

This program, was able to scale down a batch of pictures in one go to a selected resolution (I usually chose 800x600 and 640x480), to use for the likes of blogs, social networking sites, forum posts etc. Naturally, it also saved on storage space on Photobucket and the like.

So, I need something that can preform the above feature. I have F-Spot (naturally, a part of Lucid Lynx) and I have installed Gimp recently.

Maybe it is there already, and I have overlooked it? As I may have mentioned earlier I have been doodling around with Jaunty on my Notebook in dual boot with XP and decided to wipe my main PC entirely of Windows7 for Lucid Lynx (enjoying it very well so far).

Many thanks in advance.

---

### Post by Tamlynmac on 2010-05-10
I use XnView for resizing and it works great.

Located [here]("http://www.xnview.com/en/index.html"). 

One trick I'll share is don't try and install it. Just create a folder in your home folder for it and once unpacked simply save the folders and files to the folder your created. To start it simply run 
home/"created folder"/bin/xnview

The first time it open you will get a small setup window. Do the setup and when you close the setup window and the next time you open it it will open to full screen. Should you make error in the setup or wish to increase thumb size, etc. in the xnview menu they're located under "tools/options".

You can add that run file to your start menu after that. It also does quite q bit of filtering and I've found it to be a nice photo editor. Plus you can save photos to many different formats 

Good Luck and I hope it works for you.

---

### Post by -humanaut- on 2010-05-10
You can use F-Spot to resize images. It's preinstalled and works good enough I think.

---

### Post by Phosphorror on 2010-05-12
> **Tamlynmac said:**
> *snip* I use XnView for resizing and it works great.

Located [here]("http://www.xnview.com/en/index.html"). 

One trick I'll share is don't try and install it. Just create a folder in your home folder for it and once unpacked simply save the folders and files to the folder your created. To start it simply run 
home/"created folder"/bin/xnview

The first time it open you will get a small setup window. Do the setup and when you close the setup window and the next time you open it it will open to full screen. Should you make error in the setup or wish to increase thumb size, etc. in the xnview menu they're located under "tools/options".....

Hi,

I am a relatively new user to Ubuntu, and I have usually installed programs via the terminal method or from Synaptic Package Manager. Unfortunately, this is a bit over my head and there are that many options to choose from for downloading that I don't know what format to download for. I know for certain it's not the RPM files as that would be for Red Hat Linux variants and the like.

Can F-Spot not do batches of photos in one go? If so, how?

---

### Post by hannaman on 2010-05-12
You can attach multiple photos to an e-mail directly from f-spot.  Just select the photos you want and select "Send by Mail..." from the "Photo" menu.  You will then get an option to resize the photos using vague terms like "Medium".  I am not sure what the sizes are but you may be able to find that information in the User's Guide at f-spot.org/User_Guide.

---

### Post by Phosphorror on 2010-05-12
Incredibly, I was chatting to a friend this evening who has only started dabbling with Ubuntu via Wubi, and they found this program called SIR (Simple Image Resizer):

[Clickerage here](http://linux.softpedia.com/get/Multimedia/Graphics/SIR-Simple-Image-Resizer-9805.shtml)

It's a simple debian file that you just click and install. Voila, it appears to work and does exactly the same job as Pixresizer! :)

Anyway guys, cheers for the help. I shall be sticking with using SIR as it appears to do precisely what I want it to do. Many thanks.

---

### Post by The Cog on 2010-05-12
package imagemagick is a good bet. It's command line tools, use **man convert** to see the options. example: **convert -size 800x600 *.jpg**

Use the command **mogrify** instead of **convert** if you want to change the originals - **convert** creates new files leaving the original ones intact.

[http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)

---

