---
title: "Graphics Card problems"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by Touchyfoil on 2011-04-15
I have tried installing ubuntu on my computer and successfully install it. I can use it when i switch my primary card to onboard but when i change it back to pci it just goes to black screen and shows nothing. I was wondering if anyone can help me with my problem. Thank you in advance.

---

### Post by rosencrantz on 2011-04-15
Can you post your system specs in detail? Is this hybrid graphics with a BIOS switch?

---

### Post by Touchyfoil on 2011-04-17
My computer is a hp pavilion a1113-w. Pentium 4 2.93Ghz, 2.5Gb Ram, Main os is XP, my graphics card is a Nvidia Geforce 8400gs pci not pci express. If there is anything else you need to know please tell me.

---

### Post by Skaggz on 2011-04-17
I know this might sound like a stupid question, but it does happen.

Are you remembering to move your monitor cable down to your graphics card from the onboard port when you switch?

---

### Post by Touchyfoil on 2011-04-17
> **Skaggz said:**
> I know this might sound like a stupid question, but it does happen.

Are you remembering to move your monitor cable down to your graphics card from the onboard port when you switch?

It is always on the dedicated card it is what i use on windows. I can use ubuntu if i have it on my onboard card but not when i switch it to my dedicated.

---

### Post by K_45 on 2011-04-17
What happens when you disable the onboard GPU in the BIOS, then boot the live CD connected to the dedicated card?

---

### Post by Touchyfoil on 2011-04-17
> **K_45 said:**
> What happens when you disable the onboard GPU in the BIOS, then boot the live CD connected to the dedicated card?

The screen is just black but i can type stuff it is not in the tty1 mode either its just a black screen that i can type

---

### Post by K_45 on 2011-04-17
Can you try the live cd of Ubuntu 11.04, the latest beta?

---

### Post by Touchyfoil on 2011-04-17
> **K_45 said:**
> Can you try the live cd of Ubuntu 11.04, the latest beta?

I will if you can give me the link to download it.

---

### Post by K_45 on 2011-04-17
Link:

