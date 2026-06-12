---
title: "Wireless not recognised LUbuntu Live"
date: 2014-04-12
forum: Networking &amp; Wireless
---

### Post by happyhacker on 2014-04-12
I have just loaded the live distro and copied to CD. In my COMPAC Pressario V4000 the live version is not seeing the wireless hardware (I assume this because the wireless button (on/off) is not lit). I have been into the config. page ans set the logon, etc. Any advice?

PS I have just tried AVLinux and that did not work but when I tried Knoppix it came up as "Wireless disabled by hardware switch" so I pressed the button and the wireless light came on. So I just need to know (if I use LUbuntu and install it as my alternative to Windows XP) what to do.

Thanks.

---

### Post by varunendra on 2014-04-12
Please show us the outputs of the following commands -
```
lspci -nnk | grep -iA2 net
rfkill list all
```
The first one will tell us about your wireless hardware, the second one about its block state.

---

### Post by happyhacker on 2014-04-13
> **varunendra said:**
> Please show us the outputs of the following commands -
```
lspci -nnk | grep -iA2 net
rfkill list all
```
The first one will tell us about your wireless hardware, the second one about its block state.

The first gives details of the Network Controller (HP Broadcom WLAN 802.11 b/g;kernal driver b43-pci-bridge) and Ethernet Controller (Kernal driver 8139too).
The second:
0: hp-wifi: wireless LAN
softblocked: no
hardblocked: no

Sorry the delay. Hope that helps.

Also, when I shutdown the Lubuntu splash screen with the activity dots just hangs there and the laptop does not turn off.

---

### Post by praseodym on 2014-04-13
Install the package **linux-firmware-nonfree** for the wireless card

---

### Post by varunendra on 2014-04-13
If what praseodym suggested couldn't fix the problem, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

If posting the contents of the report file, please use 'Code' tags. Follow the "Use Code Tags" link in my signature if you need to see a quick How To with screenshots.

---

### Post by varunendra on 2014-04-22
@happyhacker,

I'm replying to **[your post]("http://ubuntuforums.org/showthread.php?t=2082305&p=12997846#post12997846")** here, since this is the right place to continue the discussion. I have reported that post to be moved here as well.

As per the dmesg part of the report, you still haven't installed the firmware that praseodym suggested. While being connected to internet, please open a terminal (Ctrl-Alt-T) and run the following command to install it -
```
sudo apt-get install linux-firmware-nonfree
```
Then either reboot, or manually reload the driver with -
```
sudo modprobe -rv b43
sudo modprobe -v b43
```

This should activate your wireless. However, you *may* face a bug associated with this particular card + driver combination due to which you may not be able to see available networks despite a working wifi interface. If that happens with you, just run the command -
```
sudo iwlist scan
```
..and you should be able to see the networks and connect to them. If this bug occurs and you need this workaround, we can make it automatic by adding the above command (without 'sudo') in your **/etc/rc.local** file.

---

### Post by happyhacker on 2014-04-23
Well, I did what varunendra instructed (can't seem to copy the XTERM window text for you to see) and when I did the last cmd on wlan0, lo and eth0 all said "interface does not support scanning". Don't even get the wireless symbol in the task bar now.

PS no point in adding this (when it works) to rc.local due to running alive at the moment. Want to install but proving it will all work before I do that.

PS2 if I use (install) the full Ubuntu version will I get it to work that way?

---

### Post by varunendra on 2014-04-23
Erm.. I'm slightly confused by your post -
> **happyhacker said:**
> ..when I did the last cmd on wlan0, lo and eth0** all said *"interface does not support scanning"*. Don't even get the wireless symbol in the task bar now.**

PS no point in adding this **(when it works) to rc.local due to running alive at the moment.**

Please clarify, did it work or not?

The last line says "..running alive at the moment.." which suggests it did work. If so, be assured that it'll work in the installed version too. All you'll need to install the "linux-firmware-nonfree" package like suggested for current case.

The required driver for this card is already available in the kernel, only the firmware is required to be installed manually (licensing reasons).

---

### Post by happyhacker on 2014-04-23
Ah, silly me. Yes it did work. I had to press the switch and then put in the pwd. Many thanks for your kind help. Hopefully I can now move ahead with capturing the essential parts of the windows 7 settings and then install the Lubuntu. I understand I will have to come back to this thread and perform the same to get wireless back working again. Couple of things to round up:

1. What are the items needed in the config. file to set it in the installed version?

2. Is there any advice on porting the windows 7 settings (e.g. firefox stuff and folders) into Lubuntu installation?

Many thanks.

---

### Post by varunendra on 2014-04-23
> **happyhacker said:**
> 1. What are the items needed in the config. file to set it in the installed version?
If you mean getting just the wireless working, all you need to run the command -
```
sudo apt-get install linux-firmware-nonfree
```
..while being connected to internet via cable.

Another precaution is to NOT choose the "Install Updates" option during installation. It will install a wrong driver which will have to be removed to get the wireless working. You can perform the updates later once the OS is installed.

On the first attempt to connect, Network Manager will ask for your wireless security key. It will automatically store the security key that you will supply, plus other related settings to connect to the wifi automatically next time.

So installing the firmware and supplying the wireless security key are the only things that you'll need to do manually (only once). Rest of the settings will be automatically detected and stored.

> **happyhacker said:**
> 2. Is there any advice on porting the windows 7 settings (e.g. firefox stuff and folders) into Lubuntu installation?
Firefox bookmarks can be exported from Win7, then imported in Ubuntu from firefox's menu. For other settings (homepage, plugins, etc.), I don't know of a way other than manually setting those.

For folders (e.g. User Documents, Music etc. in Win7's User folders), the setup will ask you if you want to import them in Lubuntu (I haven't installed Lubuntu in a long time, so saying this from the experience of installing Ubuntu). Choose "NO" to this prompt, because all it does is simply copy all that data from Win7 into your Home directory in Lubuntu. Means duplicate copies occupying double the space on your hard disk drive.

The Windows partition can be accessed from Lubuntu, so you can always simply browse to your user data in Win7.

However, if you want to have the same data directly accessible from your Home directory, there is a much better way than duplicating it. You will need to add some mount entries in /etc/fstab file, and I'd be glad to help with that. But that is certainly far beyond the scope of the topic of this thread.

If I misunderstood your questions, or if you need more detailed help on them, I suggest you start new thread(s) for each topic with suitable title and in suitable section of the forum, and elaborate your questions there (what all you want/expect with the installation).

If your system is working with Legacy BIOS (not UEFI), and the hard disk already has 4 primary (or 3 primary + 1 extended) partitions, you may also need help with partitioning. That again is a topic suitable for a different thread. Feel free to PM me or post here the links to your new threads if you start them, and I'd be happy to help with whatever I can.

---

