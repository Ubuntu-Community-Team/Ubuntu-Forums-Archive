---
title: "gnome network manager doesn't check dial-up status --&gt; no vpn possible"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by airflow on 2007-07-06
Hi there,

I'm trying ubuntu for the first time these days, and I'm fairly impressed. Many things work quite easily and without much config-hassling. I'm in the progress of completing the missing links to really come on par with my windows-installation to finally make the move to linux not only at my home (where I use Gentoo for years), but also with my laptop for work.

One of those links is a problem I have with the gnome network manager. I need wireless with WPA (works), I need dial-up for my UMTS/GMS PCMCIA-Datacard (works), and I need VPN-client functionality (works like a charm with vpnc in connection with the network manager).

The problem is using dial-up and VPN *together*. It's just not possible - the network manager is not offering me connecting via VPN if I'm in the Internet via the Datacard. It works, if I'm wired or wirelessly (802.11b/g) connected.

I think the real problem is that the tool is not aware of the actual status of the dial-up connection and because of this the tool can't show it to the user. This also has a big consequence/drawback - as the tool doesn't know about the status of the connection, the icon above is shown as "not connected" --> and then you also can't start a VPN-connection!

This is really a broken design of the tool. A common use-case is the following: I'm travelling with my laptop and have a UMTS/GSM PCMCIA-Datacard with me. I connect to the Internet (with the dial Up functionality of network-manager) and then want to start VPN to establish a secure tunnel to my company. I can't do that, because network-manager doesn't let me start VPN (it's greyed out), because it doesn't know about the dial-up status and thinks it's not connected. If I were at a wireless-hotspot, network-manager does check the status and offers me to connect via VPN (works perfectly, by the way).

Perhaps I'll find a workaround by using some scripts to manually start the VPN-connection, but I would rather like to see this fixed. If i can help/test/do anything (except programming, which I can't), I'll gladly do it.

Best Regards,
airflow

---

### Post by bimargulies on 2007-12-20
The scenario you described was working for me until a day or two ago, when it stopped.

I'm nearly tempted to look at the source of the network manager and see what it is thinking.

---

### Post by madjr on 2007-12-22
am also having this problem with network manager and dial-up

firefox works fine, but pidgin or other messegers don't work because they depend on network manager ...??

any help here :confused:

---

