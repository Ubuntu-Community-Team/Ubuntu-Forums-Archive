---
title: "iOS-like randomizing of Wi-Fi MAC address in Ubuntu 16.04?"
date: 2016-06-10
forum: Networking &amp; Wireless
---

### Post by &amp;KyT$0P# on 2016-06-10
In (L)ubuntu 14.04, is there a way to use random (spoofed) MAC addresses when scanning for Wi-Fi networks, and use the real (not spoofed) MAC address only for interacting with a Wi-Fi network I actually want to connect to and use?
(I think Ubuntu 16.04 NetworkManager has this capability, but can't upgrade yet.)

Also, in case something goes wrong when testing out possible solutions, how to work around the problem that changing MAC address after having connected to a network seems to prevent connecting to the network again?

---

### Post by kurt18947 on 2016-06-11
I'm not sure if this will help but this makes it easy to 'forget' previous wifi connections.

```
nm-connection-editor
```

I do get this message in the terminal:

> Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

Does Lubuntu 14.04 have "connections editor"? If so, that would be best. Ubuntu-Gnome 16.04 has made it difficult to access, don't know about Lubuntu. The terminal command is easier for me.

---

### Post by &amp;KyT$0P# on 2016-06-11
> **kurt18947 said:**
> I'm not sure if this will help but this makes it easy to 'forget' previous wifi connections.
Thanks, it looks like (re-)creating a new NetworkManager connection solves the connectivity loss issue.

---

### Post by &amp;KyT$0P# on 2016-08-28
bump

---

### Post by jeremy31 on 2016-08-29
Does this not work in Ubuntu [https://bbs.archlinux.org/viewtopic.php?id=216402](https://bbs.archlinux.org/viewtopic.php?id=216402)

---

### Post by &amp;KyT$0P# on 2016-08-29
Thanks for the link, I don't see anything about this in my NetworkManager.conf man page, I would assume because the NetworkManager in 14.04 is too old for that?
Still can't upgrade to 16.04 yet.

(By the way, that "halogen" is not me.  I'm not even a member of that board - Arch Linux is too advanced for me, I top out at Slackware and the 3 major BSDs.)

---

### Post by &amp;KyT$0P# on 2016-09-12
bump

---

### Post by &amp;KyT$0P# on 2017-04-19
I've now upgraded to 16.04, and I'm getting extremely mixed messages about whether this feature is available in NetworkManager or not.  Some sites say that NetworkManager 1.2 and wpa_supplicant 2.4, both of which are in Ubuntu 16.04, are all that's required.  Others say wpa_supplicant 2.6 is required.  Still others say this feature is actually not available until NetworkManager 1.4.0.  And even others say NetworkManager 1.2 can only randomize the MAC address for connecting to a network, **not** when scanning.

:confused:


I've tried adding this to [FONT=Courier New]/etc/NetworkManager/NetworkManager.conf[/FONT]...
```
[wifi]
mac-address-randomization=2

```
... and ensuring that my Wi-Fi connections all show "default" for MAC address randomization.  But I don't know how to see what effect, if any, the change had.


So which information is correct?

---

### Post by jeremy31 on 2017-04-19
You may want to try Ubuntu 17.04 as it may have this enabled but it could cause issues when trying to connect to wifi

---

### Post by &amp;KyT$0P# on 2017-04-19
Cool, 17.04 does have NetworkManager 1.4 :).  However, given stability requirements, using a non-LTS OS on this machine just isn't an option.  So worst case scenario is I'll have to wait for 18.04.

But, on the plus side, it looks like the zesty source package for NetworkManager [compiles]("https://www.debian.org/doc/manuals/maint-guide/build.en.html#completebuild") successfully on 16.04.  And with a couple manual tweaks...

1) fixing the "Device not managed" error - solution from [here]("https://askubuntu.com/a/882812") works -
```
sudo touch /etc/NetworkManager/conf.d/10-globally-managed-devices.conf
```

2) manually specifying dnsmasq for DNS - add this line to the "main" section of [FONT=Courier New]/etc/NetworkManager/NetworkManager.conf[/FONT] -
```
dns=dnsmasq
```

... the newer NetworkManager appears to work in my Xubuntu 16.04 VM.  Will need to test it a lot more to be sure it's good to go.

Thanks jeremy31 for pointing me in that direction!

---

### Post by &amp;KyT$0P# on 2017-04-28
Upgrading to NetworkManager 1.4 is the solution for 16.04.  syslog entries confirm that it's doing what I want.

As noted [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1681513"), the MAC address randomization feature makes USB Wi-Fi adapters unable to connect to anything.  And in testing, I found that installing the newer NetworkManager in 16.04 brings that same issue to 16.04.  Fortunately, my laptop's internal Wi-Fi adapter isn't USB, so it isn't a problem for me.

Since I no longer use 14.04 on bare-metal hardware, thread title adjusted and problem solved for me.  Thanks again jeremy31! :D

---

