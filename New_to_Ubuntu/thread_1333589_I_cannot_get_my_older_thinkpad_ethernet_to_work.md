---
title: "I cannot get my older thinkpad ethernet to work"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by joekennedy36 on 2009-11-21
I have installed Ubuntu successfully but I cannot get online to do the updates. I have read whatever I can to help but still no luck. I was able to get the IP address configured, there is power to the card but I cannot Ping anything. My final goal is to use a wirelss card. Just a note here (which may hold a clue or not), this thinkpad is a referb that has an ethernet port that controls a token ring connection, this is why I am using a ethernet card. 
 
I like the look of Ubuntu and look forward to delving into this new area of OS. I have been a microsoft drone for too long. 
 
Thanks for any help you can offer.

---

### Post by joekennedy36 on 2009-11-23
I was able to reload windows and install a bios update. This allowed me to reinstall Ubuntu and do the updates. I know it is probably the long way around but it was the only way I knew how to do it. When I looked for ways to update the bios in Ubuntu, there were ways to program in a terminal window but I could not do that being a newbie and all.
 
The only problem now is the updates are stalling on one package that is errored and "broken". It says that I have repaired it but it still errors on loading. Firefox will not open but at least I can ping out to WWW. Maybe I need to learn more about updating and installing packages. I do like to solve my own problems by trial and error (you learn a lot by doing so), but if anyone wants to throw their two cents in, please do.
 
Joe

---

### Post by ukripper on 2009-11-23
run these commands in terminal and check for any errors:
```
sudo apt-get update
```

and then run firefox in terminal;
```
firefox
```

If you get any errors post here.

---

### Post by joekennedy36 on 2009-11-23
Thanks UKRIPPER. I will try this later when I am in front of the laptop. I will let you know the results.

---

### Post by joekennedy36 on 2009-11-23
Ukripper
 
It appears that the sudo script you had me run worked. I tried to load firefox in a terminal but it did not run and no errors were reported. I am thinking that there is not enough RAM to run it. I have only 256mb. Is there a minimum requirement?

---

### Post by ukripper on 2009-11-24
if you got low RAM I think you should use lightweight DE like xubuntu or LXDE instead of GNOME. you install xubuntu-dektop by just using below commands:
```
sudo aptitude update
```
```
sudo aptitude install xubuntu-desktop
```

This will install xubuntu-desktop for you and 256 RAM is enough for it.

---

### Post by joekennedy36 on 2009-11-24
I noticed that Windows was hogging everything and somehow Ubuntu loaded inside of it or beside it and 245 MB was being used up somehow. So I reinstalled just Ubuntu on the HDD. I then ran updates and it all went smoothly with the ethernet PCI card. I tried to install my wireless PCI card next and no go!. I removed network manager and installed WCID and the card will not even power up. I have been here before once but at least I can use the ethernet to do updates. (note: I can also use Firefox and surf the web. Wahoo!) I would really like to use the wirelss card though. Any suggestions UKripper?
 
Thanks

---

### Post by ukripper on 2009-11-25
can you post output of the folowing:
if internal card
```
lspci
``` 

otherwise if usb:
```
lsusb
```

---

### Post by joekennedy36 on 2009-11-25
Here is info that you requested.


joe@joe-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Communication controller: Agere Systems WinModem 56k (rev 01)
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
joe@joe-laptop:~$

---

### Post by ukripper on 2009-11-26
what is the model of your thinkpad?

---

### Post by joekennedy36 on 2009-11-26
Sorry UK

I did not have the wireless card in but the ethernet card for the first try. Here is the wireless card.

Thanks



joe@joe-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Communication controller: Agere Systems WinModem 56k (rev 01)
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
06:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
joe@joe-laptop:~$

---

### Post by joekennedy36 on 2009-11-26
The laptop is an A21m.

---

### Post by ukripper on 2009-11-26
you have notorious Broadcom BCM43xx family. I remember them back in days of dapper fiddling around. Now i think they are in legacy support of 9.10. You may need to follow this and see if it works:

[SIZE="4"]**Method 1**[/SIZE] try this:
```
sudo apt-get install bcmwl-kernel-source
```


unplug any wired ethernet cable so you can use wireless.

Reboot and see if it comes up. If it doesn't follow method 2



**[SIZE="4"]Method2:[/SIZE]**
in terminal :
```

sudo apt-get install linux-backports-modules-karmic b43-fwcutter
```

3. Blacklist the ssb module.


```
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-ssb.conf

```
4. Blacklist the wl module.


```

echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist-wl.conf
```

5. Reboot and unplug any wired ethernet cable so you can use wireless.

Now after login see if your wireless comes up

---

### Post by joekennedy36 on 2009-11-26
Thanks UK
 
I will try this and let you know. If it does not work, I guess I would need a new wireless card.

---

### Post by ukripper on 2009-11-26
No man i'd stick to bcm until it dies or linux kernel won't support it as i'd think i paid for it so why to waste buying new one.

We will make it work dont worry!

---

### Post by joekennedy36 on 2009-11-26
Thanks for the confidence you have in this. This is why I like this OS. People helping people. :D

I ran both options. Here is the script.

