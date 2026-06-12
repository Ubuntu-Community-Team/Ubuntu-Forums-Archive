---
title: "OS can't find installed software after upgrade"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Varsch on 2009-04-24
Hello!

I upgraded to Jaunty while it was still in Beta and got some bugs. Hoped that they'd be fixed with software update but sadly most have remained.

First problem is that the OS can't find the program Vuze anymore. It is installed and I reinstalled it using Synaptic, but the shortcut in the Applications menu doesn't do anything.

When trying to load it from a terminal, I get
> exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found

And the auth.log says
>  CRON[27231]: pam_unix(cron:session): session opened for user root by (uid=0)
 dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.42" (uid=1000 pid=3676 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.178" (uid=0 pid=27231 comm="/USR/SBIN/CRON "))
 CRON[27231]: pam_unix(cron:session): session closed for user root

Anyone got a hunch on how I could get Jaunty to find Vuze again?

Thanks!

---

### Post by spikoley on 2009-04-24
Sounds like the short cut is broken.  Try opening it from the command line first.

```
vuse
```

It should run and if not there will be error displayed in the terminal.  If it doesn't run then run the next command.

```
which vuse
```

That command will show you the path to the vuse program.  Copy the full path and run it in the terminal.

To fix your short cut right click on Applications> Edit Menus> Applications> Internet> Vuse and click properties.  Put the full path from the command above into the command box, save and test.

This could be some bigger issue since you upgraded.  I prefer doing a clean install instead of an upgrade.

---

### Post by Varsch on 2009-04-24
Thanks for the tip! 

However, the command "which vuze" does give me an adress (/usr/bin/vuze) but when I type that path in the terminal it gives me the same error as before, i.e:
> exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found

The idea of a clean install is tempting, but wouldn't I lose all my data and applications?

---

### Post by Peter09 on 2009-04-24
It looks like java is not installed, have you checked your java environment?

---

### Post by clive littlewood on 2009-04-24
Hi

Search for java 6 in synaptic and install then you should be good to go !!

Clive

---

### Post by Varsch on 2009-04-24
> **clive littlewood said:**
> Hi

Search for java 6 in synaptic and install then you should be good to go !!

Clive

Thanks! There are several files available in Synpatic, some of which are already installed. Which one(s) should I get?

---

### Post by Varsch on 2009-04-24
OK, Nevermind! I found it!

Installing Java indeed fixed my problem. Why it had been uninstalled when I upgraded remains a mistery, though...

Thank a lot!

---

### Post by clive littlewood on 2009-04-24
Your very welcome  !!!! :)

Clive

---

### Post by happyisland on 2009-04-24
Installing the openjdk-6-jdk package solved my problem.

---

### Post by asgard_command on 2009-04-30
Same problem here even after reinstalling java.

---

