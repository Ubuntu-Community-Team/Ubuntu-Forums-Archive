---
title: "Open File On Startup"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by ventolinmono on 2010-02-25
Hello

I want to open a file on system start up.
I tried it with System > Startup Applications, and it only opens applications, not files.
The file i'm trying to open is a .swf, and i can only open the Flash Player stand alone application.
I'm on Ubuntu Remix; Release 9.10 (karmic), on an Acer Veriton nettop.

Thankyou.

---

### Post by skatinjj on 2010-02-25
> **ventolinmono said:**
> Hello

I want to open a file on system start up.
I tried it with System > Startup Applications, and it only opens applications, not files.
The file i'm trying to open is a .swf, and i can only open the Flash Player stand alone application.
I'm on Ubuntu Remix; Release 9.10 (karmic), on an Acer Veriton nettop.

Thankyou.

You can add this into the command box when adding a new startup application:

```
"name of application"_"name of file"
```

Replace "name of application" with the name of the application that opens the .swf file.

The "_" means space.

Replace "name of file" with the path to the .swf file.

Also, take out the quotes.

That should work, you can test it in a terminal before you add it to start up.

---

### Post by ventolinmono on 2010-02-25
Thanks skatinjj for the quick reply.

I tried it with the terminal and it works fine.
When i restart nothing happens.
I think there is something wrong with my Startup Applications because I'm also having problems with the Network Manager as it is supposed to launch on startup.

Any ideas?

---

### Post by skatinjj on 2010-02-25
Have you verified that the check box next to the item is checked?

---

### Post by ventolinmono on 2010-02-25
> **skatinjj said:**
> Have you verified that the check box next to the item is checked?

Yes, it is checked.

---

### Post by skatinjj on 2010-02-25
Some things to check and do in no particular order:
1. You've already checked .xsession-errors. I would also check /var/log/
syslog, daemon, user, gdm/:0-slave.log (this one you have to sudo to root
to read). Maybe there's some clues lurking there in the logs.

2. check if there are any .X or .x files in the user's home directory.
Files like ~/.Xession or ~/.xinit provide a user-controlled X session
startup/configuration that overrides the system defaults. Maybe there's
something in one or more of them that gnome-session doesn't like, or
causes it to be bypassed altogether.

3. Start gnome-session in debug mode. One way to do this is to edit one
of the desktop files in /usr/share/xsessions and modify its Name= line to
"Gnome Debug Session" and the exec lines to "gnome-session --debug". Save
the file as gnome-debug.desktop. Then, when you are at the gdm login
screen, choose the Gnome Debug Session from your list of sessions and
proceed to login.

Note that starting gnome-session in debug mode may generate copious
amounts of data in ~/.xsession-errors so you don't want to stay logged
into that session any longer than it's necessary to gather the data that
you need to pinpoint the problem. Once you logout, do NOT log back in
right away because if you do ~/.xsession-errors will be overwritten.
Switch to a vt and make a copy of .xsession-errors before logging in
through gdm. Also, don't forget to choose GNOME from the session selector
so you get the regular Gnome session on login and not the debug one.

4. clear out user startup files from ~/.config/autostart then selectively
put them back in.

5. clear out user saved sessions from ~/.config/gnome-session/saved-
session/ and, if any exists, ~/.gnome2/session*.

Post taken from [http://forum.nginx.org/read.php?26,54704]("http://forum.nginx.org/read.php?26,54704")

---

### Post by ventolinmono on 2010-02-25
> **skatinjj said:**
> Some things to check and do in no particular order:
1. You've already checked .xsession-errors.re in the logs.
2. check if there are any .X or .x files in the user's home directory.
3. Start gnome-session in debug mode.
4. clear out user startup files from ~/.config/autostart then selectively
put them back in.
5. clear out user saved sessions from ~/.config/gnome-session/saved-
session/ and, if any exists, ~/.gnome2/session*.
Post taken from [http://forum.nginx.org/read.php?26,54704](http://forum.nginx.org/read.php?26,54704)
OK so i tried some of that but it looks like the last alternative for a newbie like me and went looking somewhere else when i decided to log out and...

The problem was that i was logging in with Failsafe GNOME.
Logged in with normal GNOME session and now the .SWF opens with the Flash Player Standalone on startup. With the use of the command: "name of application"_"name of file".

Though I'm still having trouble with the Network Manager.

---

