---
title: "Can't connect to internet, clean install"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by killswitch1 on 2010-09-08
Hello,

I'm totally new at Linux and finally got around to doing a clean instal on a Compaq 6720s laptop- Ubuntu 10.04.1 LTS. All went well until I tried to connect to the internet. My network does not show up, the network monitor icon shows a red exclamation point. If i type lspci |grep "Network" in terminal it comes back with Ethernet Controller: Intel Corporation 8256GT 10/100 Network Connection (rev03) and Network Controller: Broadcom Corporation BCM4312 802.11a/b/g. Now if I go into System > Administrator > Hardware Drivers I then get a dialog box which states "Download package index failed, please check your network status. most drivers will not be available". What can I do to resolve this issue.
Any help would be greatly appreciated.

killswitch1

---

### Post by Madrias on 2010-09-08
As new as I am to this, I'll ask a simple question:   Do you have your wired internet connected?

---

### Post by Strategist01 on 2010-09-08
Hi there.

I don't know if it's drivers that are causing the problem - are you trying to connect via wireless? If so, just make sure that the LAN cable is unplugged and that your wireless button/switch is set to "on".

Others will help you with more advanced stuff :)

---

### Post by cake nom nom on 2010-09-08
> **Madrias said:**
> As new as I am to this, I'll ask a simple question:   Do you have your wired internet connected?

to download the download package you might have to be connected to the internet via Ethernet if you cant connect wirelessly

---

### Post by Madrias on 2010-09-08
OP has a Broadcom Wifi.  Wired will likely be needed.

---

### Post by wojox on 2010-09-08
You'll need to plug your Ethernet cable back in to download you wireless drivers.

---

### Post by bredman on 2010-09-08
It's not much help until you get your Ethernet connection working, but here is how to get your BCM4312 WiFi working.

Full details are at [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43), but here is the part you need...
**Ubuntu/Debian**

 In recent versions of Ubuntu and Debian, installing the b43-fwcutter package will handle everything for you: 

 [FONT=monospace]
  [/FONT]sudo apt-get install b43-fwcutter



You will be asked to automatically fetch and install the firmware into the right location.

Note that the BCM4312 may have problems with WEP encryption (which is useless anyway), so you should use WPA or WPA2 encryption.

---

### Post by bredman on 2010-09-08
To diagnose the status of your Ethernet connection, plug in the cable and put the following command in a terminal
ifconfig eth0

I understand that you have to type in everything by hand, so I am only interested in the line starting with "inet addr"

This will tell us if the Ethernet port can connect to your router or not.

---

### Post by killswitch1 on 2010-09-25
Sorry for the late reply. Correct, I was on wireless and all I had to do was               go wired to the internet.

Thanks for all your help.

---

### Post by mörgæs on 2010-09-25
Good. Please mark the thread 'solved'.

---

