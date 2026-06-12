---
title: "Network disconnected after dual-booting from Windows"
date: 2013-12-10
forum: Networking &amp; Wireless
---

### Post by dimitri6 on 2013-12-10
Hi all,

As I mentioned in the Subject, The [Wired] Network is disconnected after dual-booting from a Windows 7 session.

I've noticed that issue in all Ubuntus I tried (Ubuntu 13.04, Ubuntu 13.10, Ubuntu Studio 13.04, Ubuntu Studio 13.10 and Ubuntu Studio 12.04 LTS) on all my 3 different computers (Toshiba Satellite A60 Laptop, Compaq Presario  C700 Laptop and on my Lenovo ThinkCentre M57 desktop) that dual-boot with Windows 7 SP1.

Booting to Windows 7 I have a network connection. Turning off the machine and/or restarting to boot with Ubuntu, the Network Connection won't be available.

To get a network connection in Ubuntu after dual-booting from Windows, the only remedy is to Reboot my Cisco Linksys E4200 v.1 router!, Then boot in Ubuntu!

-- again, that issue is on all 3 wired computers, and occurs only when the previous session was with Windows.

I didn't have this issue in the past when I was dual-booting with openSUSE 12.3/Win7 and/or openSUSE 13.1/Win7.

Is this a known bug in Ubuntu?  Is so, is there any workaround or fix?  I prefer not to reboot the router each time I come from Win7 because it causes inconveniences in other people's computers, IPTV's and VoIP phones in the house.

Thank you for any suggestions.

EDIT:  I realized that I can reproduce the issue even when booting from a Ubuntu Live DVD with the same message. Network: "Disconnected - You are now offline" (provided I just logged off from a Windows 7 session)

---

### Post by varunendra on 2013-12-12
Not sure if I can find or suggest a remedy, but are you getting the IP from DHCP in the router? Can you try a fixed IP (or opposite of it if already using fixed IP).

Also, if getting IP from DHCP, does the IP remain the same in both windows and Ubuntu?

I remember having read about some bug in many routers' firmware sometimes ago, but since you said it worked fine with Suse, let's hope we can work this out.

---

### Post by dimitri6 on 2013-12-12
Thank you for the quick reply.
The IP of the computer(s) is obtained via DHCP but it's fixed via DHCP Reservation at the hardware level.
With SUSE I don't have issues dual-booting, with Ubuntu I do.

Now I'm typing this reply from Windows7. If I will re-boot to long-in with Ubuntu and won't also reboot the router, I won't have any connection -- this occurs in all my 3 computers with Ubuntu/Win7, which wasn't the case with openSUSE/Win7 (same router).

---

### Post by varunendra on 2013-12-12
> **dimitri6 said:**
> The IP of the computer(s) is obtained via DHCP but it's fixed via DHCP Reservation at the hardware level.

You mean binding IPs with MAC addresses, right? That again relies on a smooth operation of both DHCP client and server. How does it behave if you (temporarily, just for a test) disable DHCP altogether and try manually assigning the same IP in both Windows and Ubuntu.

This may not be a solution or even an acceptable workaround, but at least it may help pin-pointing the problem.

Also, the fact that Suse worked and Ubuntu doesn't, does not mean much unless you can confirm that Suse was using the same kernel as well, which is probably not the case. Many things have changed since kernel 3.8 and are still changing rapidly. This has caused severe regressions in many drivers and many of them still haven't fully recovered. I personally know a few drivers that were working perfectly before kernel 3.8, but are facing many bugs now. Yours may be a similar case, although there can be several other possibilities.

---

### Post by dimitri6 on 2013-12-17
> **varunendra said:**
> You mean binding IPs with MAC addresses, right? 

Exactly.

> That again relies on a smooth operation of both DHCP client and server. How does it behave if you (temporarily, just for a test) disable DHCP altogether and try manually assigning the same IP in both Windows and Ubuntu. 

Just tried your suggestion, and IT WORKS!  I assigned a different Fixed IP address to Windows 7, No DHCP (192.168.1.131) and I left Ubuntu to obtain it's reserved IP via DHCP (192.168.1.101)

and I can now dual-boot and switch between Win7 and Ubuntu and have a network connection with no issues!

>  This may not be a solution or even an acceptable workaround, but at least it may help pin-pointing the problem. 

Indeed.  It all appears that it's a bug in Ubuntu, but the workaround you suggested is acceptable for me, therefore I consider this thread solved.

However, Canonical may want to take a closer look at this bug, because people that have Windows 7 installed and want to try the Ubuntu Live DVD.... may not be able to have an internet connection.... (at least those with a LinkSys E4200 router, for sure)

Thanks again you saved me lots of trouble from re-booting the router each time!!

---

### Post by varunendra on 2013-12-17
Good to know it works. :)

Since you have been experiencing the same behaviour on all versions of Ubuntu you've tried so far, I'd encourage you to file a bug report (or add yourself to "affects me" list of an existing one) at launchpad. The following command runs apport wizard application that collects all the relevant info for the bug report -
```
apport-bug
```

How to effectively Report a Bug : [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

**PS:**
Your situation sounds more like a known bug in the firmware of some routers, but still it is worth reporting if Suse or any other Linux distro worked consistently with the same router.

---

### Post by dimitri6 on 2013-12-17
I also tried to assign the same IP to Windows (manually from windows no DHCP) and and via DHCP to Ubuntu. Both 192.168.1.101.  And the network connection works! And I will leave it like that.

I may report it, as this issue is only with Ubuntu on many computers, and it consistently worked with openSUSE with the same router.

As long as Windows won't "bother" the DHCP server in the router,  Ubuntu works in the same machine.  That's a mystery to me... but as long as this workaround  works, I'm happy.

Thanks again.

---

### Post by varunendra on 2013-12-18
You're welcome ! :)

My way of interpreting this bug (in the routers' firmware, sounds like it is indeed that) is like the router saying -

*"[COLOR="#FF0000"][s]I [/s][/COLOR] O lord (windows), I'm your slave, I'd always serve you.... oh, wait, who's that fella (ubuntu) in your house (the same MAC), let me deny him any service, since I've been told that house (the same MAC) belongs to you".*

Take-home lesson is : The firmware simply gets stuck with windows part once it has granted a lease on its request. This problem was mostly found in old D-Link routers, but occasionally in other brands as well. Although I rarely hear about it with models less than 3 years old.

You may try 'Spoofing' a different MAC ID from Ubuntu* (using Network Manager's "Cloned MAC address" field is one of the many ways to do that)* so that whenever Ubuntu starts, the router 'sees' it as a different machine. Although that also means you'll have to assign (or will automatically be granted) different IPs in Windows and Ubuntu.

---

### Post by dimitri6 on 2013-12-24
> **varunendra said:**
>  My way of interpreting this bug (in the routers' firmware, sounds like it is indeed that) is like the router saying -

*"I lord (windows), I'm your slave, I'd always serve you.... oh, wait, who's that fella (ubuntu) in your house (the same MAC), let me deny him any service, since I've been told that house (the same MAC) belongs to you".* 

Hahahahaha.  So true! LMAO

---

