---
title: "My desktop to LAMP experience"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by Big_Rog on 2008-03-20
Well, I've spent the last week or so trying out different web development systems and have had a few interesting experiences.  Most of this stuff is covered on one site or another, but the problems seemed to be fairly common, and few if any of it was posted with resolution on the site where the problem was reported.  So anyway, I wanted to offer up my experiences to the community at large.  Hopefully this will help someone else too.  =)

[COLOR="Red"][ ! ][/COLOR] BE CAREFUL WITH[FONT="Fixedsys"] tasksel[/FONT]!  I looked at the distro topics pages and followed most of the advice for installing a LAMP setup from the feisty instructions.  I'm currently running gutsy, but the instructions still largely apply.  The problem I ran into was the vague suggestion that you can use [FONT="Fixedsys"]tasksel[/FONT] to install a LAMP setup hands-free.  I was having issues with getting apache to run php scripts, so I un-installed the packages from apt-get, and ran tasksel to reinstall.  I saw that there was an option for a video editing station listed as well, so I selected that too.  Hit OK and watched it crank away and--OH NO!--saw apt-get REMOVING some rather important packages, like gdm, gnome-desktop and the like.  I halted the process to see just why it was doing that, and attempted to reinstall the packages it had already tossed.  Turns out that using tasksel doesn't add LAMP function, it completely removes anything not directly related to a bare-bones LAMP ubuntu install, including your desktop and other lovely things.  If you have an existing desktop and you want LAMP functionality for web-dev or whatnot, just install the packages by hand and save yourself the trouble I had.

[COLOR="Orange"][ ? ][/COLOR]The default location that Apache2 will look for your html is in /var/www.  If you want to add virtualhosts, there's plenty of good documentation around, but it took me a few days to sort out why it wasn't running php in my virtualhost location (in /home/user/public_html/ ) and it boiled down to permissions.  This lovely chap at [slicehost]("http://articles.slicehost.com/2007/9/18/apache-virtual-hosts-permissions") had exactly the information I needed to get it all sorted out.

more as things progress...

---

