---
title: "OpenConnect Cisco VPN - DNS not resolving"
date: 2019-02-19
forum: Networking &amp; Wireless
---

### Post by Arbiter on 2019-02-19
Hello all,

I've looked around quite a bit elsewhere for a resolution to this, but I can't see to find a resolution that works.

I'm using Ubuntu 18.04.2 LTS and using OpenConnect to connect to a Cisco VPN.  I can connect to it, and I can ping IPs across the VPN, however I cannot resolve DNS.  Even if I manually define the DNS servers in OpenConnect VPN settings in Network Manager it seems to ignore the DNS servers for the VPN.

Is there a fix?  I've seen some bugs related to this and I've tried a few but none seem to work for me.

Any help greatly appreciated!

- Arbiter

---

### Post by Arbiter on 2019-02-20
Anybody?  ::crickets::

---

### Post by mrunknown96 on 2019-03-20
@Arbiter have you found a solution to the problem? Running into the exact same issue

---

### Post by jameslmoser on 2019-05-24
This is broke in the current versions of Ubuntu as well, so I decided to go back and stick with the latest LTS version, and of course now it appears to be broken there as well.  It worked find the last time I used my machine so I reverted it back to the last snapshot I had, looked at what needed updating, the only thing that stood out was "libopenconnect5" and "openconnect" so I marked those packages as hold, updated everything else and it still works.  Not sure which version broke it, and I don't have a bunch of time/expertise to figure it out.

I'm debating changing distros now because I can't work if I can't reliably connect to our vpn.  I installed fedora 30 and it works fine with all updates applied... we use redhat at work anyways...

---

### Post by Arbiter on 2020-03-18
@mrunkown96 I know it's been a year but nothing's changed with this issue. It's even present in 19.10.  I've been troubleshooting this on and off now for a year.  With OpenConnect VPN, nothing works right. DNS does not resolve properly.

This issue is even present in 19.10.  For whatever reason, this works perfectly well in Fedora 30, 31.  More and more I need this to work right.  No one else run into this yet?  Strongly debating abandoning Ubuntu over it.  Ubuntu more and more strikes me as all good for fun and games, but when it comes down to real enterprise use it falls flat.

---

### Post by SeijiSensei on 2020-03-18
Try adding the IP addresses of the DNS servers you want to use to the "DNS=" line in /etc/systemd/resolved.conf, then restart the resolver with "sudo systemctl restart [systemd-resolved]("https://manpages.debian.org/testing/systemd/resolved.conf.5.en.html")".

---

### Post by Arbiter on 2020-03-18
Hello and thank you for the suggestion SeijiSensi, but unfortunately didn't help.  Same effect.  

I connect to my company's VPN and when I type in an IP address (which is what I have to do initially) the DNS doesn't translate or reverse translate properly.  Some work, some do not.  It's very intermittent.  I get resolution from our internal blah.com domain, but resources on our blah.local domain does not resolve regardless of what I specify in resolv.conf or resolved.conf.

It's just interesting that on Fedora and Windows this works out of the box but Ubuntu has this issue which seems to have been ignored by the dev team.  It's a documented bug (don't have the bug ticket number in front of me unfortunately).

---

### Post by Arbiter on 2020-03-18
Hello and thank you for the suggestion SeijiSensi, but unfortunately didn't help.  Same effect.  

I connect to my company's VPN and when I type in an IP address (which is what I have to do initially) the DNS doesn't translate or reverse translate properly.  Some work, some do not.  It's very intermittent.  I get resolution from our internal blah.com domain, but resources on our blah.local domain does not resolve regardless of what I specify in resolv.conf or resolved.conf.

It's just interesting that on Fedora and Windows this works out of the box but Ubuntu has this issue which seems to have been ignored by the dev team.  It's a documented bug (don't have the bug ticket number in front of me unfortunately).

---

### Post by Arbiter on 2020-04-01
Responses to my problem, while not non-existant, have been sparse and no permanent solution.  However I can verify that this problem is present in Ubuntu and its derivatives.  Is even present in the 20.04 LTS release betas.  However, OpenConnect VPN functionality works in Debian 10 and all latest releases of CentOS/RHEL/Fedora.

I'm surprised at this as I've been a user of Ubuntu for 16 years (since Warty Warthog) and I can honestly say I'm surprised that this is the case.

---

