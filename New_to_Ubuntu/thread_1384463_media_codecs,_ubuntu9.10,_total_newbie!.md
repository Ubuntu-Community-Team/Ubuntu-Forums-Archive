---
title: "media codecs, ubuntu9.10, total newbie!"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by duncanmaybury on 2010-01-18
Hello folks
I am new to this world of ubuntu having been on windows for along time. I am enjoying ubuntu but finding it pretty hard to get my head around how to do things.

At the moment I am stuck trying to get DVD's to play.
I have been trying to use the Totem Player but it is saying:
[COLOR=Red]No URI handler implemented for "dvd".[/COLOR]
I dont know what this meens, I am guessing it is something to do with codecs?
I installed VLC as this has always been very versatile when playing videos in windows, but it seems it too needs some further tweeking as it doesn't play DVD's.
I have had a look around for some answers/guidence but since I am new to this world I am not quite sure what I am doing(putting stuff in the command line etc).
Any Beginners Talk on this would be very appreciated by me and my 3year old daughter who is patiently waiting for me to sort it out so she can watch her DVD.

Kind Regards
Dunc

---

### Post by papuccino1 on 2010-01-18
Hi there. Have you installed Ubuntu Restricted Extras?

Go to Applications > Ubuntu Software Center.

In the search box (upper right hand corner) type in 'flash' and it will load for a bit and show a list of results.

The first one should be Ubuntu Restricted something something. Click on the arrow and install that.

Should work now.

---

### Post by snowpine on 2010-01-18
Ubuntu Restricted Extras is a good thing to install :) but the specific solution for playing DVDs is described here:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Basically, you need to install and enable libdvdcss. Good luck!

---

### Post by audiomick on 2010-01-18
There is something else as well as that. go and look here
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by J V on 2010-01-18
[Click this]("apt://ubuntu-restricted-extras")

[And this]("apt://libdvdread4")

Then paste this into a terminal:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by duncanmaybury on 2010-01-18
Wow quick and very helpful replies. I have got it up and running on the first reply. I will investigate the other answers, thanks.
Dunc

---

### Post by snowpine on 2010-01-18
> **duncanmaybury said:**
> Wow quick and very helpful replies. I have got it up and running on the first reply. I will investigate the other answers, thanks.
Dunc

We are all basically saying the same thing, if you installed ubuntu-restricted-extras you should be all set. There is usually more than one way to do the same thing in Linux. :)

---

### Post by blazemore on 2010-01-18
> **snowpine said:**
> We are all basically saying the same thing, if you installed ubuntu-restricted-extras you should be all set. There is usually more than one way to do the same thing in Linux. :)

ubuntu-restricted-extras does NOT allow you to play back encrypted DVDs. For that you will need to install libdvdcss. [[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs])

---

### Post by llawwehttam on 2010-01-18
Personally I always enable the medibuntu repo as soon as possible.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

