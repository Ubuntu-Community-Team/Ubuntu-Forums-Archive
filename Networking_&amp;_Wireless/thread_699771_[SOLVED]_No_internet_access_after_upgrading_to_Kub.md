---
title: "[SOLVED] No internet access after upgrading to Kubuntu 7.10"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by tinmon on 2008-02-17
Hi,

After upgrading to Kubuntu 7.10 I can no longer access the internet - can't ping and no luck with the applications I've tried. Nothing wrong with the modem using Win XP (dual-booting).

At first I assumed it was a glitch in the upgrade process (which stopped just as it had downloaded all the packages) so I figured it might be something related to this - a conflict between config files or something like that. The newest installed kernel fails to boot (fairly late in the process) and that might be a sign that there was a problem during upgrade that affected a number of packages. In addition, there are a number of menu items that simply won't run - not from the menu and not in a terminal. (I'll make a list when I get home)

Now I'm thinking that it might be more of a problem related to hardware or software. Or even a different way of handling the modem than in 7.04.

My ISP is Bredbandsbolaget and it's a Xavi 8222 modem which should be accesible through 192.168.1.1 but I can't do that. Maybe pppoeconf might work (as I've seen suggestedin a couple of threads) - not sure if I have that installed. Might be worth a try...

Any help or suggestions and ideas would be appreciated.

Here's a list of what I've tried so far (in reverse order):

**[COLOR="DarkRed"]PPPoE[/COLOR]**: Tried pppoeconf but it couldn´t connect. Suggested that I check the cables but considering that I can access the modem with XP and live-cd... It also suggested that another process might be using it. I'll have to check that.

**[COLOR="DarkRed"]Deactivated eth1[/COLOR]**: I figured there might be a conflict between wired and wireless card so I deactivated the wireless card.

**[COLOR="#8b0000"]Static DNS with DHCP[/COLOR]**: Edited /etc/network/interfaces
```

auto eth0
iface eth0 inet dhcp
dns-nameserver XX.XX.XX.XX

```

then ```
sudo invoke-rc.d networking restart
```

Nothing. I guess that the problem isn't if it's a static IP or not, it's getting an IP to the eth0 interface at all! An alternative would have been to prepend the DNS in /etc/dhcp3/dhclient.conf Been there, done that...

**[COLOR="#8b0000"]Live-cd[/COLOR]**: Used the cd for 6.06 LTS which gave me access to the internet. Loooking at the different configuration files I realised that I should have used the IP of the modem as the DNS rather than the DNS the modem uses.  In hindsight maybe I should have copied the configuration files but they looked so very similar that I didn't see the point at the time.

**[COLOR="#8b0000"]IPv6[/COLOR]**: Blacklisted IPv6 just in case...

**[COLOR="#8b0000"]Booting different kernels[/COLOR]**: Tested booting a different kernel (can't boot the latest one so I've only tested one other kernel).

**[COLOR="DarkRed"]Pulling the plug[/COLOR]**: Tried to pull the plug and begin with a fresh start the day after but same old problem. Guess I could do a hard reset but I don't think thats addressing the real problem.

---

### Post by tinmon on 2008-03-09
```
dpkg --configure -a
```

I suspected that a broken package might be causing the problem and when I tried to (re-)install **network-manager-kde_0.2ubuntu1-0ubuntu5_i386.deb** I found out that it was installed but not configured...

Then all I had to do was issue that simple command and that took care of a lot of issues for me. 

In retrospect this should have been on my list of possible solutions as I've come across this type of problem before. On the other hand, those instances have surfaced after upgrading a single package with dependencies rather than a system upgrade.

:KS:KS:KS

---

