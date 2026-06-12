---
title: "How incorporate a &quot;terminal&quot; like in a webpage to let the visitors connect to telnet"
date: 2014-12-29
forum: Networking &amp; Wireless
---

### Post by DiogoSaraiva on 2014-12-29
Hi,
how can I incorporate a terminal like in a webpage for users when click in link open the terminal with the telnet connection "telnet://subdomain.example.com:7300"
without other previleges of normal terminal?

Or if not possible a web page that contain a "terminal" and I let the users know that they have to issue the command "telnet subdomain.example.com 7300"

You maybe ask me why not simply put a link with the "telnet://subdomain.example.com:7300": because I tryed , and when I try to open it in a microsoft windows 8.1 and xp too and does nothing.... I tested in my Machintosh and it works... in ubuntu I didn't tested.... 

Is hosted in my ubuntu desktop 14.04.1 64 bits

Thanks in advance

---

### Post by TheFu on 2014-12-29
Telnet generally shouldn't be used anymore due to security issues. Using it to share information that is available publicly is old-school and a web server would normally be used for this today.

Allowing system access through a webpage without added security (strong VPN) is asking for trouble.  The solutions that I've seen all depend on a java applet - which has major security implications (to the point I cannot consider it at all).  That's just what I've seen - not all that there could be.

As for why it works in OSX - there is a native terminal app there. Does Windows have one and is it configured in the system-wide MIME types to launch a program and provide any arguments?

If you still want to try this - definitely use a chroot env for the sessions, but also understand that breaking out of chroot has been relatively common over the years which provides access to the complete system.

Do you want to have a terminal game -  which would have extremely limited functions
or
do you want to have nearly a full shell - which would have major security implications.

I googled "telnet game servers" to see some options. Interesting.  How-To setup a nethack server: [http://nethackwiki.com/wiki/User:Paxed/HowTo_setup_dgamelaunch](http://nethackwiki.com/wiki/User:Paxed/HowTo_setup_dgamelaunch)

Most telnet systems for games will have setup instructions.

---

### Post by steeldriver on 2014-12-29
not sure why you'd want to do that, however newer Windows versions do not include a telnet client by default (although it can be enabled as a 'feature')

---

### Post by DiogoSaraiva on 2014-12-29
Hi,
try "telnet dxcluster.cr7akg.com 7300" and in login CR7AKG
you will understand....

Its a informative plataform... that can be acessed via telnet and optional java applet.. but java applet I cant't do... it's hard...

I will post again soon

Thanks

---

