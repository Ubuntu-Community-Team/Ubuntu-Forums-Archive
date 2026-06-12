---
title: "Two users in one machine AT THE SAME TIME?"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by sergiodlc on 2009-11-21
My laptop has suddenly broken. My wife usually works at her Acer One netbook connecting an external keyboard, mouse and monitor. Would it be possible that either of us uses the external peripherals while the other one uses the included peripherals so both of us can work AT THE SAME TIME?

I know of the LTSP project but this is a somewhat different concept.

Cheers,

Sergio

---

### Post by peculiar penguin on 2009-11-21
A config like that is usually called "multiseat", no idea if this is supported with current versions but the term should help you when searching/googling.

---

### Post by Johnneylee on 2009-11-21
Sorry to just drop a link to send you on your way, but I've not tried this before.
So here you go [MultiseatX]("https://help.ubuntu.com/community/MultiseatX")
Good luck.

Oh and to install the legacy gdm just run this
> sudo apt-get install gdm-2.20

---

### Post by steveneddy on 2009-11-21
Just make her a user with her own account on your laptop and have her log in remotely over your home network.

Linux will support many different users before the system folds.

You can use your account while she uses her account on the same computer and neither one will know the other is even there.

EDIT:

I misunderstood the original post. Sorry.

I leave my original post there anyway.

I know nothing about multiseat.

---

### Post by sergiodlc on 2009-11-21
Yes, I found the MultiseatX community documentation. Seems fine to me. Thanks a lot. Does anyone know if it works in an Acer One netbook?

I'm looking forward to further ideas!

Sergio

---

### Post by Johnneylee on 2009-11-21
As far as I know the Acer One netbook is supported. It might help to know the model, but to save some time for you here is a link to the community documentation
[AspireOne]("https://help.ubuntu.com/community/AspireOne/Home")

if you need anything just let us know.

---

### Post by steveneddy on 2009-11-21
> **sergiodlc said:**
> Yes, I found the MultiseatX community documentation. Seems fine to me. Thanks a lot. Does anyone know if it works in an Acer One netbook?

**I'm looking forward to further ideas!**

Sergio

Buy a new laptop.

---

### Post by Johnneylee on 2009-11-21
> **steveneddy said:**
> Buy a new laptop.
Well, duh. He might need a computer right now. So your post was sort of rude and useless.

OnSubject: I found a easy tutorial on setting up a multiseat computer.
[http://www.linuxtoys.org/multiubuntu/multiubuntu.html]("http://www.linuxtoys.org/multiubuntu/multiubuntu.html")

---

### Post by steveneddy on 2009-11-21
:roll:> **Johnneylee said:**
> Well, duh. He might need a computer right now. So your post was sort of rude and useless.

OnSubject: I found a easy tutorial on setting up a multiseat computer.
[http://www.linuxtoys.org/multiubuntu/multiubuntu.html]("http://www.linuxtoys.org/multiubuntu/multiubuntu.html")

:roll:

---

### Post by sergiodlc on 2009-11-21
> **steveneddy said:**
> Buy a new laptop.

Are you kidding? I'm in Cuba so my main concern is how we'll get to next month. Can't afford one. If you want to play the Good Samaritan, let me know ;-)

---

### Post by sergiodlc on 2009-11-24
Well, I have tried several solutions and none worked up to now. The second screen always look corrupted. Does anyone know about a success story setting up multiseat in an Acer Aspire One netbook?

---

### Post by sergiodlc on 2009-12-08
Hi:

I finally got it to work :popcorn:. [The instructions provided here proved very helpful]("http://netpatia.blogspot.com/2009/06/multiseat-in-ubuntu-904.html"). It works OK in my Acer One netbook.

Thanks for your helpful comments.

Sergio

---

