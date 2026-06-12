---
title: "Lenovo G50-30 Wifi disabled by hardware switch: RTL8723BE PCIe"
date: 2015-12-18
forum: Networking &amp; Wireless
---

### Post by Vikas_K_R on 2015-12-18
Hello Friends,
I am new to ubuntu. Got a new laptop and can't connect it to wifi. I don't have a UTP LAN so can't connect to ethernet as well. I've tried ubuntu help from the laptop's system settings but to no help. The issue don't arise if I install Win10.
Please, can someone help me resolve it? Many thanks for any and every support.
[U]
Following is a code that I ran on it if it is of any help:[/U]
[I]kiara@kiara-Lenovo-G50-30:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3816]
    Kernel driver in use: r8169[/I]

---

### Post by jeremy31 on 2015-12-18
```
sudo modprobe -r ideapad-laptop
rfkill unblock all
sudo apt-get update && sudo apt-get upgrade
```

Hopefully it will work after the sudo modprobe -r ideapad-laptop command and if it updates the kernel with the final command, it might work after a reboot

---

### Post by Vikas_K_R on 2015-12-18
Hi ieremy31, thanks for your support. I ran first two commands 
Code:
sudo modprobe -r ideapad-laptop
rfkill unblock all
and the wifi got enabled and also connected to my wifi.I then ran the last command
Code:
sudo apt-get update && sudo apt-get upgrade
It ran for some time and before i could do a reboot, the "Software Updater" came up with needed to update software. But then, after several minutes, it prompted, "check your internet connection". Well, on reboot, the system hung and I tried booting it by long press of power switch. Now it is back to same state: Wifi disabled by hardware switch. It is hanging on every restart.

---

### Post by jeremy31 on 2015-12-18
Hopefully this can be deleted after a kernel update ```
echo "blacklist ideapad-laptop" | sudo tee -a /etc/modprobe.d/idealist.conf
```
That should keep the wifi going after reboot instead of ```
sudo modprobe -r ideapad-laptop
```

What kernel are you using? ```
uname -a
```

