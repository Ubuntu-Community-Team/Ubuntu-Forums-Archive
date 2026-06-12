---
title: "New to Kubuntu"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by Don1500 on 2009-08-18
I just loaded Kubuntu Karmic Koala and it's really nice looking. I think the KDE interface is much sharper than Ubuntu's Gnome. 
I just have a few questions. 
1. Where is a good "users Manual"? I know what I'm looking for in Kubuntu, I just don't know how to fide it. 
2. Is there a synaptic manager?
3. Amarok 2 needs some instruction! I can load 1000's of files but it will not play anything!

I'll admit I've only had about 2 hours to play with it last night and there is a lot I will find out on my own (as I did with Ubuntu), but a couple of User manuals would get me started.

---

### Post by credobyte on 2009-08-18
> **Don1500 said:**
> 
2. Is there a synaptic manager?


No, Kubuntu uses Adept Package Manager ( info @ [http://linux.about.com/od/kubuntu_doc/a/kubudg19t01.htm](http://linux.about.com/od/kubuntu_doc/a/kubudg19t01.htm) ).

---

### Post by Crunchy the Headcrab on 2009-08-18
> **Don1500 said:**
> 
3. Amarok 2 needs some instruction! I can load 1000's of files but it will not play anything!


You probably need to install an audio codec.  It doesn't use Gstreamer so you are going to need a different codec then you used under gnome.

---

### Post by SuperSonic4 on 2009-08-18
> **credobyte said:**
> No, Kubuntu uses Adept Package Manager ( info @ [http://linux.about.com/od/kubuntu_doc/a/kubudg19t01.htm](http://linux.about.com/od/kubuntu_doc/a/kubudg19t01.htm) ).

Nay, Kubuntu uses KPackageKit


> 1. Where is a good "users Manual"? I know what I'm looking for in Kubuntu, I just don't know how to fide it.

google is your friend, alternatively post what you want :)

> 2. Is there a synaptic manager?

No, Kubuntu uses KPackageKit although I believe Adept and Synaptic are available. I always used to use the terminal

> 3. Amarok 2 needs some instruction! I can load 1000's of files but it will not play anything!

Probably needs a codec of some kind, it used to be libxine but I don't know any more. KDE 4.x uses phonon so you'd need a backend too.

---

### Post by Crunchy the Headcrab on 2009-08-18
> **SuperSonic4 said:**
> Nay, Kubuntu uses KPackageKit
And it's absolutely awful.

---

### Post by SuperSonic4 on 2009-08-18
> **Crunchy the Headcrab said:**
> And it's absolutely awful.

I agree, Shaman ftw but it's not available on kubuntu

---

### Post by credobyte on 2009-08-18
> **SuperSonic4 said:**
> Nay, Kubuntu uses KPackageKit

When it was replaced ( 8.04/10 ) ? I tough it's still in use :lolflag:

---

### Post by lykwydchykyn on 2009-08-18
> **Don1500 said:**
> 
1. Where is a good "users Manual"? I know what I'm looking for in Kubuntu, I just don't know how to fide it. 

Have you tried the "help" link in the menu?  Also, for configuration stuff the "system settings" tool has a search bar up top.  What are you looking for exactly?
> 
2. Is there a synaptic manager?

Others have covered this, but I just want to say that I use Synaptic in Kubuntu out of habit since it's never had a good package manager tool and still doesn't.  Works fine, if you like it, install it and use it.  
> 
3. Amarok 2 needs some instruction! I can load 1000's of files but it will not play anything!

Amarok 2 needs a lot of things, but once you get used to it it's ok.  It uses Xine backend, but that can be changed.
> 
I'll admit I've only had about 2 hours to play with it last night and there is a lot I will find out on my own (as I did with Ubuntu), but a couple of User manuals would get me started.
[http://kubuntuguide.org/Jaunty](http://kubuntuguide.org/Jaunty)

---

### Post by JK3mp on 2009-08-18
Use VLC possibly? I think it includes codecs built in. That or you might need to download some. And sure KDE LOOKS better, but after you give it a bit you'll notice performance diffrences, whether they effect your choice of DE is up to you some people can stand it, i can but only so far... *note im used to using multiple programs switching back and forth constantly etc etc so im easily frustrated even by the lag time of opening and minimizing windows etc. lol.

---

### Post by MickS on 2009-08-18
When I first put Kubuntu on here Amarok wouldn't work, not liking it much anyway I installed VLC, funny thing is when I tried Amarok again it was now working fine so I presume VLC brought some with it that Amarok needed, might be worth a try.


Mick

---

### Post by Knacker_Ned on 2009-08-18
> **lykwydchykyn said:**
> 
Others have covered this, but I just want to say that I use Synaptic in Kubuntu out of habit since it's never had a good package manager tool and still doesn't.  Works fine, if you like it, install it and use it.  

Synaptic in Kubuntu works for me, too. IMO much better than the other package managers.

---

### Post by SuperSonic4 on 2009-08-18
> **JK3mp said:**
> Use VLC possibly? I think it includes codecs built in. That or you might need to download some. And sure KDE LOOKS better, but after you give it a bit you'll notice performance diffrences, whether they effect your choice of DE is up to you some people can stand it, i can but only so far... *note im used to using multiple programs switching back and forth constantly etc etc so im easily frustrated even by the lag time of opening and minimizing windows etc. lol.

Ooh, is that a veiled dig at KDE I see?

I use alt+tab to switch windows and it works perfectly quickly, loading programs is quick too and even the laptop's CLI looks nicer than gnome

---

### Post by Don1500 on 2009-08-19
Thanks for all the info and I'm sorry if this Newbe question in the Newbe area was a bit, well, Newbe.

---

### Post by Ji Ruo on 2009-08-19
You can install Synaptic yourself or it will be installed as soon as you add any GNOME applications, such as firefox or VLC. I tend to use the command line to install programs and to update ('sudo apt-get update' then 'sudo apt-get dist-upgrade' will update every application, as well as upgrade your distro if a new one is available).

No manuals but this is a great unofficial guide - [http://kubuntuguide.org/Jaunty](http://kubuntuguide.org/Jaunty)

---

### Post by Don1500 on 2009-08-19
tried to loas VLC, got this:
```
don@kubuntu:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 1.0.1-1ubuntu1) but it is not going to be installed
E: Broken packages

```
Maybe VLC isn't ready for the Karmic Koala   :guitar:

---