[http://mirror.anl.gov/pub/ubuntu-iso/CDs//natty/](http://mirror.anl.gov/pub/ubuntu-iso/CDs//natty/)

---

### Post by Touchyfoil on 2011-04-17
> **K_45 said:**
> Link:

[http://mirror.anl.gov/pub/ubuntu-iso/CDs//natty/](http://mirror.anl.gov/pub/ubuntu-iso/CDs//natty/)

ok downloading i will let you know when it is done. Do you happen to have skype this might be easier that way?

---

### Post by K_45 on 2011-04-17
No, no Skype.

---

### Post by Touchyfoil on 2011-04-17
> **K_45 said:**
> No, no Skype.

oh ok well i will just reply on here when it is done shouldn't be too long i have downloaded 200mb already

---

### Post by K_45 on 2011-04-17
Takes around 5 - 10min for me, depending on the mirror.

---

### Post by Touchyfoil on 2011-04-17
> **K_45 said:**
> Takes around 5 - 10min for me, depending on the mirror.

ok its done ill mount it and see how it does

---

### Post by Touchyfoil on 2011-04-17
nope same thing

---

### Post by K_45 on 2011-04-17
Try here:

[http://ubuntuforums.org/showthread.php?t=1716468](http://ubuntuforums.org/showthread.php?t=1716468)

---

### Post by Touchyfoil on 2011-04-17
> **K_45 said:**
> Try here:

[http://ubuntuforums.org/showthread.php?t=1716468](http://ubuntuforums.org/showthread.php?t=1716468)

i have tried something similar to that i searched google before posting when i installed a driver it just went to tty1 mode nothing i could do. Ubuntu just doesnt recognize my card for some reason it didnt detect my old card either the ati radeon x1300

---

### Post by K_45 on 2011-04-17
But did you try the nomodeset option?

---

### Post by Touchyfoil on 2011-04-17
> **K_45 said:**
> But did you try the nomodeset option?

Yup

---

### Post by K_45 on 2011-04-17
Boot ubuntu with the integrated GPU and leave the PCI connected. If that works open a terminal and type

```
lspci | grep "VGA"
```

What is the output?

---

### Post by Touchyfoil on 2011-04-17
> **K_45 said:**
> Boot ubuntu with the integrated GPU and leave the PCI connected. If that works open a terminal and type

```
lspci | grep "VGA"
```

What is the output?

This is what i got

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
03:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)

---

### Post by K_45 on 2011-04-17
Well its recognized. Try this:

```
gksu gedit /etc/modprobe.d/blacklist.conf
```Then scroll to the bottom and add on separate lines

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

Save and shutdown. Then disable onboard, and boot with the 8400GS. If that doesn't work we'll try something else . . .

---

### Post by Touchyfoil on 2011-04-17
Nope didn't work

---

### Post by K_45 on 2011-04-17
Try this Xorg file:

```
cd Downloads
``` (or where you put the file).

```
mv xorg.txt xorg.conf
```

```
sudo cp xorg.conf /etc/X11/
```

---

### Post by Touchyfoil on 2011-04-17
> **K_45 said:**
> Try this Xorg file:

```
cd Downloads
``` (or where you put the file).

```
mv xorg.txt xorg.conf
```

```
sudo cp xorg.conf /etc/X11/
```

what file? Nvm

---

### Post by Touchyfoil on 2011-04-17
> **K_45 said:**
> Try this Xorg file:

```
cd Downloads
``` (or where you put the file).

```
mv xorg.txt xorg.conf
```

```
sudo cp xorg.conf /etc/X11/
```

tyler@tyler-PX744AA-ABA-a1113w:~$ cd Desktop
tyler@tyler-PX744AA-ABA-a1113w:~/Desktop$ mv xorg.txt xorg.conf
mv: cannot stat `xorg.txt': No such file or directory
tyler@tyler-PX744AA-ABA-a1113w:~/Desktop$ sudo cp xorg.conf /etc/X11/
tyler@tyler-PX744AA-ABA-a1113w:~/Desktop$

---

### Post by K_45 on 2011-04-17
Where did you put the .txt file?

---

### Post by Touchyfoil on 2011-04-17
my desktop

---

### Post by K_45 on 2011-04-17
What does

```
ls Desktop
```

give?

---

### Post by Touchyfoil on 2011-04-17
Could you do remote desktop viewer?

---

### Post by K_45 on 2011-04-17
No. Does the file come up?

---

### Post by Touchyfoil on 2011-04-17
tyler@tyler-PX744AA-ABA-a1113w:~$ ls Desktop
xorg.txt

---

### Post by K_45 on 2011-04-17
Then the command should work, rename it from the desktop, right click, rename to xorg.conf Then continue on.

---

### Post by Touchyfoil on 2011-04-17
tyler@tyler-PX744AA-ABA-a1113w:~/Desktop$ mv xorg.txt xorg.conf
mv: cannot stat `xorg.txt': No such file or directory

---

### Post by K_45 on 2011-04-17
Try if from the desktop:

```
gksu nautilus
```

Then navigate to Desktop, rename, then copy to the folder. Reboot. I'm off now till tomorrow, maybe someone else can help.):P

---

### Post by Touchyfoil on 2011-04-17
> **K_45 said:**
> Try if from the desktop:

```
gksu nautilus
```

Then navigate to Desktop, rename, then copy to the folder. Reboot. I'm off now till tomorrow, maybe someone else can help.):P

Well that didn't help i can't log onto ubuntu now.

---

### Post by K_45 on 2011-04-17
Scroll down to the boot options here before Ubuntu boots and enter vga=224:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

then we can reconfigure X.

---

### Post by Touchyfoil on 2011-04-17
alright ill try

---

### Post by Touchyfoil on 2011-04-17
mine does not look like that it looks like this one [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by K_45 on 2011-04-17
You can still press 'e'. Before we do that, can you boot a live CD, as I've modified the Xorg for a generic driver, rather than Nvidia specific, which should work fine. Try the steps previously and reboot. File is attached.

---

### Post by Touchyfoil on 2011-04-17
ok ill try

---

### Post by Touchyfoil on 2011-04-17
This is what it said in the terminal

ubuntu@ubuntu:~$ cd Downloads
ubuntu@ubuntu:~/Downloads$ mv xorg.txt xorg.conf
mv: cannot stat `xorg.txt': No such file or directory
ubuntu@ubuntu:~/Downloads$ sudo cp xorg.conf /etc/X11/
ubuntu@ubuntu:~/Downloads$

---

### Post by K_45 on 2011-04-17
Try

```
gksu nautilus
```and copy/rename it manually.

This is the new Xorg file, right?

---

### Post by Touchyfoil on 2011-04-17
ya new file it opened my root folder thing

---

### Post by K_45 on 2011-04-17
Right, rename xorg.txt to xorg.conf, then copy and overwrite to /etc/X11/

---

### Post by Touchyfoil on 2011-04-17
ok done i should reboot now right? All this will save to what since i just used the try ubuntu

---

### Post by K_45 on 2011-04-17
Move it to the installed filesystem, where you have installed Ubuntu, in should be on the left when you open up nautilus.

---

### Post by Touchyfoil on 2011-04-17
in the file system?

---

### Post by K_45 on 2011-04-17
Yes, /etc/X11/, where you installed Ubuntu before.

---

### Post by Touchyfoil on 2011-04-17
Error while copying "xorg.conf".
There was an error copying the file into /media/64116627-3ef3-49d8-b682-0747cd44db6f/etc/X11.
Error opening file '/media/64116627-3ef3-49d8-b682-0747cd44db6f/etc/X11/xorg.conf': Permission denied

---

### Post by K_45 on 2011-04-17
Run

```
gksu nautilus
```

and copy it to where you installed Ubuntu. This will give you permission.

---

### Post by Touchyfoil on 2011-04-17
> **K_45 said:**
> Run

```
gksu nautilus
```and copy it to where you installed Ubuntu. This will give you permission.

ok it worked

---

### Post by K_45 on 2011-04-17
Right, if it copied, reboot, with your Nvidia card installed, and onboard disabled. Result - ?

---

### Post by Touchyfoil on 2011-04-17
black screen where i can just type no change

---

### Post by K_45 on 2011-04-17
Type this

```
sudo dpkg-reconfigure xserver-xorg
```

choose vesa, then

```
startx
```

---

### Post by Touchyfoil on 2011-04-17
after a while some words popped up i took a picture [IMG]http://img819.imageshack.us/img819/3429/1000636c.jpg[/IMG]

---

### Post by K_45 on 2011-04-17
So what happened next?

---

### Post by Touchyfoil on 2011-04-17
As i post this my screen just went completely black
[IMG]http://img857.imageshack.us/img857/4303/1000637.jpg[/IMG]

---

### Post by K_45 on 2011-04-17
When this finishes post the final screenshot.

---

### Post by Touchyfoil on 2011-04-17
its just a black screen i didnt enter the stuff you told me to cause it is not the ubuntu command thing it is just a black screen [IMG]http://img402.imageshack.us/img402/3847/1000638p.jpg[/IMG]

---

### Post by K_45 on 2011-04-17
I'm out of ideas. You'll just have to use the onboard GPU.

---

### Post by Touchyfoil on 2011-04-17
> **K_45 said:**
> I'm out of ideas. You'll just have to use the onboard GPU.

alright well thank you very much for trying to help.

---

### Post by xd20 on 2011-04-26
I use the same graphics card.  No one could help me either.  Ubuntu is just going to have to fix it themselves.

---

