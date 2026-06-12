---
title: "network manager quit working after patches yesterday"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by BillGod on 2007-04-12
Running Feisty Beta

Network manager was working perfect.  I had a vpn setup to connect to my MS PPP vpn at work and was working fine.  Yesterday a patch came out for it.  The second the patch installed my network broke.  I was at work using vnc to run the update.  When I got home I had no network connection.  network manager says "no network connection" when moused over.  I checked my network settings and rebooted thinking it was just a glitch.  Still no network.  Changed my NIC over to DHCP instead of static and the internet  was working.  Network manager still says no network connection.  I removed every trace of network manager through synaptic.  then re-installed.  If I run nm-applet from prompt I still get same problem.  Any ideas on what to check?

Thanks
Bill

---

### Post by cary67 on 2007-04-12
You're not alone.  The exact same thing happened to me.  Feisty had actually been a big improvement with Network Manager and the overall stability of the wireless connection using my Belkin F5d5060.  However, that update hosed Network Manager.  I was able to get things running again, but the link now drops out periodically, as it used to on 6.10.  There was a second update to NM, but it didn't change.  It still says "No Network Connection" when I mouse over and "No Network Devices Have Been Found" when I click on it.

Hopefully another patch will clear this up....

---

### Post by davidsrsb on 2007-04-13
I have a couple of machines that always show "no network connection" although I am on a wired network and it IS working.
Disabling and reenabling the wired network makes the network icon staus correct.
This has been happening for a few patches of the nm software

I want to manually set a local dns server, but the dhcp setting overides anything I enter at the next reboot with the (Slow) ISP servers.

---

### Post by creekbaum2 on 2007-04-13
I have a similar problem... I installed Kubuntu Feisty today, and my network was working fine, but my screen resolution was off and I couldn't change it so I decided to download any updates available, and after doing so I can't connect to my network anymore. It doesn't say no connection, instead it acts like it is going to connect, gets to 57%, and then restarts at 0%, it does this very rapidly, and constantly. It never actually connects. Any ideas?

---

### Post by kasprowv on 2007-04-13
I seem to have a similar problem. the little icon on the taskbar (?) has a minus sign through it. I double click on it and I get the message SIOCGIFFLAGS error: No such device. It is a belkin card and the device manager sees the card.

I dont know if this is exactly the same problem as everyone else is experiencing, but it did start after installing 2 updated files yesterday.

---

### Post by Zdravko on 2007-04-13
[cary67]("http://ubuntuforums.org/member.php?u=272117"), I was running FF Beta with wireless working OK. But after updating, my network manager just refuses to connect. Why? Can you help me?

---

### Post by pgroover on 2007-04-13
I had the same problem after the update but it appears that I was able to fix my wireless connection by enabling roaming in NetworkManager.  I didn't have to uninstall NM or anything else, just enabling that has cured my problem so far and I've gone through several reboots since doing so.

---

### Post by Mr Squiddy on 2007-04-13
[http://ubuntuforums.org/showthread.php?t=407204](http://ubuntuforums.org/showthread.php?t=407204)

This has some suggestions for workarounds.  I got mine working by rolling back to the previous version of NetworkManager.

---

### Post by pixar on 2007-04-13
Wireless stopped working after an update about an hour ago. On hovering my mouse over the icon I get a message "No network connections" when there is a working network connection and on mouse-click I get a message "No network devices found".

---

