---
title: "Getting started whit unbutu wirless linksys-G pci"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by Erik. on 2006-10-20
Hi,
i always used windows but i wanted to try linux.
Frist i had Linux Fedora Core and tried to installed the Wireless driver for my Linksys-G pci adapter.
i need to buy a new cable to connect to the internet so i can try Linux but i wanted to use my Wireless card.
i have tried to install it but it does not work.

Now i am downloading The new version of Ubuntu 6.01
Now do i have a Linksys-G pci adapter and want to use it for internet so i do not need a cable.
My dad do not want that u use a cable:-? 

Now did i read some posts of people that have tried to install an driver and someof u it will work.
Now am i completly noob whit linux so i need your help:p 
i have read that i need to download ndiswrapper
i have found how to install:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

i also read that i needed to download the windows driver called:
wpc54g_v2_driver_utility_v2.zip
Into that zip file i needed the file: lsbcmnds.inf
Then i need to do somethings whit startup ect...

Now did i read one more thing and do not understand that
i need to do:
in gnome, goto networking and put your settings
What is gnome?? and how to get there and how to edit my settings?

i have found it at this forum and here is a link:
[http://ubuntuforums.org/showthread.php?t=5645&highlight=linksys+WPC54g](http://ubuntuforums.org/showthread.php?t=5645&highlight=linksys+WPC54g)

i have started this post because i do not that i get into tangle

i hope you understand my text because my english is not so well....

Gr, Erik...

P.s Maby this is a good time to make a spread for completly noobs so every step is typed so it must be working?

---

### Post by mozetti on 2006-10-20
You might get lucky and your card will work automagically after you install Ubuntu -- my Linksys WPC54G wireless card did. If your wireless car doesn't work, do some searching on these forums because the answer is already here.

Gnome is the desktop environment - the program that gives you a "Desktop" and a Graphical User Interface (GUI) - that is used in Ubuntu. Unlike Windows, GNU/Linux is a command-line (the dos window) operating system, and you install a Desktop Environment to give you the GUI. **K**DE, and **X**FCE are different desktop environments and correspond to **K**ubuntu and **X**ubuntu, respectively.

---

### Post by Erik. on 2006-10-20
Hi,
How to configure my network into ubuntu so i can use my linksys card? where to do that on the desktop or console?

---

### Post by Erik. on 2006-10-21
Hi,
I have now some other problems...
I have downloaded the new ubuntu 6.01 i have burned on a cd but it won't boot.
When i start windows and i look at the cd i see some .exe files 
When i start them i see that i can install firefox for windows etc...
how to make it so i can boot?
i have downloaded this one:
[http://releases.ubuntu.com/dapper/\](http://releases.ubuntu.com/dapper/\)
then the 64-bit PC (AMD64) desktop CD
i have burn it into a cd and i can explore it ect.. but it does not boot

Now did i installed ubuntu 5.10 because i have a cd of it that will boot.
i installed it on my hd whit windows.
so i have windows and ubuntu on the same disk.
Now after the instalation ubuntu asked me is i wanted that ubuntu installed some program that when i boot my pc that i can choose what i want to start ubuntu or windows.
i say yes

Now ubuntu was installed and i rebooted my pc.
after the bios i get an error: mbr error 1
why can i not choose ubuntu or windows?
i can now do nothing whit my pc.
Could someone help me please so i can run windows again and i can install ubuntu???

---

### Post by Erik. on 2006-10-21
Hi,
My windows and linux are now running again.
I want to install ndis wrapper but have the error:
```

root@EJP:~/Desktop/ndiswrapper-1.26# make install
make -C driver install
make[1]: Entering directory `/root/Desktop/ndiswrapper-1.26/driver'
Can't find kernel build files in /lib/modules/2.6.12-9-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Fout 1
make[1]: Leaving directory `/root/Desktop/ndiswrapper-1.26/driver'
make: *** [install] Fout 2
root@EJP:~/Desktop/ndiswrapper-1.26#

```
i am complte noob whit linux so what to do now?
i have looked but i can not find some explain how to do this...
How to update all my kernels?

please help me...

---

