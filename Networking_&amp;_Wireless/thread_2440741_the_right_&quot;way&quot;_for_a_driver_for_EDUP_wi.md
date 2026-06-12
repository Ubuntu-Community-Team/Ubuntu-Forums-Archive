---
title: "the right &quot;way&quot; for a driver for EDUP wireless USB adapter"
date: 2020-04-14
forum: Networking &amp; Wireless
---

### Post by datagueule on 2020-04-14
Hi All,

I purchased a wireless USB adapter for my desktop (supposed to work on linux) 
But I got a bit lost with the driver installation. 

I found on the [website ]("http://www.szedup.com/product-item/wireless-usb-adapter-6dbi-antenna/#tab-id-1")that the model is EP-MS8551. So I could find the driver on the website brand [here]("http://www.szedup.com/support/driver-download/ep-n8551-driver/"). 
The driver is a .zip file, so I first search where to copy past the folder, but I realized that might be a bad idea. from the README:

```
Build Instructions:  
====================

1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.

3> In os/linux/config.mk 
    define the GCC and LD of the target machine
    define the compiler flags CFLAGS
    modify to meet your need.
    ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
       => #>cd wpa_supplicant-x.x
       => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
    ** Build for being controlled by WpaSupplicant with Ralink Driver
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       => #>cd wpa_supplicant-0.5.7
       => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make
    # compile driver source code
    # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
      => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
    $/sbin/rmmod rt2870sta
```

but I m confused here. they say to define the kernel to the LINUX_SRC. But there are a lot of lines in the makefile with that, and I have no idea what to modify and how. That s just point 2. Point 3 I don t know how to define all this. It seems really complicated so I tried to find another source looking for RT2870STA which I understood was the driver name. I found [this]("https://wiki.debian.org/rt2870sta#supported") but in the list of supported devices, there is no EDUP EP-MS8551. Would it still work?

anybody has an easier way? 

thank you!

---

### Post by chili555 on 2020-04-14
Please insert the device and help us identify the exact device by running and posting:

```
lsusb
uname -r
```

Also, check to see if the probable built-in driver has already loaded:

```
lsmod | grep -e rt2 -e mt76
```

If you are having trouble with the built-in driver, or there isn't a built-in driver, you aren't going to fix it by installing this creaky old antique.

---

### Post by datagueule on 2020-04-14
Hi again chili! thanks for your help :D 

```
5.3.0-46-generic
```

```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 003 Device 003: ID 1532:022a Razer USA, Ltd 
Bus 003 Device 002: ID 045e:077b Microsoft Corp. 
Bus 003 Device 015: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter
Bus 003 Device 005: ID 0a5c:21f1 Broadcom Corp. HP Portable Bumble Bee
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
mt7601u               110592  0
mac80211              847872  1 mt7601u
cfg80211              704512  3 wl,mt7601u,mac80211

```

---

### Post by chili555 on 2020-04-15
> mt7601u               110592  0
mac80211              847872  1 mt7601u
cfg80211              704512  3 [COLOR="#FF0000"]wl[/COLOR],mt7601u,mac80211Ahhh! The old "install a Broadcom driver for a Ralink/Mediatek device" technique! It never works, sadly.

Let's remove it:

```
sudo apt purge bcmwl-kernel-source
sudo modprobe -r wl
```

Any improvement?

As you can see, the built-in driver mt7601u loaded. Does the wireless not work or not work properly? Please tell us the issue.

May we also see:

```
dmesg | grep -e wlx -e mt76
```

---

### Post by datagueule on 2020-04-15
Hi Chili! 

just for a background, I came from [here]("https://ubuntuforums.org/showthread.php?t=2439972&p=13944377#post13944377")
:D so my wifi was working but super slow and you told me the driver had an issue, so I got an USB wireless :) 

so I purged the bcmwl-kernel but upon  ```
sudo modprobe -r wl
``` I got this: ```
modprobe: FATAL: Module wl not found.
```

