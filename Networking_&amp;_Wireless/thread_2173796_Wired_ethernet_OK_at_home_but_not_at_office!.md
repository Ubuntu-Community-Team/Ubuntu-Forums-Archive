---
title: "Wired ethernet OK at home but not at office!?"
date: 2013-09-11
forum: Networking &amp; Wireless
---

### Post by daniel-clement on 2013-09-11
Hello,

A colleague of mine will need some help, but I was trying to figure out whit his problem could be. He's got a HP dv6-1120ef laptop (AKA "Entertainment PC") and he has installed the latest Xubuntu beside Vista which came with the PC.

When he's at home, his laptop connects like flawlessly, as well wired as wireless.

But when he's at our office (wired connection only), he can't connect with ethernet. Even stranger, this happens only under Xubuntu: Windows does connect (same plug - same cable).

How can that be? I can't have a close look at his PC until tomorrow, but I'd like to gather ideas before. Because all the pieces of solution I've seen here and there talk of an ethernet connection that is *never* working, whatever the place...

Many thanks for any input on that matter. Best regards, Daniel

---

### Post by sanderj on 2013-09-11
And on a third LAN?

Maybe the office LAN forbids/blocks non-official OSes?

I would do this:
- boot the Ubuntu machine, open a terminal, connect cable, type 'dmesg' and 'cat /var/log/syslog' to see what it says
- take another office machine and live-boot Ubuntu to see if that works.

---

### Post by daniel-clement on 2013-09-12
Thanks for helping, Sanderj
> **sanderj said:**
> And on a third LAN?Good question. I'll try and test at my home if he's willing to lend me his laptop.
> Maybe the office LAN forbids/blocks non-official OSes?No, definitely not, there's also a bunch of Ubuntu PCs over there.
> I would do this:
- boot the Ubuntu machine, open a terminal, connect cable, type 'dmesg' and 'cat /var/log/syslog' to see what it saysI'll do that tonight.
> - take another office machine and live-boot Ubuntu to see if that works.This works I'm sure, I've done it several times with live Ubuntu USBs. However, I'll test a latest live Xubuntu. Then I'll post the result of all this.

---

### Post by bab1 on 2013-09-12
> **daniel-clement said:**
> ... When he's at home, his laptop connects like flawlessly, as well wired as wireless.

But when he's at our office (wired connection only), he can't connect with Ethernet. Even stranger, this happens only under Xubuntu: Windows does connect (same plug - same cable).

This sure sounds like a configuration problem.  What have you done to confirm that you have *no connectivity*?  Have you tested to see if you can connect directly with an IP address?  By that I mean something like finding out what the IP address of google.com and trying that in a web browser like this```
http://74.125.239.0
```...that should bring up Google without needing to resolve the IP address from the DNS name.

My guess is that you are not resolving the DNS correctly with the Xubuntu configuration.

---

### Post by daniel-clement on 2013-09-12
Here I am, back from some testing. (That was the 1st time I got my hands on this PC.) First, his Xubuntu is a rather oldish 11.10. 

The good new : his network connection is definitely OK. Network-manager as well as ifconfig show it working. We are able to ping the router.

