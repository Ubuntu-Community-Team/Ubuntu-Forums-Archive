---
title: "empathy..."
date: 2009-11-04
forum: New to Ubuntu
---

### Post by HungryOcopus on 2009-11-04
My empathy spends ages to sign in, sometimes 10 mins, even when i enter my log in information again. Also, I have no idea how to block users, and I cannot see my offline contacts. Can anyone help me out? the help guide in empathy is really bare.
 
I have no idea why they replaced pidgin, it seemed decent enough. I looked it up quite a lot online, and I know apparently empathy has a strong 'backend' and some other technical advantages that I'm utterly clueless about, but it seems that as just a regular im client it's pretty inferior from my first impressions. 
 
I know I should just grab pidgin if it's not working out for me, but when they make it the default, it makes me think that there must be something great about it that I'm missing.

---

### Post by nhasian on 2009-11-04
you are welcome to switch back to pidgin.  its easy to do with:

```
sudo apt-get install pidgin
```

it would help to know which protocol you are talking about in empathy?  are you talking about your account in msn? yahoo? icq?

pidgin only has audio/video with googletalk, but empathy can do it with googletalk as well as msn messenger.  plus I like the option to share your desktop in empathy.

---

### Post by LarryMi on 2009-11-04
Has anyone been able to get a Yahoo "Room List" with empathy?  I'm using the 32 bit version, and it's blank.

---

### Post by LunaticHiatus on 2009-11-04
they got rid of pidgin for empathy because empathy has *some* webcam support and a lot of people where complaining that they could not get webcam to work with pidgin (which it sounds like from pidgin developers that they will never get it any time soon.)

---

### Post by The Funkbomb on 2009-11-04
> **LarryMi said:**
> Has anyone been able to get a Yahoo "Room List" with empathy?  I'm using the 32 bit version, and it's blank.

You're probably better off :P

---

### Post by HungryOcopus on 2009-11-04
I mainly use msn, and really I'd just like to know how to block a contact. Is it even possible in empathy?

---

### Post by nomnex on 2009-12-27
> **HungryOcopus said:**
> I mainly use msn, and really I'd just like to know how to block a contact. Is it even possible in empathy?

Pidgin has this function, empathy does not

---

### Post by gcs1984 on 2010-02-01
Empathy does not have the ability to block contacts? That is one of the most basic IM features, I cannot believe this hasn't been implemented.

---

### Post by NightwishFan on 2010-02-01
I think empathy could get good, and I like the interface.. For otherwise use Pidgin. Since I only chat, and not video or transfer files, I use Empathy.

---

### Post by inchkape on 2010-02-02
I use aMSN for MSN. it has file transfer webcam and sound. You can block users. You can do all you usually need to do.
For Yahoo I use Gyachi - again it does most things as well as the original chat client (some of them better) but not IM voice (I don't think).
I tried Empathy. It has all the hallmarks of being brought in before it's mature in my opinion. I would call it an alpha release.
Pidgin is great for my general use (keeping an eye on buddies in multiple protocols. When I want to use webcam I just switch to aMSN or Gyachi

---

### Post by nomnex on 2010-02-02
empathy follows the Ubuntu philosophy "available to all" with a all or nothing setting "on/off line"

there is already a bug report on launchpad [1] and a follow-up upstream. With a bit of hope, lynx will offer the option to block contacts. Later, empathy might even provide an encryption plug-in (?)

Most of the IM clients if not all are bloated and plain ugly (pidgin, amsn, etc.) sur enough they came from windoze to linux (when they are not clones).  I like empathy quite well for  IM.

[1] [https://bugs.launchpad.net/empathy/+bug/411898](https://bugs.launchpad.net/empathy/+bug/411898)

---

### Post by Merk42 on 2010-02-02
> **nomnex said:**
> 
Most of the IM clients if not all are bloated and plain ugly (pidgin, amsn, etc.) sur enough they came from windoze to linux (when they are not clones).  I like empathy quite well for  IM.

[1] [https://bugs.launchpad.net/empathy/+bug/411898](https://bugs.launchpad.net/empathy/+bug/411898)

Not sure how to measure "bloat", but Pidgin started in Linux...

---

### Post by cbert78 on 2010-02-03
> **inchkape said:**
> I use aMSN for MSN. it has file transfer webcam and sound. You can block users. You can do all you usually need to do.
For Yahoo I use Gyachi - again it does most things as well as the original chat client (some of them better) but not IM voice (I don't think).
I tried Empathy. It has all the hallmarks of being brought in before it's mature in my opinion. I would call it an alpha release.
Pidgin is great for my general use (keeping an eye on buddies in multiple protocols. When I want to use webcam I just switch to aMSN or Gyachi

My webcam works on aMSN, only to the point where the MSN user tries to accept my cam and then the picture goes blank. Does anyone else have this experience?

---

### Post by nomnex on 2010-02-03
> **Merk42 said:**
> Not sure how to measure "bloat", but Pidgin started in Linux...

*GTK+ AOL Instant Messenger, back in 99. right, but I have the feeling that the IM software have followed the MS messenger influence along the time. empathy is quite refreshing for the matter, minus some missing feature*s.

---

### Post by locodog on 2010-05-12
I don't get any sound when i get message on empathy, i've checked in Preferences and there is sound activated in program, but it doesn't seem to work... It's version 2.30.1

---

### Post by xtremesupremacy3 on 2010-07-15
> **cbert78 said:**
> My webcam works on aMSN, only to the point where the MSN user tries to accept my cam and then the picture goes blank. Does anyone else have this experience?

Blame Microsoft for that, turns out, they did a little upgrading which now makes the webcam feature provided by aMSN useless.
According to aMSN's makers, they are looking at bringing this back in the future but are currently restricted and cannot bring it back right now.

---

### Post by xsinsx on 2010-07-15
Empathy makes a noise on mine but its so soft i hardly hear it.

---

### Post by NightwishFan on 2010-07-15
Check your mixer settings in System -> Preferences -> Sound, and using this command (in terminal)
```
alsmixer -c0
```

---

### Post by t3chn0b0y on 2010-10-14
> **nomnex said:**
> empathy follows the Ubuntu philosophy "available to all" with a all or nothing setting "on/off line"


how about a security issue more like it.. When i use Yahoo i am
invisible and check those i want to see me for a reason, not because
Im hiding from people on my list but because anyone can check online
on many sites to see if im logged in and if I have them blocked, so
having the ability to be visible/invisible to difference people is
important.

as for the on/off ubuntu philosophy seems to me to be a good excuse to be lesser then one can become in comparison to its competition. So all those porn bots can't get blocked or that old girlfriend that wants to stalk me, can't be either?  all or nothing..  well heres to no privacy or
security for the sake a philosophy. and for the record pidgeon came from
linux first.

I don't believe it should of been implemented into the distro yet, because of those issues, and the issue i have with pidgeon is it doesn't follow the new standard of getting away from the notification bar as of yet. :(

---

### Post by nomnex on 2010-10-14
> **t3chn0b0y said:**
> as for the ubuntu philosophy

There is no such thing. Empathy is a GNOME application. Ubuntu uses Empathy as its default IM client --as other distributions based on GNOME do.

- A forum will help with installation and technical questions.
- Packages will contain more or less bugs on n' or y' distribution. (broken packages and software bugs are different things).
- Upstream is the place to report bugs and feature requests for the software included with your distribution, or the applications you install.

Expressing your views about a software on the Ubuntu forum is like telling your hairdresser your wife is having an affaire with the milkman. At best you will get sympathy.

---

