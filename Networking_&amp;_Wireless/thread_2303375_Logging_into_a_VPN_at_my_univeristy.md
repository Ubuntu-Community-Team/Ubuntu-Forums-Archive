---
title: "Logging into a VPN at my univeristy"
date: 2015-11-18
forum: Networking &amp; Wireless
---

### Post by TheCommissar on 2015-11-18
Hi folks.

Running Ubuntu 64-bit 15.04 and trying to connect using Google Chrome to my university's VPN service (Cisco AnyConnect Secure Mobility Client).

I've got as far as the failure of the web-based installation (which doesn't work in Firefox either) and have downloaded the vpnsetup.sh shell script. I can't run that by clicking on it in Downloads, it pops up with a gedit window which is instantly not responding. I have to force quit.

I attempted to follow these instructions: [http://www.snekul.com/wordpress/blog/2012/05/02/installing-cisco-anyconnect-client-on-ubuntu-12-04-x64/](http://www.snekul.com/wordpress/blog/2012/05/02/installing-cisco-anyconnect-client-on-ubuntu-12-04-x64/)

and this was the result on my terminal

```

charlie@Malinowski:~/Downloads$ sudo apt-get install ia32-libs lib32nss-mdnsReading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32z1 lib32ncurses5


E: Package 'ia32-libs' has no installation candidate
charlie@Malinowski:~/Downloads$ chmod +x vpnsetup.sh
charlie@Malinowski:~/Downloads$ sudo ./vpnsetup.sh
Installing Cisco AnyConnect Secure Mobility Client...
Extracting installation files to /tmp/vpn.XX6U82/vpninst179962116.tgz...
Unarchiving installation files to /tmp/vpn.XX6U82...
Starting Cisco AnyConnect Secure Mobility Client Agent...
Failed to start vpnagentd.service: Unit vpnagentd.service failed to load: No such file or directory.

```

I'm not terribly experienced in this sort of thing I'm afraid. Where have I gone wrong?

Thanks in advance.

---

### Post by matt_symes on 2015-11-18
Hi

You have done nothing wrong but the *ia32-libs* package is not available in 15.04, in fact it's not even available in my 14.04 installation. It was removed in a previous version; i forget the exact one.

```
matthew-laptop:/home/matthew:1 % apt-cache search ia32-libs
matthew-laptop:/home/matthew:1 % 
```

The instructions you are following are out of date. 

Look for newer instructions if you can find them.

Kind regards

---

### Post by TheCommissar on 2015-11-18
Do you know what the source of this might be?

```
[COLOR=#000000][FONT=Ubuntu Mono]Failed to start vpnagentd.service: Unit vpnagentd.service failed to load: No such file or directory.[/FONT][/COLOR]
```

---

### Post by matt_symes on 2015-11-18
Hi

Sorry. I had to get pop out for a moment there and my last post was a bit rushed and i didn't finish my thought.

Anyway to replace ia32-libs you need to install these two packages

```
sudo apt-get install lib32z1 lib32ncurses5
```

Firstly have you installed the above two packages ? It looks like they are required from your post #1.

> Do you know what the source of this might be?

I would have to look into it but i cannot do that until tonight as i have a busy afternoon.

Someone else may be able to help you in the meantime.

Kind regards

---

### Post by Bucky Ball on 2015-11-18
With uni/school network issues we generally advise the IT department as the first port of call. Have you talked to the IT department at your uni about this? By all means, keep troubleshooting, but they may be able to help you out directly and quickly. Good luck. :)

---

### Post by TheCommissar on 2015-11-18
I hadn't installed the above packages, so thanks. Still displaying the same message sadly, but I'll get to the bottom of it! Thanks again for your help.

---

### Post by TheCommissar on 2015-11-18
I did not solve the problem, however I found this workaround, which means I should now be connected on a VPN.

[http://askubuntu.com/questions/154699/how-do-i-install-the-cisco-anyconnect-vpn-client](http://askubuntu.com/questions/154699/how-do-i-install-the-cisco-anyconnect-vpn-client)

---

### Post by matt_symes on 2015-11-18
Hi

Thanks for posting your workaround. I'm glad it's fixed.

I'll mark this thread as [solved] for you.

Kind regards

---

### Post by refael on 2016-07-11
> **TheCommissar said:**
> Do you know what the source of this might be?

```
[COLOR=#000000][FONT=Ubuntu Mono]Failed to start vpnagentd.service: Unit vpnagentd.service failed to load: No such file or directory.[/FONT][/COLOR]
```

On Ubuntu 16.04 on Dell XPS 9434 installing the openconnect addition did the trick:

[CODE] sudo apt-get install network-manager-openconnect-gnome
[CODE] sudo ./vpnsetup.sh

Now things worked.

---

