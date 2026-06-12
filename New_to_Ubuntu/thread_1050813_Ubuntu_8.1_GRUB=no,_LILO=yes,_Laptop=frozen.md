---
title: "Ubuntu 8.1: GRUB=no, LILO=yes, Laptop=frozen"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by stadubu on 2009-01-26
Hi all
I'm new to Linux and Ubuntu. I go straight to the point:
Installed Ubuntu 8.10 in an older laptop from a CD.

Issue 1)
During installation, the GRUB did not install (remember some error that it won't boot etc.). However, after that it did fine: The LILO installed fine, and the machine was booting fine.


Issue 2 and final)
Saw the little arrow on top of the screen, saying something like "there are 435 items for update". so I went for it. After some activity, the screen went black: then no activity, seemed dead. Tried to Restart the machine ...but...tt comes to the Username screen, and then just freezes, it stays there for ever (it won't display input from keyboard, mouse mointer won't move ..its frozen.).

So, guys, whats wrong here? Should I try to re-install everything from scratch? and then, how would I do the updates then? Can I boot before I get to the 'username' screen? and then what?

Thanks
stad-ubu

Info: the laptop is older, 20G HD, totally dedicated to Ubuntu (no dual boot, no fancy stuff)

---

### Post by kestrel1 on 2009-01-26
What CPU & RAM do you have?
You may be better off with an older version of Ubuntu or even Xubuntu, as this runs better on older hardware.

---

### Post by halovivek on 2009-01-26
Could you please post the full configuration of your Laptop?
how much hard disk, Ram , video card details?

---

### Post by stadubu on 2009-01-26
Hi again
*laptop is a Toshiba 8100, Pentium III Coppermine (650MHz cpu). 
*RAM is small 256, but the little it ran, had no problem
*HD is a Toshiba 20Gb - I think now there is about 15Gbytes left.
*video: sorry can't recall, but I think was running on 1024x768 last time I remember.

-somehow I managed to getoff the gui frozen screen (pressed Alt + > or something), and I managed to login into terminal (console) mode. so I'm logged in, but not GUI.

I'm tempted to blast away this darn thing, but I'll give it a chance, if you guys help on this.

thanks

---

### Post by kestrel1 on 2009-01-26
With that spec I would be more inclined to try out Xubuntu. The following link shows the min spec. 
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
The recommended minimum is above your current spec for Ubuntu, but Xubuntu should run fairly well:
[http://xubuntu.org/](http://xubuntu.org/)

---

### Post by stadubu on 2009-01-26
Hi thanks for the reply, I give it a go.

ir really looked cool, and it reminded me by old unix days..
but just before I do that...is there a way to start off the gui from command line? for some reason I think it won't recognise the mouse (or the drivers got screwd up or something).

thanks

---

### Post by kestrel1 on 2009-01-26
To get the GUI (X server) to start from a command line: ```
startx
```
This will only work if X server is installed & there are no problems.

---

### Post by stadubu on 2009-01-31
thank you Kestrel1. I have reinstalled ubuntu. Now it works fine. Seems that I have to do the updates from the console though, so it won't get stuck.

---

### Post by kestrel1 on 2009-02-01
Did you think of trying Xubuntu? This does run much quicker on older hardware.

---

