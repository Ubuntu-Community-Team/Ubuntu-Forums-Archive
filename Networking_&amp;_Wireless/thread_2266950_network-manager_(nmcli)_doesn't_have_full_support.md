---
title: "network-manager (nmcli) doesn't have full support?"
date: 2015-02-26
forum: Networking &amp; Wireless
---

### Post by billyb351 on 2015-02-26
Hi, I'm trying to use the command line form of network-manager to edit my connection lists, however it doesn't look like it supports some key commands such as adding an interface.
```
nmcli con add
nmcli connection add
```

These two commands above seem to error out.  They aren't in the man page for nmcli (on Ubuntu) either.  I'm at a loss of how to add a network connection using the command line tool nmcli. However, when I use my Debian Jessie install, 'nmcli connection add ...' works just fine, though Jessie has a slightly more recent version of network-manager (0.9.10.0) than Ubuntu 14.04 (0.9.8.8) but I wouldn't think that's the cause of huge blocks of functionality being missing... correct me if I'm wrong.  On both Debian and Ubuntu, I can use nm-connection-editor from the desktop to accomplish the manipulation of my connections... but I don't want this.  I use a kickstart config to install Ubuntu and it runs a post-install configuration script that is supposed to setup all the packages and configurations automatically so that when you first boot into the desktop everything is all setup.  Having to try manually add and create the "eth0" connection file, for instance in the post-install script, under /etc/NetworkManager/system-connections seems like a PITA when nmcli is supposed to do it for you.  Why does Debian have the full set of commands and not Ubuntu?  I thought that Ubuntu got most of its lower level packages from the upstream Debian? Should I be using something other than network-manager?

On a somewhat related note, the default connection that gets made is called "Ifupdown" and is not editable or deletable by the nm-connections-editor.  It seems that the /etc/network/interfaces file controls that and I have to manually delete two lines in there to get rid of that connection.

It seems that I can do a 'nmcli con delete'.  That seems silly to be able to delete a connection but not add one.

---

### Post by idanori on 2015-06-09
I have same problem!! (using network-manager-gnome 0.9.4.1-0ubuntu2.5)

did you solve it?

---

### Post by steeldriver on 2015-06-09
Assuming Ubuntu respects Debian's package numbering, the changelog seems to indicate that the feature was added in 0.9.6.0 (*"Add ability to connect to new WiFi networks from nmcli"*), however it is accessed via the 'dev' object rather than the 'con' object e.g.

```

nmcli dev wifi connect <SSID> password <PASS> iface <IFACE>

```

This seems to work in Trusty (nmcli version 0.9.8.8)

---

