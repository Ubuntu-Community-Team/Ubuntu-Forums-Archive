---
title: "How about removing mscorefonts dependancies from restricted extras"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by powel212 on 2009-11-16
I have now switched back to Jaunty and have advised my friends and clients to do the same.

The missing mscorefonts in restricted extras causes Karmic to be unusable due to all the errors created by the missing fonts.

The fonts are still missing in Jaunty but this fact does not cause as many errors as it does in Karmic.

It seems to me that if some programs have these font dependencies and the fonts are no longer available then should not the programs especially core elements like restricted extras swap out the problem fonts for something else. Maybe it is way more complicated than that.

Jaunty has always been a favorite of mine since its release so i'm not so unhappy to be running it but I was looking forward to some of the features in Karmic. 

Powel

---

### Post by philinux on 2009-11-16
Not had this problem. ttf-mscorefonts-installer is in synaptic and is a recommends only not a dependency as are all the restricted bits.

Easy enough to just look at the list and install just what you want

---

### Post by powel212 on 2009-11-16
What server are you using. I have tried several.

P

---

### Post by coffeecat on 2009-11-16
I've never had a problem installing the ms fonts with the ttf-mscorefonts-installer package - latest was only yesterday with a fresh install of Karmic - but I have seen some of the threads where people are having problems.

One way round this would be to mark ubuntu-restricted-extras for installation in Synaptic, and then look for ttf-mscorefonts-installer and unmark it. That worked for me once in Jaunty when I wanted the restricted-extras goodies without the ms fonts.

Then, if you already have the ttf fonts files on another/older Ubuntu installation, it's an easy enough job copying them over to a custom folder in /usr/share/fonts/truetype and then running 'sudo fc-cache -fv'.

---

### Post by powel212 on 2009-11-18
I am in Taiwan but I have tried The main US server as well and have still received the same error. Ubuntu admins please run install from Taiwan servers to see the problem. We are all suffering here. Karmic is unusable in this state. Can't install programs... error, error, error...mscorefont-error

Thanks

Powel

---

### Post by powel212 on 2009-11-19
I just tried it again using the United Kindom main Ubuntu server and still got the same error when installing restricted extras.

Powel

---

### Post by philinux on 2009-11-19
> **powel212 said:**
> I just tried it again using the United Kindom main Ubuntu server and still got the same error when installing restricted extras.

Powel

[https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)

See post #21.

This bug seems to affect wireless more than wired machines.

---

### Post by powel212 on 2009-11-19
My system is 100% wired

P

---

### Post by philinux on 2009-11-19
> **powel212 said:**
> My system is 100% wired

P

Is that the error/bug you're getting. If so the fix works.

---

### Post by powel212 on 2009-11-19
I just noticed in the link you provided that there is a bunch of Chinese in the error message. Could it be location specific. I am in Taiwan. I'll try again but at install I will set my location as USA instead of Taiwan and see if that makes any difference.

Thanks for the feedback.

Powel

---

### Post by philinux on 2009-11-19
> **powel212 said:**
> I just noticed in the link you provided that there is a bunch of Chinese in the error message. Could it be location specific. I am in Taiwan. I'll try again but at install I will set my location as USA instead of Taiwan and see if that makes any difference.

Thanks for the feedback.

Powel

It varies for different users as you can see. I just got a load of timeouts on my lappy. But desktop did not.

Post #21 has the fix just cut out and paste the fix in then you're good to go. It still took a couple of updates on the lappy as the wireless was crappy. 

I cant believe a fix has not been released either.

---

### Post by wojox on 2009-11-19
What does the error say?

---

### Post by powel212 on 2009-11-19
Tried with fix from Post 21 as stated.

Still returns error
```
E: ttf-mscorefonts-installer: subprocess post-installation script returned error exit status 1
```

I'll keep plugging away at it.

P

---

### Post by philinux on 2009-11-19
Post back all the error messages it spits out.

---

### Post by powel212 on 2009-11-19
```
All done, errors in processing 1 file(s)
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
```

and lots of 

```

conection timed out.
giving up.
```

I wasn't allowed to copy from the log window so I typed out the above. How do you copy the error log? I tried cntrl c but it wouldn't allow it.

Powel

going to bed now - almost 2AM

Thanks for the help.

---

### Post by wojox on 2009-11-19
Try this: [http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/](http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/)

---

### Post by powel212 on 2009-11-19
> Try this: [http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/](http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/)

Thanks to all and especially "wojox" as above works perfectly.

Thanks again.

Powel

---

