---
title: "Ubuntu can't access XP shares by name, only IP address"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by sipickles on 2007-11-27
Hello,

Although a fairly steep learnng curve for an ubuntu newbie, I have managed to get my Gutsy box to talk to most of the windows machines in our office....

even a VISTA machine! I know, how good (and patient) am I???

One small snag - One XP pc is proving problematic (typically the one I need to access most often. I can see it in the Windows Network as ATKINSON, but when I click on it, it says

Sorry, couldn't display all the contents of "Windows Network: atkinson".

if I type its IP address into the bar, I get access no problem:

smb://10.0.0.5/

Can anyone suggest a way to get the name to work without having to resort to IP address, since I can never remember it?


Many Thanks

Simon

---

### Post by spd106 on 2007-11-27
If you're using static IPs then you can add an alias for it in System -> Administration -> Network, under the hosts tab.

If you're using DHCP then you'll probably need to enable netbios lookups in the /etc/samba/smb.conf file. There are a few guides to doing this in the wiki and forum e.g. [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by kevdog on 2007-11-27
I think you need the winbind module installed and then appropriately configured.  dbott67 or dbott69 wrote a short how-to for this.

---

