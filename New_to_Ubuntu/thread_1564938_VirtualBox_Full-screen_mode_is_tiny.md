---
title: "VirtualBox: Full-screen mode is tiny"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-08-31
Hello:

I installed 6 linux distributions using VirtualBox.

Only one, PCLinuxOS, gives me a true full-screen mode which uses my entire screen. All the rest, in full-screen mode, provide only a small box surrounded by a black border that is about 3 inches wide.

I looked at the settings for any differences but I don't see any.

Any ideas?

Thanks,

Rob.

---

### Post by coffeecat on 2010-08-31
Have you installed guest additions in the distros that aren't going into fullscreen mode?

---

### Post by CharlesA on 2010-08-31
Do you have the guest additions installed?

Also, what OS are you running on each?

---

### Post by Robert.Thompson on 2010-08-31
> **coffeecat said:**
> Have you installed guest additions in the distros that aren't going into fullscreen mode?

"guest additions" ?????

I don't know what this is.

All I did was download the ISO files to my PC and then install it by choosing 'New' from the VirtualBox menu.

I don't think I ran any of the update managers.


Rob.

---

### Post by coffeecat on 2010-08-31
> **Robert.Thompson said:**
> "guest additions" ?????

I don't know what this is.

If you downloaded the installer from [the Virtual Box site]("http://www.virtualbox.org/"), the manual came with it. It's worth reading! :wink:. Tells you all about guest additions. :p

If you installed VirtualBox from the Ubuntu repository, you've got the OSE version without USB support. Either way, you need to read the manual.

What is your host OS?

---

### Post by Robert.Thompson on 2010-08-31
> **coffeecat said:**
> If you downloaded the installer from [the Virtual Box site]("http://www.virtualbox.org/"), the manual came with it. It's worth reading! :wink:. Tells you all about guest additions. :p

If you installed VirtualBox from the Ubuntu repository, you've got the OSE version without USB support. Either way, you need to read the manual.

What is your host OS?

I am using Ubuntu 10.04 LTS

---

### Post by scrooge_74 on 2010-08-31
> **Robert.Thompson said:**
> I am using Ubuntu 10.04 LTS

VirtualBox is full of features, you need to read **[this]("http://www.virtualbox.org/manual/UserManual.html")** before asking questions

---

### Post by coffeecat on 2010-08-31
> **scrooge_74 said:**
> VirtualBox is full of features, you need to read **[this]("http://www.virtualbox.org/manual/UserManual.html")** before asking questions

@Robert.Thompsom, the manual I was referring to is identical to that link, but comes as a PDF in the installer package.

---

### Post by Robert.Thompson on 2010-08-31
Sorry for wasting your time...

I did not read the manual. I just assumed that there was something wrong because one is working in full screen and the others are not.

I found the manual and will read it - even try to understand it!:)

Thanks for your time - I would delete this thread but I don't know how. I will mark it as solved.

Rob.

---

### Post by coffeecat on 2010-08-31
> **Robert.Thompson said:**
> Sorry for wasting your time...

I did not read the manual. I just assumed that there was something wrong because one is working in full screen and the others are not.

No problem! :) As scrooge_74 said, there are lots of goodies in VirtualBox, so it's certainly worth reading the manual.

I'm intrigued by PCLinuxOS working properly. If I remember correctly, an earlier release of Mandriva I once played with did come with guest additions pre-installed - which was nice. Perhaps PCLinuxOS is doing the same. PCLinuxOS was once a fork of Mandriva but it's really an independent distro now so the fact that Mandriva includes guest additions doesn't necessarily mean that PCLinuxOS would.

Out of interest, what were the other five distros?

 > **Robert.Thompson said:**
> I would delete this thread but I don't know how. I will mark it as solved.

You can't delete it - only a moderator can by jailing it. But it deserves to remain readable. Don't forget that there are many people scouring the boards who don't often (or ever) post but who find solutions to their problems in the threads.

---

### Post by CharlesA on 2010-08-31
Also the F1 help file is pretty good too. :)

---

### Post by eriktheblu on 2010-08-31
> **Robert.Thompson said:**
> "guest additions" ?????

I don't know what this is.

The guest additions are basically a set of drivers, and a bit of other software to make it integrate better with your host OS.

---

### Post by Robert.Thompson on 2010-08-31
CrunchBang
Lubuntu (I think I like this best of all.)
Peppermint
Ubuntu 10.04 (which is also the host OS)
Xubuntu
Windows XP

Tried but installation didn't work well (probably me) for:
Puppy
Ubuntu 10.04 Mini

Thanks,


PS. did alittle RFM on VBox and installed Guest Additions on Lubuntu and it immediately worked properly in full-screen mode!

Rob.

---

