---
title: "Wireless broken, can't configure panels... Did I turn stupid?"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by karasuman on 2011-01-25
I have an Acer Aspire One that's been working great with Ubuntu since I got it, but I somehow never got around to updating it beyond Jaunty.  I finally went all the way up to Lucid, and... bam.  

I can't connect to the internet wirelessly at school.  I can get on my home wireless network with its happy useless WEP encryption, but this netbook lives at school.  Both the normal network manager and WICD can detect the networks and attempt to connect, but the normal network manager just pretends my username/password is wrong (which is why I went to WICD originally), and WICD authenticates fine but always returns an error saying that I can't get an IP address.  Help?

Also, I can't configure my top panel.  I can't add thinks to it or take things away.  Right clicking on any object has the useful (like, lock in place, remove, etc.) options greyed out, and right clicking on the panel will let me change the properties, but the other options (like add a panel, add something to the panel) are greyed out.  Help?

---

### Post by Bucky Ball on 2011-01-25
I found this:

> 1. Boot computer.
2. When GDM loads, select your user name.
3. Next to "Session" at the bottom of the screen, select Ubuntu Netbook Edition
4. Right click anywhere in the panel, and notice that there is no way to  unlock or move existion panel applets and icons, nor is there a way to  add any new icons.
 *BUT* if in step 3 above you select "GNOME" as the current session to run, all gnome-panel  applets behave as expected.


From here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/519583](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/519583)

Wondering if you're school network requires some specific setup. Static IP? Doesn't sound like you are being served one if you know your user and pw are correct.

---

### Post by karasuman on 2011-01-25
Thanks for the help with the panels.  It didn't even occur to me to ask whether they deliberately made the panels a fresh new mandatory form of stupid for the lucid release.  I can get that under control thanks to your advice.

Nothing has changed with the way WICD is set up since I was using jaunty.  There's definitely something stupid about my school's wireless network, but I can't figure out what changed about my system to make it stop being able to connect.  :-/

---

### Post by Bucky Ball on 2011-01-25
Maybe a word to the systems admins at school, probably won't know anything about Linux, of course!

And no, don't think you turned stupid! These things happen from time to time. I am about to endure the joys of connecting to the uni network when I go back in a month. ;)

---

### Post by karasuman on 2011-01-25
Looks like my desire to blame my stupid university is going to be thwarted.  Turns out, it's a bug in WICD combined with the upgrades reinstalling network manager and purge failing to actually, like, purge all of the packages.

This link helped:
[http://kubuntuforums.net/forums/index.php?topic=3111518.0](http://kubuntuforums.net/forums/index.php?topic=3111518.0)

So now I'm back to having a useful panel (seriously, WHO THOUGHT THAT WAS A GOOD IDEA?!) and back online, and now I just have to look up how to reconfigure the button position again.  :rolleyes:

When I first switched to Ubuntu from Windows, I was astounded at how, all of a sudden, I could make my computer do what I wanted it to do and look how I wanted it to look!

Why the back-pedaling with the latest few releases?  Can't customize the log-in screen, and it's a pain to un-Mac-ify the button layout on the window frames... and this business with just not being able to do anything with the panels is completely asinine.

---

### Post by Bucky Ball on 2011-01-26
karasuman, try this:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

... and this:

[http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html](http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html)

These will allow you to customise the login screen (and more). IMHO they should both be available in the repos but aren't. ;)

I don't love the setup myself so I tend to create hybrids. My desktop is an Xubuntu install with gnome-desktop installed (and openbox, fluxbox, all available from 'Sessions' at the login screen), Ubuntu Studio AV packages added, Edubuntu and Ubuntu Satanic Edition artwork added to that! My laptop is another blend again - Ubuntu 10.10 install but using the Xfce desktop environment which I much prefer (I use shortcut key combos to access virtually EVERYTHING rather than icons - nightmare for others using my machine but easy as choosing Gnome from 'Sessions' for that). I prefer it stripped back, sleek, slick and fast. 

ps: I also love Chopin. In my last year of Bachelor of Music Studies ... Saint-Saens another favourite, the list goes on ... and on ... lol

---

