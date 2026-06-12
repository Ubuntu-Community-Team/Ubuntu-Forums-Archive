---
title: "Start Vino server from command line in 18.04"
date: 2018-05-11
forum: Networking &amp; Wireless
---

### Post by ginovh on 2018-05-11
Hi,

until 17.10 I could start/enable Vino server from command line with 
>gsettings set org.gnome.Vino enabled true

In 18.04 the 'enabled' key is not there anymore ( checked with  `gsettings list-recursively org.gnome.Vino`)

So my question: how can I enable/start Vino from the command line in 18.04 ?

(I know how to do it via GUI, but I want via command line as I have to enable it remotely via ssh)

Best regards,

Gino

---

### Post by weiyin on 2018-07-09
Vino is now enabled by network connections via network manager. Run the following to get the UUID of your network connection: ```
 nmcli connection show
```

Then run the following command, replacing the xxx's with your UUID. Reboot and you should be able to connect to Vino.

```

dconf write /org/gnome/settings-daemon/plugins/sharing/vino-server/enabled-connections "['xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx']"

```

---

### Post by weiyin on 2018-07-10
If not using network manager, you can symlink /usr/share/applications/vino-server.desktop into the $HOME/.config/autostart directory. See these links for reference:

[https://mail.gnome.org/archives/desktop-devel-list/2015-November/msg00047.html](https://mail.gnome.org/archives/desktop-devel-list/2015-November/msg00047.html)
[https://mail.gnome.org/archives/desktop-devel-list/2015-November/msg00048.html](https://mail.gnome.org/archives/desktop-devel-list/2015-November/msg00048.html)

---

