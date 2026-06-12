---
title: "xfix broke my computer"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by robbiehoodyso on 2009-01-29
hello,

my laptop was running slow and someone sugested doing xfix in recovery mode. once i selected it and restarted it worked fine up to right after the ubuntu loading screen. after that the screen blinks black a few times and i can hear the login promt noises, just no graphics. i can log in blindly and hear the login noises. so the compter is running fine.

when i hook it up to external monitor it works fine. i have tried reinstalling ubuntu and nothing seems to work.

thanks for any help,


robbie

---

### Post by stoogiebuncho on 2009-02-01
You could always try 

```
dpkg-reconfigure xserver-xorg
```
Boot into recovery mode and get to the command line and enter that.

If that doesn't work the problem might take a little more figuring out.  If you boot from a live CD, does everything work properly?

---

### Post by DaLinel on 2011-08-13
I have the same or a very similar problem, and i think this is the right post.
My problem is this: xfix broke the hability of my PC to use X.org graphical enviorement [IMG]http://www.linuxforums.org/forum/images/smilies/icon_sad.gif[/IMG]
Not only it did messed up using X.Org with my (hard disk) []("http://www.linuxforums.org/forum/#")Ubuntu but if i use an from a CD (LiveCD), the XOrg of that LiveCD OS also doesn't work !!!
 
But VESA works good.
So the solution that i found is to always boot my system in VESA mode or in "Safe graphics" mode.
If i do that, i can enter the graphical enviorement and everything works great.
 
I have tryied out some solutions to fix my graphic card, but none work.
I may have accidentally ovewritten the original /etc/X11/xorg.conf file that was backed up by xfix, so the initial working xorg.conf file is gone.
But that doesnt matter because i decided to delete all of my Ubuntu partition.
 
By now i dont have the same OS installed on that PC, but still, the X.Org problem persists! Any Linux OS that i use in that PC, i have to be carefull to boot it in VESA mode.
(by VESA mode i mean "Safe graphics mode", i don't know if is the same but that is what i mean)
 
 
My PC (laptop) is a Asus and my graphical card is: Nvidia 8600M GS with 256MB of Dedicated Cache.
 
My output:
# sudo lspci | grep -i vga
01:00.0 VGA compatible controller: GeForce 8600M GS (rev a1)
 
 
(This is just a suggestion, but from my point of view the problem lies in the Dedicated Cache memory of the Graphical card.
Maybe if i could erase the content of that memory maybe that would do trick.
I say this because the X.Org problem is portable to any Linux OS that i use from a LiveCD  )
 
In need of help
 

One more note;
The ubuntu OS that my Asus PC used to have was a Ubuntu Hardy 8.04.
My X.Org and all the graphical thing was working right before i run xfix.
The way that i run xfix was by enterering the Grub option "Ubuntu 8.04 (recovery mode)" and then on the Recovery Menu i choose the "xfix Try to fix X server".
I don't know if it only runs xfix but i am assuming that is what this option does.
After choosing that option it simply destroyed the ability of my graphical card to use any X.Org. therefore any linux OS...

---

