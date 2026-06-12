---
title: "Wired/Wireless Issues-1st try at Linux since XP has reached &quot;end of life&quot;"
date: 2014-05-23
forum: Networking &amp; Wireless
---

### Post by happyytilton on 2014-05-23
**What I have...**
Dell Inspiron E1705
XPPro (32bit)
Intel dual core @1.83Ghz
2G ram
150G HDD
Broadcom 440x 10/100 Integrated Controller
Dell Wireless 1390 WLAN Mini-Card

**Problem 1...**
I'm trying to use Ubuntu v14.04 in a dual boot along w/XP, but when U14.04 boots it has no IC (internet connection), hardline or wireless.
During the install process U14.04 was able to access the internet (hardline) and downloaded several updates, so I know it can access the internet.

**Problem 2...**
A reboot of U14.04 results in a hung OS in the middle of the shutdown splash screen.
XPPro reboots normally, though.

**Course of events leading to problems (all in a dual boot config)...**
**1. **Installed Xubuntu 14.04;
rebooted normally, but no IC (hardline or wireless)

**2.** Next installed Ubuntu 14.04;
rebooted normally, had IC by hardline but NO wireless, unable to find the terminal emulator, so

**3.** Then tried Kubuntu 14.04;
no IC and the reboot problem (hung at shutdown splash screen) began

**4.** Reinstall U14.04;
this time, no IC and the reboot problem (hung at shutdown splash screen) remains

This is my 1st try at Linux since XP has reached "end of life", but being new to Linux, I'm not doing too good.
I would at least like to give Linux a fair shot before throwing in the towel, but it is hard to do without an IC and shutdown/reboot problems.

---

### Post by oldrocker99 on 2014-05-23
OK, your wireless card has no Linux support. Download the driver from here:[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php).
Then, extract the file, and cd to that directory.
Then, type this:

```
sudo apt-get install build-essential
```

A number of programs will be installed. Once done, type

```
make
```

when it finishes, type

```
sudo make install
```

You'll probably need to reboot, but your wireless should now work.

---

### Post by grahammechanical on 2014-05-23
What graphic adapter does that machine have? When we install and tick the box "Install third party software" we get a proprietary video driver. So, if the live session works fine but the first reboot after install does not, then in my opinion the problem is with the proprietary video driver.

I suggest to install without ticking that box and then if the reboot get to a working desktop we can use the software centre to install Ubuntu restricted extras and System Settings>Software and Updates>Additional Drivers tab to experiment with proprietary video drivers. Or continue using the open source video driver.

People wishing to move away from XP will have video driver problems if the hardware is very old. The latest Ubuntu brings with it the latest proprietary video drivers. As we would expect. But the developers of proprietary video drivers often drop support for their old video adapters from their latest drivers. So, we get a situation where Ubuntu 12.04 from 2 years ago would provide a proprietary video driver for the adapter but 14.04 will not. The software centre may allow us to install an older proprietary video driver.

Regards.

---

