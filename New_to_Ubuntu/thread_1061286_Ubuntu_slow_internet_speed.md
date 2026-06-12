---
title: "Ubuntu slow internet speed"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Joakal on 2009-02-05
I installed Ubuntu and followed the synaptic updates which took over 12 hours to update. Thought it was normal until I did internet speed tests with speakeasy. I got 50 KB/s compared to my Windows 666 KB/s. I re-ran the tests again, results were pretty average.

I searched some threads;
[list][*]disabled IPv6 but unsure if it's disabled. [How-To: Disable IPV6 to [s]speed[/s] **free** up Internet [bandwidth].](http://ubuntuforums.org/showthread.php?t=87798)
[*]disabled firestarter firewall. No real increase.
[/list]

Since I'm new to Ubuntu, I have no idea how to check anything! Someone told me it's probably driver compatibility problems. 

Using ASUSTek Computer Inc. F3JV. I'm using Windows XP for now since I want the bandwidth

EDIT: I'm using Cable, the wireless internet threads aren't helpful :(

---

### Post by LowSky on 2009-02-05
funny, I get about the same connection regardless.
Have you tried changing the server you download updates from. that could help.

What site were you using to test your speeds?

---

### Post by Joakal on 2009-02-05
I've already fully updated my Ubuntu. So I can't really do a synaptic test again.

I did tests here:
[http://speakeasy.net/speedtest/](http://speakeasy.net/speedtest/)
Also [http://www2.dslreports.com/speedtest?flash=1](http://www2.dslreports.com/speedtest?flash=1) (Gave less speed overall to both tests on XP and Ubuntu)

Is there anyway to test if I have IPv6 enabled?

---

### Post by Joakal on 2009-02-06
Bump?

(That's allowed, right?)

---

### Post by spcwingo on 2009-02-06
> **Joakal said:**
> I've already fully updated my Ubuntu. So I can't really do a synaptic test again.

I did tests here:
[http://speakeasy.net/speedtest/](http://speakeasy.net/speedtest/)
Also [http://www2.dslreports.com/speedtest?flash=1](http://www2.dslreports.com/speedtest?flash=1) (Gave less speed overall to both tests on XP and Ubuntu)

Is there anyway to test if I have IPv6 enabled?

If you're still running Firefox, then just open it and in the address bar type:

```
about:config
```

then search for ipv6.  This will tell you if ipv6 is disabled in Firefox.

---

### Post by bigfootnmd on 2009-02-06
The Site Speedguide.net has a treasure trove of information on how to tweak connection settings in both Linux and Windows.

[http://www.speedguide.net/](http://www.speedguide.net/)

Click on Broadband, Registry Tweaks.

---

### Post by the.phantom on 2009-02-06
might go here
[http://www.dslreports.com/stest](http://www.dslreports.com/stest)

and run a few java test to different sites?

i have found that i can get lower speed test results when i do the flash test and the java ones seem to be more "real world

---

### Post by superprash2003 on 2009-02-06
post output of ifconfig from the terminal..

---

### Post by ihatetryingtopickaloginna on 2009-02-06
This is what I did:

sudo gedit /etc/modprobe.d/blacklist   

And then added 'blacklist ipv6' to the end of the file

---

