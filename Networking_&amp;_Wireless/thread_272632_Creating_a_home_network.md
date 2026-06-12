---
title: "Creating a home network"
date: 2006-10-06
forum: Networking &amp; Wireless
---

### Post by Gannin on 2006-10-06
Greetings.  I'm trying to create a wireless home network for the purpose of sharing an Internet connection.  But first, a bit of background.

My main desktop computer has my cable modem plugged directly into it, and it also has a wireless network adapter.

My laptop also has a wireless network adapter, and I'll be getting another wireless adapter for another computer soon.

My desktop computer, the one directly connected to the cable modem, is using Firestarter as its firewall.  I would like to turn my desktop computer into an access point for the other computers in my house.  I enabled Internet connection sharing in Firestarter and set up the host (desktop) and client (laptop) computers according to the instructions in the Firestarter manual.

I should mention when it comes to accessing already established access points (such as a wireless router) the wireless capabilities of both my desktop and laptop work perfectly.

I know that the basic idea is to create a wireless network, and then share the Internet connection through Firestarter, but my desktop can't see my laptop, and my laptop can't see my desktop.

When I run iwconfig on my desktop, this is what I get:

wlan0     IEEE 802.11-DS  ESSID:"NETTEST"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I noticed it said that the mode is managed, and if I remember correctly, in order to create the sort of network I'm looking for, where all the computers in my house are networked wirelessly and my desktop is acting as an access point to share my Internet connection, then the mode needs to be ad hoc, but I'm not sure how to go about doing that.

How do I get my desktop and laptop to see each other?  And how do I get my desktop to broadcast itself as an available access point?  Thank you.

---

### Post by Gannin on 2006-10-06
As an update, I tried doing:

sudo iwconfig wlan0 mode master

on my desktop, but I received the following message:

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

---

### Post by Gannin on 2006-10-07
Another quick update.  I set both my desktop and laptop to ad-hoc, and they could then see each other, but I still haven't been able to share the Internet connection of my desktop, despite setting it up in Firestarter to do so.

---

### Post by spd106 on 2006-10-07
When you say "they can see each other" do you mean that they can ping each other?
If so then have you set the default route on the client (laptop) to the ip address of the desktop? This shouldn't be a problem if you are using the desktop as a dhcp server.

You should be able to ping a remote server on the internet. Try 128.30.52.45 (w3c.org), making sure that you haven't blocked icmp in firestarter.

---

### Post by Gannin on 2006-10-08
I actually can't ping the desktop from the laptop, even though I disabled ICMP filtering in Firestarter just to be sure.

Here's the way I'm currently setting things up as I'm trying to get this all going.

I plug my wireless network adapter into my desktop, then I open the Networking window.  I activate the wireless network adapter, give it an ESSID, then I choose static and give it the following information:

IP Address:  192.168.0.1
Netmask:  255.255.255.0
Gateway:  <empty>

Then from the command line, I use the following command:

sudo iwconfig wlan0 mode ad-hoc

Then I boot up my laptop, and when I go into the configuration for its wireless network adapter, the ESSID of my desktop is available in the available networks drop-down, so I select that and set it to static and give it the following information:

IP Address:  192.168.0.2
Netmask:  255.255.255.0
Gateway:  192.168.0.1

And then I set it to ad-hoc mode on the command line.

But I can't ping my desktop (192.168.0.1) from my laptop (192.168.0.2) or vice-versa, and enabling Internet sharing in Firestarter on my desktop doesn't seem to do anything either.

---

