---
title: "Can Firestarter Firewall be used by non-administrative users?"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2010-12-13
Is it possible to invoke the Firestarter firewall program so that it will run with a non-administrative privileges user signed on?

I would like the firewall to start when my wife logs on to her desktop.

Ed

---

### Post by oldos2er on 2010-12-13
Firestarter's not a firewall, it's a configuration tool for iptables. It also hasn't been updated in years. The recommended tools are ufw and gufw (CLI and GUI versions of the same tool). See [https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw) and [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by bodhi.zazen on 2010-12-13
> **ozark_hillbilly said:**
> Is it possible to invoke the Firestarter firewall program so that it will run with a non-administrative privileges user signed on?

I would like the firewall to start when my wife logs on to her desktop.

Ed

Firestarter does not work that way.

You run firestarter, configure yoru firewall, and then close firestarter.

All you really need to do is use ufw, it is a single one time command:

```
sudo ufww enable
```

1. It is highly likely you do not need a firewall at all as by default there are no listening services.

2. Unless you need to configure your firewall, you almost certainly do not need either firestarter or gufw (ufw from the command line is sufficient for the vast majority of desktop users, if not overkill).

---

### Post by rburkartjo on 2010-12-16
oz after you enable ufw -sudo ufw enable -will ask for your password. it should be enabled on every start. if you want to check just type in sudo ufw status and after you enter you password you should see Status:active

---

### Post by QLee on 2010-12-16
[QUOTE=ozark_hillbilly]Is it possible to invoke the Firestarter firewall program so that it will run with a non-administrative privileges user signed on?

I would like the firewall to start when my wife logs on to her desktop.[/QUOTE]

When Firestarter is installed, it configures the system to start with the rules you have used the Firestarter GUI to write into iptables with it, simply stated, it automatically starts the "firewall" at boot time, your wife is already protected. No you can't run it as a user because a user doesn't have permissions to configure system files. And you really shouldn't leave a Program running as root open all the time anyway because of the security risk although a knowledgable system admin might use it for specific tasks for a while. Probably no good reason for your wife to see all the "hits" the GUI would display anyway, it would likely just confuse her and make her worry

Many Ubuntu users don't like Firestarter, although it hasn't been upgraded in years (not sure what upgrades are necessary for a GUI to write iptables rules), it is still maintained by the Debian maintainer and will be in the newest Debian release. 

If you do choose to switch, purge it completely and install the recommended ufw and gufw (GUI).

---

### Post by bodhi.zazen on 2010-12-16
> **QLee said:**
> Many Ubuntu users don't like Firestarter, although it hasn't been upgraded in years (not sure what upgrades are necessary for a GUI to write iptables rules), it is still maintained by the Debian maintainer and will be in the newest Debian release. 

"maintained" meaning re-packaged, there are no bug fixes.

Because firestarter is no longer maintained, as more and more people run into bugs, it is becoming less popular.

[https://bugzilla.gnome.org/buglist.cgi?quicksearch=firestarter](https://bugzilla.gnome.org/buglist.cgi?quicksearch=firestarter)

---

### Post by Spyderkid on 2010-12-16
install 'Firewall' from the sofware centre it can only be used by administrators or people with your password.

---

