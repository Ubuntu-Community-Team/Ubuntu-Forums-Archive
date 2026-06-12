---
title: "Change TightVNCServer Port"
date: 2016-02-21
forum: Networking &amp; Wireless
---

### Post by mebunto on 2016-02-21
Hi, I want to be able to allow remote access to my home Kubuntu machine.  
[LIST]
[*]I was advised not to use Krfb & Krdc - any comments?
[/LIST]

So I've successfully installed and run TightVNCServer, which listens on port 5901 by default.  I've spent hours trying to find out how to change from the default port, but I haven't managed to do so - and I'd rather change it so that I keep a reasonable level of security on my machine.
[LIST]
[*]How do I change the TightVNCServer listening port to something other than 5901?
[/LIST]

I understood that I should put the following at the start of the vncserver script:[INDENT]### BEGIN INIT INFO
# Provides:          vncserver
# Required-Start:    $remote_fs $syslog[/INDENT]
[INDENT]# Required-Stop:     $remote_fs $syslog[/INDENT]
[INDENT]# Default-Start:     2 3 4 5[/INDENT]
[INDENT]# Default-Stop:      0 1 6[/INDENT]
[INDENT]# Short-Description: Start daemon at boot time[/INDENT]
[INDENT]# Description:       Enable service provided by daemon.[/INDENT]
[INDENT]### END INIT INFO[/INDENT]
[INDENT]
[/INDENT]

[LIST]
[*]Can anyone tell me where it tells me what to put into the various arguments?
[/LIST]

Thank you in advance!

---

