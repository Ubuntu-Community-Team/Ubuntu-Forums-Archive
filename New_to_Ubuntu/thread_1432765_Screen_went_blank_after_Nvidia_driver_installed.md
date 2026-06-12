---
title: "Screen went blank after Nvidia driver installed"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by Nidwow on 2010-03-18
[FONT=Calibri]I am a new LINUX user. I have no prior experience to LINUX up until about 8 hours ago. And please forgive me, English is not my first language either.[/FONT]

[FONT=Calibri]I have a new laptop and it is an ASUS UL50VT.[/FONT]
 
[FONT=Calibri]Intel Core 2 Duo 1.3 GHz[/FONT]
[FONT=Calibri]4 GB DDR3 RAM[/FONT]
[FONT=Calibri]Nvidia GeForce G210M with 512 MB DDR3[/FONT]
 
[FONT=Calibri]I made 40 GB partition using Windows 7 and installed Ubuntu 9.10 on a newly created partition and my laptop is now dual boots with Win 7 and Ubuntu.[/FONT]
 
[FONT=Calibri]The installation of Ubuntu went pretty well. I updated everything, everything work perfectly fine. Then I installed a recommended Nvidia driver 185 and the Ubuntu asked me to restart the computer – so I did.[/FONT]
 
[FONT=Calibri]Dual boots working fine but right after that my screen went blank only two a little white cursors on the top of the laptop screen. I thought I did something wrong so delete the partition and starts the installation all over again 3 more times and it still doing the same thing after I activated the Nvidia driver otherwise everything working fine so far up to that point.[/FONT]
 
[FONT=Calibri]And that is when my experience with LINUX ended LOL.[/FONT]
 
[FONT=Calibri]I really like to try LINUX but I have no idea how to fix this problem.[/FONT]
 
[FONT=Calibri]I have 3 options here. Reinstall it again and do not update the NVIDIA driver, giving LINUX up or have some experienced users guide me through this process. I do not plan to play games or doing any 3D stuff so I may not need the driver at all, but I would like to learn how to fix this.[/FONT]
 
[FONT=Calibri]I do not have laptop with me but could someone help starting the debug process. I will try it when I get home after work. [/FONT]
 
[FONT=Calibri]Please help and again I have no idea what I am doing.[/FONT]
 
[FONT=Calibri]Thank you,[/FONT]
[FONT=Calibri]Nid[/FONT]

---

### Post by realzippy on 2010-03-18
Welcome!
Have a look here:

[http://www.nvnews.net/vbulletin/showthread.php?p=2108701](http://www.nvnews.net/vbulletin/showthread.php?p=2108701)

Geforce 210M is supported since the Nvidia 190.42 driver...

I would download it an install it manually,instructions
can be found in the README file,but,feel free to ask....

---

### Post by Nidwow on 2010-03-18
> **realzippy said:**
> Welcome!
Have a look here:
 
[http://www.nvnews.net/vbulletin/showthread.php?p=2108701](http://www.nvnews.net/vbulletin/showthread.php?p=2108701)
 
Geforce 210M is supported since the Nvidia 190.42 driver...
 
I would download it an install it manually,instructions
can be found in the README file,but,feel free to ask....
 
 
Very nice, thank you kindly. Can't wait to get home and try that. I really want to learn this thing :D

---

### Post by Nidwow on 2010-03-18
Well, got the driver installed it per instruction I still get the blank screen ](*,)

I don't know how to get back to the Ubuntu. I will have to delete the partition and re install the whole thing again one more time and see if it work.  Maybe Linux and I weren't meant to be together LOL

Any other suggestion?

Thank you kindly,
Nid

---

### Post by penguinv on 2010-03-18
If your Nvidia driver is known to work in Windows then ignore the rest of this post.

I had this situation but in Windows. I assume it would be the same in linux. In my case linux only installed the VGAdriver so I could not tell. 

Every time, in windows, I would install the Nvidia driver the  monitor would go black. )And then Windows would crash.) At last I figured that it was a bad (motherboard or Nvidia card. I gave up on that computer.  

(PS I still have it in case anyone has a clue.)

Best of luck to you.

---

### Post by GSF1200S on 2010-03-18
EDIT** I just realized the vid card you mentioned. The driver in Karmic Koala will not support your video card. As said above, download the driver from Nvidia's website and then do the following (Assuming you have a functioning desktop where you have NOT installed any prior nvidia driver):

Rename the driver something easy to remember, like nvidia.run and place it in your /home/username.

Then, kill X:
```
sudo /etc/init.d/gdm stop
```
(You might have to hit Alt+F2 or Alt+F1 if the screen is black after this)

Run the nvidia driver:
```
sudo sh nvidia.run
```

Tell it yes for everything it asks you. Once installed, run nvidia's xconfig (im pretty sure the installer does this for you, but just to make sure):
```
sudo nvidia-xconfig
```

Then, go ahead and restart X:
```
sudo /etc/init.d/gdm restart
```

Hope this helps and let us know if you run into issues...

---

### Post by Nidwow on 2010-03-18
I think I have come to the conclusion that my new laptop stinks LOL :p

My laptop ASUS UL50VT came with 2 video cards. One is an integrated Intel GMA graphics chip and then the  Nvidia GeForce G210M GPU.  I think the early version of this laptop have a switch on the side that user can switch between the regular work (intel) or some 3D gaming (G210M).

My laptop is the later version ASUS removed the switch and I think Windows 7 or NVIDIA know when to use the integrated intel or G210M GPU. I guess depending on what application I am using at time. So it switch between the two. Power saver I guess, no wonder this darn laptop battery lasted for 9 hrs+ on regular uses like reading email, surfing the Internet.

I have no way to disable the integrated Intel, no external switch or anything in the BIOS.

Now, I logged in as root and deleted xorg.conf and I was able to get back in to Ubuntu (yay - learned one more thing about Liunx LOL)

I guess it is what it is. stuck with whatever driver I am currently using now :lolflag:

---

### Post by GSF1200S on 2010-03-18
> **Nidwow said:**
> I think I have come to the conclusion that my new laptop stinks LOL :p

My laptop ASUS UL50VT came with 2 video cards. One is an integrated Intel GMA graphics chip and then the  Nvidia GeForce G210M GPU.  I think the early version of this laptop have a switch on the side that user can switch between the regular work (intel) or some 3D gaming (G210M).

My laptop is the later version ASUS removed the switch and I think Windows 7 or NVIDIA know when to use the integrated intel or G210M GPU. I guess depending on what application I am using at time. So it switch between the two. Power saver I guess, no wonder this darn laptop battery lasted for 9 hrs+ on regular uses like reading email, surfing the Internet.

I have no way to disable the integrated Intel, no external switch or anything in the BIOS.

Now, I logged in as root and deleted xorg.conf and I was able to get back in to Ubuntu (yay - learned one more thing about Liunx LOL)

I guess it is what it is. stuck with whatever driver I am currently using now :lolflag:

Please read my above post- give it a try. Im not familiar with your setup, but if you have an Nvidia card, the latest driver from Nvidia should work. :)

