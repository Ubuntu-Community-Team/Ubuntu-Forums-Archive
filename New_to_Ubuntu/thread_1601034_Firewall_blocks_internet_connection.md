---
title: "Firewall blocks internet connection"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by narthir on 2010-10-19
Hi everyone,

a few days ago i started working on samba ([http://ubuntuforums.org/showthread.php?t=1600264](http://ubuntuforums.org/showthread.php?t=1600264)) and i probably broke my firewall (or something like that). I installed guarddog, disabled > enabled firewall, uninstalled guarddog. Now i have firestarter. Every time i start my PC i have no internet connection. If i start firestarter (FS) it shows the firewall is running, but there is no activity. If i stop and then start the firewall, the connection is back.

---

### Post by robsoles on 2010-10-19
Firestarter appears to be a bit of an abandoned lemon - last update to it was 2005 I am told.

Please try:
```
apt-get purge firestarter
apt-get install gufw
```

Try gufw out and see if that corrects your "internet doesn't work till firewall is restarted" problem - post back if it is same (or other undesirable) condition and I will try harder (or someone else will turn up).

---

### Post by narthir on 2010-10-20
I did purge, install gufw, reboot > no internet. I tried to restart the firewall with gufw but it didnt help. So i reinstalled firestarter (luckily the packages where still there), stopped and started the firewall and it helpped :/

---

### Post by robsoles on 2010-10-20
Would you please try following in terminal followed by a restart and try to use internet without referring to firestarter after restart:
```
ufw reset --force
```

If that works you can uninstall firestarter and try gufw again.

---

### Post by jtarin on 2010-10-20
How do you connect to the internet (hardware)?
Are you using network manager? Is your connection configured to come up automatically?

---

### Post by narthir on 2010-10-20
[FONT=monospace]"uwf reset --force" didn't help (IMs and HTTP[/FONT][FONT=monospace] was still blocked[/FONT][FONT=monospace] before i had to use firestarter again to write this post). I connect through a router connected to a dsl modem (should be alright because every other box still works). I do use network manager and connect aromatically but i didn't change there anything. All the problems started after installing guarddog and firestarter (is it possible that guarddog (now uninstalled) left something behind)? And as I said a simple stop/start firewall in firestarter unlocks Internet connection.
[/FONT]

---

### Post by jtarin on 2010-10-21
>  if you are behind a home router, you are better than nothing. If you have no services to connect to *maybe* you don't need a firewall. ssh is on by default. make sure you have a strong password. firewall recommended over none.

First I would like to address your configuration. **#1**. You have a router therefore there is no need for a software (firestarter) firewall....it's redundancy. Consult your Mfg's manual for your router on how to set it up for further hardening if you think you need it. I have run PPPOE with and ADSL modem and router for over 10years and have "never" needed or wanted a software firewall.**#2** If you still want to use Firestarter have you consulted the [manual]("http://firestarter.sourceforge.net/manual/index.php")? **#3** Remove Firestarter and all config files in /home/username folder.(usually hidden)probably look for Guarddog config files in the same place and start clean with a new Network Manager configuration.

I currently run no services except the occasional FTP.

---

### Post by narthir on 2010-10-21
My bad, i should have written it before. I don't want the damn firewall i actually installed those stupid programs to turn it of. I had some sharing problems and there was a possibility that it block samba. If there is a way to turn of iptables i would be happy (as i understand iptables is the actual firewall and the programs just configure it or something like that). I will try deleting configs in home and see if it helps.

---

### Post by perspectoff on 2010-10-21
> **jtarin said:**
> First I would like to address your configuration. **#1**. You have a router therefore there is no need for a software (firestarter) firewall....it's redundancy. Consult your Mfg's manual for your router on how to set it up for further hardening if you think you need it. I have run PPPOE with and ADSL modem and router for over 10years and have "never" needed or wanted a software firewall.**#2** If you still want to use Firestarter have you consulted the [manual]("http://firestarter.sourceforge.net/manual/index.php")? **#3** Remove Firestarter and all config files in /home/username folder.(usually hidden)probably look for Guarddog config files in the same place and start clean with a new Network Manager configuration.

I currently run no services except the occasional FTP.

There are many reasons to fine tune network access within a LAN using iptables. A router's NAT is insufficient to do this, and to advise someone to rely only on a router's NAT as a firewall is not very good advice.

The user's problem is probably with the networking cache and likely has nothing to do with the firewall or iptables (especially if the problem exists no matter which firewall he tries). There are other threads on Ubuntu Forums about the networking cache.

If

sudo /etc/init.d/networking restart

allows Internet access for this user, then the problem is in the networking cache and he should look for the threads that concern this.

With Firestarter it is easy to merely click the "Stop firewall" button, which will allow all traffic in or out. If there is still no traffic after doing this, it has nothing to do with the firewall or iptables or anything, but with the network cache.

I have no idea whether there is a similarly easy solution to open up all ports (in realtime) with ufw or not.

---

### Post by perspectoff on 2010-10-21
> **narthir said:**
> My bad, i should have written it before. I don't want the damn firewall i actually installed those stupid programs to turn it of. I had some sharing problems and there was a possibility that it block samba. If there is a way to turn of iptables i would be happy (as i understand iptables is the actual firewall and the programs just configure it or something like that). I will try deleting configs in home and see if it helps.

Oh, you have suffered from the misinformation that is commonly disseminated on these forums.

You don't need a firewall to allow Internet traffic. All Internet traffic is allowed by default in Ubuntu. You only need a firewall if you want to disallow traffic.

There are some users who say "ports are closed" by default in Ubuntu, and that is very very misleading. A closed port merely means that there currently is no traffic. It does not mean that traffic is blocked or can't be "opened" by an application at any time.

If you simply want all traffic to be able to go in and out from the Internet, you don't actually have to do anything after installing Ubuntu. You don't need any firewalls. Remove them all and be happy.

---

### Post by narthir on 2010-10-21
Well, i had enough with this ******** so i risked e little. I started "sudo gnome-search-tool", selected "*firestarter*" "*guarddog*" and deleted everything i found, not carrying if the damn thing boots again (i had my mind set to download right away a older Ubuntu, many people seem to think there are more stable). Restarted and TADA, it works. Maybe there where some scripts that where started at boot up and wouldn't be updated by the changes in firestarter/guarddog. Anyway thanks a lot for your help and time. Thats the great thing about linux that there are so many people wanting to help.

P.S. How do I change the Thread to [Solved]? Or do the admins that?

---

### Post by robsoles on 2010-10-21
Well done, look at 'Thread Tools' in red above, option to mark thread as solved is there.

---

### Post by jtarin on 2010-10-21
> **perspectoff said:**
> There are many reasons to fine tune network access within a LAN using iptables. A router's NAT is insufficient to do this, and to advise someone to rely only on a router's NAT as a firewall is not very good advice.

While I will agree to various reasons to fine tune your connection but the OP did not state that he needed a fine tuning machine.As to routers and protection. Lower cost products provide a DHCP server, PAT/NAT services, 1-8 physical ports to network computers and/or wireless service. NAT hides your computer(s) from the Internet which makes it a simple but effective firewall. Higher cost products, but still under $200, provide additional features like built-in stateful packet inspection (SPI), support for Virtual Private Networking (VPN), Public Key Infrastructure (PKI), content filters, anti-virus protection, and more.

---

