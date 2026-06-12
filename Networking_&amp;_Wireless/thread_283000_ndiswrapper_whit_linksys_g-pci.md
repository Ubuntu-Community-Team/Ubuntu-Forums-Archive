---
title: "ndiswrapper whit linksys g-pci"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by Erik. on 2006-10-23
Hi,
i have installed ubuntu 6.6 and i have kernel k7
Now did i installed all the build-essentail 11.1
I want to install ndiswrapper and i do:
1) tar zxvf ndiswrapper-1.8.tar.gz
2) cd ndiswrapper-1.8
3) make uninstall
4) make
Then it goed wrong:
```

root@ejp:~/Desktop/ndiswrapper-1.8# make
make -C driver
make[1]: Map '/root/Desktop/ndiswrapper-1.8/driver' wordt binnengegaan
Can't find kernel sources in /lib/modules/2.6.15-27-k7/build;
  give the path to kernel sources with KSRC=<path>             argument to make
make[1]: *** [prereq_check] Fout 1
make[1]: Map '/root/Desktop/ndiswrapper-1.8/driver' wordt verlaten
make: *** [all] Fout 2

```

When i do make install i get the same error so i can not install ndiswrapper...
i am stuck here
how can i make a solution for this?

I have a linksys WMP54G pci
I also have a linksys router WRT54G Firmware Version: v3.03.6.
To connect whit the card i need a key so other people can not internet free at us...
I know my key ect.. 
 
Could someone please help me whit this problem...

---

### Post by Malakia on 2006-10-23
The problem is ndiswrapper can't find the link to your kernel. You have two choices, download the kernel source from synaptic or compile a new kernel. There is an excellent guide in the How-to section to compile the 2.6.18 kernel. I tried it and know that it works.

---

### Post by Erik. on 2006-10-24
Hi,
i find another way to install nidwrapper!
Use the program automatrix.
Now do i have installed ndiswrapper and many tools of automatrix.
Now when i go to mij menu i see a program named Windows wireless drivers.
Whit that program i can install drivers...
I have installed the driver and i have seen whit ndiswraper that my hardware is present.
What do i need to do now to use my wireless card and to activate it?
When i go to network i see as first option wireless card and it has the name eht0 and it is not active.
When i pres activate i get an error:Could not activate eth 0
please look if your options are correct.
and the computer correct is connected to this network.
How to fix that error?

---

### Post by Erik. on 2006-10-25
Where can i find that howto?
i try it and i hope it will work...

---

