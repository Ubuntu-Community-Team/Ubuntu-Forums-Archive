---
title: "Wireless Network Adapter not ON"
date: 2020-08-30
forum: Networking &amp; Wireless
---

### Post by Alienspecimen on 2020-08-30
My school requires that I have a dual boot Ubuntu/Windows machine.

After installation, I was surprised to see that I have no wireless network capabilities. The Windows side works perfectly, the Ubuntu thinks that I have only Ethernet adapter.

I then followed these directions:

[https://itsfoss.com/fix-no-wireless-network-ubuntu/](https://itsfoss.com/fix-no-wireless-network-ubuntu/)

Unfortunately, it tells me that it is applying changes, but the progress bar is not moving, it is stuck at about 10%. I then erased the image, placed a fresh one and tried again, but the result was the same.

I know that Ubuntu knows about the adapter as after query (do not remember off the top of my head how exactly) I got the following:

04:00.0 BCM43142 802.11 b/g/n (rev 01)

What else can I do? I'd rather not try to reinstall Ubuntu, as I had a install crash on another system and this is my working machine. I'd rather fix whatever is wrong with it. 

The computer is a Dell XPS 8700 desktop with a Windows 10 OS and intel Core i5 processor, about four years old.

Thanks in advance.

---

### Post by Alienspecimen on 2020-08-30
I have an update.

I tried to reinstall Ubuntu number of times and found out that when I am running it from the USB stick, I am able to turn on the adapter. Once I proceed with installation, I end up with a system that is unable to recognize my wireless adapter.

---

### Post by Alienspecimen on 2020-08-31
Update number two:

I reinstalled several times. During the last installation I tried to trick it by connecting to the Wi Fi first while running Ubuntu from the USB stick. That gave me the opportunity to select the option of downloading third party drivers for the Wi Fi adaptor and others during the installation. 

Unfortunately, once installed, the Wi Fi adapter cannot be seen again as if I dont have it.

Any help would be appreciated.

---

### Post by tea for one on 2020-08-31
> **Alienspecimen said:**
> 

04:00.0 BCM43142 802.11 b/g/n (rev 01)

It looks like you have proprietary Broadcom wireless.

Have a look at this thread [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

I think that you need to ```
sudo apt install bcmwl-kernel-source
```

You will need internet acces via:-

Ethernet 
Tether to your mobile if you have a suitable device
Borrow a linux friendly usb wireless adaptor

---

### Post by grahammechanical on 2020-08-31
You also need to make sure that WiFi is not turned off in Windows. Run this command

```
rfkill list
```

You should see something like this

> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

If Hard blocked = yes then the WiFi adapter is switched off at a hardware level. May be in windows or in the BIOS/UEFI setting utility. Soft blocked = yes means that it is switched off in Ubuntu. We can switch off WiFi in Settings. Or Ubuntu lacks a driver.

Regards

---

### Post by Alienspecimen on 2020-08-31
I do not know. Using your code did not yield any results, but then I used 1lspci -knn | grep Net -A3; rfkill list. Below is what I got:


04:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
    Kernel driver in use: bcma-pci-bridge
    Kernel modules: bcma
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no






1b/g/n [14e4:4365] (rev 01)
    Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
    Kernel driver in use: bcma-pci-bridge
    Kernel modules: bcma

---

### Post by Alienspecimen on 2020-08-31
It is not working, it is asking to do this:

Media change: please insert the disc labeled
 'Ubuntu 18.10 _Cosmic Cuttlefish_ - Release amd64 (20181017.3)'
in the drive '/media/cdrom/' and press [Enter]


I previously mounted the image in the directory using this code:

sudo mkdir /media/cdrom
cd ~
sudo mount -o loop ubuntu-* /media/cdrom

Do I need to make a CD? and if so, is it with the image only? Why the need for Ethernet?

---

### Post by Alienspecimen on 2020-09-01
The computer is a Dell XPS 8700 desktop with a Windows 10 OS and intel Core i5 processor, about four years old. I just configured it as a dual-boot machine. Unfortunately, the wireless isnt working. lshw -C network yields the following result:

                        *-network UNCLAIMED
        description: Network controller
        product: BCM43142 802.11b/g/n
        vendor: Broadcom Inc. and subsidiaries
        physical id: 0
        bus info: pci@0000:04:00.0
        version: 01
        width: 64 bits
        clock: 33MHz
        capabilities: cap_list
        configuration: latency=0
        resources: memory:f7100000-f7107fff
  
Also, there is no WiFi information in settings menu just as if I do not have a card.

Any help would be greatly appreciated.

Thanks in advance.

P.S. I searches, but the info found was relevant to older distributions and upon attempting to apply those fixes,  I mostly got that whatever code is needed is no longer downloadable.

P.P.S. Interestingly enough, If I run it only from the USB stick it does not have any problems showing and connecting to WiFi.

---

### Post by tea for one on 2020-09-01
Please post the output within code tags **#** using Adv Reply.

```
lsb_release -a
```

---

### Post by Alienspecimen on 2020-09-01
Thank you for your reply. Below is the requested output:

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal

---

### Post by tea for one on 2020-09-01
From your post no. 6

> 04:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
Kernel driver in use: bcma-pci-bridge
Kernel modules: bcma
0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no

From the advice in this thread [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

> 14e4:4365                  Special case #2                       bcmwl-kernel-source

You need to use a different driver but it is difficult to understand exactly what you have done so far, especially when you mention Cosmic Cuttlefish in post no. 7.

In your position, I would back up my data, reinstall cleanly 20.04 and then add the correct driver as follows:-

```
sudo apt install bcmwl-kernel-source
```

Alternatively, ask the mods to move the thread to **Networking & Wireless**, where more knowledgeable users can help you remove and replace your wireless drivers.

---

### Post by Alienspecimen on 2020-09-01
Sorry,

I did not want to burden with details, but I started with 18.10 installation, because a link on Ubuntu website let me to it as being the latest version (dont ask me how, I tried to retrace my steps already).

Subsequently I did install the 20.04.1, but the exact same problem persists.

Best

---

### Post by CelticWarrior on 2020-09-01
A good clean, from scratch, installation of Ubuntu 20.04 it's a good starting point. It's supported for 5 years.
That you had an older release before is confusing for the people trying to help you and irrelevant if you now installed Ubuntu 20.04 from scratch.

The solution is the same though.
Get an alternative internet connection (Ethernet cable, USB tethering from your Android or iPhone, etc.) and run in terminal:
```
[COLOR=#000000][FONT=&quot]sudo apt install bcmwl-kernel-source[/FONT][/COLOR]
```

[COLOR=#000000][FONT=&quot]This is a one time only. 
[/FONT][/COLOR]

---

### Post by coffeecat on 2020-09-01
Threads merged and merged thread moved to Networking & Wireless sub-forum.

---

