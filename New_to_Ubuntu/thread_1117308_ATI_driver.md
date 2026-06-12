---
title: "ATI driver"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by djk21108 on 2009-04-05
Hi, I'm currently using FGLRX driver for my Mobility x1400 graphics card.  It seems to be turned on, but my performance is still really slow, especially with some of Ubuntu's flashy options turned on.  

What can/should I do?  New drivers, different settings, what?

---

### Post by Zero Prime on 2009-04-05
You could try the ATI driver from their website.  Its the only one I use and it works great.

Waiting for the inevitable switch to Nvidia post :popcorn:

---

### Post by djk21108 on 2009-04-05
Any other ideas?

---

### Post by jenova_skill on 2009-04-05
I have mobility x1250 The only driver that works for me is one from ATI site.

---

### Post by djk21108 on 2009-04-05
Ok, I'm very shitty with downloading stuff not from repositories.  Is there anyone that can explain how to install stuff from ATI's website.

---

### Post by RedSingularity on 2009-04-05
Did you go to the site and download the package for your Video card?

---

### Post by keypox on 2009-04-05
ATI driver for 4800s suck.  Sleep/Hibernate doesnt work, bad tearing... hope a fix comes soon :(

go to ati's website they have install instructions very easy, but you need to do sudo before most of the commands.

---

### Post by keypox on 2009-04-05
sudo sh ./ati-driver-installer-9.2-x86.x86_64.run
follow promts 
sudo /usr/X11R6/bin/aticonfig --initial

---

### Post by djk21108 on 2009-04-05
> **keypox said:**
> sudo sh ./ati-driver-installer-9.2-x86.x86_64.run
follow promts 
sudo /usr/X11R6/bin/aticonfig --initial

When i tried

sudo sh ./ati-driver-installer-9.2-x86.x86_64.run

It said it couldn't find the file.  It's on my desktop, sorry I really just don't know whats going on.

---

### Post by kdreimiller on 2009-04-05
aren't they up to 9.3?  i think thats what i just installed.  it works a LOT better than the previous releases. i have a radeon 3100 on a toshiba satellite

---

### Post by djk21108 on 2009-04-05
I just really need someone to explain what to do with this .run file on my desktop.

---

### Post by kdreimiller on 2009-04-06
whats the exact name of the file?

the ati install instructions from their website are spot on

---

### Post by djk21108 on 2009-04-06
I'm really having a lot of trouble with this.  I can't uninstall the old drivers and I can't install the new ones with the commands they're giving me.

Help!!

---

### Post by CLomax on 2009-04-06
Did you change directory to the desktop?

```
cd Desktop
```
N.B: Capital letter D matters.

Afterwhich, run the commands given in the posts above.

```
sudo sh ./ati-driver-installer-9.2-x86.x86_64.run
```

Follow the prompts.

```
sudo /usr/X11R6/bin/aticonfig --initial
```

---

### Post by djk21108 on 2009-04-06
> **CLomax said:**
> Did you change directory to the desktop?

```
cd Desktop
```
N.B: Capital letter D matters.

Afterwhich, run the commands given in the posts above.

```
sudo sh ./ati-driver-installer-9.2-x86.x86_64.run
```

Follow the prompts.

```
sudo /usr/X11R6/bin/aticonfig --initial
```

Alright CLomax yours helped.  I was able to use the installer with your help.  As for the second command, this is what it spit out when it was done,

Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0


Is this what I want?

---

### Post by kdreimiller on 2009-04-06
i think thats the message i got

type: fglrxinfo
in the terminal and see what it says

you can also do: glrxgears
to see the open gl running with a nifty display and it'll tell your framerate

---

### Post by CLomax on 2009-04-06
> **djk21108 said:**
> Alright CLomax yours helped.  I was able to use the installer with your help.  As for the second command, this is what it spit out when it was done,

Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0


Is this what I want?

Looks good to me. I didn't install my driver through this method so I'm not sure about the ins and outs of it.

Essentially, those messages are telling you that it found the device, added its details to the X configuration file and saved a backup in case something didn't go quite right.

If your graphics became unusable after this or you'd like to try installing them again for whatever reason; press CTRL + ALT + F1 and run the following commands:

```
cd /etc/X11
mv xorg.conf.fglrx-0 xorg.conf
```

This replaces the faulty configuration file with the previous one.

---

