---
title: "another ssh x11 forwarding thing"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by riseringseeker on 2008-11-17
I am having a little problem that I cannot for the life of me figure out.  I am using ssh to go from my laptop to my desktop and have X11forwarding enabled.  So far so good.

I type "xclock" and the clock appears almost instantly - still good.  When I type "nautilus" however I get a slew of errors, beginning with this:

```

(nautilus:11138): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-K3fOvcequi: Connection refused)

```

This repeats a few times, only the socket it can't connect to gets a name change with each iteration.  Then I get a pair of popup windows shown in the attached file.  After all this (and about 1 minute total), nautilus opens any way.

OK, now for the odd part.  I have two user names on both machines, and using my secondary user name (same privileges) and opening nautilus via ssh works without a hitch!  

Just as odd, if I use my primary account, and try to open nautilus as root, I do not get errors if I type 
```
sudo nautilus
```, but any other way I could get nautilus open as root gives errors, or doesn't work at all.

I know it's not a system wide setting on either machine, as I can ssh with another account and things are fine.  What I don't know is what settings are different from one account to another.

Anyone got any ideas, would sure appreciate hearing from you.  I have searched these and other forums without coming up with an answer.

---

### Post by riseringseeker on 2008-11-19
bump

---

### Post by riseringseeker on 2008-11-20
I guess this should make me feel better, no one else can come up with an answer either.

---

### Post by craiger316 on 2009-03-04
I have this same problem, after an upgrade from 8.04->8.10 when I ssh -X to my box and type gvim it takes a long time to start and when it does I get an error box which states:

> 
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-AW6XNjXBV3: Connection refused)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-SUqRs0Y31l: Connection refused)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-2oRHyZxCwY: Connection refused)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-Jn5wHNhF7a: Connection refused)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-ftXbRjxeTq: Connection refused)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-x6L3rJxPad: Connection refused)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-bVGF4NsFcD: Connection refused)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-r9e8foxmvw: Connection refused)


The only peculiar thing I see in my terminal window after typing gvim is a new message:
> Xlib:  extension "RANDR" missing on display "localhost:10.0".

Any help would be greatly appreciated.

---

### Post by sterence on 2009-03-10
If anyone's still reading this, I'm getting the same problem trying to run a few select programs over ssh (gvim).

I'm using a Fedora install for the client, if that helps any!

---

### Post by *uu on 2009-03-11
@sterence: I can reproduce your issue on my machine as well. After closing the error boxes, gVim appears to be working fine, though.

I guess this has to do with certain parts of the window manager (Gnome in my case) that need to be loaded on the remote machine but cannot be tunneled for some reason. I too can tunnel standalone applications like Skype or Pidgin (manually compiled, not the version from the repositories) and even web browsers (just tried with Opera, Firefox) without any troubles. Though, they run very  slow and laggy, the browsers take ages for their windows to appear on the local machine and they then respond unusably slow. Considering that speed I really wonder how someone would forward a whole Xsession...

On the other hand I cannot forward gnome-embedded applications like epiphany, eog or gedit. That would fail with some "Failed to connect to socket /tmp/dbus-xRTh8uBYIH: Connection refused"-like error message in the terminal. So I guess some part of gnome would be needed - maybe stuff from the theme - but is not accessible. So far I haven't found out what would be needed or could be done about that... 

KDE-embedded applications - I just tried with kate and kpat - seem to be forwarded fine, though. They take ages to appear and are unusably slow, as well, and they may output some error messages like "No DBUS session-bus found" or "kdeinit4: Communication error with launcher. Exiting!" and similar, but as opposed to the Gnome apps at least they appear and function - albeit after a while and slowly.

Regards,
*uu

---

### Post by kbuel on 2009-04-28
Hey,

I am receiving this error in Jaunty after a clean install. I have created a bug report describing my experience.  If you guys have more information that might help, could up comment on this bug?

[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/367169](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/367169)

---

### Post by TechBeastie on 2009-05-30
Hi everybody,
  I'm having exactly the same kind of issue as the one described above: whenever I try running any core gnome app (and in my case, this seems to include firefox) through tunneling as a regular user, I'll get a bunch of those lovely "Failed to get connection to session: Failed to connect to socket..." errors.  
What's interesting, however, is that running tunneled apps as root (ie, root on the remote machine) seems to completely "fix" the problem.  I discovered this accidentally, when I was trying to modify ssh and cups config files on the remote machine.  After getting a bunch of these strange error messages (which forced me to resort to vim) I eventually ended up typing "sudo gedit ..." at some point through force of habit.  Lo and behold, up popped gedit with only the briefest of lags, and everything seemed to work as well as I might expect if it were running locally.  The same went for Firefox, gnome-system-monitor, and virtually every other app I tested.  
What all this indicates, obviously, is that this is some sort of strange permissions issue.  The only questions that remain are (a) why I've never seen anything even remotely similar to this behavior on any other distro, and (b) what I can do to fix it - because I sure as heck don't want to go around running Firefox as root.  

Hope this sheds a bit of light on this weird problem; I'll attach this note to the bug report as well.

[Edit]:  Oops - that was a collosal waste of my time; it looks like the good people who submitted the bug report have already figured out the problem, and it is indeed a permissions problem.  Go to [https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/367169](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/367169)
for the solution - and then please add a note telling the Ubuntu development people that this is MOST CERTAINLY a bug, and needs to be fixed (again, see the linked page for an explanation).  
Thanks everybody!

---

### Post by *uu on 2009-05-31
Hi everyone,

as sort of a solution I by now resorted to using NX Client/Server from [NoMachine]("http://www.nomachine.com/download.php"). This application uses the SSH port if needed and allows you to forward your whole desktop (VNC-like, haven't tried that, though) or only a terminal window, from which you can run any application on the remote machine as if you where sitting in front of it -- well, depending on both machine's internet connection speeds, of course.

For me, this works really fast and so far without troubles. Applications open and run as fast as if they were run locally.

The downside: The client and server application are proprietary and closed source. Though, there's a free alternative called [FreeNX]("http://freenx.berlios.de/"), which, according to [Wikipedia]("http://en.wikipedia.org/wiki/NX_technology"), appears to provide the same functions.

Maybe this helps somebody. :-)

Regards,
*uu

---

### Post by oddiofile on 2010-09-02
I am using a Meego Linux distro, and i have the same problem, in that normal X11 apps work fine over ssh, but when I try to run gnome apps, it fails. 

But for me, what is interesting is that gnome-terminal and other apps did run fine remotely over ssh until I changed my hostname! And yes, I rebooted and cleared the .dbus dir. 

So I think changing the hostname broke my dbus configuration somehow.

---

### Post by vitamin on 2011-01-28
Hi,
I had exactly the same problem when forwarding X applications from my ubuntu server to my mac laptop. Thanks so much for the link to bugreport above!
Changing the permissions in .dbus/session-bus/* to my user solved everything.

---