---

### Post by Nidwow on 2010-03-18
> **GSF1200S said:**
> Please read my above post- give it a try. Im not familiar with your setup, but if you have an Nvidia card, the latest driver from Nvidia should work. :)


I follow it to the t, no joy. 

Black screen of death LOL

Also Alt+F2 or Alt+F1 doesn't do anything either. May be it does I just can't see it. I had to power off the laptop and on again then I select the recovery mode and logged it as root then deleted the xorg.conf file. That is the only way I can get back in.

I am sure having two video cards installed have something to do with my black screen of death, Unfortunately I can not disable the integrated one.

Is there a way to see what is the current driver I am using right now? Windows have "Device Manager" what does Linux have that will show me the same?

Thank you kindly,
Nid

---

### Post by Nidwow on 2010-03-18
I have found a very interesting site.

[http://www.linlap.com/wiki/asus+ul50vt](http://www.linlap.com/wiki/asus+ul50vt)

---

### Post by GSF1200S on 2010-03-18
> **Nidwow said:**
> I have found a very interesting site.

[http://www.linlap.com/wiki/asus+ul50vt](http://www.linlap.com/wiki/asus+ul50vt)

Wow man.. this is new territory for me. Ive never had a laptop with 2 different GPUs, especially considering they serve 2 entirely different purposes. I think your best bet is to upgrade to 10.04 as soon as possible to get the latest kernel version. Chances are the technology will be incorporated soon- this has to be a kernel level technology. Sorry I couldnt help- Im usually very good at getting Nvidia users going :(

---

### Post by realzippy on 2010-03-18
[http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2)

...extracting the monitor's EDID under windows,linking to in xorg.conf
seems to work.But first you should get your system running (without NVIDIA driver).

BTW,what does:

**lspci | grep VGA**

say?

---

### Post by Nidwow on 2010-03-18
> **GSF1200S said:**
> Wow man.. this is new territory for me. Ive never had a laptop with 2 different GPUs, especially considering they serve 2 entirely different purposes. I think your best bet is to upgrade to 10.04 as soon as possible to get the latest kernel version. Chances are the technology will be incorporated soon- this has to be a kernel level technology. Sorry I couldnt help- Im usually very good at getting Nvidia users going :(

No problem at all, thank you for all your time trying to help.

---

### Post by Nidwow on 2010-03-18
> **realzippy said:**
> [http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2)

...extracting the monitor's EDID under windows,linking to in xorg.conf
seems to work.But first you should get your system running (without NVIDIA driver).

BTW,what does:

**lspci | grep VGA**

say?

Thank you for the link and the info.  I will read through it. I just starting to play with Linux last night :D

---

### Post by Nidwow on 2010-03-19
[FONT=Calibri][SIZE=3]Still no go for me and I have read everything on that thread. There was a person who has the exact model posting a few pages back on that thread. That person could not get it to work even with forced custom EDID in the xorg.conf.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I just can&#8217;t believe it, so far I have got everything work but the display. I may just have to wait until the problem is fixed since I can&#8217;t dim the LED backlight, my screen is really I mean it&#8217;s REALLY bright. My eyes will be all watering if I am looking at it for about 30 min.[/SIZE][/FONT]

[FONT=Calibri][SIZE=3]After I spent over 15 hours edit, cut, paste, delete xorg.conf and reading forums and I could not get the display to work with the NVIDIA driver I have raised the white flag ):P[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I may have another way to play Ubuntu, I will try to resurrect my good old Dell D610 and play around with it.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Thank you all for trying to help.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3]Nid[/SIZE][/FONT]

---

### Post by Nidwow on 2010-05-04
[http://ubuntuforums.org/showpost.php?p=9218020&postcount=13](http://ubuntuforums.org/showpost.php?p=9218020&postcount=13)

Did the trick at least for ASUS UL50VT laptop and thank you dakilla :D

---

