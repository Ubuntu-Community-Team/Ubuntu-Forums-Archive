---
title: "Trouble with F5 SSL VPN"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by rivercitybuntu on 2008-11-18
I am able login to my company's SSL VPN (F5 FirePass), and use the preset shortcuts to resources just fine. But when I try to activate "Full Network Access" (necessary to reach network drives, etc.), the process fails.

Specifically, what happens is that Firefox tells me an application wants to download a plugin. I grant permission, the download happens, and then stops at the plugin install step with this message (edited for ID):

Firefox could not install the file at 

[https://COMPANY_URL_HERE/vdesk/vpn/nogzip/downloads.php/linux/SSLVpn.xpi?rnd=RANDOM_NUMBER_HERE](https://COMPANY_URL_HERE/vdesk/vpn/nogzip/downloads.php/linux/SSLVpn.xpi?rnd=RANDOM_NUMBER_HERE)

because: Install script not found
-204

Anyone have ideas of what's wrong here?

---

### Post by david3x3x3 on 2008-11-26
I'm having the same problem.

I actually get the same error from Firefox on Windows.

---

### Post by jlukescott on 2009-03-24
Have you guys tried restarting your browser? I have got the same problems as you, but when restarting the plugin name goes from 'default' to 'F5 SSL VPN'. It does connect for me (I use it for SSH terminal access) but only stays up for about 30 seconds. During this time it interferes with other sessions (SMB mounts, web browsers, etc). After 30 seconds the connection drops, the SSH sessions lock up, and when I close the F5 windows, the other sessions wake back up.

My environment:
Ubuntu Intrepid Ibex 32 bit
uname -a results:
2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
default firefox3 install AND clean download of firefox2 directly from mozilla.org
wireless AND/OR wired networking (very reliable 6meg internet connection)

I tend to think it's a problem with the F5 plugin, especially since the installation process is so buggy - gives me a feeling they didn't test it very thoroughly.

Anyone try the forums over at F5? 
[http://devcentral.f5.com/Default.aspx?tabid=53&forumid=4&tpage=1&view=topic&postid=27364#29186](http://devcentral.f5.com/Default.aspx?tabid=53&forumid=4&tpage=1&view=topic&postid=27364#29186)
[http://devcentral.f5.com/Default.aspx?tabid=53&forumid=4&tpage=1&view=topic&postid=29842#29842](http://devcentral.f5.com/Default.aspx?tabid=53&forumid=4&tpage=1&view=topic&postid=29842#29842)

---

