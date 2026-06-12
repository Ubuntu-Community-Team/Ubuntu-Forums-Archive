---
title: "Need help:  Startup Applications"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by kate9954 on 2010-05-27
Hi, guys,

This isn't exactly an emergency - more of an annoyance.  Still, I find it hard to believe that I can't find a similar post on this, and I am fairly sure that a simple answer exists.

Ubuntu 10.04, Lucid Lynx, Gnome desktop, are all running flawlessly on my Acer.  I just have a minor configuration problem.

Several things start automatically when I log in, including Truecrypt and Vidalia, which I *want* to start automatically.  Unfortunately, Skype (which uses Tor), PSI (which uses Tor) and qBittorrent (which uses Tor *and* saves to an encrypted Truecrypt partition) all start automatically also.  Skype, PSI and qBittorrent are not shown in the startup programs dialogue box, so I cannot uncheck them there.  I do *not* have the box checked to remember my running programs at logout either.  

As a result of this, I have to shut Skype, PSI and qBittorrent down at every boot and restart them manually.  To add insult to irritation, having no media drive available at startup results in qBittorrent having to fully recheck any downloads and/or seeding files also.

I was a Windows techie for 20 years, but I'm definitely a newbie at Linux and Ubuntu.  And I'm going stark, raving bonkers trying to figure out where to disable those three programs at startup.

Can anyone point me in the right direction?  I'd be truly grateful.

Kate

---

### Post by Brandon Williams on 2010-05-28
If you previously had "remember my running programs" checked at logout at some point, you might have an old session cached with those programs running. With all three of the problematic programs stopped, log out with the "remember my running programs" box checked and then log back in. Did the problematic programs restart? If not, then log out again, this time with the "remember my running programs" box unchecked and then log back in. If the troublesome programs still restarted after logging out with  "remember running programs" checked, then you might have to each clear your cache (rm -rf $HOME/.cache/*) or look around in gconf-editor to see if those programs are listed somewhere as being associated with session startup.

---

### Post by kate9954 on 2010-05-28
Worked like an absolute charm, Brandon!!!  Bless you, bless you.  I am in your debt, sir.

Kate

---

