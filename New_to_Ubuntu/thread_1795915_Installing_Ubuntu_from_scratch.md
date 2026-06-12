---
title: "Installing Ubuntu from scratch"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by jermza on 2011-07-03
I downloaded Unity yesterday, created a CD from it, inserted the CD, and rebooted Ubuntu (10.10) in the hopes that I could install 11.04.  Nothing happened and Ubuntu booted up, skipping the CD, but once logged in, prompted me to upgrade (because it detected the CD).

So I upgraded.

But I'm not happy with my installation of Unity.  Things are not working properly and I'd like to install it from scratch.

I have two hard drives; one has all my docs, pics, videos, etc; the other has ONLY Ubuntu. (I simply redirected the shortcuts of those folders so that I can access them from my main menu.)  My assumption is that a clean installation won't affect those files because they're on a different drive to Ubuntu.

How do I do a clean installation?  Putting in the CD and rebooting doesn't seem to do anything.

---

### Post by Rex Bouwense on 2011-07-03
Actually, putting the CD in and rebooting is all that you have to do.  However, there are some things to check.
Did you run run an md5sum on the download?
Did you burn the ISO at the lowest speed possible?  (That is burn the ISO, not merely copy the files to a CD.)
Did you change the boot order in your BIOS to have the CD drive boot before your hard drive?

---

### Post by jermza on 2011-07-03
> Did you run run an md5sum on the download?
I don't know what that is.

> Did you burn the ISO at the lowest speed possible?  (That is burn the ISO, not merely copy the files to a CD.)
I used the default setting (maximum, I think).

> Did you change the boot order in your BIOS to have the CD drive boot before your hard drive? 	
No. I suppose I could try that, yes?

---

### Post by Rex Bouwense on 2011-07-03
Any one of those could have bonked the CD.
To check the md5sum look here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
There are more chances for errors when burning at a faster speed.
Change the boot order first and try it.  After the CD boots you will get a screen that asks you do you want to try Ubuntu without changing anything on your computer or install Ubuntu.  Be very careful that you choose the correct partition or you will overwrite your data.  So, as a very wise man once said back up your data before you reinstall.  Enjoy.  :popcorn:

---

