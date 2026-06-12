---
title: "likewise-open problem"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by mo0on on 2008-01-04
Hello,

my problem is that I have to integrate Edubutnu into a Windows-AD. That works sometimes really good but in my case it did not work. The Problem is that the domain and the NetBios-name are different and this causes much trouble (sometimes I can log in, sometimes I have first to log in local, log out and then I can log in with a domain user).
On my search through the internet I found "likewise-open" which should make an integration very easy. Should is the right word because nowhere I can find an install-guide, a how-to or some other informations. All I can find is how great it is ;).

Does anybody in this forum now a good Howto or something like that?
Good tips how to integrate Edubuntu into a Windows-AD are also welcome. But it has to be a easy way because the people this is for aren't very fit in these things^^

so long
mo0on

---

### Post by perfecttao on 2008-01-21
Similarly, I can't find any man pages for the application  - installed using the .deb, and the installation works fine, but what then....?  There are no installation instructions at all, and the README that installs as part of the application is pretty much empty!

The write-ups I've read on this are really encouraging - so really keen to give it a go!

---

### Post by ewtesterman@cox.net on 2008-02-05
Okay this one took me a few minutes to find as well. After you run the installer you will find the following  executable in the system.

```
/opt/likewise-open/bin/domainjoin-gui
```

I did find a gotcha, before you run that program do the following:
Get your current ip address run ifconfig in a terminal
Then set your network settings to static and assign that ip address
Then you can run the program without problems. I found that if you network-manager is set to roaming and dhcp that the domain join will fail, it seems that during the process your networking gets restarted, and network-manager takes too long to get an address, so the process will time out and die. Anyway after you are joined to the domain you can then go back to your normal network settings. 

My question is if anyone knows how to map the domain users to unix groups?

---

### Post by perfecttao on 2008-02-06
Thanks mate :)  Will give that a go today and let you know how I get on. To log on to the domain do you have to enter the username as 

DOMAINNAME\username 

or

DOMAINNAME+username

?

---

### Post by ewtesterman@cox.net on 2008-02-06
DOMAIN\username or [email]username@domain.net[/email]

Update: I am still looking for a way to map domain users to linux groups I have found the following all config files that have been backed up with this convention filename.ext.lwidentity.bak you will see this for /etc/nsswitch.conf /etc/krb5.conf and /etc/hosts. I also see a few referances to /lib/libnss_lwidentity.so.2 and /lib/security/pam_lwidentity.so, but I think most of the magic for user mappings is taking place inside of /opt/likewise-open/bin/ConfigureKrb5.pl

---

### Post by mo0on on 2008-02-19
So far so good, with static ip it worked fine. The other little tool (lwiinfo) says that I'm in the right domain and users and groups are also visible.
But there are other things which don't work. The log in for examble. After the domain joining I tried to log in with Domain\name and name@domain but both didn't work.

Do I have to edit the smb.conf? Or should likewise do anything for me?
still many questions without answers^^

Hope anybody can help me.

EDIT: After configuring smb.conf it works fine. Only the homes are not mounted correctly but this is only a bit more work to do ;)

---

### Post by DMGood on 2008-02-19
I believe you can look here, [http://lists.likewisesoftware.com/pipermail/likewise-open-discuss/](http://lists.likewisesoftware.com/pipermail/likewise-open-discuss/)

Go to the 2007 threads, I believe their are some instructions there.  Hope that helps.

---

### Post by perfecttao on 2008-03-19
After much fiddling I still couldn't join the domain - got the same error despite static IP.

I checked the nsswitch.conf again and I was missing the appropriate winbind entries....

When added the nsswitch.conf should look like:

> # /etc/nsswitch.conf
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat winbind lwidentity
group:          compat winbind lwidentity
shadow:         compat winbind

hosts:          files dns winbind
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis


Hope this helps someone!

---

### Post by leftcase on 2008-03-22
I found that I could join the domain without problem, but then had issues logging onto the local machine as a domain user.

Each time I tried I got a box saying 'error'. 

Doing a bit of digging, it looks like the likewise-open script wasn't set to start up with my system. I don't know if that's unique to me, or a software error but I've filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/205111"). The winbind errors that people are seeing are due to the likewise-winbindd service not running.

To fix the problem permanently, using sysv-rc-conf I turned the likewise-open service on for runlevels 2,3,4 & 5 and restarted. 

Now AD logins work fine.

Hope that helps someone with the same problem and if it does, click the little medal thing. I never gets any points lol!!!

---

