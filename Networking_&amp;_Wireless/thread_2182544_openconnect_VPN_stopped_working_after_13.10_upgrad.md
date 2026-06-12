---
title: "openconnect VPN stopped working after 13.10 upgrade"
date: 2013-10-21
forum: Networking &amp; Wireless
---

### Post by mikecole on 2013-10-21
Has anyone seen this?  I have an openconnect VPN configured, worked fine for months in 13.04.  After updating to 13.10 this morning (2 different computers) I get "Authentication failed." on both machines.  On one box, I removed then re-installed openconnect.  That seemed to have no affect.  

Anyone got any great ideas?  I'm not a total noob, but frankly, I'm not a *nix expert either.  Go with KISS theory for me and I'll be extra happy.  Appreciate any help you might be able to provide.

---

### Post by ccrs8 on 2013-10-23
Yes, I experienced this as well.  Two different computers.  Both when I upgraded from 13.04 to 13.10 and when I did a clean install of 13.10.  Openconnect worked great from Ubuntu (Xubuntu, actually) 10.10 through 13.04, and then stopped working for 13.10.

If you run it from the command line you can see a better error.  I was getting an error about not being able to create a vpnc folder.  I created that folder, then I got a permission error about not being able to write to it (I'm not at my computer right now - sorry for not having the exact messages).  If you run openconnect from the command line using sudo, it does work.  I've tried adding my regular user to the vpn group, that didn't help.

Openconnect was so nice to use - integrated with network manager just like any other connection, and connected to my office beautifully.  It's actually not that big of a deal to me right now because great improvements have been made with the 64-bit AnyConnect client from Cisco and it now installs quite easily for me (battling with that client in 2010 was what drove me to the beauty and simplicity of openconnect in the first place).  But I would still go back to openconnect in a second if it started working.  I still have it installed on my machines so that I can see if it ever gets updated via the software updater.

---

### Post by bradlehner on 2013-10-26
I've had the exact same problem.  I'm unfortunately a bit of a noob, so I've struggled to find a fix for this.  I have been searching for a few weeks now, and I've tried reinstalling packages and various workarounds from posts online.  I've tried both the connect manager approach and using openconnect directly as sudo.  I can't find a fix.  Very frustrating.  It worked fine for me up through 13.04.

---

### Post by heruan on 2013-11-08
Same problem, I get "login failed". No solutions yet?

---

### Post by MorrisseyJ on 2013-11-15
Bugs are filed here:
[URL="https://bugs.launchpad.net/ubuntu/+source/openconnect/+bug/1229195"]
https://bugs.launchpad.net/ubuntu/+source/openconnect/+bug/1229195[/URL] & [https://bugs.launchpad.net/ubuntu/+source/network-manager-openconnect/+bug/1202204](https://bugs.launchpad.net/ubuntu/+source/network-manager-openconnect/+bug/1202204)

It appears the answer is to run openconnect from the command line specifying the --no-mxlpost option. 

I am not sure how to do this, but will now post on the bug asking for directions. 

If anyone has any suggestions that would be great. 

Also confirming the bug will likely get it fixed faster. 

j

---

### Post by MorrisseyJ on 2013-11-15
Workaround for me is to use the terminal:

Do the following: 

1. Open terminal

2. sudo openconnect --no-proxy https<gateway>

3. enter (admin) password

4. enter username (I had to do this without any domain/gateway extension)

5. enter (vpn) password

Connection started and worked for me. 

Thanks to Cherif Tawil ([https://bugs.launchpad.net/ubuntu/+source/openconnect/+bug/1229195](https://bugs.launchpad.net/ubuntu/+source/openconnect/+bug/1229195)) for the instructions. 

j

---

### Post by ccrs8 on 2013-12-03
In reading some of the bug reports, it looks like there is a funny work-around to this.  When you open up the connection manager dialog and click the "connect" button, click it twice rapidly.  Then log in as normal, and it will work.

---

### Post by dr-alves on 2013-12-06
yeah, I can confirm the "click twice in quick succession" trick works. how random...

---