And the following code should help with disconnects on wifi ```
echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

Reboot for the new commands to take affect and see if you can download updates

---

### Post by Vikas_K_R on 2015-12-18
Hi,
Thanks for your response. Well, as it hung on every restart so, I did a reinstall of ubuntu 14.04 and as it came up, before your latest response arrived, I quickly ran your first suggested command:
Code:
*sudo modprobe -r ideapad-laptop*and 
it connected to wireless as it did last time. I had planned to run Software Updater hoping this would resolve the issue. Well, at the moment it is updating. I will post the result.
The Kernal details before update:
[I]kiara@kiara-Lenovo-G50-30:~$ uname -a
Linux kiara-Lenovo-G50-30 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux[/I]
After the update, should I run your last suggested command as follows:
Code:
* echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf*
At the moment, update is going on okay and there is no disconnect issue.

---

### Post by Vikas_K_R on 2015-12-18
Voila! Seems like the issue is resolved. Thanks a ton jeremy31.
Though the laptop still hangs on "Restart" and I have to reboot it by hard pressing power switch, the wifi issue is resolved. 
After Software update, the wireless now connects automatically. The kernel also is a new version now:
[COLOR=#000080][I]kiara@kiara-Lenovo-G50-30:~$ uname -a
Linux kiara-Lenovo-G50-30 3.19.0-41-generic #46~14.04.2-Ubuntu SMP Tue Dec 8 17:46:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux[/I][/COLOR]
Hopefully it should work now. Must I start a new thread about the Hang on Restart issue?

---

### Post by jeremy31 on 2015-12-18
The hang is likely from the interrupted update but we should be able to get rid of the blacklist on ideapad-laptop with ```
sudo rm /etc/modprobe.d/idealist.conf
```

Does it hang when you ```
sudo shutdown -r now
```

---

### Post by Vikas_K_R on 2015-12-18
Hi,
The Code:
[COLOR=#000080]sudo rm /etc/modprobe.d/idealist.conf[/COLOR]
returns following message:
[COLOR=#800080]*rm: cannot remove &#8216;/etc/modprobe.d/idealist.conf&#8217;: No such file or directory*[/COLOR]
However, it still hung after following Code:
[COLOR=#000080]sudo shutdown -r now[/COLOR]

---

### Post by jeremy31 on 2015-12-19
So is ideapad-laptop being loaded ```
lsmod | grep idea
```

I hope the next updates fixes the shutdown hang, or since you know how to get wifi working, you could do a new clean install of Ubuntu

---

### Post by Vikas_K_R on 2015-12-21
Hi, Thanks for response.
Upon running the code:
[COLOR=#000080]lsmod | grep idea
[/COLOR]I get following result:
[COLOR=#800000]kiara@kiara-Lenovo-G50-30:~$ lsmod | grep idea
**idea**pad_laptop         24576  0
sparse_keymap          16384  1 **idea**pad_laptop[/COLOR]

There is something that reminded me of the issue that popped up while I did an install of ubuntu on this laptop. I've done install three times and all the three times, after the installation is done, to complete it, it reboots itself and at reboot the message prompts "*[COLOR=#ff0000]please remove the installation media and hit ENTER[/COLOR]*". After that as it reboots, the system hangs with a blank screen. I have to long press the power switch to bring it up.
Is the problem of system hang born from that installation reboot hang? If yes, can you suggest some remedial action?
Thanks a bunch for your time and attention.

---

### Post by jeremy31 on 2015-12-21
I have had the install media hang on shutdown and it hasn't caused any issues.  Did you verifiy the md5sum on the ISO

---

### Post by Vikas_K_R on 2015-12-22
apologies jeremy31 for my less knowledge, please can you guide me as to how to check md5sum on the ISO?
Thanks for your continued support.

---

### Post by praseodym on 2015-12-22
Download the ISO to your "Download" folder and run:
```

md5sum ~/Downloads/*.iso
```

---

### Post by Vikas_K_R on 2015-12-26
Hello **jeremy31** & **praseodym**, Thanks for your response. (Apologies for delayed response, I was travelling).
I got following output when I ran the code as given by you:

kiara@kiara-Lenovo-G50-30:~$ **[COLOR=#000080]md5sum ~/Downloads/*.iso[/COLOR]**
[COLOR=#800000]**cab6dd5ee6d649ed1b24e807c877c0ae  /home/kiara/Downloads/ubuntu-14.04.3-desktop-amd64.iso**[/COLOR]

Does it detail he issue of hang on restart?
Many thanks for your support.

---

### Post by praseodym on 2015-12-26
According to [http://releases.ubuntu.com/14.04/MD5SUMS](http://releases.ubuntu.com/14.04/MD5SUMS) the checksum shall be
```

cab6dd5ee6d649ed1b24e807c877c0ae , yours is
cab6dd5ee6d649ed1b24e807c877c0ae
```
which is identical. Check these steps:

[http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

---

### Post by Vikas_K_R on 2015-12-27
Hello **praseodym**, I tried this solution before and it did not work. Well, the issue of *disabled by h/w switch* no longer exist. However, a new issue propped up. It connects to internet and remains connected so long I am working / accessing internet. If I leave it idle for a small time, though it shows wifi connected to same hotspot, it won't access internet anymore and wouldn't open any page. I got to restart the laptop in order to have internet access. 
Please, can you advise any solution?
Thanks.

---

### Post by jeremy31 on 2015-12-28
Sounds like power management kicking in
```
echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

Reboot

---

### Post by Vikas_K_R on 2015-12-31
Thanks very much my learned friend **jeremy31**. You are a master!
i ran this code as advised by you and over last 2 days, worked with different wifi hotspots on two same laptops and found the issue resolved. Thank you.
Thanks to **praseodym** too.
Happy new year. 
I shall close this thread as resolved.

---

