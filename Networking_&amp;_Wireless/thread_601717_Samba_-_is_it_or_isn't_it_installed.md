---
title: "Samba - is it or isn't it installed?"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by AlanSmithee on 2007-11-03
I want to run samba on my Dapper system.  Synaptic shows 'samba-common' as being installed, and I see that the directory /etc/samba/ exists, with default smb.conf.  However, there is no file /etc/init.d/samba, so I can't run 'sudo /etc/init.d/samba start [stop]' - which makes me wonder if samba is properly installed.  Here's the result of 'sudo find -name samba'

/var/cache/setup-tool-backends/backup/network/First/etc/samba
/var/lib/samba
/etc/dhcp3/dhclient-enter-hooks.d/samba
/etc/pam.d/samba
/etc/samba
/media/samba
/usr/share/samba

(I made /media/samba whilst following Stormbringer's HOWTO on this site)

So far I haven't run 'sudo apt-get install samba' since I think it's best to use just one packet manager (to stop everything getting out of sync) - is that right?

Suggestions?

thanks!

---

### Post by AlanSmithee on 2007-11-03
Well, it appears samba *wasn't* installed, notwithstanding what Synaptic "said".  Whilst reading other posts I learned you could share out folders via the GUI.  So I did that, and as part of the process samba got donwloaded and installed.  Now I'm going to have a look and see whathappened to smb.conf ...

---

### Post by froy02 on 2007-11-03
You say samba-common is installed but is samba installed also?

---

### Post by Meson on 2007-11-03
I think the tools for a samba client are available by default, but the samba server is not.  You should also look into using cifs instead of samba.

---