joe@joe-laptop:~$ sudo apt-get install linux-backports-modules-karmic b43-fwcutter
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-karmic
joe@joe-laptop:~$ sudo apt-get install bcmwl-kernal-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcmwl-kernal-source
joe@joe-laptop:~$ sudo apt-get install linux-backports-modules-karmic b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-karmic

I guess we have to keep trying.

---

### Post by alexcckll on 2009-11-27
This is a little unnerving.

I run a Thinkpad R61i preinstalled with Hardy.. and am worried that my kit may not be fully supported by Lucid - on first install...

Here's my lspci - 
alex@ubuntu:~$ lspci
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
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)
alex@ubuntu:~$ 
alex@ubuntu:~$ 

I trust this lot will be supported directly off the Alternate CD when the time comes to do an LTS-LTS update..

---

### Post by dearingj on 2009-11-27
> **joekennedy36 said:**
> 
I ran both options. Here is the script.

joe@joe-laptop:~$ sudo apt-get install linux-backports-modules-karmic b43-fwcutter
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-karmic
joe@joe-laptop:~$ sudo apt-get install bcmwl-kernal-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcmwl-kernal-source


I see two problems here:
1) It sounds like you haven't enabled the backports repository. Open System->Administraion->Software Sources, click on the Updates tab, and check "Unsupported upates (karmic-backports)".
2) You misspelled the word 'kernel' in 'bcmwl-kernel-source'

---

### Post by joekennedy36 on 2009-11-27
UK

Did I tell you that I am learning a lot in this process? Well, I am. I am sad to say that this last attempt did not work either. I loaded the packports module as you said and reran the command and it is the same. Here it is 

joe@joe-laptop:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcmwl-kernel-source
joe@joe-laptop:~$ 

I am at your mercy here once again. Am I beyond hope?

---

### Post by Soffia on 2009-11-27
**Re: I cannot get my older thinkpad ethernet to work**
 		 	Quote:
 	 	 		 			 				 					Originally Posted by **joekennedy36** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8393057#post8393057") 				
 				[I]I ran both options. Here is the script.

joe@joe-laptop:~$ sudo apt-get install linux-backports-modules-karmic b43-fwcutter
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-karmic
joe@joe-laptop:~$ sudo apt-get install bcmwl-kernal-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcmwl-kernal-source[/I]
 			 		 	 	 
I see two problems here:
1) It sounds like you haven't enabled the backports repository. Open System->Administraion->Software Sources, click on the Updates tab, and check "Unsupported upates (karmic-backports)".
2) You misspelled the word 'kernel' in 'bcmwl-kernel-source' 	

i was having a similar problem, turned out I had to put jaunty instead of karmic since that is my linux version so I put:

sudo apt-get install linux-backports-modules-jaunty b43-fwcutter

---

### Post by ukripper on 2009-11-27
can you confirm which version of ubuntu you using? 8.04, 9.04 or 9.10?

The guide i posted above only applies to 9.10

---

### Post by joekennedy36 on 2009-11-27
> **ukripper said:**
> can you confirm which version of ubuntu you using? 8.04, 9.04 or 9.10?
 
The guide i posted above only applies to 9.10
 
 
The version I am using is 9.04 I see that Soffia has posted that I insert jaunty and try that. I will give that a shot. Maybe you were going to suggest the same thing now that you know which version I am using. I will keep you apprised of my progress.

---

### Post by joekennedy36 on 2009-11-28
> **Soffia said:**
> **Re: I cannot get my older thinkpad ethernet to work**
              Quote:
                                                                      Originally Posted by **joekennedy36**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8393057#post8393057")                 
                 [I]I ran both options. Here is the script.

joe@joe-laptop:~$ sudo apt-get install linux-backports-modules-karmic b43-fwcutter
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-karmic
joe@joe-laptop:~$ sudo apt-get install bcmwl-kernal-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcmwl-kernal-source[/I]
                                 
I see two problems here:
1) It sounds like you haven't enabled the backports repository. Open System->Administraion->Software Sources, click on the Updates tab, and check "Unsupported upates (karmic-backports)".
2) You misspelled the word 'kernel' in 'bcmwl-kernel-source'     

i was having a similar problem, turned out I had to put jaunty instead of karmic since that is my linux version so I put:

sudo apt-get install linux-backports-modules-jaunty b43-fwcutter



Sophia.

SUCCESS! I copied your script into my terminal and it ran a bunch of stuff as well as the b43 driver. it picked up the wireless network like nothing. I am using it right now.

I want to thank Ukripper and yourself for all your help on this. What a team! I still have lots to learn but I look forward to it.

If Ubuntu responds as well as its users, I will be with it and all of you for some time.

Thanks again.

Joe

---

### Post by ukripper on 2009-11-30
> **joekennedy36 said:**
> Sophia.

SUCCESS! I copied your script into my terminal and it ran a bunch of stuff as well as the b43 driver. it picked up the wireless network like nothing. I am using it right now.

I want to thank Ukripper and yourself for all your help on this. What a team! I still have lots to learn but I look forward to it.

If Ubuntu responds as well as its users, I will be with it and all of you for some time.

Thanks again.

Joe

That's great! see I told you, your card will work no need to buy a new one. 

Ubuntu will repond in its greatest no doubt, I have full faith in its delivery. Any question or problem just create a new thread, someone surely will respond to you.

Have fun mate!

---

