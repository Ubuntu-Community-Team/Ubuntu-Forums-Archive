---
title: "xbmc maverick ppa"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by bprins on 2010-10-15
Why is the XBMC ppa still not available? Is it that complicated to copy the binaries from the lucid ppa and make them available in a maverick ppa? There must be a good reason not to do such a thing, I would love to know why. 

Does anybody have the answer for me? :)

---

### Post by sandyd on 2010-10-15
> **bprins said:**
> Why is the XBMC ppa still not available? Is it that complicated to copy the binaries from the lucid ppa and make them available in a maverick ppa? There must be a good reason not to do such a thing, I would love to know why. 

Does anybody have the answer for me? :)
maverick brings newer updated programs.
xbmc must be compiled against those newer updated programs instead of the older versions in lucid in order to gaurentte functionality.

---

### Post by bprins on 2010-10-15
I can imagine the XBMC crew has more stuff to do then test if it works for ubuntu maverick.

It's just that, maverick is alive for quite a while. Alpha, beta, release candidate and now since 10-10-10 the official release, but still no Maverick PPA. 

But ok, no more nagging, I'll just shush and be patient :)

Thanks for the reply btw.

Grtz, Bas

---

### Post by clhsharky on 2010-10-15
bprins

PPAs are Personal Package Archives by individuals or Developers. Ubuntu doesn't test, build,or maintain them. Add PPAs from trusted sited at your own risk.

Sharky

---

### Post by rburkartjo on 2010-10-15
cant wait until it is avail. great app

---

### Post by sandyd on 2010-10-15
> **bprins said:**
> I can imagine the XBMC crew has more stuff to do then test if it works for ubuntu maverick.

It's just that, maverick is alive for quite a while. Alpha, beta, release candidate and now since 10-10-10 the official release, but still no Maverick PPA. 

But ok, no more nagging, I'll just shush and be patient :)

Thanks for the reply btw.

Grtz, Bas
if your impatient....
```

sudo apt-get install svn
mkdir ~/dev
cd dev
svn co http://xbmc.svn.sourceforge.net/svnroot/xbmc/trunk xbmc
cd xbmc

```
and compile it yourself.

---

### Post by bjb1959 on 2010-10-23
> **sandyd said:**
> if your impatient....
```

sudo apt-get install svn
mkdir ~/dev
cd dev
svn co http://xbmc.svn.sourceforge.net/svnroot/xbmc/trunk xbmc
cd xbmc

```
and compile it yourself.

I did compile it but it crashes and doesn't see my upnp server so this isn't the best solution. I guess we just have to wait or use boxee since it works now.

---

### Post by sandyd on 2010-10-23
> **bjb1959 said:**
> I did compile it but it crashes and doesn't see my upnp server so this isn't the best solution. I guess we just have to wait or use boxee since it works now.

then your not compiling it right.

---

### Post by cerberos on 2010-11-26
> **sandyd said:**
> 
```

sudo apt-get install svn

```


sudo apt-get install subversion 

:P

---

### Post by hunter99507 on 2010-11-26
I had this questions a couple of weeks ago and someone helped me out with it. I am running 10.10 and XBMC works great. Check out this response to get XBMC on ubuntu 10.10

 				 				**Re: ubuntu dlna question help** 			
 			 			 		   		 		 		Try again. Try harder. Be more verbose :smile:
Seriously xbmc is the app you want.

Open a terminal and type

 	Code:
 	sudo add-apt-repository ppa:team-xbmc 
 	Code:
 	sudo apt-get update 
Then open the software center, go edit/software sources/other  software. You should find 2 entries for team-xbmc. Edit them both and  replace "maverick" with "lucid" (since the ppa doesnt provide packages  for maverick yet, but the ones for lucid work fine).

Let it reload and then just install xbmc from the software center.

[http://ubuntuforums.org/showthread.php?t=1609732](http://ubuntuforums.org/showthread.php?t=1609732)

---

### Post by udjinn on 2010-12-10
thanks for sharing. that worked like a charm for me.

---

