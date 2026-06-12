---
title: "[SOLVED] Trying to get a network printer working with Ubuntu"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by dash86no on 2008-12-11
Desktop: Ubuntu 8.10 
Printer: Canon iRC3100
Print server: Windows 2003 on a domain. 

I add a printer via SAMBA, using the ip address of the server like so:

smb://10.10.0.165/iRC3100

I input the authentication details and hit the "Verify" button, which tells me the share is available. 

I click next, and select the make of printer manually, Canon - iRC3100.

The printer seems to be added. I try to print a test page. The printer kicks into life and for a moment I think I've cracked it. But the printer is actually printing out around 50 pages of random characters.

Anybody had success stories with Ubuntu and networked printers? Any advice would be most appreciated. 

Cheers,

---

### Post by dash86no on 2008-12-11
> **dash86no said:**
> Desktop: Ubuntu 8.10 
Printer: Canon iRC3100
Print server: Windows 2003 on a domain. 

I add a printer via SAMBA, using the ip address of the server like so:

smb://10.10.0.165/iRC3100

I input the authentication details and hit the "Verify" button, which tells me the share is available. 

I click next, and select the make of printer manually, Canon - iRC3100.

The printer seems to be added. I try to print a test page. The printer kicks into life and for a moment I think I've cracked it. But the printer is actually printing out around 50 pages of random characters.

Anybody had success stories with Ubuntu and networked printers? Any advice would be most appreciated. 

Cheers,

Sorry, should have done a little more research before posting.

Found this: [http://www.openprinting.org/show_printer.cgi?recnum=Canon-imageRunner_C3100](http://www.openprinting.org/show_printer.cgi?recnum=Canon-imageRunner_C3100)

So will try it and report back my results.

---

### Post by dash86no on 2008-12-24
Well this has been one of the most harrowing experiences of my life. 

Downloading the PPD did not work. Nothing seems to. 

I have been reading up on CUPS, and am currently trying to set up the printer through the CUPS web interface, for kicks. 

So I come up against a really weird problem:

1: I try to add a printer through the CUPS web interface
2: It asks me for a user name/password
3: I google, and see this is a common problem
4: the advice always sems to be "edit the cupsd.conf"
5: I edit the cupsd.conf, restart the daemon
6: Go back to the we interface,, nothing has changed
7: Look at the config file through the web interface, it has not changed!
8: double check my cupsd.conf through vim, yes that one is just as I edited it, with the auth lines commented out...
9: try editing the cupsd.conf.default then rebooting the machine in desperation. 
10: Check out the config files again. Bizarre, changes to the conf files do not seem to be being registered when I look at the conf file through the web interface.
11: Now for the really strange thing: stop the cups daemon, try the web interface: and find the thing is STILL RUNNING.

So what's going on here? Is the web interface (accessed through 127.0.0.1:631) not connected to the cupsd daemon?

I have to say I've had great times with Ubuntu but printing (or trying to print and seeing page after page of garbage flying out of the printer) has been a hardcore nightmare. 

Cheers,

---

### Post by nakama85 on 2008-12-24
with 8.10 it should be simple. Providing that your printer is something like an hp. When I set mine up the only thing I did was go to system--->admin--->printing   add new printer.
on one of my computers it detected it right away. On the other I just had to enter the router assigned IP manually. Either way you should not have to do much.... Let me know if this helps.

note: I would not go and try configuring cups or samba in 8.10. configuration should not be needed.

---

### Post by dash86no on 2008-12-24
> **dash86no said:**
> Well this has been one of the most harrowing experiences of my life. 

Downloading the PPD did not work. Nothing seems to. 

I have been reading up on CUPS, and am currently trying to set up the printer through the CUPS web interface, for kicks. 

So I come up against a really weird problem:

1: I try to add a printer through the CUPS web interface
2: It asks me for a user name/password
3: I google, and see this is a common problem
4: the advice always sems to be "edit the cupsd.conf"
5: I edit the cupsd.conf, restart the daemon
6: Go back to the we interface,, nothing has changed
7: Look at the config file through the web interface, it has not changed!
8: double check my cupsd.conf through vim, yes that one is just as I edited it, with the auth lines commented out...
9: try editing the cupsd.conf.default then rebooting the machine in desperation. 
10: Check out the config files again. Bizarre, changes to the conf files do not seem to be being registered when I look at the conf file through the web interface.
11: Now for the really strange thing: stop the cups daemon, try the web interface: and find the thing is STILL RUNNING.

So what's going on here? Is the web interface (accessed through 127.0.0.1:631) not connected to the cupsd daemon?

I have to say I've had great times with Ubuntu but printing (or trying to print and seeing page after page of garbage flying out of the printer) has been a hardcore nightmare. 

Cheers,

Ignore this, I was being an idiot. I am behind a proxy server  (I use my home ubuntu server with squid for this purpose) so when I was inputting 127.0.0.1 it was coming up with the local host of my server not the local client. 

Still, the CUPS browser isn't even coming up on my Ubuntu 8.10 desktop. I assume it's disabled by default.

---

### Post by dash86no on 2008-12-24
Well for some reason with my home laptop running 8.10 I can access the CUPS browser based page no problem. I just added my home Epson printer using the 127.0.0.1:631 after installing a driver from [http://www.openprinting.org](http://www.openprinting.org) and it's printing out perfectly.

I'm going to mark this thread as solved and recommend anyone having problems with Printers in Ubuntu to check out CUPS on port 631 local host (IMHO a much nicer UI than the gnome printer set up tool) and check out [http://www.openprinting.org](http://www.openprinting.org) for drivers. 

Thanks

---

