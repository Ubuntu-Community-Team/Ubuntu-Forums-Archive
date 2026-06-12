---
title: "fresh install, no GUI ??????"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by 3dz on 2008-12-23
I just did a fresh install of Ubuntu studio 8.04.
When I booted the first time, there was no GUI login screen.
I successfully logged in commandline mode.  I tried to get a GUI, by typing in "startx", but that didn't work either. Does anybody know how I can get the GUI started in Ubuntu studio? :confused:

---

### Post by Coder543 on 2008-12-23
Ubuntu studio may inherently have settings turned on that are too powerful for your computer or are not supported by your computer natively. Try installing a regular version of Ubuntu. Also, startx might work but you should best try 

sudo gdm

to start the display manager.

---

### Post by krisfrajer on 2008-12-23
what happen when you typed startx?
Maybe problems with the video driver?

What type of video card do you have?

---

### Post by 3dz on 2008-12-24
Thank you for coming to my aid Coder543.
                                                                    I tried sudo gdm, but that didn't work either.  I think I found a workaround.  For some reason my computer doesn't seem to like a fresh install.  I had Ubuntu studio loaded in earlier versions.
When I went from 7.04 to 7.10 I upgraded.  I did that, now I'm upgrading to 8.04.  Because the computer I loaded it up on, doesn't have an Internet connection. I have a feeling I'm not getting all the updates.  But I do have a GUI now.
Thank you for your help. :)

---

### Post by 3dz on 2008-12-25
> [QUOTE]what happen when you typed startx?
Maybe problems with the video driver?

What type of video card do you have?[/QUOTE]

Hi kris,
              I  think you may be right about the video driver.  I can't seem to get to desktop affects to work.
When I typed in startx, I get back "command not found" :confused:
the video card I have is: EVGA 7200 pci express.
in the hardware information, it's showing that it is a 7300 and its saying it's just the PCI. :confused::confused:

---

### Post by obsrv on 2008-12-25
do you get internet connection? Try do this:

```
ping pirate.lt
```

If you get answer like network unreachable, then you dont have internet and solution is more complex, if you get answer that pinged packets gets back, then write this:

```
apt-get install xorg
```

Write here all the output if it does not work, I will help :)

---

### Post by nynoah on 2008-12-25
I know when I install the studio packages, I need to have a dependacy installed to run my proprietary drivers work.

---

### Post by 3dz on 2008-12-25
> do you get internet connection? Try do this: 

Hi obsrv,
          
 No, I don't have an Internet connection on that computer yet.  

That's a whole other issue.  I have a USB 727 modem, and have been struggling to get Ubuntu studio to recognize it.  I just read last night on this forum, where a guy got the software to work using wine. :)

---

### Post by 3dz on 2008-12-25
> I know when I install the studio packages, I need to have a dependacy installed to run my proprietary drivers work. 

What package was that? 
I really do think I'm having a driver problem.  Even on my last install of 7.10, I tried to enable the desktop effects, I would get this:

[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/enable_driver.png[/IMG]

I would click on enable driver, and get this:

[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/glx.png[/IMG]

I was thinking about running the install disk with wine. :confused:

---

