---
title: "WUSB54G v4 drivers installed yet invalid by Gutsy Gibbon"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by linuxquestusa on 2008-07-28
Recently upgraded to Gutsy Gibbon.

Currently have a Linksys WUSB54G v4 wireless adapter that I'm trying to use with Gutsy Gibbon.

Downloaded the latest non Vista drivers from Linksys web site.

Here's what I've done so far to resolve this situation along with the results:

1. Installed WUSB54Gv4.exe into the home directory and extracted it to a folder titled Linksys in the home directory.

2. Opened a terminal session and typed the following:

sudo ndiswrapper -i rt2500usb.inf
sudo ndiswrapper -i rt2500usb.sys
sudo ndiswrapper -i rt2500usb.ca  (this is what is listed in the drivers folder)

3. Installed ndiswrapper as a module. Typed

sudo depmod -a
sudo modprobe ndiswrapper

4. Prevented the native driver for this device from loading by typing the following:

sudo modprobe -r rt2500usb

5. Then edited the /etc/modprobe.d/blacklist file by typing the following:

sudo gedit /etc/modprobe.d/blacklistrt2500usb

6. Connected the Linksys wireless adapter via usb to the computer. Then typed the following:

ndiswrapper -l

The result is that it shows these drivers as invalid.

It would be a BIG help if anyone on this forum could provide quick and easy instructions to resolve this situation.

It would also be greatly appreciated.

Paul

---

### Post by caljohnsmith on 2008-07-28
> **linuxquestusa said:**
> 
sudo ndiswrapper -i rt2500usb.inf
sudo ndiswrapper -i rt2500usb.sys
sudo ndiswrapper -i rt2500usb.ca  (this is what is listed in the drivers folder)
When using ndiswrapper, you only need to install the .inf and make sure the .sys file is in the same directory. Thus all you need is the "sudo ndiswrapper -i rt2500usb.inf" but don't try to install the .sys or .ca file. Do a "ndiswrapper -l" and uninstall any drivers it lists, and then make sure that the /etc/ndiswrapper directory is empty. If it is, then just install the .inf file with ndiswrapper. 
> 
sudo gedit /etc/modprobe.d/blacklistrt2500usb

Is that a typo? It should be:
```
gksudo gedit /etc/modprobe.d/blacklist

```
And then in that file you would add the line:
```
blacklist rt2500usb

```
Try those steps and let me know how it goes. :)

---

### Post by linuxquestusa on 2008-07-28
> **caljohnsmith said:**
> When using ndiswrapper, you only need to install the .inf and make sure the .sys file is in the same directory. Thus all you need is the "sudo ndiswrapper -i rt2500usb.inf" but don't try to install the .sys or .ca file. Do a "ndiswrapper -l" and uninstall any drivers it lists, and then make sure that the /etc/ndiswrapper directory is empty. If it is, then just install the .inf file with ndiswrapper. 

Is that a typo? It should be:
```
gksudo gedit /etc/modprobe.d/blacklist

```
And then in that file you would add the line:
```
blacklist rt2500usb

```
Try those steps and let me know how it goes. :)
Great news!

I've got the following info from typing ndiswrapper -l

rt2500usb : driver installed
device (13B1:000D) present (alternate driver: rt2500usb)

Now the situation I have is that I'm not able to pull and web pages even the Linksys wireless adapter light is on.

Do you have any recommendations to resolve this?

---

### Post by linuxquestusa on 2008-07-28
> **caljohnsmith said:**
> When using ndiswrapper, you only need to install the .inf and make sure the .sys file is in the same directory. Thus all you need is the "sudo ndiswrapper -i rt2500usb.inf" but don't try to install the .sys or .ca file. Do a "ndiswrapper -l" and uninstall any drivers it lists, and then make sure that the /etc/ndiswrapper directory is empty. If it is, then just install the .inf file with ndiswrapper. 

Is that a typo? It should be:
```
gksudo gedit /etc/modprobe.d/blacklist

```
And then in that file you would add the line:
```
blacklist rt2500usb

```
Try those steps and let me know how it goes. :)
Hi caljohnsmith,

I have even better news!

I now have Internet access using Ubuntu 7.10!  YA BABY!!

Talk about an accomplishment!  WOW!

This was a frustrating and learning expierence for the record books.

Your right, cleaned out ndiswrapper directory and checked the Internet settings and rebooted the computer and everything is working fine.

Thanks again.

Linuxquestusa

---

