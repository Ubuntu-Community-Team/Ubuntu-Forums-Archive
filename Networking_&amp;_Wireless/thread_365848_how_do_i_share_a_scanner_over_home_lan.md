---
title: "how do i share a scanner over home lan?"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by mmoalem on 2007-02-20
hi there all - trying to setup a shared epson scanner on my home network. been following this howto ([http://www.linux.com/article.pl?sid=06/10/13/1751234](http://www.linux.com/article.pl?sid=06/10/13/1751234)) but it doesnt seem to work... on the server the scanner runs fine but the client cant see it over the network
when following the instructions the first error i got was on -
*kill -HUP `cat /var/run/inetd.pid`*
the error is -
*cat /var/run/inetd.pid: no such file or directory*
any ideas how to get it working?
cheers
michel

*** just checked the system>adminstration>services and it doesnt mention neither inetd nor xinetd or any other networking service...

---

### Post by spd106 on 2007-02-20
xinetd is not installed by default, this is a good thing because we don't want too many open ports on a default install.

So, you will have to install it yourself. xinetd is available in the main repo and is installed easily through synaptic.

---

### Post by mmoalem on 2007-02-20
hi there and thanks for the reply. unfortunatly it didnt make a difference... i have install xinetd through synaptic, added the lines needed from 'man saned' to xinetd.conf and rebooted but still client cant see scanner... tried to switch off xinetd and start inetd in the services applet and than rebooted and still no joy... 
any other ideas?

---

### Post by jsampaio57 on 2007-07-10
In Ubuntu, the saned is in /usr/sbin/saned, not in /usr/local/sbin/saned  
Change your conf file.

Jorge

---

### Post by needhelpplease on 2007-07-23
[Linux network scanning with saned](http://chiralsoftware.com/blog/Linux-network-scanning-with-saned-9404a25b8342ba4e.html)

---

### Post by Hellaxe on 2007-11-26
> **needhelpplease said:**
> [Linux network scanning with saned](http://chiralsoftware.com/blog/Linux-network-scanning-with-saned-9404a25b8342ba4e.html)

I tried this how-to but I can't see the scanner as a network scanner.
It's a Epson Perfection 3490 Photo and works perfectly in my box.
I've made all the steps but haven't no luck.
Probably there's a permission issue.
Can anyone give me some light???
Thanks

---

### Post by PhrankDaChickenGeek on 2008-01-26
I know this is an older thread, but if anyone is still searching on how to share a scanner, here is a different solution.
I wrote a small script that uses a webserver and a cgi script to share the scanner. Any computer with a web browser on the network can then access and use the scanner.

Info on setting up/installing it:
[http://ubuntu.online02.com/linux_scan_server](http://ubuntu.online02.com/linux_scan_server)

---

