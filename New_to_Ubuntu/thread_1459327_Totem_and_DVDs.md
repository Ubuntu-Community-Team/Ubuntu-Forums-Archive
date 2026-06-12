---
title: "Totem and DVDs"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by ambient007 on 2010-04-21
So,
linex noob (me)+fresh install of ubuntu 9.10 on laptop+DVD=missing plugin need.

Said linex noob googles his problem and comes across this:[http://shibuvarkala.blogspot.com/2009/10/how-to-play-dvd-in-ubuntu-910-karmic.html](http://shibuvarkala.blogspot.com/2009/10/how-to-play-dvd-in-ubuntu-910-karmic.html)

opens terminal, does this:

[COLOR=Green]sudo apt-get install ubuntu-restricted-extras[/COLOR]

When he then tries to do this:

[COLOR=Green]sudo /usr/share/doc/libdvdread4/install-css.sh[/COLOR]

He gets this:[COLOR=Purple]
--2010-04-21 23:51:31--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... failed: Connection timed out.
Retrying.

--2010-04-21 23:54:41--  (try: 2)  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb)
Connecting to packages.medibuntu.org|88.191.82.11|:80... [/COLOR]

Which continues indefinitely if I let it



Now when I load up a DVD and open up totem, the application window closes as soon as I click 'play'.

NOT the intended result.

Is there anyone out there that can shed some light on my situation?

domo arigato.

---

### Post by e4uforums on 2010-04-21
I'm timing out on that link also...

what you need to install (and what the script is trying to do) is libdvdcss.  Search Google for libdvdcss or libdvdcss2 and see if you can't download it elsewhere.  I'd find you a link but I'm at work.

---

### Post by ambient007 on 2010-04-21
> **e4uforums said:**
> I'm timing out on that link also...

what you need to install (and what the script is trying to do) is libdvdcss.  Search Google for libdvdcss or libdvdcss2 and see if you can't download it elsewhere.  I'd find you a link but I'm at work.

I'll see if I can find it now.

---

### Post by e4uforums on 2010-04-21
libdvdcss is the library that descrambles retail dvd's - get that setup and you should be good to go.

---

### Post by ambient007 on 2010-04-21
[INDENT]This site: [http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-9-10-karmic.html)


Says to do this:

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list  --output-document=/etc/apt/sources.list.d/medibuntu.list
[/INDENT] [INDENT]sudo apt-get -q update
[/INDENT] [INDENT]sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring
[/INDENT] [INDENT]sudo apt-get -q update






Is this right?


I'm still getting my head around installing stuff without using synaptics (like I said, really new to ubuntu). 

[/INDENT]

---

### Post by HarrisonNapper on 2010-04-21
If you have the medibuntu repositories (if not, adding them is worth considering), I believe libdvdcss3 is in synaptic directly. I haven't had to run the install script since Jaunty (and even then I think libdvdcss3 was in the repos). They also have an entire page at Medibuntu's site about how to watch DVDs in Ubuntu.

---

### Post by ambient007 on 2010-04-21
> **HarrisonNapper said:**
> If you have the medibuntu repositories (if not, adding them is worth considering), I believe libdvdcss3 is in synaptic directly. I haven't had to run the install script since Jaunty (and even then I think libdvdcss3 was in the repos). They also have an entire page at Medibuntu's site about how to watch DVDs in Ubuntu.

Thanks,

I can't find libdvdcss3 in synaptic, so maybe I don't have medibuntu repositories.
How do I go about adding them?

---

### Post by HarrisonNapper on 2010-04-21
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by ambient007 on 2010-04-21
> **ambient007 said:**
> Thanks,

I can't find libdvdcss3 in synaptic, so maybe I don't have medibuntu repositories.
How do I go about adding them?

Actually when I go to synaptic, settings, repositoris, other software:
'medibuntu' and 'medibuntu (source)' seem to be on the list - though their boxes aren't checked.

---

### Post by ed-koala on 2010-04-21
The Medibuntu repositories have been down since the weekend.  I saw another post somewhere that that might be up Wednesday (today).  That's what is causing the timeouts.

---

### Post by 3rdalbum on 2010-04-21
Normally everything you'd be trying would have worked. But the Medibuntu repository is down at the moment, for reasons seemingly unknown. I hear it will be back in a day or two, so hang tight until then or see if you can get libdvdcss2 from somewhere else.

