---
title: "Virtualbox Update?"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by migs73 on 2010-08-05
Virtual box is telling me there ia an updated version available. Is there any way to upgrade it without having to re-install my guest OS's??

---

### Post by hudsonl on 2010-08-05
> **migs73 said:**
> Virtual box is telling me there ia an updated version available. Is there any way to upgrade it without having to re-install my guest OS's??

The upgrades will keep your Guest O/S's in tack.  

Works very well ... I have used it many times and never had to redo any of the guest VMs.

---

### Post by migs73 on 2010-08-05
Thanks Hudson

How do I do the upgrade? I am pretty sure when I clicked on the link for the new version it downloaded a .deb at which point I chickened out instead of unpacking/installing. Is that all there is to it?

---

### Post by hudsonl on 2010-08-05
> **migs73 said:**
> Thanks Hudson

How do I do the upgrade? I am pretty sure when I clicked on the link for the new version it downloaded a .deb at which point I chickened out instead of unpacking/installing. Is that all there is to it?


Yes ... VirtualBox will install just fine if you use the GUI installer (double-click on the .deb file) or thru the command line.  Whichever is your preference.

I believe it removes/updates the VirtualBox binaries as needed ... and so all you VMs which are normally stored in your home drive under .VirtualBox are left alone.

You will see Machines, HardDisks, etc in that directory ... so the installer won't touch those.

---

### Post by snowpine on 2010-08-05
Actually if follow the ["Debian-based Linux distributions" instructions from the VirtualBox website]("http://www.virtualbox.org/wiki/Linux_Downloads"), it will add a repository to your sources.list and updates should come through your regular Update Manager. 

If you just install a .deb you will not necessarily get updates in a timely fashion. :)

---

### Post by migs73 on 2010-08-23
Thanks guys, sorry for the delay in posting, I've had a lot on my plate. Finally got round to trying this. The GUI route (download and use GDebi) resulted in a reported clash with the installed virtual box. Went to the link from snowpine and followed the terminal commands from there. All went okay and hopefully will have the auto updates now too. If only my windows vista (the guest OS) was as helpful. Had to install SP1 once I opened it. What a waste of a night!!

Many thanks.:D

---

### Post by Paqman on 2010-08-23
> **migs73 said:**
> The GUI route (download and use GDebi) resulted in a reported clash with the installed virtual box.

That's to be expected. It's telling you that it's going to remove the old version and install the new one.

Adding the repo is always the best way to go though, for any software.

---

### Post by dazvansgillio on 2010-08-23
Not sure but you may have to re install Guest additions if you are using that.

---

### Post by TNT1 on 2010-08-23
> **snowpine said:**
> Actually if follow the ["Debian-based Linux distributions" instructions from the VirtualBox website]("http://www.virtualbox.org/wiki/Linux_Downloads"), it will add a repository to your sources.list and updates should come through your regular Update Manager. 

If you just install a .deb you will not necessarily get updates in a timely fashion. :)

Yip.

---

### Post by migs73 on 2010-08-23
Paqman,

There was no option to install the new version after the warning. The 'install' button was greyed out.


Next time I download stuff I'll make sure to read the whole page to make sure I have all the prerequisite stuff onboard and to add it to my repo if possible. Been caught out with that before with printer drivers.

I need to develop some patience  ):P

Maybe they should put the .debs etc at the bottom of the page!!

By the way my guest additions are still there.

---

