---
title: "DSL Ethernet Modem Help!"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by ThorsDecree on 2007-07-07
Hi, my ISP is totally useless... ("Sorry, your operating system is not supported") and I MUST have internet access on my Xubuntu6 box. I have an Alcatel SpeedTouch Home Ethernet DSL modem and a DSL subscription. I want to be able to access internet from my room. Under network-admin I have listed Eth0 (the modem, active connection) and ppp0 ("modem connection", unconfigured). The ppp0 is an internal dial-up modem, right? The ppp0 modem locations are:

/dev/modem
/dev/tty0
/dev/tty1
/dev/tty2
/dev/tty3

None of which work when configuring the modem. It will not autodetect, and fails configuration. I want to configure the Eth0 connection, the external DSL modem.

My modem has sockets for "power", "10Base T/MIDI-X", and "line." I connected "line" to a dsl filter and phone jack via a telephone line. I connected 10Base T/MIDI-X to the computer via the larger ethernet port with the telephone symbol by it. Of course, I plugged "power" into my power strip.

Did I configure this correctly? I don't know if my computer has a built-in dialup modem (is that ppp0? Or would that show up as unconfigured even if I don't have one?)

How can I find out if I have the built-in modem, and how can I get info about my internet connection details without asking my totally useless ISP? (Bellsouth, if it's relevant)

Basically, I need to connect to the internet. I don't care if it's dialup or DSL, but I'd obviously prefer DSL since I have many xubuntu components to download. When I configure Eth0, there's a field for "host" and "password"

Is that my ISP account or my computer? I can phone my ISP for info but over chat they were totally unhelpful, I don't think I'll get anything more out of a conversation with a barely-english-speaking tech support n00b anyway. Can someone please help me with some of this, or even walk me through setting up my connection?

Here's my ifconfig info:

uberhacker@uberhacker-hackpad:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:44:00:FB:8F
          inet6 addr: fe80::202:44ff:fe00:fb8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:719352 (702.4 KiB)
          Interrupt:9 Base address:0x6800

If it means anything the line sync light on my modem comes on (meaning it reads DSL connection?) and the Line RX came on once I think. IDK what that is, but the LAN light has never come on (duh...)

PLEASE HELP I'VE BEEN STRUGGLING WITH THIS FOR A LONG TIME!

Edit: lspci shows that I am using a Realtek Ethernet controller and a 3Com Corp WinModem

Cannot install pppoe due to lack of internet connection :( rofl

---

