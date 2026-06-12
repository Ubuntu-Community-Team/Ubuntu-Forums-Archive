---
title: "Booting into Ubuntu Messed Up"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by magicbullet077 on 2011-03-10
I am dual booting Ubuntu (10.10 or something like that) and windows 7. In my boot manager I can choose "Ubuntu, with Linux 2.6.35-27-genric-pae" or "Ubuntu, with Linux 2.6.35-25-genric-pae" to get into Ubuntu. I always used to use the first option "Ubuntu, with Linux 2.6.35-27-genric-pae" which would take me directly to my desktop. Now when I choose this option it takes me to a black login screen and I can't do much from there. However the other option "Ubuntu, with Linux 2.6.35-25-genric-pae" does take me directly to the desktop as I would like. I would like to fix the first option so that it works as before and takes me directly to my desktop. I am very inexperienced with Linux so any help would be appreciated. Thanks.

---

### Post by acrazyplayer on 2011-03-10
To fix it could be a struggle so I say you just remove the higher up kernel and use the bottom one since it works fine.

There are not many advantages to using a newer kernel unless you specifically need to or if there is a security vulnerability in the older ones, but you should be fine. 

To uninstall the newest kernel you can use a nifty little program called "ubuntu tweak" just look it up and you'll find it, after installing it you will find it in the menu at "applications --> system tools --> ubuntu tweak"

then you go to "package cleaner --> clean kernels"

to remove them you first have to unlock it by the "unlock" button in the bottom right then just select to remove anything with the number of the kernel that doesn't work, chances are it will be everything in the "clean kernels" that can be safely removed.

---

### Post by Rubi1200 on 2011-03-10
Hi and welcome to the forums magicbullet077 :-)

It sounds like an upgrade that did not work too well which is why it is always a good idea to have at least one older kernel for troubleshooting purposes.

I suggest 2 things:

1. post information about the specifications for the computer, especially RAM and graphics card

2. boot into the older kernel and run these commands one at a time (if there are errors let us know)

```
sudo apt-get install -f

sudo dpkg --configure -a

sudo apt-get update

sudo apt-get upgrade
```

This might fix the problem, but there are no guarantees.

---

### Post by magicbullet077 on 2011-03-10
Hello, first of all I did start noticing this problem after using the update utility as you seem to have suspected.

Information about my computer:
Model: Sony VAIO (VPCF111FX)
Ram: 4GB DDR3 1333Mhz(I don't know the model)
Video: Geforce 310M
CPU: i7 Q720

I ran the suggested commands. The only command that seemed to do anything was apt-get update. The others stated that there were 0 things to do. I did not see any errors. 

After trying the commands I did a reboot and nothing has changed with regards to the first boot option. The first option still boots to black login screen and the second goes to the desktop.

This scares me if the automatic update utility can screw up the OS like this (with no way to revert or repair). So should I "remove the higher kernel" as someone suggested? or can it still be fixed? I am skeptical about removing it because then I will only have one left, so if that one gets messed up I could be in real trouble. Any more advice would be great. Thanks.

---

### Post by Rubi1200 on 2011-03-10
Nope, we ain't out of options just yet which is why I wanted to know about the specs.

Try this at next boot:

when the first entry is highlighted press "e" to edit

navigate using the arrow keys and find the line that ends with quiet splash

add nomodeset so it looks exactly like this:

> quiet splash nomodeset

Then "Ctrl" + "x" to boot.

Let me know if this helps at all.

---

### Post by magicbullet077 on 2011-03-10
I tried "quiet splash nomodeset" followed by ctrl-x.

It did not change anything. Boots same as before. When booting it shows a screen that says Ubuntu 10.10 with a few dots under it, after a few seconds it goes to a black login screen.

Thanks for the suggestions, anything else I can try?

---

### Post by Rubi1200 on 2011-03-10
Do you have the entries for Recovery Mode on the GRUB menu?

If yes, choose the one for the kernel in question, drop to the root command prompt and try the following;

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
```

Then, reboot.

If you don't have recovery mode enabled, use the same procedure as before to edit the entry but this time type single after quiet splash instead then "Ctrl" +"x" to boot. This should also bring you to the option to choose a command prompt and then run the commands above.

---

### Post by magicbullet077 on 2011-03-10
Success!!! 

The commands have fixed my issue. In the process I seem to have lost my video driver as my resolution is now much lower than before.

Now to replace the video driver. The first time I installed the video driver I used the built in utility and it screwed everything up and I had to re-install the OS. After a clean install I downloaded the video driver from the Nvidia website and installed it manually with some help from the internet. It was kind of a hard process though. (this all happened about a month ago)  

What is your advice on installing the video driver this time around? Thanks so much for helping me out.

---

### Post by Rubi1200 on 2011-03-10
Great news :-) A step in the right direction.

I don't use NVIDIA, but read these links carefully and hopefully it will help:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

