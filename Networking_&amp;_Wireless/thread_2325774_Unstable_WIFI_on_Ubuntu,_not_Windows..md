---
title: "Unstable WIFI on Ubuntu, not Windows."
date: 2016-05-25
forum: Networking &amp; Wireless
---

### Post by fgg2 on 2016-05-25
Hello. I have a dual boot with Windows 10 and Ubuntu 16.04. My router uses DHCP. I don't have any connection problems on Windows. 
On Ubuntu, however, I sometimes have Internet access, other times I don't. I usually get redirected to 192.168.0.1 when I use a web browser.
Sometimes the connection drops and the WIFI connections on the Network Manager disappear. The Network Manager shows "Wifi device not ready".
The same happens if I disconnect from my WIFI connection. I have to restart the Network Manager to make the WIFI connections reappear.
One time it crashed completely, with the icon disappearing and a message showing:

Ubuntu has experienced an internal error.
ExecutablePath
 usr/bin/NetworkManager

Rebooting doesn't seem to bring the connection back, it's just random.
Sometimes I start having connection problems after a couple of minutes of using Ubuntu; other times I don't have any problems for hours, but there's not a single day where these appear.

Any help would be appreciated.

---

### Post by praseodym on 2016-05-25
If it works, try
```

sudo apt-get install --reinstall network-manager network-manager-gnome
```

---

### Post by fgg2 on 2016-05-25
I tried the code, but I'm still having problems.

---

### Post by jeremy31 on 2016-05-25
This might be related to the bug I referenced [here](http://ubuntuforums.org/showthread.php?t=2321311&p=13481428#post13481428)

---

### Post by fgg2 on 2016-05-26
```
systemctl restart NetworkManager.service
```

Doesn't seem to fix it. I'm still having errors loading webpages, getting redirected to 192.168.0.1, etc.

Would installing an older Ubuntu be worth it, say 12.04, to see if it's a 16.04 related problem?

---

### Post by praseodym on 2016-05-26
Please run the wireless-script from the sticky thread and show the outputs

---

### Post by fgg2 on 2016-05-29
Hi. I did what the sticky thread said, updated and ran the script.
These are the results:

[http://pastebin.com/vtuxSUsq](http://pastebin.com/vtuxSUsq)

On a sidenote, my Network Manager can't find any WIFI now, it always shows "Wi-Fi Network device not ready".
Turns out I have a Broadcom card... I'm going to reinstall Ubuntu and install the right driver.

I'll post later with the results.

I reinstalled Ubuntu 16.04 64-bit, and updated using:

```

[SIZE=2]sudo apt-get update
sudo apt-get dist-upgrade[/SIZE]
```

The Network Manager is working properly now, but I still have connection problems.
This is my wireless card:

[FONT=courier new]Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)[/FONT]

The sticky thread about Broadcom says to install the following for 14e4:4365:

[FONT=courier new]bcmwl-kernel-source

[FONT=arial]But Additional Drivers indicates the following:

[/FONT]The device is using an alternative driver: Using Broadcom 802.11 Linux STA wireless driver source from [FONT=courier new]bcmwl-kernel-source (propietary).
[FONT=arial]
Do I still purge it and install it again?

```

[SIZE=2]sudo apt-get purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source[/SIZE]
```
[/FONT][FONT=arial]
I'm also getting this message:
“Network service discovery disabled. Your current network has a .local  domain, which is not recommended and incompatible with the Avahi network  service discovery. The service has been disabled.”[/FONT][/FONT][/FONT]

---

### Post by jeremy31 on 2016-05-29
Run the script again and post the new results.  You have the correct driver

---

### Post by fgg2 on 2016-05-29
I ran the script again with a wired connection; these are the results:

[http://pastebin.com/XrQK3dEJ](http://pastebin.com/XrQK3dEJ)

---

### Post by jeremy31 on 2016-05-29
Can you change the router to channel 9 and set the encryption to WPA2?

---

### Post by fgg2 on 2016-05-29
I'm gonna try that later, but isn't there something else I can try that doesn't involve changing router settings?

Ok, I changed "Autoselect" to "Channel 9" and "WPA (recommended)" to "WPA2".
Still no results, connection is still unstable.

I set settings back to "Autoselect" and "WPA (recommended)".

I'm starting to guess my problem doesn't have a solution. So Ubuntu is incapable of providing WIFI connection and that's it?

---

### Post by jeremy31 on 2016-05-31
No, Ubuntu is capable of wireless but the Broadcom supplied driver for your chipset seems to be very unstable at this point in time, there have been complaints on arch linux forums for the past few months about bcmwl on kernel 4.2 and higher

---

### Post by fgg2 on 2016-05-31
I see. So I just have to wait for an update/upgrade/fix ?

---

### Post by jeremy31 on 2016-05-31
It may help to file a [bug report](http://ubuntuforums.org/showthread.php?t=1011078) against package bcmwl-kernel-source

I tried adding patches to a version used in 14.04 from the 16.04 module and it failed.  You could try Ubuntu 14.04 or 14.04.1 and see if it works better until Broadcom fixes this

---

### Post by RobGoss on 2016-05-31
> **fgg2 said:**
> I see. So I just have to wait for an update/upgrade/fix ?

Hello and welcome, this may sound odd but have you try doing a re-installation again? sometimes things don't download for some reason or other with a new installation and if installed a second time may correct anything that may me missing and fix any issues you're having. It's worth a try after all it might help

Second, there are lighter versions of Ubuntu you might also want to try that may work better like [Lubuntu]("http://lubuntu.net/") or[ Kubuntu]("http://www.kubuntu.org/")

---

### Post by fgg2 on 2016-06-01
> **RobGoss said:**
> Hello and welcome, this may sound odd but have  you try doing a re-installation again? sometimes things don't download  for some reason or other with a new installation and if installed a  second time may correct anything that may me missing and fix any issues  you're having. It's worth a try after all it might help

Second, there are lighter versions of Ubuntu you might also want to try that may work better like [Lubuntu]("http://lubuntu.net/") or[ Kubuntu]("http://www.kubuntu.org/")

Hi. I already reinstalled Ubuntu 16.04 a couple of times.
Now I have a triple boot with Windows 10, Ubuntu 16.04 and another Linux distro (I'm using this last partition to try different Linux distros).
I tried Lubuntu 15.04 and Linux Mint 17.3 Cinnamon. Wi-Fi is also unstable in those, just like Ubuntu 16.04.

> **jeremy31 said:**
> It may help to file a [bug report]("http://ubuntuforums.org/showthread.php?t=1011078") against package bcmwl-kernel-source

You could try Ubuntu 14.04 or 14.04.1 and see if it  works better until Broadcom fixes this

I'm unable to install Ubuntu 14.04 or 14.04.01, during installation I get this message:

[FONT=courier new]The 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot.[/FONT]

Then another message pops up saying the installer has crashed.

---

