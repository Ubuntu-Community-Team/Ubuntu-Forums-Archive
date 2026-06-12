---
title: "No wifi lubuntu 16.04.1"
date: 2016-10-08
forum: Networking &amp; Wireless
---

### Post by nginmu on 2016-10-08
I have a Compaq Presario v6000 laptop. When I installed lubuntu 15.04 I couldn't get wireless working at first, but eventually I did figure out the right commands, drivers etc.

I've now installed lubuntu 16.04.1 LTS as an 'alongside' install, with a view to completely ditching the 15.04 install in due course. Once again, no wireless in the virgin install.

Unfortunately I've entirely forgotten how I got wireless working back in 15.04

I've posted my wireless-info.tar.gz file (which I made whilst in the old 15.04 install, on the same machine) in the hope maybe someone could take a look and give me some memory joggers as to what I have to do to get the wifi working in the 16.04.1

Thanks for any help.

Snippet from wireless-info.txt:

```

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1364]
    Kernel driver in use: b43-pci-bridge

```

---

### Post by jeremy31 on 2016-10-08
You attached the script itself, not the results.  If you have ethernet access ```
sudo apt-get install bcmwl-kernel-source
```
Reboot

Due to changes in the kernel, you will need Secure Boot disabled in BIOS to use this wifi module

---

### Post by nginmu on 2016-10-08
Thanks. Tried to go back and change the attachment but had great difficulty. Hopefully this is the right file:

(yes, should be able to find a patch lead and rig up ethernet.. will try)

---

### Post by jeremy31 on 2016-10-08
I actually see that chili555's sticky post on Broadcom recommends installing the b43 firmware for that card but the wireless wiki says the bcmwl should work.
If bcmwl doesn't work just ```
sudo apt-get remove bcmwl-kernel-source && sudo apt-get install firmware-b43-installer
```

If you can't get an ethernet hook up, copy the contents from the 15.04 installs /lib/firmware/b43 and just add the files to 16.04 after ```
sudo mkdir /lib/firmware/b43
```

Reboot

---

### Post by Hadaka on 2016-10-08
Hi, if you have no access to the TalkTake router for a wired connection then try the
b43 install no internet access method.
[https://ubuntuforums.org/showthread.php?t=2316978](https://ubuntuforums.org/showthread.php?t=2316978)
else..
Please follow jermy31's suggestion.
thanks.

---

### Post by nginmu on 2016-10-08
```
sudo apt-get install bcmwl-kernel-source
``` - no joy

```
sudo apt-get remove bcmwl-kernel-source && sudo apt-get install firmware-b43-installer
``` - all now working

Thanks :-)

---

