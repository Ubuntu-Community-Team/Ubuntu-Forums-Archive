---
title: "Sony Vaio shuts down when move player starts"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2010-11-28
Hi All,
I have finally managed to install 10.04 on a 2004 Sony Vaio (previous thread - 10.04 won't boot on sony vaio) and everything seems to work except that if I try to watch a dvd or a video already on the computer, soon after I start movie player everything goes black, the opening script at the top of the screen flashes a few times then just a blank screen. If I open movie player without selecting something to watch it doesn't shut down.
I think that the issues with older Vaios and 10.04 was with the video cards, though I'm already getting out of my depth. Could this be the problem? 
I should say that previous to this I was using 9.10 on the Vaio and everything worked.

---

### Post by warfacegod on 2010-11-28
Sounds like it may be over heating. Might be a good idea to give the machine a thorough cleaning for dust. It's a place to start anyway.

---

### Post by Dermot Doyle on 2010-11-29
Hi warfacegod,
No it doesn't appear to be that. From what I've seen on the internet this is a problem with some older Vaios, but I've barely understood a word of the replies and some people seem to have just given up. I may have to go back to 9.10 which would be a real shame, but I can't not have the capability to watch a DVD or video.
Can anyone else offer any help?

---

### Post by no2498 on 2010-11-30
install htop to see what is running as you watch a video
type htop in a terminal click enter it tells you how to install it
now type htop click enter
it may be in/on your applications/ system tools

just watch it you will see something change


if its hitting the processor hard try this it helped me
this comes from the program cheese

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    

think i had to restart the computer to get it to work

---

### Post by 00arthuryu on 2010-11-30
Could you also give us the vaio model number and/or the hardware used?
Although it does sound like issue is with the video-card overheating and/or dodgy drivers. Are you using an ATI card with the free drivers + playing a video in fullscreen by any chance?

---

### Post by khelben1979 on 2010-11-30
> **00arthuryu said:**
> Could you also give us the vaio model number and/or the hardware used?
Although it does sound like issue is with the video-card overheating and/or dodgy drivers. Are you using an ATI card with the free drivers + playing a video in fullscreen by any chance?

I agree. Free open source drivers makes your cpu work harder, you get more heat inside the laptop, also as the graphic chip get's ineffective it haveto work harder and that generates more heat as well or... the laptop have gotten too worn out for usage because of inefficient cooling.

---

### Post by Dermot Doyle on 2010-11-30
Hi and thanks for all the replies and ideas. My main computer has gone away for a while and in desperation I have reloaded 9.10 for the moment, but I will try again with 10.04 in a week or so. 
no2498, I'll try htop, but the computer shuts down before anything plays so it will have to be quick, or will it keep a record that I can access once I restart the computer. 
OOarthuryu, from my research on the web people have mentioned graphics cards and drivers at the base of some of the problems with Vaios and 10.04, but I have to admit most of what they said went over my head. Mine is a VGN-B55S, a model rarely mentioned here because I bought it in Thailand. As to the ATI card with free drivers I'm afraid I don't know. Where should I look for the information that would be of use?
khelben1979, You could well be right, I just hope it isn't too worn out just yet. A friend put a new hard drive and upgraded memory in it about a year ago and it hasn't had much use since then.
As to retrying 10.04 I assume I can simply upgrade from the update manager and save the hassle I had loading it from a CD in the first place.
Thanks again and no doubt you'll hear from me when I give it another go. I'm certainly impressed with 10.04 on my Dell.

---

### Post by AndyM3 on 2010-11-30
Be kind and post the output of the following two commands (run them using the Terminal):
```
sudo lspci | grep VGA
sudo lspci | grep Display
```
Both of them should show the same thing, but I'm not sure that's the case with every computer.
(You can run them from 9.10.)
It may sound like a stupid suggestion, but try running Jockey (System > Administration > Hardware Drivers or Additional Drivers) the next time you try 10.04.

Also, may I ask why you didn't try 10.10? It might just fix your issues.

---

### Post by Dermot Doyle on 2010-11-30
Hi AndyM3,
The outputs are:

dermot@dermot-laptop:~$ sudo lspci | grep VGA
[sudo] password for dermot: 
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
dermot@dermot-laptop:~$ sudo lspci | grep Display
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

Rightly or wrongly and being not very computerate I thought the long term support version would be better for me, though I'd be happy to go to 10.10 if it fixed the problem.
Just another thought, as I stated in the begining I have gone back to 9.10 because I can watch DVDs and videos perfectly well with movie player so in theory the problem is more likely to be some difference between 9.10 and 10.04 than a hardware issue. Or is that wrong?

---

### Post by no2498 on 2010-11-30
i do not think it saves a file if you can get a screen shot may help you

as far as an upgrade do a clean install
the software sources list gets mucked up with a online upgrade

---

### Post by khelben1979 on 2010-12-01
> **Dermot Doyle said:**
> Just another thought, as I stated in the begining I have gone back to 9.10 because I can watch DVDs and videos perfectly well with movie player so in theory the problem is more likely to be some difference between 9.10 and 10.04 than a hardware issue. Or is that wrong?

I can now see that the problem is not with your video drivers. Ubuntu 10.04 uses a newer kernel than 9.10 and that affects all the hardware which is in your laptop, and apparantely the kernel is not good with your laptop..

---

