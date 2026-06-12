---
title: "Intel PRO/Wireless 3945ABG, HP Compaq nx7400"
date: 2014-03-26
forum: Networking &amp; Wireless
---

### Post by daniel131 on 2014-03-26
Hi guys.

I just installed Ubuntu 12.04 on my old laptop HP Compaq nx7400.
It seem to have become so much faster and all, i love it! It works well though it is so old.

BUT ofcourse the wireless function does not work. I have this little toggle-button above the keyboard that should start the WiFi-receiver.'
BUT this button doesnt work.

I have now for the past 6 hours straight been searching the net. Testing that comando here, downloading that there, blacklisting blah blah blah!
I am sick of it! Nothing works!

I therefore reach out to you guys to get personal suport.

And yes the wireless driver worked just fine in my former Windows XP.

---

### Post by chili555 on 2014-03-26
Let's start by identifying the wireless device. Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my keyboard on the same key with \. Thanks.

---

### Post by daniel131 on 2014-03-26
Thanks for the quick help! I hope we can fix this! :)
```
lspci -nn | grep 0280  
```
This is what i get:
```
10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
```

---

### Post by chili555 on 2014-03-26
The Intel device you have should work like a champ in 12.04. I know, I have both. It seems that this is the problem:> I have this little toggle-button above the keyboard that should start the WiFi-receiver.'
BUT this button doesnt work.Let's see:```
lsmod | grep hp
rfkill list all
```And, just for fun:```
dmesg | grep iwl
```Thanks.

---

### Post by daniel131 on 2014-03-26
lsmod | grep hp
gives:
```

sparse_keymap          13658  1 hp_wmi
wmi                    18744  1 hp_wmi

```

rfkill list all
gives:
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

dmesg | grep iwl
gives:
```

[   11.449926] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   11.449930] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   11.449979] iwl3945 0000:10:00.0: can't disable ASPM; OS doesn't have ASPM control
[   11.503550] iwl3945 0000:10:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   11.503555] iwl3945 0000:10:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   11.503628] iwl3945 0000:10:00.0: irq 44 for MSI/MSI-X
[   11.850124] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'

```

I only program website and that jazz I know nothing about ubuntu! Thanks for your help!

---

### Post by chili555 on 2014-03-26
Let's try a bit of magic:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```Thanks.

---

### Post by daniel131 on 2014-03-26
Nothing happens when i do the first 2 lines.

with
rfkill list all
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

That is weird? Is the commands wrong?

---

### Post by chili555 on 2014-03-26
> Is the commands wrong? It isn't wrong. The proof is that there was no response. No response means, roughly, 'command executed and there are no errors to report.' However, trying a command doesn't mean it is actually effective. Please reboot so we have a clean slate. Let's have a look at:```
dmesg > wifi.txt
```Find the file wifi.txt in your user directory and paste it here. Give us the link in your reply.[http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by daniel131 on 2014-03-26
Okey, great!
I rebooted and here is the link to the wifi.txt file.
[http://paste.ubuntu.com/7159260/](http://paste.ubuntu.com/7159260/)
Hope it works? It was a big ass file! ;)

Oh! I am biting my nails and crossing my fingers that you are the magician that will turn my Ubuntu-project with this computer to a great deal. I love how quick it is to reboot and so on.
I am so glad for all your help!

---

### Post by chili555 on 2014-03-26
> [   13.888210] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.888215] Disabling lock debugging due to kernel taint
[   13.891619] wl: module verification failed: signature and/or required key missing - tainting kernelYou have been indeed busy! As you haven't a Broadcom wireless device, let's remove that driver:```
sudo apt-get purge bcmwl-kernel-source
```Reboot and show us:```
rfkill list all
```If you are still blocked, give me another paste as above. I hope we're narrowing in on it!

Please also let me see:```
cat /etc/modules
cat /etc/modprobe.d/blacklist.conf
```

---

### Post by daniel131 on 2014-03-26
okey, I now removed the driver.

After that and a reboot
rfkill list all
same as before :(
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

I then removed the old wixi.txt and created a new one.
[http://paste.ubuntu.com/7159625/](http://paste.ubuntu.com/7159625/)

After that
cat /etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

```

