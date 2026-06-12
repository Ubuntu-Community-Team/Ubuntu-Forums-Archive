---
title: "No Internet on boot after latest upgrade"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by Red Knuckles on 2007-04-06
After latest upgrade of Kubuntu Fiesty internet no longer connects on boot. I found a crude fix by >System Settings>Network Settings>Network Connection>Administrator Mode>Network Interfaces>eth0 Enabled Ethernet Network Device and changing >Protocol>dhcp to >Protocol>bootp and selecting Apply THEN changing >Protocol>bootp BACK to Protocol>dhcp and selecting Apply again and then I have an internet connection. What the... And how can I correct this so Internet [eth0] connects on boot???:confused:

Would it be correct to assume some file has been rewritten so that eth0 or dhcp aren't being started on boot?

---

### Post by Red Knuckles on 2007-04-06
More info on this problem.

1. I can set-up internet connection with static ip and have connection until I reboot then same thing  all over again.

2.Adept Package Manager works after establishing an internet connection EXCEPT for the Version Upgrade currently being offered. When I select >Version Upgrade>Next I get 'Error: Could not download the release announcement. Check that your Internet connection is active.' This even though I had to have an internet connection to run 'Fetch Updates'.

:confused:

---

### Post by Red Knuckles on 2007-04-06
> **Red Knuckles said:**
> More info on this problem.

1. I can set-up internet connection with static ip and have connection until I reboot then same thing  all over again.

2.Adept Package Manager works after establishing an internet connection EXCEPT for the Version Upgrade currently being offered. When I select >Version Upgrade>Next I get 'Error: Could not download the release announcement. Check that your Internet connection is active.' This even though I had to have an internet connection to run 'Fetch Updates'.

:confused:

I removed 'network-manager' and now internet starts up on boot. I still can't do a 'Version Update' though.

---

### Post by daradib on 2007-04-07
> When I select >Version Upgrade>Next I get 'Error: Could not download the release announcement. Check that your Internet connection is active.' This even though I had to have an internet connection to run 'Fetch Updates'.
 
Same problem over here. I have internet, Adept works perfectly, except I can't do Version Upgrade. I get:

```
Could not download the release announcement. Please check that your internet connection is active.
```

I am thinking it may have something to do with IPv6 interfering with IPv4. Adept may be using IPv6, but we have IPv4 connections. I may be wrong, but I'll try disabling IPv6, etc. and tell you my results.

---

### Post by Red Knuckles on 2007-04-07
> **daradib said:**
> Same problem over here. I have internet, Adept works perfectly, except I can't do Version Upgrade. I get:

```
Could not download the release announcement. Please check that your internet connection is active.
```

I am thinking it may have something to do with IPv6 interfering with IPv4. Adept may be using IPv6, but we have IPv4 connections. I may be wrong, but I'll try disabling IPv6, etc. and tell you my results.

Yeah, I also tried from command line 'sudo aptitude dist-upgrade' and 'sudo apt-get dist-upgrade' and they did nothing. Don't know what's up but I've posted under 'Why can't I update my version?' in >Ubuntu Forums>Installation and Upgrades, >Kubuntu Forums>Feisty Fawn>Software Support, and >LinuxQuestions.org>Ubuntu.
:lolflag:

---

### Post by daradib on 2007-04-07
Same here, I had tried sudo apt-get dist-upgrade as well. It is also possible that there is no version upgrade, but that doesn't make sense (or else Adept is buggy and won't let you version upgrade because there probably isn't a version upgrade release announcement).

---

### Post by bitphire on 2007-04-08
Having the same issue, was just curious if there was a fix. :)

---

### Post by daradib on 2007-04-08
See this thread on kubuntu forums:
[http://kubuntuforums.net/forums/index.php?topic=3081566](http://kubuntuforums.net/forums/index.php?topic=3081566)

---

### Post by daradib on 2007-04-08
Similar bugs on Launchpad (but not exactly the same):

[https://bugs.launchpad.net/ubuntu/+source/adept/+bug/103607](https://bugs.launchpad.net/ubuntu/+source/adept/+bug/103607)
[https://bugs.launchpad.net/ubuntu/+source/adept/+bug/82034](https://bugs.launchpad.net/ubuntu/+source/adept/+bug/82034)
[https://bugs.launchpad.net/ubuntu/+source/adept/+bug/102782](https://bugs.launchpad.net/ubuntu/+source/adept/+bug/102782)

---

### Post by Red Knuckles on 2007-04-08
> **daradib said:**
> Similar bugs on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/adept/+bug/103607](https://bugs.launchpad.net/ubuntu/+source/adept/+bug/103607)
[https://bugs.launchpad.net/ubuntu/+source/adept/+bug/82034](https://bugs.launchpad.net/ubuntu/+source/adept/+bug/82034)
[https://bugs.launchpad.net/ubuntu/+source/adept/+bug/102782](https://bugs.launchpad.net/ubuntu/+source/adept/+bug/102782)

Those bug reports relate to the next button not working, [grayed out]. My problem is different so I filed this bug report:

[https://bugs.launchpad.net/ubuntu/+source/adept/+bug/104542](https://bugs.launchpad.net/ubuntu/+source/adept/+bug/104542)

:guitar:

---

### Post by daradib on 2007-04-08
A noted in the below bug report, the issue has been fixed and is in the process (in source right now, going to be compiled). Should see it in the updates soon:

[https://launchpad.net/ubuntu/feisty/+source/adept/2.1.2ubuntu25](https://launchpad.net/ubuntu/feisty/+source/adept/2.1.2ubuntu25)

---

