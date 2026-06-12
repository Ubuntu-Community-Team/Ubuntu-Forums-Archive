---
title: "Hostname change broke kubuntu"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by kooldino on 2007-11-20
My coworker used the System Settings applet to change his hostname.

He rebooted and logged in.  While KDE was logging him in, it would hang right before the "loading desktop" message.

Apparently many services rely on your hostname, so if you change it, it seems to break things.

I was able to boot up in a command prompt and do a "startx" to get to the desktop.  From there, we set the hostname back to what it used to be.  Upon reboot, all was normal.

Discuss.

---

### Post by cmnorton on 2007-11-20
I am not sure what you are asking or what you want from a discussion.

I have found if you change hostname, you have to change anything that depends on it, including the 127.0.0.1 and 127.0.1.1 entries in /etc/hosts.

As an example, we use Informix SE. That means our daemon's reference to the old host name changes, in addition to Informix's config files. Finally, our users' .bashrc files that reference the old host name have to change to the new. 

If this is a massive change -- many modules involved -- and you're up for it, you can often write a shell script that finds these dependent files, moves them to a new name with an extension like .input, runs them through sed to change the hostname and then outputs each file to its original name. 

If you are asking is their a global way to do this, I do not know of any. It's a massive thing to change hostname. Given the example of our town's internal Accumail server, I left the server's name alone and created an alias for it, because it has been migrating to various Windows IIS systems. It certainly beats changing the host name.

---

### Post by kooldino on 2007-11-21
Well, I'm honestly just let down that the system doesn't make all of the changes for you.  I realize that I may be asking a lot here, but if nothing else, a simple script that basically grep'd your old hostname and replaced each instance of it with your new hostname would be a good start.

---

