---
title: "Startup applications configuration file"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by c-lou on 2011-06-04
Hi,

I just upgraded from 10.10 to 11.04 on my Dell D630. It all went fine, until I did something kind of stupid . . .

I went into startup applications, and unchecked a few things that I thought I didn't need, in an attempt to speed up the startup. However, I obviously removed something that I DID need, and now I can't boot :(

I can still boot into a terminal in recovery mode, so I was wondering where the configuration file for startup applications is, so that I can edit it. Also, where could I find a copy of the original configuration file so that I can restore it?

Thanks very much for the help
c-lou

---

### Post by frankbooth on 2011-06-04
Have you tried:
```

sudo /etc/init.d/gdm start

```
To get your GUI back?

I think the configuration can be found in:
```

~/.gnome2/session

```
But it might be located elsewhere in 11.04, I'm not sure.

---

### Post by c-lou on 2011-06-04
Hi, thanks very much for the suggestions.

```

sudo /etc/init.d/gdm start

```

gives the following error message:
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.19" (uid=1000 pid=1832 comm="start_gdm") interface="com.ubuntu.Upstart0-6.Job" member="start" errorname="(Unset)" requested_reply=0 destination="com.ubuntu.Upstart (uid=0 pid=1 comm=/sbin/init"))

I don't have anything that looks like a configuration file in ~/.gnome2/session

c-lou

---

### Post by frankbooth on 2011-06-04
Alright, you might be able to find them in here:
```

/etc/xdg/autostart

```

[COLOR="Red"]If you only did changes to YOUR user, then you could always delete the configuration files, [COLOR="Black"]**as a last resort**[/COLOR].
**The following command will delete your desktop settings.**
[/COLOR]
```

rm -rf .gnome .gnome2 .gconf .gconfd .metacity 

```

---

### Post by rtimai on 2011-06-04
Don't know if it's too late, but you could have restarted and logged into Recovery Mode or one of the other possible desktops and reviewed your Startup Applications tool.

---

### Post by c-lou on 2011-06-05
Hi,

Thanks very much for the suggestions. They were indeed in /etc/xdf/autostart, but after checking that everything there seemed fine I realised that the problem must have been elsewhere . . . and it turned out to be that the NVIDIA driver is saving a faulty xorg.conf file when I update the screen resolution.

---

