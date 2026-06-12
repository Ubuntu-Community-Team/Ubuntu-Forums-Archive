---
title: "Please save me a headache. Orinoco Gold"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by Tempest99 on 2008-05-03
Hi Everyone, 

Long time reader, first time poster.  Like the title, please save me a headache, I've been working on this for days with no progress.

I've just purchased an a Airstation WLI-PCM-L11G.  Which is a spinoff and should be the same as the Orinoco Gold.  Lately I have been pulling my hair out trying to get it to work.  

1. The card shows up in my wireless manager, but picks up no networks.  Does anyone know whats up with that?

I've tried downloading the drivers.  They were the Orinoco 0.15 patched drivers.  I downloaded them, but when I use the make command it tells me. 

```
make -C /usr/src/linux-headers-2.6.24-16-generic M=/home/tempest/Desktop/orinoco-0.15 KERNELRELEASE=2.6.24-16-generic modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
/home/tempest/Desktop/orinoco-0.15/Kbuild:34: *** Wireless extensions are not enabled.  Stop.
make[1]: *** [_module_/home/tempest/Desktop/orinoco-0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2

```

Long story short, wireless extensions are not enabled.  I've read different articles on wireless extensions, and have gotten nowhere.  

If someone points me in the right direction I will be so thankful.  Here is my iwconfig also.  It seriously looks like the driver is already installed.

```
eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.484 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Ill be checking this frequently.  Thanks everyone.

---

### Post by itix on 2008-05-03
Have you ./configured the driver?
Have you tried sudo make (the rest)??

If you do get it right, remember to also do sudo make install.

Sudo is a command that gives your user "super powers", but if you're clusmy with your powerful super power, you might brake stuff. Use it wisely :p
EDIT: I wonder if this last part really useful to you since you seam to be pretty handy with linux considering the iwconfig post...

---

### Post by Tempest99 on 2008-05-03
Hah, any help is really appriciated at this point.  Yeah, I'm familiar with sudo and all that jazz.  

It shows up, but doesn't roam or anything.... ughh help

---

### Post by itix on 2008-05-03
I understand your turmoil. I'm actually quite useless on wireless. I've been lucky in my wireless department and everything has just worked from scratch so I haven't learned anything about that department yet. I just know how to install things in the terminal thanx to trying (and succeeding) to set up a media server and a reciever.

I do hope someone who do know will find your thread soon. Good luck :)

---