Now for the weird part. Let's say we start Firefox (v.23, BTW). It searches for its start page, and doesn't find it (nor any other site). BUT, if we type a numeric address (e.g. [http://74.125.239.0](http://74.125.239.0) as bab1 suggested), it displays the page correctly. *THEN* if we type in a symbolic address (*not necessarily* [www.google.com]("http://www.google.com")), the page is displayed OK! -- but unfortunately, this doesn't survive a restart. Even stranger, a simple ping 74.125.239.0 successfully "unlocks" Firefox...

We tried to use OpenDNS's DNS servers ourselves (they are working quite well for me), but then we couldn't reach *any* address and we backpedaled.

We gave a look at his /etc/resolv.conf; it reads:
```
nameserver 127.0.0.1
search [*the office DNS server*]
```is that normal? (However, I know this file is auto-generated and I don't know how to "freeze" it.)

Now, we tried and installed Chromium, which appears to work 100% trouble-free. Perhaps it's a Firefox-specific issue? But Thunderbird also has this connection problem (BUT, doesn't it share its settings with Firefox)?

However, I'll offer my colleague to try a newer flavor of XFCE. Because if he's to become a Linux fan (which I hope), I don't see why he would want to stay with that aging version: maybe the latest Xubuntu doesn't have this issue.

---

### Post by bab1 on 2013-09-12
> **daniel-clement said:**
> ...

We gave a look at his /etc/resolv.conf; it reads:
```
nameserver 127.0.0.1
search [*the office DNS server*]
```is that normal? (However, I know this file is auto-generated and I don't know how to "freeze" it.)

Yes this is normal with the latest Nework Manager.  It uses resolvconf instead of /etc/resolv.conf.  See [**[COLOR="#FF8C00"]here[/COLOR]**]("https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/") for why.

You add DNS servers in /etc/network/interfaces with this setup (resolvconf).  It looks something like this```

auto eth0
    . . .

    dns-nameservers 8.8.8.8 8.8.4.4

```...note that the above are Google's DNS name servers.

---

### Post by varunendra on 2013-09-13
> **bab1 said:**
> You add DNS servers in /etc/network/interfaces with this setup (resolvconf).  It looks something like this```

auto eth0
    . . .

    dns-nameservers 8.8.8.8 8.8.4.4

```

Wouldn't the "eth0" entry cause Network Manager to NOT manage the eth0 interface ? (unless mode "managed=" is set to "true" in the [s]keyfile[/s] [COLOR="#FF0000"]Correction : conf file[/COLOR] instead of "false" which is default)

I believe *Network Manager's drop-down menu > Edit Connections... > edit desired connection > settings under IPv4 (or IPv6,if that is applicable) tab* is the correct place to enter the DNS, unless someone wants the interfaces file to manage the interface, not NM.

To be able to save settings for an interface (eth0 here) in NM-

1) the /etc/network/interfaces file should NOT contain anything about that interface (or NM will by default disable its own settings pertaining to that interface)
2) to set only DNS, the "Method" should be set to "**Auto (DHCP) address only**" in NM settings.

Of course both NM and the interfaces file can be made to manage an interface by changing the mode "manged=false" to "managed=true" in the NM [s]connection's keyfile[/s] [COLOR="#FF0000"]Correction : conf file[/COLOR], but that is generally not recommended.

---

### Post by bab1 on 2013-09-13
> **varunendra said:**
> Wouldn't the "eth0" entry cause Network Manager to NOT manage the eth0 interface ? (unless mode "managed=" is set to "true" in the keyfile instead of "false" which is default)


I believe *Network Manager's drop-down menu > Edit Connections... > edit desired connection > settings under IPv4 (or IPv6,if that is applicable) tab* is the correct place to enter the DNS, unless someone wants the interfaces file to manage the interface, not NM.

To be able to save settings for an interface (eth0 here) in NM-

1) the /etc/network/interfaces file should NOT contain anything about that interface (or NM will by default disable its own settings pertaining to that interface)
2) to set only DNS, the "Method" should be set to "**Auto (DHCP) address only**" in NM settings.

Of course both NM and the interfaces file can be made to manage an interface by changing the mode "manged=false" to "managed=true" in the NM connection's key file, but that is generally not recommended.

If the OP was asking about NM actually managing the interface then this would be correct.  But the OP didn't really ask that IMO.  The OP asked how to add a DNS server to the /etc/resolv,conf output.  I assumed that he was managing the interface manually.  If not (and therefore using NM to manage the interface) then you are correct.  NM should be used, as you say, for all aspects of the configuration.  That would be obvious by looking at the tabs available.

---

### Post by varunendra on 2013-09-13
Thanks for the confirmation :)

I saw this in OP's post -
> **daniel-clement said:**
> The good new : his network connection is definitely OK. **Network-manager** as well as ifconfig show it working....
..and probably jumped the gun.

But I think it's good that it is now clear to not only OP, but others as well possibly following the thread later, that what should go where in both kinds of setup.

---