and here is the blacklist i got from:
cat /etc/modprobe.d/blacklist.conf
[http://paste.ubuntu.com/7159653/](http://paste.ubuntu.com/7159653/)

I am so glad that someone understands this. 
Is it often problem with the wireless drive when you instal ubuntu on a laptop?

(by the way, it is getting late for me here in Sweden so that is why i wont answer so much more for tonight) thanks!

---

### Post by chili555 on 2014-03-26
> Is it often problem with the wireless drive when you instal ubuntu on a laptop? It is seldom a problem. In this case, it isn't the wireless driver; it is the little helper *hp-wmi* that is supposed to properly translate key presses into action; i.e. turn on the wireless, please.

Please open a terminal and do:```
tail -f /var/log/syslog
```Press the wireless button a few times and see if the syslog recognizes anything at all. If so, record the messages. Then get out of tail with Ctrl+c. Now do:```
sudo modprobe -r hp-wmi
tail -f /var/log/syslog
```Press the wireless button some more and see if the syslog _now_ recognizes anything at all. If so, record the messages. Then get out of tail with Ctrl+c. 

We are running out of options.

---

### Post by daniel131 on 2014-03-26
Hm...

The first recording saw nothing. Nothing att all.

Then the code: sudo modprobe -r hp-wmi     -- nothing happened
Then: tail -f /var/log/syslog  --- again nothing.

I rebooted now aswell and i might have been opening the syslog verry early on after the start up.
So it might have been an coincidence but something happened at first. That might have been an update running
in behind but i dont know.

i paste the code i got: [http://paste.ubuntu.com/7159822/](http://paste.ubuntu.com/7159822/)

Oh please tell me what to do next.... The toggle/hotkeys for increas/decrease sound and mute sound that look pritty much the same work just fine... Cmon.. It must be possible to run through the darn button? Should i try to boot the computer again?

---

### Post by chili555 on 2014-03-26
> Then: tail -f /var/log/syslog --- again nothing.
After which you manipulated the button repeatedly and still nothing?

Your paste is simply apt starting the process to check for updates. No problem there.

If you see no activity from syslog both with and without *hp-wmi*, then our options are rapidly narrowing. One is pretty drastic: [http://ubuntuforums.org/showthread.php?t=1689100](http://ubuntuforums.org/showthread.php?t=1689100) See post #6.

Another is to try the live USB for Ubuntu 13.10 or even 14.04 and see if things have improved.

Finally, for US$10-15, you could buy a supported USB wireless. Some laptops, including my Lenovos, disable USB wireless as well if the hardware switch is off; test yours to be sure.

Googling 'HP Compaq NX7400' rfkill ubuntu will show several unsolved instances of this same issue.

---

### Post by daniel131 on 2014-03-26
No i do and did not get a single output when i toggle the wifi-button.
This I get when i: sudo modprobe -r hp-wmi
```
Mar 27 01:24:42 Krubb kernel: [ 2789.784726] wmi: Mapper unloaded
```

> 
Another is to try the live USB for Ubuntu 13.10 or even 14.04 and see if things have improved.

What do you mean? That i should mount a newer version of Ubuntu? 
I will try 13.10 in the morning

Oh well crap, this sucks. I will search a bit more and maby considering going back to windows i guess... baaah.. 
Dont want an usb-wifi-stick pointing out on the side, one of the main reasons was to be able to be flexible and mobile.. Maby there is extremly tiny reseivers.. Darn.. I dont think i will go in and tape the pins.. :p

Oh man.. Why....

---

### Post by chili555 on 2014-03-27
> What do you mean? That i should mount a newer version of Ubuntu? Exactly. If you download 13.10 or even 14.04 and burn a DVD or place it on a USB, you can try it without installing. There are two choices offered; try without disturbing your current install, or, simply install. I suggest you try it and see if *hp-wmi*, your wireless button and your wireless card are now working as expected. 

We live in an imperfect world, unfortunately.

---

### Post by daniel131 on 2014-03-27
I tried 13.10 without success. 
I have to face the dissapointing truth that it won't work.

I have orderd an USB-wifi now so i hope that will work just fine.

thanks for all your help though!

---

### Post by mitryaev-p on 2015-03-10
I feel myself like Necromancer, when typing to this thread, but this issue is actual for me.

My system:
xUbuntu 14.04 with kernel 3.13.0-24-generic
wicd to manage networks

Issue:
Like topic starter - WiFi can be turn on only in OS Windows. This is key to solution - Windows with "HP Quick Launch Buttons".

Solution:
1. *ifconfig -a* don't show interface *wlan0 *Driver is needed:
** sudo apt-get install firmware-b43-installer**

2. RF-kill block tries to interface wlan0 up, *ifconfig wlan0 up* tell (in russian):
 **SIOCSIFFLAGS: &#1054;&#1087;&#1077;&#1088;&#1072;&#1094;&#1080;&#1103; &#1085;&#1077; &#1087;&#1086;&#1079;&#1074;&#1086;&#1083;&#1103;&#1077;&#1090;&#1089;&#1103; &#1080;&#1079;-&#1079;&#1072; RF-kill** 

3. Restart laptop and go to BIOS (F10) "System Configuration" - "Built-In Device Options" - "LAN/WLAN Switching" and switch "Disable" -> "Enable". Save the changes and restart.

4. Restart laptop againg and go to BIOS "File" - "Restore Defaults". Save the changes and restart.

5. Button work correctly now: enable/disable WiFi and Bluetooth

I find this solution on YouTube: [http://www.youtube.com/watch?v=0B-oKtq2fv0](http://www.youtube.com/watch?v=0B-oKtq2fv0)

---

