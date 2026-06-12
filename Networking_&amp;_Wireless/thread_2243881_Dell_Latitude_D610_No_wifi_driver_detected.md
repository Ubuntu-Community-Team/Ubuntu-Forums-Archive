---
title: "Dell Latitude D610: No wifi driver detected"
date: 2014-09-11
forum: Networking &amp; Wireless
---

### Post by christian40 on 2014-09-11
Hey guys im new here, never written one of this before.

i have a problem. i was running Windows 7 on my Dell latitude D610, but it always runs so slow. so i gave Linux Ubuntu 14.04 a try and i'm in love with it. its a thing that i have to get use to but i know i can do it. My problem is that i was gonna install linux side by side with windows 7 but it didnt or wasnt letting me do it. so i installed linux over windows 7. i have been on it for last 2 days. I been going around google for answers on how to get my wireless connect to work but nothing.

i went into the additinal drivers when i first installed and there was a driver for the wifi. i click on apply and it started to do it. when it finish it said that there was an error. so i tryed it again. this time it said installed but and error message pop up saying something went wrong. and now the driver doesnt pop on the additnal drivers and i have closed everything and even restarted my laptop. but nothing..

idk if those messages when the laptop reboots have anything to do with it. but it always changes.\
sometimes it gets stuck on the boot logo and i have to do a hard shutdown and restart it and it startes up normally the 2nd time.

I have wired connection on right now and its working great no problem.. but i want to fix my wifi connection so i can take the laptop of Ethernet cord.

i have tryed so many command lines and nothing seems to work. If someone could help me out, i would really appreacte it.

Thanks again.
Christian.

---

### Post by Hadaka on 2014-09-11
Hi, please post the output of..
```
lspci -nnk | grep -iA2 net
lsmod
rfkill list all

```
thanks.

---

### Post by mörgæs on 2014-09-11
Hi, welcome to the fora. Please read the sticky notes.

---

### Post by christian40 on 2014-09-11
Code
> chistian@chistian-Latitude-D610:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
    Subsystem: Dell Latitude D610 [1028:0182]
    Kernel driver in use: tg3
--
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005]
    Kernel driver in use: wl
chistian@chistian-Latitude-D610:~$ lsmod
Module                  Size  Used by
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342208  10 bnep,rfcomm
snd_intel8x0           33110  2 
snd_ac97_codec        105709  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0
gpio_ich               13229  0 
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
dell_laptop            17808  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
wl                   3999690  1 
dcdbas                 14448  1 dell_laptop
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
pcmcia                 51828  0 
lpc_ich                16864  0 
snd                    60939  12 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
lib80211               14040  1 wl
joydev                 17101  0 
i915                  705659  3 
yenta_socket           40201  0 
binfmt_misc            13140  1 
cfg80211              409394  1 wl
drm_kms_helper         47182  1 i915
pcmcia_rsrc            18319  1 yenta_socket
serio_raw              13230  0 
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
soundcore              12600  1 snd
drm                   244037  4 i915,drm_kms_helper
mac_hid                13037  0 
irda                  107386  0 
i2c_algo_bit           13197  1 i915
crc_ccitt              12627  1 irda
video                  18903  1 i915
parport_pc             31981  1 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
psmouse                91329  0 
tg3                   152132  0 
ptp                    18445  1 tg3
pps_core               18799  1 ptp
chistian@chistian-Latitude-D610:~$ rfkill list all


---

### Post by Hadaka on 2014-09-11
Hi, from a wired working conection please do..
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
then do..
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
*Ignore any offer to install proprietary or additional drivers
boot.
test wireless

---

### Post by christian40 on 2014-09-15
i did what u told me to do and after everything was loading, this error message popped up...

```
Fetched 1,742 kB in 20s (83.9 kB/s)                                            
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

---

### Post by Hadaka on 2014-09-16
hi, please do.,
```
sudo rm -rf /var/lib/apt/lists/lock
sudo dpkg --configure -a
sudo apt-get update
```
then repeat the same commands in post #5
thanks

---

### Post by christian40 on 2014-09-21
hey sorry for not getting back late., i had a family emergence so i was un able to get online...  


but i put what u told me to put and then i code the code from pst #5 and this popped up.
> 
chistian@chistian-Latitude-D610:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed InRelease                     
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [59.7 kB]             
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty InRelease                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg [933 B]        
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed Release.gpg [933 B]         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [59.7 kB]      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release [59.7 kB]          
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed Release [110 kB]            
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main i386 Packages                       
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [44.3 kB]        
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [10.8 kB]   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [700 B]   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [133 kB]  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [47.0 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1,398 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main Translation-en_US                   
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [120 kB]       
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main Translation-en                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [1,408 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                 
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [84.7 kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [3,527 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [314 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [5,820 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [203 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [9,545 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [143 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [101 kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources [4,760 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources [14 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources [12.6 kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources [1,315 B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages [6,379 B]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages [14 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages [16.0 kB]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [945 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en [4,216 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/universe i386 Packages [21.2 kB]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/main i386 Packages [114 kB]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/restricted i386 Packages [14 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/multiverse i386 Packages [1,395 B]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/main Translation-en [44.1 kB]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/multiverse Translation-en [587 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/restricted Translation-en     
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/universe Translation-en [12.9 kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 1,758 kB in 10s (162 kB/s)                                             
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
chistian@chistian-Latitude-D610:~$ sudo apt-get remove --purge bcmwl-kernel-source
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
chistian@chistian-Latitude-D610:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf


---

### Post by christian40 on 2014-09-21
nevermind, i found the fix for that.
i put 
code
> sudo dpkg --configure -a
and it started fixing it, now im gonna try ur steps again.

---

### Post by christian40 on 2014-09-21
> **Hadaka said:**
> Hi, from a wired working conection please do..
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
then do..
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
*Ignore any offer to install proprietary or additional drivers
boot.
test wireless

i put the codes one by one but when i got to this one.

```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
it says.
```
rm: cannot remove ‘/etc/modprobe.d/blacklist-bcm43.conf’: No such file or directory
```

---

### Post by westie457 on 2014-09-21
Hi, that error is not important.
Just continue with Hadaka's instructions, all should be well.

---

### Post by christian40 on 2014-09-21
> **christian40 said:**
> i put the codes one by one but when i got to this one.

```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
it says.
```
rm: cannot remove ‘/etc/modprobe.d/blacklist-bcm43.conf’: No such file or directory
```

okay after i found the sudo for the files that i was missing. i fixed them and then i came back to my post and redid post #5 and everything worked like a charm... i rebooted my laptop and now the wifi is working.

thank you again for helping me. this really means a lot.

now i can go on to loving linux =D

---

### Post by westie457 on 2014-09-21
Hadaka will be very pleased about that.

Could you mark this as solved - using 'Thread Tools' at the top of the page. This might someone in a similar situation that you were in.

Thank you

---

### Post by Hadaka on 2014-09-21
Yes I am, glad its working !!

@westie:thanks

---

### Post by Elyod on 2015-08-11
Thanks guys here it is almost a year later, I just found this post and it worked like a charm.  I will tell others that line, "sudo rm /etc/modprobe.d/blacklist-bcm43.conf" just flipped and went back to ~$ immediately and the last one for modprobe b43 hung for over 10 minutes.  However, when I rebooted all of the available wireless networks were there and worked.

Thanks a ton!!!

---

### Post by john490 on 2015-12-02
[COLOR=#000000]Hadaka [/COLOR]
Great tutorial / tips

[COLOR=#000000]Thank you for your help !!![/COLOR]

---

### Post by Hadaka on 2015-12-02
Hi, you are welcome glad to help.
Hadaka

---