### Post by happyytilton on 2014-05-23
[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323"):
Display adapter is [SIZE=2]NVIDIA GeForce Go 7900 GS[/SIZE]

[**[COLOR=#000000]oldrocker99[/COLOR]**]("http://ubuntuforums.org/member.php?u=565288"):
I don't know where to find the terminal... Guide me to its location, if you will

---

### Post by Habitual on 2014-05-23
Try Ctrl+Alt+T after logging in.

---

### Post by happyytilton on 2014-05-23
> **Habitual said:**
> Try Ctrl+Alt+T after logging in.

So that's where it's at.
I've spent hours looking for it!

Thanks

---

### Post by happyytilton on 2014-05-23
> **oldrocker99 said:**
> Download the driver from here:[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php).
Then, extract the file, and cd to that directory.


This is a little Greek to me... What is "cd" and to what directory, I assume folder?

Remember, I'm a windows guy and this is a little bit different. You need to explain things like I don't know squat, 'till I get the hang of this stuff.
I think that's why this is called the **beginners section**... **Don't worry, I won't be offended!**

---

### Post by squakie on 2014-05-23
cd = change (working) directory - just like in DOS or the command prompt in Windows

As an example:

download "xxxxxx"
use the file manager and locate the download (if via browser it by default goes in Downloads I believe)
right-click the file and select open with archive manager
click extract
this will unpack the file, and most probably it will create a folder "xxxxxx" in Downloads where it puts everything
open a terminal window (ctrl-alt-F1) and login (your password isn't echoed)
type:  cd Downloads/xxxxxx
type:  make (if it errors out, try  sudo make)
type:  make install

You may need to reboot.

---

### Post by happyytilton on 2014-05-23
> **squakie said:**
> cd = change (working) directory - just like in DOS or the command prompt in Windows

Everything was working just as you laid it out, until I got to where it asked for the PW and it would not accept any characters.
I tried typing it in then copy/paste, each time there was no movement of the courser. Just won't accept anything on that line.

Is there anything that needed to precede the PW, so it will accept it?

This booting back and forth is getting to be a real pain... If we can only get this to work so I can connect from Linux and not
have to boot back & forth.

---

### Post by oldos2er on 2014-05-23
It's normal for nothing to be echoed to the screen when you type your password into a terminal, just type it in and press Enter.

[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by Vladlenin5000 on 2014-05-23
There is NO indication whatsoever when entering a password. It's a security feature. Just type it as usual and then Enter.

PS - A mod beat me to it, as usual....

---

### Post by happyytilton on 2014-05-23
I had typed it in with no indications, hit enter... invalid PW
copy & paste with no indication, hit enter... invalid PW
tried typing a 3rd time and that was the final time.

I'll reboot back to Linux and try again.

---

### Post by Vladlenin5000 on 2014-05-23
Keep in mind you can also use BackSpace as much as you want if you feel you have mistyped something. When it says the password is incorrect be sure it really is.

---

### Post by happyytilton on 2014-05-23
Finally got it to take the PW, but the path to the folder was wrong somehow.
I've beat my head against the wall about all I can stand for one day, so I'm calling it quits for today and will resume again tomorrow.

Thanks everybody for all the help so far... We'll try to tackle it again tomorrow.

---

### Post by deadflowr on 2014-05-24
Moved thread to Networking and Wireless.

You'll have better luck solving the networking issues here, where the pros are.

Changed the title to better reflect the issues at hand.

---

### Post by happyytilton on 2014-05-24
Is there an easier way to install this wireless driver, other than the command line?
I'm not comfortable with this method since I'm used to running **executables** in Windows and **never** used DOS command prompts.

Plus I have a keyboard that needs to be replaced... Some keys double strike, no strike, shift key is intermittent, ect... I really have to watch every key stroke.
And if the key stroke is an invisible one, I have no way to know if the entry is right. So you can see from all that, I really struggle.

---

### Post by happyytilton on 2014-05-24
> **deadflowr said:**
> Moved thread to Networking and Wireless.

Thanks **deadflowr**, as any help is appreciated.

---

### Post by praseodym on 2014-05-24
Please show these terminal outputs:
```

uname -a
lspci -nnk | grep -iA2 VGA
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by happyytilton on 2014-05-24
> **praseodym said:**
> Please show these terminal outputs:
```

uname -a
lspci -nnk | grep -iA2 VGA
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

YYou do understand that I am having to reboot to Linux, do what you ask, save it to a .txt document over in the Windows partition and then reboot back to Wwindows just to post back each time.

I'm not whining, just pointing out that this in not a simple process and what i'm dealing with.
If i had anyy IC on linux, wired or wireless, conveying information back & forth would be much simpler and accurate.
in other words, transferring documents back & forth does always work.

so if there is something simpler, let me know... If not I'll endure and do what you ask to the best of my ability or what the differences in these 2 OS's will let me do.
I'll wait a few minuets  for you to reply before booting back to Linux.

---

### Post by praseodym on 2014-05-24
Hopefully, it is only necessary once ;-)

But it is, to show the hardware/network config. Please add these outputs, too:

```
cat /etc/resolv.conf
ifconfig -a
iwlist chan
cat /etc/network/interfaces
```

---

### Post by happyytilton on 2014-05-24
OOK.... But it's going to be a while!

---

### Post by happyytilton on 2014-05-24
Here's what you requested...

Please show these terminal outputs:
Code:
```

**hap@Maypop:~$ uname -a**
Linux Maypop 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux
```

```

**hap@Maypop:~$ lspci -nnk | grep -iA2 VGA**
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G71M [GeForce Go 7900 GS] [10de:0298] (rev a1)
    Subsystem: Dell Device [1028:019b]
    Kernel driver in use: nouveau
```

```

**hap@Maypop:~$ lspci -nnk | grep -iA2 net**
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 9400 Laptop [1028:01cd]
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: wl
```

```

**hap@Maypop:~$ lsusb**
Bus 001 Device 005: ID 046d:c50e Logitech, Inc. Cordless Mouse Receiver
Bus 001 Device 003: ID 050d:0237 Belkin Components F5U237 USB 2.0 7-Port Hub
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```

**hap@Maypop:~$ lsmod**
Module                  Size  Used by
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342263  10 bnep,rfcomm
joydev                 17101  0 
ssb                    51854  1 
snd_hda_codec_idt      48877  1 
snd_hda_intel          42730  3 
mii                    13654  0 
snd_hda_codec         164067  2 snd_hda_codec_idt,snd_hda_intel
gpio_ich               13229  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
wl                   3999690  1 
snd_seq_midi_event     14475  1 snd_seq_midi
dell_laptop            17808  0 
dcdbas                 14448  1 dell_laptop
snd_rawmidi            25135  1 snd_seq_midi
coretemp               13195  0 
r852                   17722  0 
sm_common              16772  1 r852
kvm                   388083  0 
nouveau               969577  3 
nand                   58760  2 r852,sm_common
mxm_wmi                12893  1 nouveau
nand_ecc               13136  1 nand
ttm                    72698  1 nouveau
nand_bch               13067  1 nand
bch                    17197  1 nand_bch
nand_ids                8547  1 nand
lpc_ich                16864  0 
drm_kms_helper         46907  1 nouveau
psmouse                91033  0 
mtd                    52813  2 nand,sm_common
drm                   243792  5 ttm,drm_kms_helper,nouveau
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
lib80211               14040  1 wl
serio_raw              13230  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60871  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
cfg80211              409394  1 wl
r592                   17711  0 
memstick               16174  1 r592
i2c_algo_bit           13197  1 nouveau
soundcore              12600  1 snd
mac_hid                13037  0 
parport_pc             31981  0 
video                  18903  1 nouveau
wmi                    18673  3 dell_wmi,mxm_wmi,nouveau
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_logitech_dj        18165  0 
hid_generic            12492  0 
usbhid                 47035  0 
hid                    87604  4 hid_generic,usbhid,hid_logitech_dj
firewire_ohci          35529  0 
sdhci_pci              18535  0 
firewire_core          61867  1 firewire_ohci
sdhci                  37779  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
```


**hap@Maypop:~$ iwconfig**
lo        no wireless extensions.


**hap@Maypop:~$ rfkill list**
hap@Maypop:~$ 


-------------------------------------

Hopefully, it is only necessary once

But it is, to show the hardware/network config. Please add these outputs, too:

Code:
```

**hap@Maypop:~$ cat /etc/resolv.conf**
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
```

```
[B]
hap@Maypop:~$ ifconfig -a[/B]
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2480 (2.4 KB)  TX bytes:2480 (2.4 KB)
```


**hap@Maypop:~$ iwlist chan**
lo        no frequency information.


**hap@Maypop:~$ cat /etc/network/interface**
cat: /etc/network/interface: No such file or directory

---

### Post by squakie on 2014-05-24
So your wireless adapter is Broadcom BCM4311.  I found some older instructions [here  ]("http://ubuntuforums.org/showthread.php?t=2156070")- I just don't know if there is any difference now in 14.04.

If you can't temporarily hard wire to the/a router, post back and we'll find a way to get the packages via Windows and then move them over for installation in Ubuntu.  Not sure yet how to do the Windows thing - I know there's a way to generate (or at least used to be) a script from the package manager that will download everything needed such as dependencies, etc..  I'll keep looking into that while you see if you can temporarily hardwire a connection.

EDIT:  I did find the linux-firmware-nonfree package, as mentioned in the thread in the link above,  in the package manager and it appears to not have any dependencies.  So, all I've got to do is figure out the repository for you to download from via Windows.

EDIT-EDIT:  Here's a [link]("http://packages.ubuntu.com/trusty/all/linux-firmware-nonfree/download") you can go to in your browser in Windows to pick a site to download the package from.  The link pretty much explains what to download.  Once you have downloaded it, you should be able to boot Ubuntu, find the file and copy it to your desktop in Ubuntu.  Once you've done that post back and I'll try to figure out how to actually install it (I *think* all you have to do is double-click on it to start up the software center to install it).

---

### Post by happyytilton on 2014-05-24
I'm assuming "**[SIZE=2]linux-firmware-nonfree_1.14ubuntu1_all.deb[/SIZE]**" was what I needed to download.
I put the file in the Windows "**My Documents**" partition, which I have access to when booted into Ubuntu.

Just let me know what to do so I can copy the instructions into a "**.txt**" file and place it in with the one I just downloaded.

---

### Post by Hadaka on 2014-05-24
Hi, Happy tilton. your problem is being caused by
additonal drivers loading the incorrect driver...it is
a very well known problem...lets fix it..
please do.
first..connect your ethernet cable so we will have internet access
when it comes to life.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf #ignore any moans or groans you get with this one...but do it
sudo modprobe b44
```
BOOT   << THIS IS A MUST !
now...with your wired connection connected to the internet lets fix the wireless
please do..
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
BOOT
you should now have wired and wireless working

*If all this worked like it should have...go here to mark solved
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

### Post by Hadaka on 2014-05-24
No complaints of smoke,fire, or smell of melting plastic..
Glad it worked for you !!!

---

### Post by happyytilton on 2014-05-24
[**[COLOR=#000000]Hadaka[/COLOR]**]("http://ubuntuforums.org/member.php?u=1599436")...
Everthing is now working; wired, wireless and the hanging on the shutdown splash screen during reboots has been fixed. Also marked the thread as, [COLOR=#b22222]**SOLVED**[/COLOR].
Your method was rather painless and I just want to extend to you a healthy, [COLOR=#b22222]**THANK YOU**[/COLOR]!

---

### Post by Hadaka on 2014-05-24
searchers...the fix for this is here -> [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by squakie on 2014-05-25
I was only half right.  The old post I referenced didn't mention removing the old B43 first.  I also didn't know you had wired access - sorry for that as well.

---

