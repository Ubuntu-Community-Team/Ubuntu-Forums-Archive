---
title: "Ndiswrapper, Static IP through command line"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by vv88 on 2007-09-01
Any help will be greatly appreciated, I've been working on this for a looong time.  A couple of questions before I get to the heart of my inquiry:

(Please note that this is a command line system: Feisty 7.04 32 Bit)

1. Is there a way to access network manager or a network manager like assistant through command line (ala lirc's module assistant).

2. Are the settings for network set in ndiswrapper then called from network/interfaces or vice versa?  If the latter:

3. Could someone please post an example file for network/interfaces for wlan0 which includes essid and wep encryption. (Static please)

This is for a myth frontend and as of now I'm doing my installing/updating via eth0, but my wlan0 will be configured to a different access point.  I followed Sam Liu's instructions in Ubuntu and Fedora and have not had a problem in getting my usb card to work (DWL-G120).   However, command line is giving me fits.  If anyone can help out I'd be grateful.

I thought I'd also note that I've followed many different tuts, documents, etc related to Ubuntu and Linux in general.  However, I'm still having problems.

---

### Post by vv88 on 2007-09-02
I figured this one out and let me first say that ssh is your best friend when dealing with this sort of issue.

Here's is what I needed to do.

**This is After successful install of ndiswrapper/prism02 drivers**

1) Set up two connections in /etc/network/interfaces (two seperate networks/access points, essid, wep)
(Note: one was for eth0, the other for wlan0)

2) Edit /etc/resolv.conf appropriately

3) Edit /etc/networks appropriately

The result was two different AVAILABLE connections: eth0, wlan0

After I had the system upgraded and necessary installations complete, I deleted every entry for eth0 and it's associated networks in resolv.conf, networks, network/interfaces.

Good to go!!!

---