### Post by daniel-clement on 2013-09-13
Wow, so many replies ! I'm getting late...
[QUOTE=bab1]Yes this is normal with the latest Nework Manager.[/QUOTE]OK (not sure however that Xubuntu 11.10 had "the latest" NM). Let's forget about resolv.conf.
[QUOTE=varunendra]Wouldn't the "eth0" entry cause Network Manager to NOT manage the eth0 interface ?[/QUOTE]Clearly, it *is* managed by NM. I remember seeing the "not managed" symptom before on another PC, there was a very explicit message about that.
> 1) the /etc/network/interfaces file should NOT contain anything about  that interface (or NM will by default disable its own settings  pertaining to that interface)It's not the case.
> 2) to set only DNS, the "Method" should be set to "**Auto (DHCP) address only**" in NM settings.Yes, that's how we tested OpenDNS's servers. I'm doing this all the time on my home PCs, but this time it seemed only to make things worse.
[QUOTE=bab1]The OP asked how to add a DNS server to the /etc/resolv,conf output.  I assumed that he was managing the interface manually.[/QUOTE]Well not quite, I just wanted to check there was no sign of a problem in this file. I usually prefer making all changes through NM, that's what we tried yesterday.

So what can I add so far?
- we had no problem browsing the *local* network, so it's definitely a question of going out to the Internet.
- we tried a WiFi connection (we have an access point but it doesn't cover all the buildings); exact same behavior.
- we observed that Chromium behave better that Firefox. Was this coincidental, or could we have a Firefox issue?
- our DNS server is at present *very slow*. I saw this again this morning when I failed to reach the Internet on another PC. Maybe this slowness is the only reason, and Chromium manages it better than Firefox?

Anyhow, I'll offer my colleague to try and test a newer flavor of XFCE, especially Xubuntu 13.04. Because it could also be a version-specific issue.

---

### Post by varunendra on 2013-09-13
> **daniel-clement said:**
> It's not the case..

Do you mean the /etc/network/interfaces file contains an (uncommented) entry for eth0 and it still shows as managed by NM?

Please show us the outputs of -
```
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```

---

### Post by daniel-clement on 2013-09-13
> **varunendra said:**
> Do you mean the /etc/network/interfaces file contains an (uncommented) entry for eth0 and it still shows as managed by NM?No, this file has just```
auto lo
iface lo inet loopback
```
(and I don't believe we've made changes there, I'll check, though).

We haven't looked at his /etc/NetworkManager/NetworkManager.conf; I'm asking him.

---

### Post by varunendra on 2013-09-13
Well, then we seem to have had a little misunderstanding then.

I thought you are contradicting my statement when you said "It's not the case". If you really did, either you misread or misunderstood my statement. If you meant "No, the /etc/network/interfaces file does not contain anything about eth0", then I misunderstood.. :P

Hope it's all clear now. You don't have eth0 in your interfaces file yet, hence NM is managing the eth0 interface, which is what is expected.

Unless you or someone manually edited the NetworkManager.conf file, it must have the line - "managed=false", which means it will NOT manage any interface that is being handled by the interfaces file.

---

### Post by daniel-clement on 2013-09-13
> **varunendra said:**
> I thought you are contradicting my statement when you said "It's not the case". If you really did, either you misread or misunderstood my statement. If you meant "No, the /etc/network/interfaces file does not contain anything about eth0", then I misunderstood.. :PI see: I "think French" (where it is customary to reply "no" to a negative question... which you agree with!):razz:

> You don't have eth0 in your interfaces file  yet, hence NM is managing the eth0 interface, which is what is expected.Yes, otherwise I believe it (NM) would display "not managed" somewhere (I don't know exactly where, but I've already seen that).

>  Unless you or someone manually edited the NetworkManager.conf file, it  must have the line - "managed=false", which means it will NOT manage any  interface that is being handled by the interfaces file.I have yet to see this file, but we have not touched it, so it has to be in its default condition. 

So you still think there can be a problem with NM, even though LAN browsing is OK?

---

### Post by daniel-clement on 2013-09-13
Update: I just received the content of his file, it comes as no surprise:

```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=00:26:9E:BE:D6:40,

[ifupdown]
managed=false
```

---

### Post by Hadaka on 2013-09-13
Hi, both your /etc/network files are CORRECT for using Network Manager
to manage your connections.~~~Please see attached to configure your Network Manager~~

[ATTACH=CONFIG]246209[/ATTACH][ATTACH=CONFIG]246210[/ATTACH][ATTACH=CONFIG]246211[/ATTACH]
configure ..wireless...IPv4...Ipv6...like this for your connection..save..close...boot
*also check your security settings.

---

### Post by daniel-clement on 2013-09-14
> **Hadaka said:**
> Hi, both your /etc/network files are CORRECT for using Network ManagerGood to know that!
> to manage your connections.~~~Please see attached to configure your Network Manager~~
[ATTACH=CONFIG]246209[/ATTACH]Do you mean we should try Google's DNS servers? Well, we didn't have much success changing the DNS servers, though we did it properly (see post #5).
> configure [...] Ipv6...BTW, we set IPv6 to "ignore".

---

### Post by varunendra on 2013-09-14
If you can ping 8.8.8.8 and 8.8.4.4 with a reasonably fast response time, I don't see any reason why setting it as the DNS should fail.

So far, all the symptoms you mentioned indicate to only one direction - DNS

Please try that and test with -
```
nm-tool
```
...to see overall effective configuration including DNS in use.

---

### Post by daniel-clement on 2013-09-17
He (my colleague) made the test, but I believe he forgot to connect the ethernet cable! I told him to redo the test, but I chose to post the output so far, just in case:```
NetworkManager Tool

State: connected (global)

- Device: eth0  ----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           yes
  HW Address:        00:26:9E:BE:D6:40

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [FreeWifi] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        00:1E:64:8F:4B:A6


```

(then follow the list of discovered access points).

Isn't is strange that *none* of the 2 connection methods, wired and wireless, be labeled as "default"? I compared with my own settings, the wired connection *is* the default (I don't even recall how that had been assigned).

---

### Post by daniel-clement on 2013-09-18
Hello again, here is the result of the real test with the network cable plugged :-) ```
NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:26:9E:BE:D6:40

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.70.13.129
    Prefix:          24 (255.255.255.0)
    Gateway:         10.70.13.1

    DNS:             8.8.8.8
    DNS:             8.8.4.4


- Device: wlan0  ---------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        00:1E:64:8F:4B:A6

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


```(followed by the list of wireless access points, not relevant here).

I not that the wired connection is indeed "default".

But my colleague told me that it was difficult to get the first connection: neither Firefox, Thunderbird nor Chromium would connect. Then he tried Google's home page, which worked (perhaps, thanks to the Google DNS servers). From then on, everything ran fine.

So it could be just a problem with our router, which is awfully slow to allow the connection these days. They're working on it, but it's a pain. Perhaps it triggers a time-out for programs which need an Internet connection...

---

### Post by Bubba_Jackson on 2013-09-18
You could try running a tcpdump or a wireshark trace to see what's really happening to the traffic. Also, is the IP address configured statically or is it getting a dynamic address from a DHCP server? Also, try pinging both an external address and an internal address to see if there is packet loss or high response times.

---

### Post by daniel-clement on 2013-09-18
I can answer at least partially:
> **Bubba_Jackson said:**
> You could try running a tcpdump or a wireshark trace to see what's really happening to the traffic.  We'll do that ASAP, but perhaps we won't have time before next Monday.
> Also, is the IP address configured statically or is it getting a dynamic address from a DHCP server?DHCP
> Also, try pinging both an external address and an internal address to see if there is packet loss or high response times.We have pinged the router (see post #5) with apparently normal response time. Next time I'll take note of it, and also try and ping an external site.

---

### Post by daniel-clement on 2013-09-19
Update: my colleague has just told me that our routers had undergone heavy maintenance works. It *apparently* made his problem vanish. My guess is, that router problem was particularly conspicuous on a laptop, because our desktops all get started automatically (around 7.30AM) and perhaps it somehow hid the slowness of the Internet access.

If that's confirmed, I guess I'll have to come back with a "solved" tag and apologies for starting a pointless thread...

---

### Post by daniel-clement on 2013-09-23
Well, it's as I feared. 

It turned out to be a hardware router problem that had nothing to to with the settings in Xubuntu.

My apologies for wasting everybody's time; now I'm trying to tag this thread as solved.

Best regards, Daniel

---

