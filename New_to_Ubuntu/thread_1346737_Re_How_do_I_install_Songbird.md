---
title: "Re: How do I install Songbird?"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by BlueCanary9999 on 2009-12-05
Hi. I'm also having troubles installing Songbird.  I tried [this]("https://help.ubuntu.com/community/Songbird#Installing%20Songbird%20with%20a%20Script") but when I click the Songbird button in Applications, it returns "Failed to execute child process "Songbird" (No such file or directory)".  Is there a getdeb like you posted, but for 64-bit?  Thanks in advance.

---

### Post by Sir Jasper on 2009-12-05
Hi,

See the signature of our friend from the US Marines in this recent thread: 

[http://ubuntuforums.org/showthread.php?t=1346644](http://ubuntuforums.org/showthread.php?t=1346644)

My regards

---

### Post by speedwell68 on 2009-12-05
The easiest way is to download the latest Songbird DEB file from GetDeb.

---

### Post by LuisGMarine on 2009-12-05
Yeah the easiest was .deb but when I was trying to install songbird I was using it in beta stages.  I didn't have time to wait on someone to make a .deb so I just installed it from source and found out it helped a lot of people.  

Try the .deb though, if it works then hey good luck on using songbird.  If not then try my tutorial out, and it will not disappoint you at all! =)

---

### Post by BlueCanary9999 on 2009-12-05
GetDEB wanted me to use apturl.  When I try that, it fails because it cannot find the package "songbird".  o_O

Regardless, I followed LuisGMarine's post and it worked fine!  Thank you so much!

---

### Post by Norm24 on 2009-12-05
> **BlueCanary9999 said:**
> GetDEB wanted me to use apturl.  When I try that, it fails because it cannot find the package "songbird".  o_O

Regardless, I followed LuisGMarine's post and it worked fine!  Thank you so much!

You have to add the getdeb repository first.This is the easiest way and insures timely updates.

But Luis' method works just as well in the end.

Semper Fi Luis!

---

### Post by LuisGMarine on 2009-12-06
I'm actually doing a bit of a side project right now to make a .deb for songbird from scratch.  I'll post it up to see if you guys would like to use it =)

---

### Post by joshzam on 2009-12-09
> **Norm24 said:**
> You have to add the getdeb repository first.This is the easiest way and insures timely updates.

As for receiving timely updates, would adding the getdeb repository be any different (better/worse) than just adding the Songbird Daily PPA?
[https://launchpad.net/~songbird-daily/+archive/ppa](https://launchpad.net/~songbird-daily/+archive/ppa)

---

### Post by hellocatfood on 2009-12-17
> **joshzam said:**
> As for receiving timely updates, would adding the getdeb repository be any different (better/worse) than just adding the Songbird Daily PPA?
[https://launchpad.net/~songbird-daily/+archive/ppa](https://launchpad.net/~songbird-daily/+archive/ppa)

The builds done of the ppa are done by a bot and, as you can see, most of them have failed to build. The getdeb ones, whilst unofficial, are built correctly.

They're hoping to release it next Monday, so you should expect to see a .deb on GetDeb by Tuesday or Wednesday

---

