---
title: "Is there a need to redownload ubuntu?"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by halfstrike on 2009-10-03
I have ubuntu 8.04 on a partition on my laptop I put it on over a year ago but never did anything with it. I want to to update/install 9.04 i have the ISO file on my computer already  but i wasn't sure if I could update from 8.04 to 9.04 from  8.04 or would i have to burn the 9.04 image to a disc and install it that way.

Thank you in advance.

---

### Post by yeats on 2009-10-03
You can go either way.  Yes you can upgrade from 8.04 to 9.04 (though when I did this it wanted to upgrade to Intrepid before going to Jaunty - whatever it does, don't interrupt it :-) ).  

If you have your /home directory on a separate partition (and if you don't, this might be a good opportunity to do so), you can just install from the disc without overwriting your data (select "manual" at the partitioning step and have your /home directory mount at the /home mount point).

---

### Post by halfstrike on 2009-10-03
excuse my ignorance but i dont know what you mean by /home directory.I have windows on one partition and ubuntu 8.04 on another and to upgradeto 9.04 to 8.04 from 8.04 do i need an internet connection?(i never got my wireless to work on 8.04)

---

### Post by yeats on 2009-10-03
> **halfstrike said:**
> excuse my ignorance but i dont know what you mean by /home directory.

The /home directory is akin to the "Documents and Settings" directory in Windows.  It's where all of your personal data (and that of any other users on the system) lives.  Some Linux folks like to move that to a separate partition because it makes reinstalling a little simpler.  If you don't want to get into all that, you can just move your files onto an external drive/disc/USB while you reinstall.

> I have windows on one partition and ubuntu 8.04 on another and to upgradeto 9.04 to 8.04 from 8.04 do i need an internet connection?

If you don't have an internet connection in Ubuntu, your only option is to download the image and burn it to a disc/USB.  (Are you not able to plug into the network with an Ethernet cord?)

> (i never got my wireless to work on 8.04)

Wireless support gets better with each release.  If 9.04 doesn't solve your problem, make sure to ask about it here on the forums.  There are lots of folks with expertise in that area. :-)

---

### Post by Paqman on 2009-10-03
There's no direct update path from 8.04 to 9.04, you'd have to go 8.04 > 8.10 > 9.04, which is probably more of a pain than it's worth.

9.10 is due out at the end of the month. I'd wait until then and then just reinstall. You'll notice a significant performance boost, and loads of new features. Reinstalling rather than upgrading will allow you to switch to the fast new filesystem, ext4.

---

### Post by XCan on 2009-10-03
If you never did anything with your installed Ubuntu I think you should reinstall everything. The only good reason not to reinstall is if one wants to retain the installed apps and settings without much hassle.

---

### Post by Paddy Landau on 2009-10-03
And do a FULL BACKUP first, in case the upgrade doesn't work as well as you would have hoped. I upgraded my 8.04 to 9.04 a couple of months ago, and I had to revert to 8.04 -- which meant restoring from my full backup. I'm waiting for 9.10 to try again.

You can use PartImage (from [SysRescCD]("http://www.sysresccd.org/")) or [CloneZilla]("http://clonezilla.org/") to fully back up your entire partition onto an external hard drive.

---