```
(base) adrien@datagueule:~$ dmesg | grep -e wlx -e mt76
[   21.022598] mt7601u 3-12:1.0: ASIC revision: 76010001 MAC revision: 76010500
[   21.023610] mt7601u 3-12:1.0: Firmware Version: 0.1.00 Build: 7640 Build time: 201302052146____
[   24.282866] mt7601u 3-12:1.0: Vendor request req:02 off:0a44 failed:-110
[   27.482957] mt7601u 3-12:1.0: Vendor request req:02 off:0230 failed:-110
[   30.722851] mt7601u 3-12:1.0: Vendor request req:02 off:0400 failed:-110
[   33.946957] mt7601u 3-12:1.0: Vendor request req:02 off:0800 failed:-110
[   37.210875] mt7601u 3-12:1.0: Vendor request req:07 off:0404 failed:-110
[   40.410861] mt7601u 3-12:1.0: Vendor request req:02 off:0404 failed:-110
[   43.642856] mt7601u 3-12:1.0: Vendor request req:02 off:0800 failed:-110
[   46.842871] mt7601u 3-12:1.0: Vendor request req:02 off:0238 failed:-110
[   50.042869] mt7601u 3-12:1.0: Vendor request req:07 off:0238 failed:-110
[   53.242947] mt7601u 3-12:1.0: Vendor request req:02 off:0238 failed:-110
[   56.442859] mt7601u 3-12:1.0: Vendor request req:02 off:0238 failed:-110
[   59.642881] mt7601u 3-12:1.0: Vendor request req:02 off:09a0 failed:-110
[   62.846880] mt7601u 3-12:1.0: Vendor request req:02 off:09a4 failed:-110
[   66.106876] mt7601u 3-12:1.0: Vendor request req:02 off:09c4 failed:-110
[   69.413828] mt7601u 3-12:1.0: Vendor request req:02 off:0a6c failed:-110
[   72.799087] mt7601u 3-12:1.0: Vendor request req:42 off:0230 failed:-110
[   76.101364] mt7601u 3-12:1.0: Vendor request req:07 off:0080 failed:-110
[   79.415365] mt7601u 3-12:1.0: Vendor request req:02 off:0080 failed:-110
[   82.774364] mt7601u 3-12:1.0: Vendor request req:02 off:0080 failed:-110
[   82.774402] mt7601u: probe of 3-12:1.0 failed with error -110
[   82.775077] usbcore: registered new interface driver mt7601u

```

is it normal? 

thanks!

---

### Post by jeremy31 on 2020-04-15
What kernel?  ```
uname -r
```

---

### Post by datagueule on 2020-04-15
5.3.0-46-generic

---

### Post by jeremy31 on 2020-04-15
Try ```
sudo apt install git dkms
git clone https://github.com/jeremyb31/mt7601u-5.3.git
sudo dkms add mt7601u-5.3
sudo dkms install mt7601u/1.0
```
Reboot

---

### Post by datagueule on 2020-04-15
thanks! 
so my desktop doesn t have an internet connection. But the dkms was already installed with newest version and git also, and I cloned the repo to my laptop, then transfer it to my desktop computer with an USB key

the ```
sudo dkms add mt7601u-5.3
``` worked

but ```
sudo dkms install mt7601u/1.0
```
said 
```
Error! could not find module source directory.
Directory: /usr/src/mt7601-1.0 does not exist
```

i tried ```
sudo dkms install mt7601u-1.0
``` with a dash
```
Error! Invalid number of arguments passed.
Usage: add <module>/<module-version> or
add -m <module>/<module-version> or 
add -m <module> -v <module-version>

```

---

### Post by CelticWarrior on 2020-04-15
> **datagueule said:**
> thanks! 
so my desktop doesn t have an internet connection. 

But it needs* an alternative internet connection to clone the repository. Use an Ethernet cable directly to the router or USB tethering from your phone.


* The alternative is likely above your paycheck, sorry to say.

---

### Post by datagueule on 2020-04-15
forgot to say that I cloned the git repository to my laptop, put it on my usb key, and put it on my desktop computer 

also, I unfortunately can t access the router, I'm leaving in the basement of my landlords who fled the coronavirus! but I have a big homework for my deep learning class so I unfortunately need internet on my desktop computer :D a nice alternative would be buying my own house and my router, I think I ll go also with two RTX 2080 to run my model if I could haha :D

---

### Post by datagueule on 2020-04-16
Anybody has a solution? I have a presentation tonight and I really need internet :( 

thank you :D

---

### Post by CelticWarrior on 2020-04-16
You should cd into the folder then run the commands.

---

### Post by chili555 on 2020-04-16
> put it on my usb key, and put it on my desktop computerWhere did you put it when you copied it over from the USB key? Your desktop? If so, then:

```
cd Desktop
```

Confirm that the file is there:

```
ls
```

It should show up as *mt7601u-5.3*. If so, proceed with the steps Jeremy posted:

```
sudo dkms add mt7601u-5.3
sudo dkms install mt7601u/1.0
```Post back any errors.

---

### Post by datagueule on 2020-04-16
Hi ! 

thanks for your help! 

so I pasted it into the /home, and from there I ran Jeremy stuff but it didn t worked. I went into the folder *mt7601u-5.3*.  and ran the command again and it did worked ! I m not sure why, because it seemed more logic to run the command on the /home. 
it seems that internet is running fine and is stable. I cross fingers that it stays like this! 

thanks again

---

### Post by jeremy31 on 2020-04-16
Post results for ```
dkms status
```

The fix I used is a modification of a patch on a bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1716301/comments/53](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1716301/comments/53)

---

