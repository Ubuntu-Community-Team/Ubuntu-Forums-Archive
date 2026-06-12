---
title: "Browser Won't Connect"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by Gnigma on 2007-04-19
I've just installed Ubuntu 6.10 on my previously Linspire computer, and I have a goofy problem. My browser won't connect. I've tried with Firefox and with Mozilla, and it won't hook up. It's directly connected to my DSL modem, and the update works fine through the modem. I can even download and install programs through the modem with Add/Remove, but the browser won't connect even though Mozilla shows it's connected in the lower right corner of the screen. I've checked my permissions and my user account has permission to connect. Any ideas?

---

### Post by Gnigma on 2007-04-19
I still haven't figured out what I have to do to connect to the web through the browser. I was afraid this would happen. For me, all Linux has been like a cheating woman--- the more chances I give, the more times I'm dissappointed.

It's been several hours and nobody seems to know or want to help. One word of advice for the Linux community--- some people consider time more important than anything else on earth. I've been looking for an alternative to Microsoft for over ten years now, and though Ubuntu could be it, if it takes too much time and effort, I'll never use it. Mostly I've been dissappointed with Linux, because it does not work. All Linux distros claim to have all this support, but none of them deliver. The closest I've found is Linspire, formerly Lindows, which at least lets me connect to the internet after the install. unfortunately, it's slow, and it's glitchy as all get out when attempting to run anything, especially wireless. I guess I'll reload Win XP and wait another ten years.

---

### Post by woro2006 on 2007-04-19
Seems like you're frustrated, very even. Have you considered upgrading the browser? Also, a log can be found using administration. Read that to see why it doesn't work.

---

### Post by erfahren on 2007-12-22
First, to clarify here, this issue has already been solved by the OP with a fresh installation and connecting to the internet with the LiveCD before starting the install.

I'm curious as to why the OP had this problem as the information could be beneficial to another user.

just a couple questions...

Gnigma, do you have your DSL router/modem set up to use static IP address(es) on your computer(s) - (DHCP) disabled? 

What kind of router/modem is it?

can you open Firefox and in the address bar type in:
```

about:config

```
and in the Filter bar that comes up underneath enter:
```

ipv6

```
and see if the value for "network.dns.disable.IPv6" is set to true or false (default is false).

the reason I ask this is because some users have had problems with ipv6. It's basisically a DNS protocol that is replacing the old one (ipv4). Some older routers (and some service providers) have poor support of the new protocol.

The workaround for this is to disable ipv6 in Firefox or systemwide discussed in these threads:
[http://ubuntuforums.org/showthread.php?p=3989760](http://ubuntuforums.org/showthread.php?p=3989760)
[http://ubuntuforums.org/showthread.php?t=373545](http://ubuntuforums.org/showthread.php?t=373545)
[http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/](http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/)

---

### Post by gilf on 2007-12-22
Could be something simple, and just the Firefox setup.

Edit>Preferences>Network>Settings  try "Direct Connection" first, then try "Auto detect proxy settings."

Firefox (and IExplorer) needs the right network settings no matter what the OS. Usually also, the ISP can help you with these

---

