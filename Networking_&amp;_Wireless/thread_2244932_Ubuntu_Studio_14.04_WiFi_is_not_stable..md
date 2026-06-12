---
title: "Ubuntu Studio 14.04 WiFi is not stable."
date: 2014-09-19
forum: Networking &amp; Wireless
---

### Post by Hanjaya on 2014-09-19
Hi,


I have a dual core Dell laptop which ran Ubuntu Desktop 32bit 14.04LTS before. When I installed that, it was connected automatically with my WiFi, I put my WiFi password and boom...the connection was very stable. Then for some reason my laptop crashed and now I freshly installed Ubuntu Studio 32bit 14.04 into the laptop, after the installation the WiFi connection is very unstable. It always connects for about the first 5 minutes after rebooting the computer and it drops afterward. I use IOGEAR GWU625 WiFi adapter. I am not sure what has happened.


Here is my **iwconfig** message.


```
wlan0 unassociated Nickname:"rtl_wifi"
Mode:Managed Access Point: Not-Associated Sensitivity:0/0
Retry: off RTS thr: off Fragment thr: off
Encryption key: off
Power Management: off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


Lo no wireless extensions.

```

Here is the **lsusb** message.


```
Bus 001 Device 002: ID 0bda:812 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter

```



Here is the **lshw** message.


```
*-network
description: Wireless interface
physical id: 2
bus info: usb@1:5
logical name: wlan0
serial: 00:21:79:c5:c0:79
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated

```

Please help. Thx.

hc.

---

### Post by weatherman2 on 2014-09-19
People will want more information to help you.  Find the "sticky" post at the top of this forum labeled "Before posting in Networking & Wireless" and download the script listed there there and post the results here.

However, one wonders why you are using a USB wireless card instead of the internal wireless card in the laptop?  Is that card disabled?  Are you sure you are connecting with this USB wireless card and not the internal card?  (The wireless script will answer these questions too.)

In many Dell laptops, it is usually cheap and fairly easy to upgrade the internal wireless card by the way.  (What model Dell laptop?)

---

### Post by Hanjaya on 2014-09-21
Hi,

My laptop doesn't have built-in wireless card.

So I did 
```
sudo apt-get update
sudo apt-get dist-upgrade
```

I downloaded the script and I saw from the output, "Broadcom" appeared next to [0280]. Then I head over to Ubuntu forum "Broadcom Guide".

The output of **lspci -nn -d 14e4:**

```
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
```

Then I sudo apt-get install firmware-b43-installer and reboot the computer. The WiFi connection is still unstable, drops after several minutes from rebooting.

Please help.

Thnx.

---

