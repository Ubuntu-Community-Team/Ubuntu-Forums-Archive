---
title: "Help with problems booting up"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by cageycarrot on 2011-02-12
hey guys im new here but I need help with a problem booting up. I have just installed ubuntu on a clear/nothing on HDD old machine year:2002 ,2Ghz ,512mb RAM and 40gb HDD. I installed it then when it told me to restart I did and then when it came back on you can log in but after login you get stuck in the purple/multi colour screen. The password is right etc. Also the CD drive won't read the installation CD now. the Cd I installed it with is proffesinally burned so no problem there. What is happening?

---

### Post by Rubi1200 on 2011-02-13
Hi and welcome to the forums :-)

This might be a graphics issue; what card do you have installed?

---

### Post by cageycarrot on 2011-02-13
I do not know. Can you find out from the BIOS/Setup screen before the OS launches? If so how? Any help greatly appriecated.
CageyCarrot

---

### Post by Rubi1200 on 2011-02-13
I think you can; been so long since I entered BIOS that I really don't remember now. Depending on the machine, it is usually accessed with something like F2, F12, Esc, Del.

What you can also try is the following:

as the computer boots hold down Shift to bring up the GRUB menu. When the entry for Ubuntu is highlighted press "e" to edit.

Navigate using the arrow keys and find the line that ends with > quiet splash

Remove this and type nomodeset instead then "Ctrl" + "x" to boot.

If this gets you in, go to Applications > Accessories > Terminal and run this command and post the output here please:

```
lspci | grep VGA
```

---

### Post by cageycarrot on 2011-02-13
I have done the nomodeset thing but now I am into some sort of command system? Also I tried typing this into it "applications>accessories>terminal" but it says applications: command not found. Where to now?

---

### Post by Rubi1200 on 2011-02-13
> **cageycarrot said:**
> I have done the nomodeset thing but now I am into some sort of command system? Also I tried typing this into it "applications>accessories>terminal" but it says applications: command not found. Where to now?
I don't understand. If you followed the instructions above you should have been able to boot into the desktop.

Try this:
start the process again and when you get to the log in screen, choose safe graphics mode before you enter your password.

Does this help?

---

### Post by cageycarrot on 2011-02-13
Is safe graphics mode the same as safe mode?

---

### Post by Rubi1200 on 2011-02-13
> **cageycarrot said:**
> Is safe graphics mode the same as safe mode?
Not really. On Ubuntu, you have the regular entry to boot, but also a recovery mode entry (this is more like safe mode so to speak). Safe graphics mode is exactly that; it should allow you to boot into the desktop so you can figure out what is going on. Basically, it provides limited functionality i.e. just the basics but good enough to get to the terminal and run the command I posted.

---

### Post by cageycarrot on 2011-02-13
Hey thanks for your help I think the computer is now a lost cause because it just quit. It was only $20 anyway. I really appreicate your help.

---

### Post by Rubi1200 on 2011-02-13
Quit as in the hard-drive died? Can you use a LiveCD to boot the computer?

If yes, go to System > Administration > Disk Utility and check the SMART status.

---

### Post by cageycarrot on 2011-02-13
Update: we are back in action power cut feigned the crash. The CD drive worked for installing the OS off the live CD then it died and won't recognise any disc is in it. so I have a feeling that I am in a hole that keeps getting deeper.

---

### Post by Rubi1200 on 2011-02-13
But can you boot Ubuntu now without the CD?

If the Ubuntu CD won't get you going, try Slax just to boot as a LiveCD and then we can try and take it from there:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

---

### Post by cageycarrot on 2011-02-13
The CD drive has quit and now won't read any disc. This happened before installing ubuntu where it would take a few restarts to read now it is dead. I have always been booting ubuntu from the HDD.

---

### Post by cageycarrot on 2011-02-14
Ok I have found out what graphics car I have. It is a nVidia geforce4 MX 440 AGP 8x

---

### Post by cageycarrot on 2011-02-15
Ok istalled new cd drive and then re-installed it and now it works fine.

---

### Post by Rubi1200 on 2011-02-16
Excellent! Glad you got things sorted out in the end.

Enjoy :-)

---

