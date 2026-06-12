---
title: "nm-applet disappeared from panel?"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by bostonvinnie on 2008-10-14
Hi, I'm running Hardy (8.04) (amd64) with current updates. 

For some reason, the very handy nm-applet doesn't show up on the Gnome panel any more. I find this to be an excellent wireless network tool, as it lets me quickly identify available networks and connect to the one I want. The applet shows current signal strength, and clicking on the icons shows all available networks and lets one switch if need be.

I can get it to show up in the panel easily enough by typing 'nm-applet' in a terminal, but I cannot for the life of me find where to tell it to run automatically -- there is no listing for it in the "add to panel" menu; the closest thing there is the "Network Monitor" applet, but that doesn't let me change networks easily as the nm-applet does.

Any suggestions on what I need to do to get nm-applet running automatically?

Thanks, BV

---

### Post by chewearn on 2008-10-16
Add nm-applet to Startup Programs.  You can find this in:
Panel Menu > System > Preferences > Sessions

Find the entry for Network Manager.  If it is missing, add one.  The entries are:
Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=88505&stc=1&d=1224134463[/IMG]

---

### Post by bostonvinnie on 2008-10-24
Thanks! Unfortunately, this was already there, but the nm-applet still won't start up automatically. Must be something else happening on my system.

-BV

---

### Post by borissssup on 2008-12-19
I had a similar problem (on Debian, just solved it).

The problem can be the privileges you are using to run nm-applet (I noticed that "sudo nm-applet" made it work properly): if you look at the file /etc/dbus-1/system.d/nm-applet.conf you should be able to see who can run "nm-applet.conf".

In mine, it appeared that only "root" and people belonging to the group "netdev" could run it: therefore "sudo adduser myusername netdev" solved my problem.

Hope this can help you!

---

### Post by physeetcosmo on 2009-12-17
> **borissssup said:**
> I had a similar problem (on Debian, just solved it).

Thanks, that's why nm-applet just disappears when I login as root (Debian). I'll add root and test it out!!!!

---

### Post by LilYoda on 2009-12-19
In my case, it seems that only the first user with an active login on the system has tne nm applet loaded.

If my wife logs her account first, she has it loaded.  If I use switch user and log mine while she is still logged in -> the applet doesn't load for me

If I log when noone else is logged in -> the applet loads

Go figure :confused:

---

