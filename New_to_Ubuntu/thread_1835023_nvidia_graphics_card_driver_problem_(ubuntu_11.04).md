---
title: "nvidia graphics card driver problem (ubuntu 11.04)"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by MilesEpps on 2011-08-28
hello,

i have a serious problem, when i install the nvidia graphics card driver (current) and i restart my computer,when it turns back on the screen freezes. i also tried removing the default driver that's installed automatically but this just gave me the background with nothing on it not even unity.

if anyone can help please do.

Miles Epps

---

### Post by angryfirelord on 2011-08-28
What kind of video card is it?

---

### Post by MilesEpps on 2011-08-28
nvidia geforce 7300 se i think

---

### Post by kyletstrand on 2011-08-28
Did you automatically install the driver using the additional drivers option?

If so, maybe try installing manually.  Drivers available here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Sorry if that's the way you did it before, you just didn't mention the method used.

---

### Post by MilesEpps on 2011-08-29
i used the additional drivers thing

---

### Post by MilesEpps on 2011-08-29
which driver do i choose? (i'm a bit of a noob sorry)

---

### Post by MilesEpps on 2011-08-29
extra info:

with what i did before i had to reinstall ubuntu because i couldn't use my computer at all, i could move the mouse around, but i couldn't click and drag or open files or anything

---

### Post by fractalman on 2011-08-29
I have an nvidia 8400gs.   once you've installed ubuntu and run the updates you should be able to use the additional drivers option System > Administration > Additional drivers.  this worked for me but if you don't want to do it this way you can use the synaptic package manager,  System > Administration > Synaptic package manager,    Then type nvidia-current in the searchbox, mark the package and click apply.  

i have found though that using the nvidia drivers causes problems with 'plymouth'  . i don't actually know what plymouth does as i'm still a noob myself but it seems to only affect the boot up and shut down screens, they appear as the wrong size

---

### Post by MilesEpps on 2011-08-29
ok i just install the driver through synaptic package manager, but now it's saying "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." i ran nvidia-xconfig as root but it didn't do anything. i am very confused. please help

Miles Epps

---

### Post by realzippy on 2011-08-29
*i ran nvidia-xconfig as root but it didn't do anything.*

So post the commands output.If id did anything,it will have returned an error

```
sudo nvidia-xconfig
```

Edit.

Just see your card is [blacklisted for unity]("ttp://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity/37686#37686"),but the classic mode and unity-2d should work.

---

### Post by MilesEpps on 2011-08-29
terminal says this when i do that: Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

but i still get the error message on the nvidia x server settings

---

### Post by realzippy on 2011-08-29
So nvidia-xconfig worked.
Did you reboot after running it?

---

### Post by MilesEpps on 2011-08-29
no, im a tard aren't i

---

### Post by MilesEpps on 2011-08-29
i'll do that now, but i think my bios is screwed up because i can't access the bios options and when i start my computer if i dont press f3 it goes all black and doesn't do anythig

---

### Post by MilesEpps on 2011-08-29
same thing as the first time :(](*,)

---

### Post by darknuts on 2011-08-29
I'm currently having a problem with my Nvidia card. Im pretty sure its related to my new kernel. You should try 'sudo apt-get install nvidia-current' and post the results.

---

### Post by MilesEpps on 2011-08-29
just found out that my card isn't unity supported, what do i do

---

### Post by MilesEpps on 2011-08-29
SOLVED: for my card you need to install the 173

---

### Post by realzippy on 2011-08-29
> **MilesEpps said:**
> just found out that my card isn't unity supported, what do i do


yep,I wrote this in post #10 already.
anyway,you could un-blacklist it:

[http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity/37686#37686](http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity/37686#37686)

---

