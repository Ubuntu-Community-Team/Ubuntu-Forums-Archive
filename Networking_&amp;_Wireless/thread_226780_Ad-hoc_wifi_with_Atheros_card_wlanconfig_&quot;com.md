---
title: "Ad-hoc wifi with Atheros card: wlanconfig &quot;command not found&quot; and no DNS"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by Leo Comerford on 2006-07-31
My laptop's wifi card has an Atheros AR5212 chipset; I've used it with success under Ubuntu in the past. Now, however, I'm trying to get it to join an ad-hoc network with several Win 2000/XP machines, and I can't find wlanconfig. I've tried the fix suggested at the bottom of [http://www.ubuntuforums.org/showthread.php?t=163701]("http://www.ubuntuforums.org/showthread.php?t=163701") - I used [linux-restricted-modules-2.6.15-23-386]("http://packages.ubuntu.com/dapper/misc/linux-restricted-modules-2.6.15-23-386") , the most recent version on my system. Without success, apparently: I tried whereis wlanconfig and locate -u; locate wlanconfig but see no sign of it. I also looked inside the package with dpkg -c - it appears not to be there. packages.ubuntu.com claims to [know nothing about it]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=wlanconfig&searchmode=searchfiles&case=insensitive&version=dapper&arch=i386").

Ironically, despite being advised that I [need to use wlanconfig]("http://madwifi.org/wiki/UserDocs/AdHoc") to set my Atheros card to ad-hoc mode, simply doing it the standard way using iwconfig seems to work. When I add

```
	wireless-mode Ad-hoc
```

to my ath0 entry in /etc/network/interfaces , ifup and ifdown both produce the error message

```
Error for wireless request "Set Mode" (8B06) :
	SET failed on device ath0 ; Invalid argument.
```

, but the connection is established or torn down anyway. (When I remove the entry, ifup fails to create a connection.) I don't get any DNS service, however; I don't know if this is a separate or related problem. (All the Windows boxes get DNS automatically: the ISP connection is through one of the WinXP machines via Windows' Internet Connection Sharing.)

All advice much appreciated,
Leo Comerford.

---

### Post by jamespi on 2006-07-31
i dont know if this advice is any good but - is it invalid because you capitalised Ad-hoc (ad-hoc)? Or is it because you didnt use sudo? the command i used to use the set this manually was "sudo iwconfig eth2 mode ad-hoc"

and the file that i edited to make my ad-hoc mode setting stick was etc/network/interfaces, where i added the line:

pre-up iwconfig eth2 mode ad-hoc
 
(under the group of settings for my wireless interface, obviously change eth2 to be whatever the relevant interface is for your card)

---

