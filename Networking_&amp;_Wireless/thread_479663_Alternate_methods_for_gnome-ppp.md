---
title: "Alternate methods for gnome-ppp"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by Bartender on 2007-06-20
Good day -
I've been trying to help some folks on this and other forums configure dial-up.  

Let's say, for the sake of argument, the person has a functional modem.  One of the suggestions made quite often is to download gnome-ppp from Synaptic.  That doesn't help very much if the person can't get to Synaptic because they can't figure out the dialer GUI, which has been broken since Dapper.

Don't know why I didn't think of this before, but gnome-ppp is available (along with dependencies) as a [package]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fg%2Fgnome-ppp%2Fgnome-ppp_0.3.23-0ubuntu2_i386.deb&md5sum=e4704859efb310eba7673c825895a6b9&arch=i386&type=main").

I downloaded it a few minutes ago on my Windows PC.  It's not a big package, anyone with a dial-up connection could get it.  Here's where I'm stuck - how would one go about getting Ubuntu to see the package and install it?  Would you burn the download to a CD then drop the CD in after bringing up Synaptic?  I've never tried using anything but the online repos.  It looks like Synaptic will accept data from a CD.

---

### Post by Bartender on 2007-06-20
Progress report -
Burned the gnome-ppp package to a CD, took it over to my test Linux PC running Dapper, and brought up Synaptic.  In the Settings, there's a button to "Add CD-ROM".  I clicked on it, it said to put the CD in.  I did that, and as soon as the CD got up to speed another program called Package Installer came up.  I tried to continue but it said that I couldn't run 2 update programs at once so I closed Synaptic, went back to Package Installer, and it appeared to re-install gnome-ppp.  I already had gnome-ppp installed.
So this looks like a good method to suggest for someone trying to get dial-up working on a newly installed Feisty or Edgy Ubuntu PC.  Any comments?

---

### Post by NutrOn on 2007-06-25
I'm about to give that a try, any thoughts on how to edit the etc / resolv file?
Nutr0n
:p

---

### Post by Bartender on 2007-07-02
HI, itron - 
Did you see my other post?
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

---

