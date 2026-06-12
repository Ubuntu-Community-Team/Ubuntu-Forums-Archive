---
title: "Ubuntu 10.10 - Services configuration"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by jeff.biggeek02 on 2011-02-02
I do not have System>Administration>Services on my Gnome desktop on a fresh Ubuntu 10.10 desktop install (i386).  I can't seem to figure out what package contains that, and how I get it to show up on the menu.  Does anyone know?

---

### Post by llamabr on 2011-02-02
I don't either.  Ubuntu is always moving stuff around.  What are you trying to do?

---

### Post by kukibird1 on 2011-02-02
> **jeff.biggeek02 said:**
> I do not have System>Administration>Services on my Gnome desktop on a fresh Ubuntu 10.10 desktop install (i386).  I can't seem to figure out what package contains that, and how I get it to show up on the menu.  Does anyone know?

There is no more System>Administration>Services. You can install bum to turn off the few services that have not been converted to the upstart way of handling the start/stop of various services.  A forum search for disabling upstart services provides various solutions.


[http://askubuntu.com/questions/19320/whats-the-recommend-way-to-enable-disable-services]("http://askubuntu.com/questions/19320/whats-the-recommend-way-to-enable-disable-services")

---

### Post by jeff.biggeek02 on 2011-02-03
Ok.  I'm mostly interested in turning off the Cups service.

---

### Post by jeff.biggeek02 on 2011-02-03
Wow...major kudos to the upstart developers for such a flexible yet simple architecture.

Here's how I turned off cups, for anyone interested:

Cups is controlled by upstart...at least in Ubuntu 10.10 (not sure about earlier versions).
Upstart apparently has one config file per service that it knows how to start.  They apparently always reside at /etc/init as a convention/standard.

So, I went to /etc/init/cups.conf, and commented out these lines (by placing a '#' in front of them) in the file:

#start on (filesystem
#         and (started dbus or runlevel [2345])
#         and stopped udevtrigger)
#stop on runlevel [016]

These tell upstart when to automatically start and stop the service.  The "how to" start the service is the exec command, which I left in the file so that I could manually start cups if desired.
exec /usr/sbin/cupsd

I also left everything else (there were some pre and post scripts that did setup/tear-down of some sort for cups, and an obscure "expect fork" statement that I don't completely understand...but anyhow, I digress).

Saved as root, rebooted, and ran this at the terminal:

ps -A | grep cups

Cups is no longer running!  Cool!

I type this to start and stop it manually in the terminal:
sudo start cups
sudo stop cups

All works as expected.  Thanks guys! :)

---

### Post by bhy on 2011-03-01
Is there any GUI for upstart? Suppose I need to disable 10 services, do I really need to edit 4 lines in each of the 10 config files? Not that I can't do it, but it's hard to imagine a newbie disabling services this way.

---

### Post by jeff.biggeek02 on 2011-04-03
A valid question, bhy.  I was unable to find one.  Upstart appears to be a fairly new project, so it may be that the needs behind configuring it are still being discovered.  Just my blind, newbie guess though. :)

---

