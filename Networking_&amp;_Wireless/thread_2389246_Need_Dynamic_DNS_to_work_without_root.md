---
title: "Need Dynamic DNS to work without root"
date: 2018-04-13
forum: Networking &amp; Wireless
---

### Post by peejaygee on 2018-04-13
Hey All, 

Looking for a solution for this. I'm wanting to run a server on a non-root user, behind a VPN, but I need the DNS to be able to update in-case my IP changes.

I've tried no-ip and dynu and both have the software and/or the commands for daemon for update, but they both seem to need sudo or root to run, which I don't want, as the software I'm using for the server doesn't run if you are root.

I'm semi-ok with console and following instruction, but I'm predominately not a linux user, so go easy on me. 

I'm using 16.04 LTS.

Is it is possible, is there either client software (for the Dynamic DNS people) that updates without root needed, or is there a work around, so I can basically say

boot machine into non-root user [currently working]
connect to the VPN [currently working]
turn on root for user i'm logged in to
send signal to dynamic dns of the ip i've connect through the vpn
turn off root
start up server software that won't run under root. [currently working]

hope you guys can help.
Thanks in advance.

---

### Post by TheFu on 2018-04-13
Network management stuff requires root.  No way around that, but you can automate the updates with **ddclient**. Once installed, it queries the router status page and gets the current WAN IP, then it will log into the dynamic DNS provider account and update their DNS settings.  I used ddclient for years and don't remember having any issues.

But, I haven't used ddclient since around 2010, but think it is still working, supported and easy.

No user action needed AFTER is it all setup.

I don't understand the steps above.  Seems most of those things, if not all should be trivial to automate.

---

### Post by peejaygee on 2018-04-13
the problem I'm facing is trying to use ddclient as a normal user, when I su in and run it (with the right conf) it updates, but if I'm a normal user, it fails. there is a package that I'm using that can only been used as a normal user, so I don't want to add the user to the sudo group.

---

### Post by TheFu on 2018-04-13
su? Huh?  Shouldn't be doing that on ubuntu.

ddclient, once install, doesn't require any user interactions. It works automatically behind the scenes when it is setup to run as a daemon, automatically at boot.  Is there something about your setup which prevents that?  The manpage for ddclient was fairly clear last time I looked.

BTW, many VPNs block all inbound connections, so for any lurkers working with the same idea, be certain to verify that the VPN used allows inbound.

If all you want to do is to have a web server available at the end of a VPN provided IP, that doesn't seem too hard to completely automate through scripting at startup and shutdown.   But, without all the background, it can seem impossibly difficult, I suppose.

All stuff that modified network settings has to run as root at some level.  Allowing a normal userid to be able to modify networking  settings requires a bunch of trust. As you learn more about Unix permissions, why that is true will become clearer.

Not really related to this specific issue, but it is possible to allow a single command to be run, with very specific options, using sudo. That command can be run as root or joeblow or slong or peter or ... any other userid. Further, the commands can be allowed to groups, netgroups, a single userid, or a list of specific users. The configuration for sudoers is extremely flexible, well beyond "I need root", though that seems to be all that most people seem to learn.  

If you don't solve this problem through startup automation, as I would suggest, I suppose you can lock down the require access to extremely specific needs through sudo configuration.

If you provided a little background about your skills, perhaps someone with a similar background could interpret and make a clearer version of what I'm trying to explain?  Sorry, I suck at this.

---