Also, Totem doesn't work well for DVDs. You should use VLC.

---

### Post by HarrisonNapper on 2010-04-21
> **3rdalbum said:**
> Normally everything you'd be trying would have worked. But the Medibuntu repository is down at the moment, for reasons seemingly unknown. I hear it will be back in a day or two, so hang tight until then or see if you can get libdvdcss2 from somewhere else.

Also, Totem doesn't work well for DVDs. You should use VLC.

Ditto. VLC > Totem (for things like DVDs, at least)

---

### Post by ambient007 on 2010-04-22
oh I see... well that makes it slightly less confusing.
 
I'll get vlc as well. I'm assuming I'll still need these codecs or whatever anyway?

---

### Post by dineshs on 2010-04-22
Have you tried SMplayer?

---

### Post by ambient007 on 2010-04-22
> **dineshs said:**
> Have you tried SMplayer?


no, good?



I don't know if this is necessary and just a hangover from my 'windows mind set' or not, but I'm pretty conscious of trying to install as few programs as possible.

In my microsoft experience, machines that have had a lot of software install and uninstalled etc etc get bogged down a slow.

Is this true with ubuntu?

---

### Post by ambient007 on 2010-04-22
yay  [COLOR=Green]sudo /usr/share/doc/libdvdread4/install-css.sh [COLOR=black]seems to have worked now.

Just gotta see if totem is now doing what it is supposed to..[/COLOR]
[/COLOR]

---

### Post by dineshs on 2010-04-22
> **ambient007 said:**
> no, good?

I use SMplayer and vlc.No problem at all

---

### Post by yetiman64 on 2010-04-22
> **ambient007 said:**
> 
In my microsoft experience, machines that have had a lot of software install and uninstalled etc etc get bogged down a slow.
Is this true with ubuntu?

Microsot uses a centralized "registry" for most settings etc, whereas ubuntu generally uses individual configuration files (quite often in hidden folders/files in your home folder). You shouldn't notice near as much bogging down because of installing-uninstalling with linux.

Also if you have anymore medibuntu access problems, [check here for a fix]("http://ubuntuforums.org/showpost.php?p=9152922&postcount=6"). (Its info from user Morbius1 - that fixed my medibuntu access). 

Have fun with any of the suggested players (I personally use "hand compiled" mplayer from a tutorial by andrew.46 as well as smplayer from a PPA and vlc from the repos, with no problems re bogging down.)

Though be aware that hand compiling from source is best left till you gain a bit more experience with your system if you're new to Ubuntu, but it is a good way to learn a bit about the system if your a bit adventurous.

---

### Post by ambient007 on 2010-04-22
> **yetiman64 said:**
> Microsot uses a centralized "registry" for most settings etc, whereas ubuntu generally uses individual configuration files (quite often in hidden folders/files in your home folder). You shouldn't notice near as much bogging down because of installing-uninstalling with linux.

Also if you have anymore medibuntu access problems, [check here for a fix]("http://ubuntuforums.org/showpost.php?p=9152922&postcount=6"). (Its info from user Morbius1 - that fixed my medibuntu access). 

Have fun with any of the suggested players (I personally use "hand compiled" mplayer from a tutorial by andrew.46 as well as smplayer from a PPA and vlc from the repos, with no problems re bogging down.)

Though be aware that hand compiling from source is best left till you gain a bit more experience with your system if you're new to Ubuntu, but it is a good way to learn a bit about the system if your a bit adventurous.


Cool,

Yea I don't feel confident trying compiling stuff just yet.

Hell, I barely have any idea what I'm doing using the terminal (GUI ftw).

I grew up using windows so I expected there to be a pretty steep learning curve for more in depth stuff with ubuntu. I can see it's potential already though and my 3 and a half year old low range laptop is running a lot better.

:thu:

---

### Post by HarrisonNapper on 2010-04-22
> **ambient007 said:**
> Cool,

Yea I don't feel confident trying compiling stuff just yet.

Hell, I barely have any idea what I'm doing using the terminal (GUI ftw).

I grew up using windows so I expected there to be a pretty steep learning curve for more in depth stuff with ubuntu. I can see it's potential already though and my 3 and a half year old low range laptop is running a lot better.

:thu:

No compiling required in that link. Just some text editing. 

```
sudo gedit /etc/hosts
``` and copy and paste the recommended line to the file

For help with using the terminal, the age old suggestion:

```
man man
```

:)

---

