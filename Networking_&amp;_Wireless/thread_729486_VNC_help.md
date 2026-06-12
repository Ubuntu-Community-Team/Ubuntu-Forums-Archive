---
title: "VNC help"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by Sinister Fister on 2008-03-19
I have look through  a lot of threads but could not find the answer im looking for. Im trying to see my Ubuntu desktop from my windows box. I want to control my Ubuntu box so i can get rid of the mouse, keyboard, and monitor.

---

### Post by GhodMode on 2008-03-20
I also wanted to control a Ubuntu (Kubuntu, actually) from another computer in my house.  I found that the quickest solution for me was to set [KRfb]("http://docs.kde.org/stable/en/kdenetwork/krfb/index.html") to "Allow uninvited connections" and "Allow uninvited connections to control the desktop".  I close KRfb after that and didn't even think about it... I can connect to that computer any time I want to.  A quick check of the process listings shows that KRfb is indeed running and must be providing VNC service... it just works :)

Having said that, though, there are a number of problems with this solution:[LIST=1]
[*]It only works if you have Krfb installed.
[*]It might only work if you're using KDE.
[*]It's potentially insecure.[/LIST]

VNC probably isn't the best way to use the computer remotely anyway.  The best way is probably to run an X Window System on your Windows box and start a session on your Ubuntu box via ssh while exporting the display.

Try installing [Xming]("http://www.straightrunning.com/XmingNotes/") on your Windows box and running your desktop manager (via plink, which comes with Xming).  I'm using KDE, so my window manager starts with the command [FONT=System]startkde[/FONT], but it will be different if you're using Gnome.

I prefer KDE over Gnome and I've been using it for years.  So, I'm a little rusty on Gnome equivalents, but there must be Gnome equivalents for all of this.

Maybe some other kind soul can come along and help to fill in all of the Gnomish details?

I've left out quite a bit of detail here, but it'll put you on the right path.  I'll consider writing up a full tutorial with screenshots and all, but that won't be today :)

--
-- Ghodmode

---

