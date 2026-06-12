---
title: "AirLive WL-1600USB 802.11g (Realtek RTL8187L) - not working"
date: 2014-07-31
forum: Networking &amp; Wireless
---

### Post by hrvojet on 2014-07-31
I can't make wireless_script.txt executable.

Lubuntu 14.04. with no internet access.

I'm trying to install AirLive WL-1600USB 802.11g (Realtek RTL8187L), downloaded drivers but don't know how to instal them.

I'm googling for a week and loosing my patiente a bit.

---

### Post by varunendra on 2014-07-31
Welcome to the forums hrvojet! :)

How are you trying to make it executable?

By the way, you can run it directly as follows -

Copy it onto your Desktop, then open a terminal and run the following command in it -
```
bash Desktop/wireless_script.txt
```
..Then provide your login password when the script asks for it.

You shouldn't need to install drivers for an RTL8187L card, the required drivers are already included with the Linux kernel. The script report should be able to tell us what the problem is.

---

### Post by hrvojet on 2014-07-31
Thanks.
Done that. 
*Results saved in "*[I]wireless_script.txt"

[/I]What next?

---

### Post by varunendra on 2014-07-31
> **hrvojet said:**
> Thanks.
Done that. 
*Results saved in "*[I][COLOR="#FF0000"]wireless_script.txt[/COLOR]"

[/I]What next?

It must be "**wireless-info.txt**" or "wireless-info.tar.gz" file.

You have to upload its contents here, or attach the file itself in your next post.

---

### Post by hrvojet on 2014-07-31
[http://pastebin.ubuntu.com/7917136/](http://pastebin.ubuntu.com/7917136/)

---

### Post by varunendra on 2014-07-31
The WiFi adapter doesn't appear anywhere in the report. Was it plugged in when you ran the script?

---

### Post by hrvojet on 2014-08-01
[I][   62.517266] **rtl8187:** Customer ID is 0xFF
[   62.574357] **rtl8187**: wireless switch is on
[   63.216873] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  462.614662] ieee80211 phy1: hwaddr <MAC address removed>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[  462.882079] rtl8187: Customer ID is 0xFF
[  462.891068] **rtl8187**: wireless switch is on
[  477.049067] **rtl8187**: wireless radio switch turned off
[  477.365434] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  477.455745] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  482.023579] rtl8187: wireless radio switch turned on
[/I]
**rtl8187** appears through text many times, tis is not it?. It is connected all the time via usb hub.
When i tried lubuntu from DVD with WinXP on WiFi worked fine

---

### Post by varunendra on 2014-08-01
Noticed that, it's the driver, but couldn't find the _device_ in lsusb or nm-tool or iwconfig, or rfkill list etc. So had to believe that maybe the messages were old, when it was plugged in, but not anymore.

Can you please post back the outputs of -
```
lsusb -t
usb-devices
```
..while it is plugged in?

And do you have only one USB port on this system? What kind of laptop/desktop it is? How old? Model name/no.?

---

### Post by hrvojet on 2014-08-03
With HUB
[http://pastebin.ubuntu.com/7946154/](http://pastebin.ubuntu.com/7946154/)

Directly into USB port
[http://pastebin.ubuntu.com/7946181/](http://pastebin.ubuntu.com/7946181/)

Old IBM, i think R31

---

### Post by hrvojet on 2014-08-03
new wireless info

[http://pastebin.ubuntu.com/7946244/](http://pastebin.ubuntu.com/7946244/)

---

### Post by hrvojet on 2014-08-04
Apparently only issue here was my lack of knowledge lubuntu :mad:.
I didn't know that I have to manually insert SSID of prefered network.(not have list available networks like in Windows)

Thanks for Your effort Varun.

---

### Post by varunendra on 2014-08-04
> **hrvojet said:**
> (not have list available networks like in Windows)

What? Do you mean missing nm-applet icon from notification area? If so, that is a bug in Lubuntu 14.04, which can be fixed with steps given here : [http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

Sorry for missing the 'Lubuntu' part twice, it should have alarmed me with the very first post, I must have been super-tired when I picked your thread up.

I was about to blame the USB 1.1 interface which is apparently the only USB interface on your laptop, and will severely limit the performance anyway (max data transfer speed of USB 1.1 is 12 Mbps! ).

---

