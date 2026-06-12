---
title: "Prism 2.5 Wavelan broken after upgrade"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by hellion0 on 2008-10-31
I upgraded a HP Pavilion ze4365us from Hardy to Intrepid earlier today. It has a Prism 2.5 Wavelan chipset for onboard wireless. The card worked perfectly under both Gutsy and Hardy.

The upgrade to Intrepid, however, broke it. I can't use it to connect to anything inside my LAN, and it's hit-or-miss connecting to anything outside it.

After a few minutes of being powered on and logged in, I get insult added to injury as the entire system is rendered unusable. It also becomes unusable if I try disabling the onboard wireless. (Alas, it dies before I can post any info from the CLI using it.) Although it does not hard-freeze, any commands given to it simply hang forever.

The one thing I did notice is that the wireless card was using an "orinoco_pci" driver, if that makes any sense here. With the older kernel, it uses driver "hostap". Blacklisting the orinoco_pci driver and forcing it to use hostap does NOT fix the problem, though.

Is there anything that I can try in the immediate term, other than downgrading to Hardy?

Edit: Switching to kernel 2.6.24-21-rt makes things work in the short-term, so it's possible that something in the 2.6.27-3-rt kernel is to blame here.

2nd Edit: The Xubuntu Intrepid (final) LiveCD runs with no problems.

---

### Post by rokky on 2008-11-02
I am having a similar problem with Prism2 Intersil on a Fujitsu P1120 Lifebook with fresh install of Xubuntu 8.10 "final release" (or whatever the Oct 31 release is called).  syslog shows the same message as this article, [http://ubuntuforums.org/showthread.php?p=6031730](http://ubuntuforums.org/showthread.php?p=6031730)  

... wifi0: invalid skb->cb magic ...

This occurs with both the ipv6 "version" of the interface used by the Network Manager applet (I do not see an option as with earlier versions of Ubuntu to clear out that v6 junk for for which I have no use - who does?), "wlan0", and the ipv4 version, "wifi0" when I try dhclient manually.

---

### Post by pytheas22 on 2008-12-09
I don't know if you two are still having trouble, but if you are, please take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=968797"); I think the fix there should apply to your situation.

(I just came across this thread while googling for information on the problem and thought I would point out what appears to be the fix...although I can't confirm it yet.)

---

