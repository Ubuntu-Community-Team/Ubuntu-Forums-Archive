---
title: "Cannot turn on wireless in FSC Amilo Li 2727"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by dthuk on 2008-09-04
I have my wireless driver installed and it would all seem to be correct but Fujitsu-Siemens seemed to have got this machine to only enable wireless when you hit Fn+F1 when running Windows Vista!:mad:

I can't find anyway of getting the wireless card to turn on for me in Ubuntu. Looking around it seems even windows users can't have the card turn on automatically without this keypress everytime unless they put some code into Startup so what chance do Ubuntu users have where Fn+F1 doesn't seem to be supported?

I have also tried the thread at

[http://ubuntuforums.org/showthread.php?t=644899](http://ubuntuforums.org/showthread.php?t=644899)

which uses a trick for Acer machines which has helped another FSC Amilo Li 2727 user in the past but doesn't seem to work for me.

So am I knackered here? Have Fujitsu-Siemens managed to build in a feature that has stopped Linux users using wireless?


BACKGROUND INFO:

I have followed the guides on installing the Madwifi driver for my chipset indicated by lspci as Atheros AR242x also known (I am told) as AR5007. I am using the madwifi-hal-0.10.5.6 as suggested by a number of other threads. Now when I type 
'lsmod | grep ath' I get:-

ath_pci      101024    0
wlan         207728    1  ath_pci
ath_hal      192592    1  ath_pci 

which I guess is good, but when I type 'iwconfig' I get 

lo     no wireless extensions

eth0   no wireless extensions

and 'lshw -C network' gives me 

network UNCLAIMED etc...etc... for my Atheros wireless card.

Does all this support my conclusion that the solution to this is to get the card to turn on?

I would happily by slave-for-life to anyone who could get me through this!:)

---

### Post by acidstorm on 2008-09-09
Hello! This is first ever post here. I actually have the same Amilo Li2727
First of all, I would try to blacklist the ath_hal on Ubuntu by adding 'ath_hal' to the /etc/modprobe.d/blacklist file , I think that gets loaded before ath_pci evens gets a chance to load its own version.

I have tried that before and it worked after I got into a similar situation.


If that doesnt work, U might want to download the latest version of the madwifi hal driver at [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/) and retry the steps again as I noticed there was a new one added recently as I tried to setup Ubuntu after removing it under circumstances beyond my control (thanks to Vista). I did not have to do the modprobe thing.
Let me know how you get on.

---

### Post by dthuk on 2008-09-09
Thanks acidstorm, that blacklisting of ath_hal has certainly helped with the driver installation although I'm still not there yet.

lsmod | grep ath gives me

[HTML]ath_rate_sample        16128  1 
ath_pci               249016  0 
wlan                  236272  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               305376  3 ath_rate_sample,ath_pci
[/HTML]

and iwconfig now gives me

[HTML]lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/HTML]


and finally lshw -C network gives me

[HTML]WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0a:e4:cd:a8:9a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.6 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wifi0
       version: 04
       serial: 00:16:44:d9:22:9c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g[/HTML]


which is quite an improvement on before when I used to get network UNCLAIMED but I am still not there yet. You can see above that I am getting 'Access Point: Not-Associated' from iwconfig.

I don't get the orange wireless LED on at all and Fn+F1 has no effect still. Does your LED come on? I have tried to install the acerhk as per the instructions, maybe I've done something wrong?

---

### Post by dthuk on 2008-09-13
Well, I've given up after many hours of trying to get acerhk to work. I've had my fill of reading about people getting their Amilo 2727 to work only to find their fix just does nothing for me. It feels like Fujitsu have made a "Windows only" piece of hardware with this horrid vista compatible software wireless switch!

At this point, many people say, they've gone back to Windows and scrapped Ubuntu. Well, not me. I've scrapped the computer (well, taken it back on a 28 day no quibble return policy if truth be told) and ordered myself a Dell Ubuntu laptop.

