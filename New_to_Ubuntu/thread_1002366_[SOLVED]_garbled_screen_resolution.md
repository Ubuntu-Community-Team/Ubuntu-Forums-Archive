---
title: "[SOLVED] garbled screen resolution"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Bill Mann on 2008-12-04
I'm such an idiot. I changed the screen resolution (Sony Vaio; Gutsy Gibbon) to something that is illegible with 4 blurred repeated screens, so I can't read anything, enter the terminal, or get to xorg.conf. 
Is there anything I can do to get out of this and even boot to a 640 x 480 resolution. Rebooting just produces the same garbled screen. Thanks a lot.

---

### Post by anewguy on 2008-12-04
The garbled screen is from X - you can still access a terminal window but you have to hold down ctrl/alt and press F1, then log in.  You won't be able to run anything graphical from there, but you can go in and either restore xorg.conf from the backup (hopefully you made one, or look for an xorg.conf~ file).  You will need to "sudo cp <backup file name here> xorg.conf" while in the /etc/X11 directory, then type "sudo shutdown -r now" and the system will reboot.  See if that fixes your problem and post back if you need more help.

Dave ;)

---

### Post by Bill Mann on 2008-12-04
> **anewguy said:**
> The garbled screen is from X - you can still access a terminal window but you have to hold down ctrl/alt and press F1, then log in.  You won't be able to run anything graphical from there, but you can go in and either restore xorg.conf from the backup (hopefully you made one, or look for an xorg.conf~ file).  You will need to "sudo cp <backup file name here> xorg.conf" while in the /etc/X11 directory, then type "sudo shutdown -r now" and the system will reboot.  See if that fixes your problem and post back if you need more help.

Dave ;)
Thanks so much. Worked like a charm. I am so grateful.

---

### Post by sptrsn on 2008-12-05
Can you suggest an alternate method if I don't have a backup of the xorg.conf file?
I've done as you suggest. I'm in terminal, looking at the files in /etc/X11. I see a file xorg.conf. I don't see anything that looks like it would be a backup of that file.

Last night was my very first foray into anything Linux. I downloaded Ubuntu and installed it on one of my machines. 
One of the first things I did was attempt to increase the screen resolution, and all I get is essentially a white screen. 

I can just reinstall since it's brand new, but it would be nice to just be able to fix it, and perhaps be able to have a little higher resolution. 

Thanks for any help. 
Steve

---

### Post by nhasian on 2008-12-05
this may fix your screen problem.  from a shell prompt, type

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by sptrsn on 2008-12-05
I appreciate your response and learned a couple cool things as a result, but that command, while it mentioned the ability to modify video setting, only walked me through setting up the keyboard. 

I've gone through it a couple times and don't see anyway to affect video settings.

Is there something you can think of that I might be missing in light of the fact that I have a whopping 2 hours of linux experience. 

I think I'm going to do a "redo". Is there something you could point me to that would describe how to back up and restore settings (like resolution) so that I can recover from noobitis?

Thanks,
steve

---

### Post by cdmike2k8 on 2008-12-05
Try posting you xorg.conf file and we could see if we could change it.  ```
sudo nano /etc/X11/xorg.conf
``` will bring it up.
EDIT:
To back up your file, you could use the command ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```  That will make a copy of the file, but it won't help you until you fix the problem.  Its not time to give up yet.

---

### Post by sptrsn on 2008-12-05
I feel like a moron. I have managed and maintained 20-30 pcs at my company for the last, well, forever. I run Server 2003 with Exchange, BES, as well as a couple other network based database apps. I've built and rebuilt probably more than 100 computers. I've built several websites. I'm maintaining 5 instances of SugarCRM on remote hosts for my company and a few others. I consider myself reasonably saavy around computers. All my friends call me when they need help. 

But I feel completely stupid right now. I think this is why I have put this Linux exploration off for so long. Ok, I got that off my chest...

I can bring up that file using your command. 
I'm looking at the screen and thinking to myself..."now what?"
I can't access the web on that computer since I can't get into the graphical interface. I never installed a printer on that machine. I haven't figured out how to navigate there from this machine to fetch the file. I'm considering rekeying that file for you so you can see it. I don't know how else to do it. I could take a picture. How moronic is that?
I seriously can't think of how to get that file for you.
I hear you laughing. Go ahead. it's ok. I can take it.

---

### Post by slinkey1981 on 2008-12-05
> **sptrsn said:**
> I feel like a moron. I have managed and maintained 20-30 pcs at my company for the last, well, forever. I run Server 2003 with Exchange, BES, as well as a couple other network based database apps. I've built and rebuilt probably more than 100 computers. I've built several websites. I'm maintaining 5 instances of SugarCRM on remote hosts for my company and a few others. I consider myself reasonably saavy around computers. All my friends call me when they need help. 

But I feel completely stupid right now. I think this is why I have put this Linux exploration off for so long. Ok, I got that off my chest...

I can bring up that file using your command. 
I'm looking at the screen and thinking to myself..."now what?"
I can't access the web on that computer since I can't get into the graphical interface. I never installed a printer on that machine. I haven't figured out how to navigate there from this machine to fetch the file. I'm considering rekeying that file for you so you can see it. I don't know how else to do it. I could take a picture. How moronic is that?
I seriously can't think of how to get that file for you.
I hear you laughing. Go ahead. it's ok. I can take it.

It's not moronic, most of us made the move to Linux from either Windows or a Mac OS, so we've all been through the "Oh no, what the heck am I doing" part of it.

If you can take a picture of the xorg.conf with a camera and post it, it will help people help you. Don't feel ashamed using the tools that will work and allow you to learn, breaking things in Linux is the only reason I have learned anything.

---

### Post by sptrsn on 2008-12-05
Thanks for your patience and kindness.
I've attached what I think is the orginal xorg.conf file. 
After running that one command several times, there are several backup versions. This is the oldest. 

Thanks

---

### Post by cdmike2k8 on 2008-12-05
It looks like it has not been configured for the computer.  Would it happen to be an nvidia card, cause then you could possibly use nvidia configuration tools.  ```
 sudo apt-get install nvidia-setting nvidia-xconfig
``` would install them if you can use them (nvidia only).  I would try running each of them and see if they help.  Will require sudo since editing the config file.  Let us know how it goes.

---

### Post by sptrsn on 2008-12-05
I'm re-installing.
However, I am still curious...
Is there a specific set of files that I could back up that will allow me to recover from stupidity? (if it were only that easy in real life)
I know I need xorg.conf. 
Any others??

Thanks again for your help.

---

### Post by anewguy on 2008-12-05
Well, in the case of modifying xorg for any reason, be sure to just back up that file first.  when I have a "clean" file that works, the first thing I do is:

(in a terminal window)

cd /etc/X11

sudo cp xorg.conf xorg.conf_good_mmddyy

That way I have a date stamped file of a known good configuration.  One of the biggest differences between Windows and Linux is there is no system registry, so you don't have to create any backup points.  It is wise to watch what gets installed by an update or installation of a new app, and see if any "normal" system files are being changed so you know where to look if an error occurs.  Removing packages normally will usually get rid of any of the "hooks" it may have installed.

BTW - if you are using a Nvidia or ATI card, you may also want to try envy (or envyng if 8.04 or 8.10) - it's available via synaptic package manager.  Run it, and it will automatically install the correct driver for your video card and create an updated xorg.conf file for you.  Since 8.04, the xorg.conf file has been delivered in a minimum state - some say that the handling is done elsewhere, but I know that in my case I used envyng which installed the NVidia driver and updated my xorg.conf so that my dual displays work.

Let us know if we can be of more help.  

Dave ;)

---

