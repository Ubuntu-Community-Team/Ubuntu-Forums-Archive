---
title: "I'm not even sure how you install... I'm a total newbie!"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by ManicPanic on 2008-10-16
Hey hey. I am completely new to the whole Linux OS deal, and I'm having trouble coming to grips with a few things here.

First off, when I installed I set up a user account and all that, and it seems as though I don't have the 'permissions' I would expect.

This is primarily an issue because I'm trying to set up a driver for an Atheros WIFI card in my laptop. [I installed on a laptop by the way =P ]... and I have no idea what I need to do with these files.

Well, anyways, I found this [http://ubuntuforums.org/showthread.php?t=123653]("http://ubuntuforums.org/showthread.php?t=123653")
and am working off the first reply, but I run into trouble where it says to install the header. I have no connection on my laptop [with no wifi] so I download the .deb onto a thumbdrive from my main computer, bring it over, and now I'm trying to put it into the /var/cache/apt/archives but it tells me I don't have permissions?

Theres apparently this other 'owner' account I cant access from my user created account or something, and can't set my permissions to do what it can, log into it, or basically interact with it in any way, so how do I get the .deb into the /var/cache/apt/archives folder?

And am I even on the right track? I'm so confused :confused:

The driver I am trying to set up is the one found through the first link here: [http://www.atheros.com/news/linux.html]("http://www.atheros.com/news/linux.html")

so I'm not entirely sure if this is where I need to be headed, with the header .deb and all that is.

Anyone know what I'm supposed to be doing? The help is greatly appreciated!

---

### Post by Agent ME on 2008-10-16
Is your account an administrator account?

On linux usually, the administrator account is just like a normal user account, but you need to use the "sudo" command to gain complete access. If you're using a terminal, put "sudo" before the commands to run it as root (admin).

... But if the file is just a .deb file, you should be able to just double-click it and it will launch a package manager that will handle this for you, getting it to the right folder, getting admin access, and installing it.

---