I'll be back in my comfort zone fairly soon.

---

### Post by dthuk on 2008-09-14
If this problem can be solved, it may help someone else.

The sticking point seemed to be permissions. The file /proc/driver/acerhk/wirelessled was never created as I think it should be. When I cd to /proc/driver and tried 'mkdir acerhk' it wouldn't let me- even with sudo.

Maybe if that problem could be overcome, this would work which may be of use to someone else with this problem. It's all academic for me now though.

Does anyone have any ideas?

---

### Post by acidstorm on 2008-09-14
I'm really sorry to reply late, I had assumed that I would receive an email if I got a response from you. If I remember correctly from the tutorial, The rm command that had to delete the acerhk module that came with Ubuntu was dependent on the kernel version. I had to change the path to point to my current kernel version before I got the light to go on. Perhaps the old version interfered and that was why you did not get the wireless light on. The wireless drivers were actually installed correctly but the card itself was switched off.

BTW I'm sorry that U had to return it tho. But I guess, there wasnt anything you could do..(OMG I sound like a sales rep)

Cheers

---

### Post by queBurro on 2008-09-16
> **acidstorm said:**
> I'm really sorry to reply late, I had assumed that I would receive an email if I got a response from you. If I remember correctly from the tutorial, The rm command that had to delete the acerhk module that came with Ubuntu was dependent on the kernel version. I had to change the path to point to my current kernel version before I got the light to go on. Perhaps the old version interfered and that was why you did not get the wireless light on. The wireless drivers were actually installed correctly but the card itself was switched off.

BTW I'm sorry that U had to return it tho. But I guess, there wasnt anything you could do..(OMG I sound like a sales rep)

Cheers

having the same trouble myself, got the amilo li2727 and had the wireless working but when I moved from kernel 2.6.24-16 to 19 it broke, 

the acerhk won't compile on 19

any clues would be appreciated, trying to get it going in 16 again now but I'm struggling, cheers

---

### Post by queBurro on 2008-09-16
> **queBurro said:**
> having the same trouble myself, got the amilo li2727 and had the wireless working but when I moved from kernel 2.6.24-16 to 19 it broke, 

the acerhk won't compile on 19

any clues would be appreciated, trying to get it going in 16 again now but I'm struggling, cheers

got it working on 16 by following the tutorial this page links to above (again), not blacklisted anything
if I dare might have a go tomorrow at getting it to work on 19, cheers

---

### Post by dthuk on 2008-09-17
I still can't help feeling permissions are a problem as everyone else using acerhk mentions 'wirelessled' in /proc/driver/acerhk but this was missing on my machine. This also came up as an error when I tried to run 

modprobe acerhk

Maybe it's a red herring, but it may tell someone who knows these things better than I do what could be going wrong. It would be interesting queBurro to know if you cd to /proc/driver whether you can 

sudo mkdir acerhk

as a test in the two kernels and see if there is a difference. Or maybe I'm barking up the wrong tree?

---

### Post by acidstorm on 2008-09-19
> **queBurro said:**
> got it working on 16 by following the tutorial this page links to above (again), not blacklisted anything
if I dare might have a go tomorrow at getting it to work on 19, cheers

