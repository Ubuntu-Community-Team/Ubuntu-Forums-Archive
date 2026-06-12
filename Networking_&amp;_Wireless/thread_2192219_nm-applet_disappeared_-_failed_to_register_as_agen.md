---
title: "nm-applet disappeared - failed to register as agent (32)?"
date: 2013-12-06
forum: Networking &amp; Wireless
---

### Post by HawkST on 2013-12-06
Hey,
I've run into an issue with my network manager - nm-applet disappeared from my notification area and attempting to run it via terminal gives the following errors:

```

sudo nm-applet
```

```
** Message: applet now removed from the notification area

** (nm-applet:12823): WARNING **: Failed to register as an agent: (32) No session found for uid 0
** Message: using fallback from indicator to GtkStatusIcon

```

```
nm-applet
```

```
** Message: applet now removed from the notification area

** (nm-applet:13122): WARNING **: Could not find ShellVersion property on org.gnome.Shell after 5 tries
```

As well as this removing the applet from the notification area, it also prevents me from connecting to any new passworded wireless networks with the GUI, as the password prompt no longer appears when I try to connect.

I've tried to google the solution, and there are very few references to the problem, the longest post on the subject I could find was [this one]("https://bbs.archlinux.org/viewtopic.php?id=143985"), where the posters seem to think it has something to do with dbus.

I'm at a bit of a loss with this one, if all else fails I could try something like wicd, but at the moment I'm in some sort of no mans land as I can still connect to the passworded networks that were stored before this became an issue (such as my home network), but can't connect to any new ones.

Any help would be appreciated!

---

### Post by steeldriver on 2013-12-06
The nm-applet runs as a user process (it's part of your desktop session) so running it with sudo is probably not going to work (the error "No session found for uid 0" is telling you that, I think - "uid 0" is root)

Let's start with what version and flavor of Ubuntu + what desktop session you are running

---

### Post by HawkST on 2013-12-07
Hey, thanks!
I'm running 13.04 at the moment (but the issue began randomly one day while using 12.10), I'm going to upgrade to 13.10 today to see if that gets me anywhere!
I'm using Unity (3d), changing the session has no effect - here's where it gets weird though.

nm-applet appears on the login screen, but disappears once I have logged in. If I try to run it in a terminal, the error message "Could not find Shell....(above)" appears, but the applet appears in the notification bar again (this did not happen in 12.10 - I'm new to 13.04) until the terminal is forced closed.

Trying to connect to a previously unknown passworded network while the applet is running gives the following error:

```
**Connection error:**
(1) Creating object for path '/org/freedesktop/NetworkManager/ActiveConnection/3' failed in libnm-glib.
```

It now shows the password prompt before the above appears, whereas the first time I noticed this and tried it it was displaying an error about wrong permissions (32) (apologies I don't remember the full message)

---

### Post by steeldriver on 2013-12-07
The "Could not find ShellVersion ... " message is only a warning - it doesn't necessarily mean there's anything fundamentally wrong. In my experience Gtk applications are often 'noisy' like that when run from a terminal - usually they aren't run that way so we don't notice.

Some desktop sessions deliberately don't display nm-applet - there's a global file /etc/xdg/autostart/nm-applet.desktop that controls this behavior (parameter 'NotShowIn'), but it can be overridden by a per-user file ~/.config/autostart/nm-applet so the first thing would be to check you don't have one of those

If you need to start nm-applet manually and don't want it to get killed when the terminal is closed, you can background and disown it e.g.

```
nm-applet & disown
```

in fact I usually do

```
nm-applet 2>/dev/null & disown
```

to suppress warning / error messages.

The problem you're having with connections may not even be related to nm-applet - it is only a front end that talks to the actual network-manager service via DBUS. The authentication process for creating connections is controlled by Polkit and doesn't always work the way you expect for non-privileged users. Or there may be a simple permissions error with the /etc/NetworkManager/system-connections/xxx files.

---

### Post by HawkST on 2013-12-07
Okay, I see what you mean about the warning, disown was a good call and it runs as expected now, appearing in the notification bar and staying there.

Also, fyi, I should have specified that the error message connecting to a passworded network (ActiveConnection) only occurs after I press cancel - and it appears to be working when I try to connect to a new network that I know the password to.

Even better, the network applet is displaying at login, your idea of ~/.config/autostart/nm-applet.desktop overriding settings was correct, when I looked at the file it contained the following:

```
[Desktop Entry]
Type=Application
Exec=nm-applet
Hidden=true
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_GB]=Network applet
Name=Network applet
Comment[en_GB]=
Comment=
```

Changing "Hidden" to false now has it showing when I log in!

So, while I'm still getting errors at a particular point, it's only when I try to connect to a network that I don't know the password for, which isn't really a situation I expect to find myself in frequently!

All things considered, I'm going to go ahead and mark this as solved, thank you steeldriver for your help!

---

