---
title: "some Questions"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by ~The~Killer~ on 2009-08-21
Hi guys. 

I've installed ubuntu and everything is ok. But I have some problems

-sometimes I feel that ubuntu is slow? I Have 2Gb of Ram - core 2 duo 1.6 

-I am using NOD32 in vista, do i need to install it again in ubuntu OS?

-In vista you can see the following options for battery " power saver/Balanced/high performance" is there anything similar to that in ubuntu ? I like to make my screen dark also because of my eyes :P

-where can i find some Great background with "ubuntu" Logo 

Guys I am really Happy, I am the first guy at my school using ubuntu and everyone is asking me what is that :guitar: 

Thanks :)

---

### Post by earthpigg on 2009-08-21
desktop linux users generally have no use for antivirus and anti-malware software. make sure you pay attention to when/why you enter your password and you will be safe.

system -> preferences -> power management.

the power options in vista are just a dumbed down version of what can be found there.


google image search 'ubuntu desktop background', set image size to 'large' and (assuming you are a legal adult and it is legal where you live bla bla bla) turn off SafeSearch. you will be pleasantly surprised, if you are in the demographic i am guessing. you can also search for 'ubuntu _body part here_' and find some fun stuff.

---

### Post by earthpigg on 2009-08-21
also, look at [http://ubuntusatanic.org/](http://ubuntusatanic.org/)

again, i am recommending this to you because i am infering certain things about you based on your writing style, what you wrote, and your handle.

if i'm off, forgive me.


edit: what, specifically, would you like to speed up? starting programs? firefox? booting? etc

---

### Post by ~The~Killer~ on 2009-08-21
> **earthpigg said:**
> desktop linux users generally have no use for antivirus and anti-malware software. make sure you pay attention to when/why you enter your password and you will be safe.

system -> preferences -> power management.

the power options in vista are just a dumbed down version of what can be found there.


google image search 'ubuntu desktop background', set image size to 'large' and (assuming you are a legal adult and it is legal where you live bla bla bla) turn off SafeSearch. you will be pleasantly surprised, if you are in the demographic i am guessing. you can also search for 'ubuntu _body part here_' and find some fun stuff.
Thanks, i am using a laptop not desktop. what password are you talking about? :P


> also, look at [http://ubuntusatanic.org/](http://ubuntusatanic.org/)

again, i am recommending this to you because i am infering certain things about you based on your writing style, what you wrote, and your handle.

if i'm off, forgive me.


edit: what, specifically, would you like to speed up? starting programs? firefox? booting? etc 	
oops a Devil site :P . Great wallpapers gonna use the 666 :D

yeah speeding up the system, and firefox especially because FF loads so slow :(

Thanks:guitar:

---

### Post by sandyd on 2009-08-21
can you open up a terminal and type in
```

sudo apt-get install htop
sudo htop

```
note your ram usage.
If its slow, its proably a problem with your grafix.

in that case
```

lspci

```
will list all your hardware.
please post it here between [code] tags.

---

### Post by JC Cheloven on 2009-08-21
> **~The~Killer~ said:**
> 
.../
 I like to make my screen dark also because of my eyes :P
/...

Just a trick: when a window is too bright for your eyes (may happen easily when at night in a dark room; just don't ask :-D  ), hitting super-n will ... ok, try and see yourself.
Hitting super-m does the same for all windows.

note: "super" is somehow the unix equivalent to the windows key, the one with the flag in your keyboard. Hold that and press n or m.

---

### Post by earthpigg on 2009-08-21
> **~The~Killer~ said:**
> Thanks, i am using a laptop not desktop. what password are you talking about? :P

yeah speeding up the system, and firefox especially because FF loads so slow :(

Thanks:guitar:

whenever you make any potentially system-altering changes, it asks you for your user password. so if following directions from random websites you find on google... and suddenly it asks your user password then you need to ask yourself:

> do i trust this website?
if not, do i understand exactly what each part of these directions are telling me to do?

installing preload, _*over time*_, will make programs launch faster. it remembers what you use and how often, and loads it into RAM in advance in the background. to install preload:

```
sudo apt-get install preload
```

it will ask you for your password. so, as we discussed above, you need to ask yourself if you trust ubuntuforums.org, if you trust this random "earthpigg" person, and/or if you understand what that command will do.

---

### Post by ~The~Killer~ on 2009-08-22
> **carlee said:**
> can you open up a terminal and type in
```

sudo apt-get install htop
sudo htop

```note your ram usage.
If its slow, its proably a problem with your grafix.

```
kr@dana:~$ sudo apt-get install htop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package htop
kr@dana:~$ sudo htop
sudo: htop: command not found
kr@dana:~$ 
kr@dana:~$ 

```
the htop isn't working dude :(


in that case
```

lspci

```will list all your hardware.
please post it here between [code] tags.
lspci : No found

---

### Post by ~The~Killer~ on 2009-08-22
> **earthpigg said:**
> whenever you make any potentially system-altering changes, it asks you for your user password. so if following directions from random websites you find on google... and suddenly it asks your user password then you need to ask yourself:



installing preload, _*over time*_, will make programs launch faster. it remembers what you use and how often, and loads it into RAM in advance in the background. to install preload:

```
sudo apt-get install preload
```it will ask you for your password. so, as we discussed above, you need to ask yourself if you trust ubuntuforums.org, if you trust this random "earthpigg" person, and/or if you understand what that command will do.
```
Couldn't find package preload
```

---

### Post by earthpigg on 2009-08-22
that is lspci, a lower case "L".... _*not*_ Ispci, with an upper case "i".

everything in UNIX is case sensitive. 

Ubuntu is UNIX-like.

---

### Post by R_W322 on 2009-08-22
[http://www.hongkiat.com/blog/60-most-execellent-ubuntu-wallpapers/](http://www.hongkiat.com/blog/60-most-execellent-ubuntu-wallpapers/)

Some of the best Ubuntu Wallpapers around

---

### Post by ~The~Killer~ on 2009-08-22
Hi.

I did lspci the result is :

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
05:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
06:00.0 Multimedia controller: Broadcom Corporation Device 1612 (rev 01)
0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

Thanks dude for the wallpaper Link

---

### Post by earthpigg on 2009-08-22
> **R_W322 said:**
> [http://www.hongkiat.com/blog/60-most-execellent-ubuntu-wallpapers/](http://www.hongkiat.com/blog/60-most-execellent-ubuntu-wallpapers/)

Some of the best Ubuntu Wallpapers around

your flag and location do not add up -- denver isn't part of chicago!

sorry, couldn't resist :)

(moj kochanie jest z warszawie)

---

### Post by ~The~Killer~ on 2009-08-22
About the power management. 

when I click the help I can see " computer speed policy" but in my power management this option is unavailable. Why ? :P 

My ubuntu is getting slower and slower :confused:

---

### Post by earthpigg on 2009-08-22
"My ubuntu is getting slower and slower"

is something eating up your CPU cycles?

run htop, sort by CPU%, and see if there is something in the top 5 that doesn't make sense.

also run 'free -m' and copy/paste the output, please.

---

### Post by ~The~Killer~ on 2009-08-22
> **earthpigg said:**
> "My ubuntu is getting slower and slower"

is something eating up your CPU cycles?

run htop, sort by CPU%, and see if there is something in the top 5 that doesn't make sense.

also run 'free -m' and copy/paste the output, please.
```
The program 'htop' is currently not installed.  You can install it by typing:
sudo apt-get install htop
```

then I put ```
sudo apt-get install htop
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package htop**
```
:(

I tried "free-m" but the output was ```
command not found
```

Thanks

---

### Post by earthpigg on 2009-08-22
free -m, not free-m. ubuntu is very case sensitive, and very _space_ sensitive.

run 'sudo apt-get update' for us, please.

then try installing htop...

---

### Post by ~The~Killer~ on 2009-08-22
Hi Thanks it worked  :)

free -m results 
```
             total       used       free     shared    buffers     cached
Mem:          2004        915       1088          0         92        433
-/+ buffers/cache:        389       1615
Swap:         1309          0       1309
``` 

htop result :
[img]http://i26.tinypic.com/29blev.png[/img]

---

### Post by earthpigg on 2009-08-22
i see.

your computer should be moving pretty snappily.

are you sure this:

> My ubuntu is getting slower and slower 

isn't all in your head...?

---

### Post by feelshift on 2009-08-22
> **~The~Killer~ said:**
> My ubuntu is getting slower and slower :confused:
I see you have the Update Manager window open, you should install all the updates available.

---

### Post by ~The~Killer~ on 2009-08-22
> **earthpigg said:**
> i see.

your computer should be moving pretty snappily.

are you sure this:



isn't all in your head...?
ubuntu is working fast but Firefox is so slow especially when I want to minimize it or change its bars. it's taking times and slow. 

is there anything I could do to speed it up ? 

Thanks

---

### Post by earthpigg on 2009-08-22
how many addons do you have going?

those can bring ff to a crawl. they _are_ fun, but you gotta pick 2-3 you need and only use those if you want ff to be fast.

also, ff is not the most efficient piece of software out there. it just takes more and more and more memmory as time passes and it is still running, to infinity. i know it sounds windows-esque, but restart ff once every 24 hours.

if you dont watch flash, etc, chromium is fast as hell.

---

### Post by BackwardsDown on 2009-08-22
Many people are noticing that Firefox is slow in Linux. The Firefox devs are blaming it on GCC (the compiler that turns sourcecode into machine language) but as chromium (a new browser like chrome) is very fast I'm not sure. The new Firefox 3.5 that will be available in the next version of Ubuntu is a lot faster.

If you think firefox is too slow, I recommend to use another browser like Chromium or Opera.

---

