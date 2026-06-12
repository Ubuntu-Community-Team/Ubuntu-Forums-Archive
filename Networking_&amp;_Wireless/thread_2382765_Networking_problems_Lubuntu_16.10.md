---
title: "Networking problems Lubuntu 16.10"
date: 2018-01-17
forum: Networking &amp; Wireless
---

### Post by ianmanning on 2018-01-17
I've had a Lubuntu 16.10 server running as a VM on an ESXi 6.5 host for a couple of weeks. Until last night it was running fine, but today it is having major problems with both inbound and outbound network connections:
- Timeouts accessing web resources on both LAN and WAN (e.g. BBC website or Logitech Media Server web GUI running on the LAN). Internal sites can sometimes be accessed, but not for long
- No inbound connections possible to VNC server or mediawiki site on the Lubuntu machine from other machines on the LAN (was working fine until this morning). The mediawiki site is up and running, and can be accessed from the Lubuntu machine itself. I did fleetingly manage to access a couple of pages from the mediawiki site from another machine on the LAN, but then it stopped responding, so it seems to be a performance rather than connectivity issue (and it was connecting fine until this morning).

There is one other VM running on the same ESXi host - a Windows machine. This has absolutely no network issues (inbound or outbound), so I assume that the networking hardware is fine on the host. I've tried shutting down the other VM but it didn't help. I've also tried rebooting the router/gateway and the Lubuntu server.

Can anyone advise on how I can diagnose this issue? I'm a Linux novice so please bear with me!

---

### Post by ajgreeny on 2018-01-17
It will be difficult to help you with this as Lubuntu 16.10 and all the other 16.10 versions are long out of support.

The best thing you can do is reinstall but this time go back to 16.04 for a long term support version or 17.10 for the short intermediate support version, and update that to 18.04 in April when it's released.

Take care with 17.10 as there was a BIOS bug which locked the BIOS meaning on certain motherboards the computer was very difficult to change OS later.
See [http://lubuntu.me/lubuntu-artful-atque-vale-released/](http://lubuntu.me/lubuntu-artful-atque-vale-released/) for details and a link to the new safe ISO file.

---

### Post by ianmanning on 2018-01-17
> **ajgreeny said:**
> It will be difficult to help you with this as Lubuntu 16.10 and all the other 16.10 versions are long out of support.

The best thing you can do is reinstall but this time go back to 16.04 for a long term support version or 17.10 for the short intermediate support version, and update that to 18.04 in April when it's released.

Take care with 17.10 as there was a BIOS bug which locked the BIOS meaning on certain motherboards the computer was very difficult to change OS later.
See [http://lubuntu.me/lubuntu-artful-atque-vale-released/](http://lubuntu.me/lubuntu-artful-atque-vale-released/) for details and a link to the new safe ISO file.

Thanks for the pointer. Support for any Ubuntu release seems to be pretty ephemeral - I think the last 3 requests that I've posted have met with a similar response.
Is it the case that longer term support is offered for .04 releases but not .10 releases?

---

### Post by QIII on 2018-01-17
Hello!

Not quite.  Every even numbered year, in the fourth month, Canonical releases a Long Term Support (LTS) version supported for 5 years (three in the case of Xubuntu and Lubuntu, as that is all that their development communities will take on.)  So 14.04, 16.04 and the upcoming 18.04 will continue to be supported until April of their 5th year.

All other versions lose support 9 months after release.

---

### Post by ianmanning on 2018-01-17
Interesting...so I installed a fresh Lubuntu 17.10 on the same ESXi host. No networking problems at first, then
- installed Bitnami Mediawiki stack
- changed IP address to static
- rebooted
...and now the new Lubuntu VM has exactly the same problems as the original VM. 80% packet loss.
???!!!

---

