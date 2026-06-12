---
title: "VPN Connection Configuration not showing up on Network Manager"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by shadowen2 on 2007-08-22
Hey everyone!  just before I start, gotta say, these forums are the best!  Thanks to everyone out there who works on them.

I have a bit of an odd problem and my guess is that it's so simple that I'm missing the obvious. 

I'm trying to set up a VPN connection with Ubuntu Feisty.  I have all the latest updates installed.  This is a fresh, cleanly installed system (configured 2 days ago).  I follwed the user guides and I got stuck right after I issue the command

"sudo apt-get install netowrk-manager-pptp"

APT went throught all the usual girations, added the dependencies needed for pptp but now when I go to click on the Network Manager in the system tray, according to the setup documentation located at [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) I'm supposed to see "VPN Connections" and all I see is "Manual Configuration"

What gives?  Do I not understand the instructions right?

I also tried installing two other VPN protocols just to see if maybe here was a bug in the installation of the first one...and still nothing.  Any ideas?

---

### Post by creedog on 2007-08-22
I have the same issue so I am interested to know how you resolve it. However I did get the cisco vpn client working...

---

### Post by shadowen2 on 2007-08-23
The plot thickens...

I found an icon in my gnome "Applications" drop down under "internet" entitled "VPN Connection Manager (PPP generic)"  so I tried launching that....still nothing. 

Next step, I saved the launcher to the desktop, then opened the properties for it and found the command it was issuing.  I tried that command in the terminal and I get the following errors, followed by a dialgon that looks like what is described in the Ubuntu documentation.  It seems like either I don't have something configured right OR I've discovered a bug?

I issued the following command:

[INDENT]shad@server:~$ nm-vpn-properties
(nm-vpn-properties:13704): Gtk-CRITICAL **: gtk_expander_set_expanded: assertion `GTK_IS_EXPANDER (expander)' failed

** (nm-vpn-properties:13704): CRITICAL **: vpnui_opt_connect_signals: assertion `opt->widget!=NULL' failed

** (nm-vpn-properties:13704): CRITICAL **: vpnui_opt_connect_signals: assertion `opt->widget!=NULL' failed

** (nm-vpn-properties:13704): CRITICAL **: vpnui_opt_connect_signals: assertion `opt->widget!=NULL' failed

(nm-vpn-properties:13704): Gtk-CRITICAL **: gtk_expander_set_expanded: assertion `GTK_IS_EXPANDER (expander)' failed

[/INDENT]


It didn't seem to help if I issued this when sudoed either.  In fact, I got exactly the same output (I know, I know...but I thought I'd try...)

---

### Post by hamidaddin on 2007-08-25
I had the same problem ans solved it by going to the manual network configuration and enabling roaming mode...

---

### Post by eeclark on 2008-02-25
> **hamidaddin said:**
> I had the same problem ans solved it by going to the manual network configuration and enabling roaming mode...

Roaming mode was already enabled for me so this did not work for me.
Anyone else get it working?

---

### Post by rekster on 2008-07-09
Same problems, no VPN Connection Manager shows up unless I enable Roaming Mode.  I DONT WANT Roaming Mode, i want a static ip address.  Grrrrr

Is this problem being looked at??

---

