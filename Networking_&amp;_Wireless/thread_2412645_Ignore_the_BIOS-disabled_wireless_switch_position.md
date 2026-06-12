---
title: "Ignore the BIOS-disabled wireless switch position?"
date: 2019-02-15
forum: Networking &amp; Wireless
---

### Post by staticx420 on 2019-02-15
OS: Ubuntu 18.04 x86_64
Desktop: Gnome

Is there a way to make NetworkManager ignore the wireless switch position?

On a few laptops (Dell E5500, E6500 and E6520) I have to manage I disabled the wireless switch in the BIOS: [https://imgur.com/a/lOig2CI]("https://imgur.com/a/lOig2CI")

In Windows, which I'm trying to get rid of, wireless will work regardless of the position of the switch when it's disabled in the BIOS. In Ubuntu, NetworkManager still honors it and turns on airplane mode when the switch is off.

rfkill says it's hardblocked when the switch is off.

Is there a way to get NetworkManager allow wireless regardless of the switch position?

This is a problem since it's in a school setting and students use the laptops. Needs to always be online. I use PolicyKit settings to keep them from disconnecting it directly in NetworkManager.

Removing the module "dell_laptop" does the trick, but I'm wondering if there is a better way.

Thanks.

---

### Post by #&amp;thj^% on 2019-02-15
If your wi-fi access point is saved, it will auto-connect. Turn wireless on or off with a simpler command:
```

nmcli nm wifi on
nmcli nm wifi off
```

on newer version:
```

nmcli radio wifi on
nmcli radio wifi off
```
Also see man nmcli: [http://manpages.ubuntu.com/manpages/cosmic/en/man1/nmcli.1.html](http://manpages.ubuntu.com/manpages/cosmic/en/man1/nmcli.1.html)
```
rfkill 
ID TYPE      DEVICE                   SOFT      HARD
 0 bluetooth tpacpi_bluetooth_sw unblocked unblocked
 **1 wlan      phy0                  blocked unblocked**
 2 bluetooth hci0                unblocked unblocked

```
With policykit You can also set all values with the * wildcard...
```

[Prevent foo from modifying all network states and settings except with admin password]
Identity=unix-user:foo
Action=org.freedesktop.NetworkManager.*
ResultAny=no
ResultInactive=no
ResultActive=auth_admin_keep
```
This will require a password to make ANY change to network settings or state.

You can do this in a single command that could be included in a script...
```

sudo su -c 'printf "[Prevent foo from modifying all network states and settings]\nIdentity=unix-user:foo\nAction=org.freedesktop.NetworkManager.*\nResultAny=no\nResultInactive=no\nResultActive=auth_admin" >  /var/lib/polkit-1/localauthority/50-local.d/10-network-manager.pkla'
```

---