I got mine working on 19, ( I needed the to blacklist the ubuntu ath_hal after the first install using the older driver, however, i noticed there was no neeed to with the more recent one (September 3rd). did you apply the patch?

@dthuk It seems you cant create a directory in /proc/driver (even with sudo), however, I think something might have gone wrong while you were installing the acerhk module. i am no expert, but that should be when the directory is created.

---

### Post by randysparks on 2008-11-18
Hi -- I've written an easy guide to getting wifi working on these annoying Fujitsu Siemens notebooks:

[http://ubuntuforums.org/showthread.php?p=6205188#post6205188](http://ubuntuforums.org/showthread.php?p=6205188#post6205188)

Covers both 8.04 and 8.10. It doesn't involve hacking together new drivers or anything complicated :)

---

### Post by dthuk on 2008-11-30
Obviously, it's all too late for me as I ended up taking the computer back and getting an Ubuntu machine from Dell so I can't try this out anymore.

But, if this works I can only say thank you so much for posting, I hope it is of some help to some other Fujitsu-Siemens users out there. 

Has anyone tried this and found it to work? If so please post and let others know!

---

### Post by tudor2k3 on 2009-07-10
If anyone still needs help, [http://ubuntuforums.org/showthread.php?t=986288](http://ubuntuforums.org/showthread.php?t=986288) did the job for my Amilo Li 2727 on Kubuntu 9.04

---

### Post by rohedin on 2011-02-25
Hey, I know this thread hasn't been touched in well over a year, but I've recently struggled to find a quick fix for this problem, and I've found one!

The issue (with 10.10 anyway) is not lack of support for the Wifi card, but the fact that the Wifi card can only be toggled on and off with some stupid proprietary program by FSC (which incidentally also breaks compatibility with Windows XP and 7)

A workaround for ALL operating systems is to upgrade the laptop's BIOS to version 1.10, which will permanently enable the Wifi (can also be disabled, but from the BIOS only). Here's how to do it:

1) Download the latest BIOS image from the FSC website: [http://support.ts.fujitsu.com/com/support/linkapplication.html?LNG=EN&ProductID=25387](http://support.ts.fujitsu.com/com/support/linkapplication.html?LNG=EN&ProductID=25387)
It's filed under Windows Vista > Flash - BIOS > BIOS Flash (ISO-CD Image)
2) Extract, then open up the disc image with Brasero, or any ISO-burning program, and burn it to a blank disc.
3) Boot up the disc (press F12 at startup to do so)
4) When prompted, enter the command FLASH. Make sure your AC adapter is plugged in (it may refuse to run otherwise)
5) Let the flash utility reprogram the BIOS chip, this should take a few minutes
6) When done, reboot the computer, but then enter the BIOS setup by hitting F2. Then make your way along the tabs (can't remember which one), until you see the option for Wireless Device. For me, it defaulted to being disabled, so enable it if you need to.
7) Press F10 to save changes and exit. Ubuntu will now recognise the wifi device without the need for any additional configuration!
This should also work for enabling compatibility on Windows XP and 7, but I haven't tested this. Hope this helps any others who may experience this issue in future.

---

### Post by eazyebeneezer on 2011-03-05
> **rohedin said:**
> Hey, I know this thread hasn't been touched in well over a year, but I've recently struggled to find a quick fix for this problem, and I've found one!

The issue (with 10.10 anyway) is not lack of support for the Wifi card, but the fact that the Wifi card can only be toggled on and off with some stupid proprietary program by FSC (which incidentally also breaks compatibility with Windows XP and 7)

A workaround for ALL operating systems is to upgrade the laptop's BIOS to version 1.10, which will permanently enable the Wifi (can also be disabled, but from the BIOS only). 

Thanks for this clear advice. I just installed Ubuntu 10.10 on an Amilo A 1665G and am having the same problem with the wifi button. However, there doesn't seem to be an updated BIOS on Fujitsu Siemens' website for the 1665G. Also, none of the threads I've found here deal with this model. 

I am a novice to Ubuntu and don't really understand the commands, etc. that most commenters are talking about. I was tired of Windows, and thought that Ubuntu would be less hassle. I wasn't planning on becoming a hacker in the process :(

Can anyone help find a solution? Thanks!!!

---

### Post by Mat11 on 2011-03-05
HI i've got an Amilo 1718i my wifi came on automatically in Ubuntu 10.10 to my surprise as i used AcerHk in the past. My Xpress 200m graphics card is not fully supported by Maverick but im still hoping, 3D one day.!!!!!!!! At least using the X86 64 bit software the three times and it finally boots up thing has gone. As for the wireless did you see any sign of the keyboard wireless light come on after the Full install  ? seemed a good sight for me at the time.

---

