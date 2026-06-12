---
title: "New distribution release 9.04"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by tsuchang on 2009-05-08
I upgraded to the 8.1 and now i have a upgrade notice on my update manager that says New distribution release 9.04 is available.
is that a solid reliable release?
I've had enough trouble wiht he present update, which brings me to my next question.  I used  to be able to go to Applications - Wine - Brouse C:/ drive and access the files there, but nothing happens when i select that now. Any solutions?

Grazi

---

### Post by billgoldberg on 2009-05-08
> **tsuchang said:**
> I upgraded to the 8.1 and now i have a upgrade notice on my update manager that says New distribution release 9.04 is available.
is that a solid reliable release?
I've had enough trouble wiht he present update, which brings me to my next question.  I used  to be able to go to Applications - Wine - Brouse C:/ drive and access the files there, but nothing happens when i select that now. Any solutions?

Grazi

Well, those files are in

/home/username/.wine/c_drive/program files

or something like that, you can launch apps from there.

Jaunty is a great release.

But as always I suggest a clean install from cd, not an upgrade.

---

### Post by pbpersson on 2009-05-08
Whether or not you like Jaunty depends upon:

1.  The unique blend of hardware you are using
2.  The unique blend of software you are using
3.  What you expect from the operating system

Some people love it, some people hate it.  It was released on April 23rd and some people suggest it takes six months for a distribution to become truly stable.

Some people have been using it since Alpha and have never had a problem, some people install the production version and they are dead in the water.

It you are using an ATI video card you might be limited to the open source driver, ATI is no longer supporting many of their cards.

---

### Post by tsuchang on 2009-05-08
> **billgoldberg said:**
> Well, those files are in

/home/username/.wine/c_drive/program files

or something like that, you can launch apps from there.

Jaunty is a great release.

But as always I suggest a clean install from cd, not an upgrade.

Oki doki
I tried to use the terminal and enter the /hom/my user name/ etc like you posted.  I didn't get anything other than "no such file exists".  I tried different drive designations like a b etc. but still no joy.  One other thing i have noticed since my last upgrade is that in places - computer there is no hard drive showing.  just the cd drives and filesystem.  That and not being able to access the drive as i mentioned before makes me wonder if i screwed up something.

---

### Post by durand on 2009-05-08
> **tsuchang said:**
> Oki doki
I tried to use the terminal and enter the /hom/my user name/ etc like you posted.  I didn't get anything other than "no such file exists".  I tried different drive designations like a b etc. but still no joy.  One other thing i have noticed since my last upgrade is that in places - computer there is no hard drive showing.  just the cd drives and filesystem.  That and not being able to access the drive as i mentioned before makes me wonder if i screwed up something.

It's /**home**/<username>/.wine

You can also just use ~/.wine as a shortcut. Copy and paste that into the file manager.

---

### Post by gandaran on 2009-05-08
> **tsuchang said:**
> Oki doki
I tried to use the terminal and enter the /hom/my user name/ etc like you posted.  I didn't get anything other than "no such file exists".  I tried different drive designations like a b etc. but still no joy.  One other thing i have noticed since my last upgrade is that in places - computer there is no hard drive showing.  just the cd drives and filesystem.  That and not being able to access the drive as i mentioned before makes me wonder if i screwed up something.
drive c is a virtual hidden drive in your home user folder, go to nautilus » view » check-mark view hidden files, now you can go to .wine folder that contains drive c.
if theres no .wine directory then click applications » wine » configure wine, this will create a new .wine directory for you.

---

### Post by tsuchang on 2009-05-08
> **gandaran said:**
> drive c is a virtual hidden drive in your home user folder, go to nautilus » view » check-mark view hidden files, now you can go to .wine folder that contains drive c.
if theres no .wine directory then click applications » wine » configure wine, this will create a new .wine directory for you.

Oki doki again
i didn't have nautilus on my computer so i had it install.  looking at it in my "system-preferences" i find it as "Nautilus Actions Configuration"
when I select that i get a little window that has ADD and import/export buttons usable.  do i impotrt my  new config? automatically? then use the above instructions?

---

### Post by gandaran on 2009-05-08
> **tsuchang said:**
> Oki doki again
i didn't have nautilus on my computer so i had it install.  looking at it in my "system-preferences" i find it as "Nautilus Actions Configuration"
when I select that i get a little window that has ADD and import/export buttons usable.  do i impotrt my  new config? automatically? then use the above instructions?
nautilus is your file manager, just click your home user folder icon, that opens nautilus!

---

### Post by albinootje on 2009-05-08
> **tsuchang said:**
> New distribution release 9.04 is available.
is that a solid reliable release?


Ubuntu Jaunty is imho very promising, but not if you're using certain Intel or ATI graphics cards and need 3D support with that.

You can however test Ubuntu Jaunty with the live session from cdrom or usb stick and see how well it works on your machine.

---

### Post by tsuchang on 2009-05-08
> **gandaran said:**
> nautilus is your file manager, just click your home user folder icon, that opens nautilus!

Much better.  I made a link to the wine folder for my desktop so i don't have to go thru this again.
you are great!!
Thansks
now how do i mark this as sloved?

---

