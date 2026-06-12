---
title: "cannot connect to wifi after sleep (14.04 trusty)"
date: 2014-04-27
forum: Networking &amp; Wireless
---

### Post by joee2 on 2014-04-27
Since upgrading my laptop to ubuntu 14.04 trusty, wifi no longer works after waking my ThinkPad X220 from sleep.  To get it working again, I have to do this after every resume:

```

sudo service dbus restart
sudo service network-manager restart
```

Any ideas how I might fix this?

---

### Post by varunendra on 2014-04-28
Welcome to the forums joee2!

Is it a fresh install of 14.04 or an upgrade over a previous version?

Please also post the outputs of -
```
cat /var/log/pm-suspend.log
lspci -nnk | grep -iA2 net
nm-tool
cat /etc/NetworkManager/NetworkManager.conf
cat /etc/network/interfaces
```

---

### Post by joee2 on 2014-06-06
This is an upgrade from 13.10 (which did not exhibit the problem).  Requested outputs attached.

[ATTACH]253785[/ATTACH]
[ATTACH]253782[/ATTACH]
[ATTACH]253784[/ATTACH]
[ATTACH]253783[/ATTACH]
[ATTACH]253781[/ATTACH]

---

### Post by joee2 on 2014-06-06
One difference I've noted.  When wifi is not working (after resume) the following two messages fail to appear in syslog:

    > May 26 06:39:53 laptop dbus[6255]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
    May 26 06:39:53 laptop dbus[6255]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'

After I do the restart dbus / restart network-manager dance, dbus seems to activate wpa_supplicant as it should.

---

### Post by oxo2oxo on 2014-06-06
Interesting i have the same problem, short term solution for me is that i have two wireless routers if I log on to the other one then everything starts working again. Also using 14.04

---

### Post by varunendra on 2014-06-07
Can you connect again if you simply reload the driver manually? That is (for joee2) -
```
sudo modprobe -rv iwldvm iwlwifi
sudo modprobe -v iwlwifi
sudo modprobe -v iwldvm
```

If yes, try adding them to "/etc/pm/config.d/modules" file. It does not exist by default in Ubuntu, so to create it with relevant entry -
```
echo "SUSPEND_MODULES=\"$SUSPEND_MODULES iwldvm iwlwifi\"" | sudo tee /etc/pm/config.d/modules
```
This will create a file "modules" in "/etc/pm/config.d" directory, containing one line -
```
SUSPEND_MODULES="$SUSPEND_MODULES iwldvm iwlwifi"
```

Now make it executable (not sure if it is necessary, but won't hurt either) -
```
sudo chmod +x /etc/pm/config.d/modules
```

---

### Post by joee2 on 2014-06-07
Aha!

Thanks [COLOR=#000000]varunendra; you got me headed in the right direction.  I looked in [/COLOR]/etc/pm/config.d/config and it turns out that it already contained:

```
SUSPEND_MODULES="iwlwifi"
```

Removing that fixed the problem.

Thank you varunendra and [COLOR=#000000]oxo2oxo for your help![/COLOR]

---

