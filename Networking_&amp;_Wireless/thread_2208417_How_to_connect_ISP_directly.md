---
title: "How to connect ISP directly"
date: 2014-02-28
forum: Networking &amp; Wireless
---

### Post by satimis on 2014-02-28
Hi all,

Ubuntu 12.04.3

I need to connect my computer direct to the cable modem without via the router provided by ISP

I have the user name and password provided by ISP.  Please advise how to config /etc/ppp/peers/provider.   Any other files I need to configure as well?

Thanks

Rgds
satimis

---

### Post by varunendra on 2014-03-03
Is it a Desktop? If so, you can directly add all the relevant settings under the "DSL" tab in Network Manager. No need to configure any files manually, on the contrary, you may need to revert any manual configurations if using Network Manager.

---

### Post by satimis on 2014-03-03
> **varunendra said:**
> Is it a Desktop? If so, you can directly add all the relevant settings under the "DSL" tab in Network Manager. No need to configure any files manually, 

Thanks for your advice.

Already solved by installing pppoeconf.  The interface is PPPoE.  Now I can connect ISP directly on Cable Modem without via Router.

> 
on the contrary, you may need to revert any manual configurations if using Network Manager.

$ apt-cache search 'network manager'```

libntrack0 - lightweight connectivity tracking library
libproxy1-plugin-networkmanager - automatic proxy configuration management library (Network Manager plugin)
nova-network - OpenStack Compute - Network manager
lft - layer-four traceroute
netdisco-frontend - Web front-end for the NetDisco network manager
python-wicd - wired and wireless network manager - Python module
wicd - wired and wireless network manager - metapackage
wicd-cli - wired and wireless network manager - scriptable console client
wicd-curses - wired and wireless network manager - Curses client
wicd-daemon - wired and wireless network manager - daemon
wicd-gtk - wired and wireless network manager - GTK+ client
wicd-kde - Wired and wireless network manager - KDE client

```
Whether install libproxy1-plugin-networkmanager ?

Thanks

satimis

---

### Post by varunendra on 2014-03-03
> **satimis said:**
> Already solved by installing pppoeconf.  The interface is PPPoE.  Now I can connect ISP directly on Cable Modem without via Router.
Yup, that's another option, although not default and not as elegant as Network Manager, usually only needed when Network Manager fails due to some bug or configuration conflicts.

Nonetheless, that's a useful info. Thanks for sharing, and please mark the thread as [SOLVED] to make it more useful. :)

> Whether install libproxy1-plugin-networkmanager ?
Nope, you don't need to install anything extra to use a PPPoE connection in Network Manager. Everything is installed by default on Desktop systems and can be configured under the DSL tab of Network Manager (accessible via "nm-applet" menu at the top-right corner of the screen).

If you need to search for it via apt-cache, search for "network-manager" or "network-manager-gnome" instead.

---

### Post by satimis on 2014-03-03
> **varunendra said:**
> Yup, that's another option, although not default and not as elegant as Network Manager, usually only needed when Network Manager fails due to some bug or configuration conflicts.

Nonetheless, that's a useful info. Thanks for sharing, and please mark the thread as [SOLVED] to make it more useful. :)
Noted thanks.

> 
Nope, you don't need to install anything extra to use a PPPoE connection in Network Manager. Everything is installed by default on Desktop systems and can be configured under the DSL tab of Network Manager (accessible via "nm-applet" menu at the top-right corner of the screen).

If you need to search for it via apt-cache, search for "network-manager" or "network-manager-gnome" instead.
$ apt-cache policy network-manager-gnome```

network-manager-gnome:
  Installed: 0.9.4.1-5
  Candidate: 0.9.4.1-5
  Version table:
 *** 0.9.4.1-5 0
        500 http://ftp.hk.debian.org/debian/ wheezy/main amd64 Packages
        500 ftp://ftp.debian.org/debian/ stable/main amd64 Packages
        100 /var/lib/dpkg/status

```
Already installed.

How to start it?  Thanks

satimis

---

### Post by varunendra on 2014-03-03
> **satimis said:**
> How to start it?
By clicking on the "nm-applet" icon beside the speaker icon in the notification area (top-right in Gnome and Unity, can be other places in other Desktop Environments) > Edit Connections..

Or,

**Alt-F2 > nm-connection-editor**

However, it may conflict with pppoeconf now that you have already configured it with that. So I think you'll need to delete the configuration profile from pppoeconf if you need to use Network Manager instead.

If you are comfortable with pppoeconf, I'd say just leave it unless you are fond of testing/tinkering. :P

---

### Post by satimis on 2014-03-03
> **varunendra said:**
> By clicking on the "nm-applet" icon beside the speaker icon in the notification area (top-right in Gnome and Unity, can be other places in other Desktop Environments) > Edit Connections..

Or,

**Alt-F2 > nm-connection-editor**

I got it.  Thanks

> 
However, it may conflict with pppoeconf now that you have already configured it with that. So I think you'll need to delete the configuration profile from pppoeconf if you need to use Network Manager instead.

If you are comfortable with pppoeconf, I'd say just leave it unless you are fond of testing/tinkering. :P
Agreed.  I won't make any change just to learn an alternative.

satimis

---

