---
title: "Network auto-start?"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by Rumor on 2007-04-26
Hello all:
I just did a clean install of 7.04. I had been running 6.10. I have a wired network at home. 

When I restart my computer, I must now click the network icon each time to enable the connection. It enables fine. Is there something I am overlooking so that it automatically starts when the computer restarts?

---

### Post by mehlkelm on 2007-04-26
I have the same problem, this is really annoying and useless... Looking around here I get the impression that network-manager makes a lot of similar problems, so maybe we should remove that..

---

### Post by Rumor on 2007-04-26
I am reluctant to remove the network-manager package . . . I just upgraded today. Ordinarily I like to wait a few days before breaking my system :) 

But yes, it is very frustrating for remote admin stuff if you should have to reboot and your computer restarts with no network connection.

---

### Post by mike2357 on 2007-04-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/107123](https://bugs.launchpad.net/ubuntu/+bug/107123) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There are several posts about this exact problem.   I agree -- it is annoying, especially since this worked fine in previous Ubuntu releases.

A bug was logged.  See [http://https://bugs.launchpad.net/ubuntu/+bug/107123]("http://https://bugs.launchpad.net/ubuntu/+bug/107123")

There is a work-around, although it's not entirely clean, and that is to let "cron" do the work for you.

First, run
sudo crontab -e

Then, insert the following line:
@reboot             ( /bin/sleep 40; /sbin/ifdown eth0; /sbin/ifup eth0 ) > OUT_BOOT_NETWORK 2>&1

Then save/exit.  You can verify that change was made with
sudo crontab -l

The above does the following:
Every time the computer boots, wait 40 seconds (so that hopefully anthing releated to invoking network-manager is finished), and restart connectivity of eth0.  Send output to /root/OUT_BOOT_NETWORK.

Don't be too fast to log in to allow the restart to finish

This worked for me.  I have connectivity when I log in, even though the network-manager icon indicates there's no connection.  But I don't care.

This isn't a cure-all.  Any services that depend on connectivity just as the system boots won't have it.

Also, I suggest that every week or so you remove the cron command (you can run "sudo crontab -e" again and insert a # (pound sign) at the beginning of the line to disable it) and reboot the system.  That way, if this bug gets fixed, you won't have the unneeded restart.

Run the command
man 5 crontab
for an excellent discussion of how cron works.

Good luck.

---

### Post by jerrylamos on 2007-04-26
I've been having that network problem since early Feisty made Network Manager default.

Achtung, it doesn't do any good to Remove the Network Manager package, because boot still uses it to disable your network connection.  Browse /var/log/syslog and you'll see where the card is disabled.

So grit your teeth, when boot finishes try to remember to click the icon and click wired connection.  So far that's the fastest way to get around the Network Manager design deficiency, namely the programmer decided to disable certain network cards even though they work fine.

Another way if you know how to get into the boot scripts (I don't) add:
sudo dhclient

Cheers, Jerry:(

---

### Post by mehlkelm on 2007-04-27
So there is no way the current stable ubuntu release boots with internet?! Does everyone with Feisty have to manually connect with this panel applet. Or is it just us unlucky guys?

---

### Post by waterzebra on 2007-04-27
I am having the same problem - no network connection upon start. Choosing 'Wired Network' form network-manager works fine though. 
Like someone said, it's more of an inconvenience than a problem, but maybe it has something to do with others wireless connection problems.

---

### Post by Rumor on 2007-04-27
> **mehlkelm said:**
> So there is no way the current stable ubuntu release boots with internet?! Does everyone with Feisty have to manually connect with this panel applet. Or is it just us unlucky guys?

I wonder if we all have the same ethernet controller?

```
lspci
00:10.0 Ethernet controller: Macronix, Inc. [MXIC] MX987x5 (rev 20)

```
This is an old Asus motherboard, an A7V333-X board.

---

### Post by mehlkelm on 2007-04-27
> **Rumor said:**
> I wonder if we all have the same ethernet controller?

```
lspci
00:10.0 Ethernet controller: Macronix, Inc. [MXIC] MX987x5 (rev 20)

```
This is an old Asus motherboard, an A7V333-X board.

I have a different one:

```

02:09.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)

```

---

### Post by Red Knuckles on 2007-04-29
This worked for me in Linux Mint Bianca KDE. The KNetworkManager icon still pops up though I'd like to figure out how to stop that. Or I'll just hide it in system tray. Here's the instructions:

Disabling network manager in your gnome session will not work as that is just the 'notification area' for the network-manager service. To disable network-manager, either uninstall it (which will break ubuntu-desktop package) or do this:

Stop network manager...

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop

Create two files with only the word 'exit' in them. These files are:

/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher

Reboot.

I know he's talking about Gnome but it worked for me in KDE. 
:guitar:

---

### Post by mehlkelm on 2007-05-01
Removing network-manager (sudo apt-get remove network-manager) doesn't remove ubuntu-desktop and works for me. The panel applet disappears and the network is up after booting.

---

### Post by Rumor on 2007-05-01
Removing the network manager worked for me as well.

::EDIT::
Just don't do like I did and do it remotely via SSH. DOH!

---

### Post by jerome1232 on 2008-01-21
with 7.10 gutsy i just clicked network manager, clicked manual config, set it to dhcp, and connection starts automaticly for me, the only annoying thing is with wifi it shows the to monitors instead of the wifi bars, not a big deal

---

