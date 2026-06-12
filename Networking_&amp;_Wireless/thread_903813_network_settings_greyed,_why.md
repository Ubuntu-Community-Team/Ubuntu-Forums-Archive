---
title: "network settings greyed, why?"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by Bahb on 2008-08-28
My network settings window is greyed out...

[img]http://img264.imageshack.us/img264/7291/networksettingsbq1.jpg[/img]

How do I get it to where I can play with it? It has never prompted me for a password. Using Network Manager, but even with it uninstalled, it would not let me in.

Linksys WMP54G v1 using RAlink 2500 driver
to a Linksys WRT54GS router.

---

### Post by kukibird1 on 2008-08-28
If the unlock button is not greyed out click on it and it should prompt you for a password .

---

### Post by Bahb on 2008-08-28
its greyed out mate.

---

### Post by dhysk on 2008-08-28
looks as if you opend it up under a non admin account.  Try typing in the command

sudo network-admin

into the command prompt.

---

### Post by Bahb on 2008-08-28
** (network-admin:27493): CRITICAL **: Unable to lookup session information for process '27493' 

still greyed

---

### Post by f8l_0e on 2008-08-28
Found the following [here]("https://bugs.launchpad.net/ubuntu/+source/policykit-gnome/+bug/231246"): 


 LuisMondesi wrote on 2008-07-09: (permalink)

This bug hit me with a fresh installation of Ubuntu Hardy and 2 things were noticeable:

1. USB volumes did not automount (that includes iPods and stuff)
2. all the *-admin utilities would not allow me to authenticate. The button was just gray-out.

To fix this I did:

1. start in single-user-mode
2. dpkg --force-all -P policykit-gnome
3. mv /var/lib/PolicyKit/user-haldaemon.auths /root
4. rm -fr /var/lib/PolicyKit/
5. apt-get --reinstall install policykit-gnome consolekit
6. mv /root/user-haldaemon.auths /var/lib/PolicyKit/
7. make sure /etc/hosts matches my hostname correctly for 127.0.x.x IP
8. make sure that the content of /etc/PolicyKit/PolicyKit.conf was:
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- XML -*- -->

<!DOCTYPE pkconfig PUBLIC "-//freedesktop//DTD PolicyKit Configuration 1.0//EN"
"http://hal.freedesktop.org/releases/PolicyKit/1.0/config.dtd">

<!-- See the manual page PolicyKit.conf(5) for file format -->

<config version="0.1">
    <match user="root">
        <return result="yes"/>
    </match>
    <define_admin_auth group="admin"/>
</config>

After this everything worked fine.

Hopefully this will help somebody out there. And please make sure this does not happen as this is very annoying and hard to troubleshoot.

---

### Post by pagaboy on 2008-09-20
Thanks for that, however, single user mode requires you to log on as root, and Ubuntu root accounts are disabled.  Does anyone know if the commands noted would work in a su-ed terminal?  I have the same problem, but don't fancy screwing up my system to try and sort it out.

---

### Post by pagaboy on 2008-09-20
OK, found it out.  So single user mode is basically recovery mode.  I had a couple of issues with the above commands.

Step 5: at this point, I found I had no network connection, so couldn't do the apt-get bit.  I booted back into normal mode for that line.

Step 6: the mv command didn't work as the /var/lib/PolicyKit directory doesn't exist at that point.  A simple mkdir /var/lib/PolicyKit did the trick.

Final result: settings are still greyed out.  Maybe because of not being in Single User Mode for step 5?  Any further help would be great.

---

### Post by CujoQuarrel on 2008-09-21
Anyone know anything more on this? Or an alternative way to do the same thing without the GUI?

---

### Post by pagaboy on 2008-09-26
Found the answer, which is in [bug 210897]("https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/210897").  You need to add to /etc/sudoers:
```

Defaults env_keep += "XDG_SESSION_COOKIE"
```

The fun tricky thing about this is that you can only open it in gedit as read-only, probably as you need sudo to open the thing.  So best off copying it, making the change on the copy, and then copying it over the old sudoers file.

---

### Post by jagsir on 2008-10-12
> **Bahb said:**
> My network settings window is greyed out...

How do I get it to where I can play with it? It has never prompted me for a password. Using Network Manager, but even with it uninstalled, it would not let me in.

Linksys WMP54G v1 using RAlink 2500 driver
to a Linksys WRT54GS router.

I faced the same problem, fixed by:
1. Re-Installing every thing which had policykit in its name using Synaptic.

Though this works only till I restart my system, but untill I find something concrete to fix it. this is good enough.

_Jagsir

---

### Post by deangl on 2009-02-21
> **pagaboy said:**
> Found the answer, which is in [bug 210897]("https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/210897").  You need to add to /etc/sudoers:
```

Defaults env_keep += "XDG_SESSION_COOKIE"
```

The fun tricky thing about this is that you can only open it in gedit as read-only, probably as you need sudo to open the thing.  So best off copying it, making the change on the copy, and then copying it over the old sudoers file.

Thank you.  This env update in sudoers file worked for me.

Dale  :)

---

