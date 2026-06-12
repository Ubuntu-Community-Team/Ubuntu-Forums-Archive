---
title: "upgrading"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by manners2345 on 2009-11-16
Last Saturday I noticed that open office 3.1 was in karmic kola,I use open office all the time.
 
  I tried to upgrade to it, which meant I had to do intrepid,then jaunty, then karmic,instead of being able to do directly to karmic kola when tried to install, got message not enough space on hard drive,delete some stuff, so I did, emptied trash and a bunch of other stuff, when finished still not ENOUGH space.
 
  So I went to synaptic and looked at was installed, never ever use Perl,Python and some other stuff.  when I started to do all those packages, I had 4gb on a 10 gig hard drive.
  Turns out Perl and python and some other stuff are system things!!!

  Also turns out ubuntu is not id10t proof,  read as idiot:D
  I was also told last Saturday that ubuntu assumes you know what you are doing. We know what assume spells RIGHT!!!

 Before I started this adventure I setup a ROOT password, just to be safer.

  FIRST ?? HOW DO I GET COMMAND LINE TO GO PAGE BY PAGE INSTEAD OF ALL AT ONCE TRIED /P, \P BEFORE COMMAND EXECUTION, NO JOY

  SECOND?? LOG IN AS ROOT, TYPE apt-get install jaunty, RESPONSE, could not find package jaunty. TYPE apt-get install karmic, same response as above.

 WHAT DO I DO NOW;):) NOW????:confused::confused::confused::confused::confused:

---

### Post by dillandriskell on 2009-11-16
Hmm...I'm not sure how much I can help with upgrading.  I always fresh install from a boot disk.

However, as far as this goes;

> **manners2345 said:**
> HOW DO I GET COMMAND LINE TO GO PAGE BY PAGE INSTEAD OF ALL AT ONCE TRIED /P, \P BEFORE COMMAND EXECUTION, NO JOY

Do you mean how do you make a page scrollable so you can see everything rather than just the bottom?  If so I believe the command you're looking for is less.  Like this;

```
less <document you're trying to view>
```just make sure you're in the right directory, or that you provide the location with the document name.

---

### Post by Merk42 on 2009-11-16
> **manners2345 said:**
> Last Saturday I noticed that open office 3.1 was in karmic kola,I use open office all the time.
 
  I tried to upgrade to it, which meant I had to do intrepid,then jaunty, then karmic,instead of being able to do directly to karmic kola when tried to install, got message not enough space on hard drive,delete some stuff, so I did, emptied trash and a bunch of other stuff, when finished still not ENOUGH space.
 
  So I went to synaptic and looked at was installed, never ever use Perl,Python and some other stuff.  when I started to do all those packages, I had 4gb on a 10 gig hard drive.
  Turns out Perl and python and some other stuff are system things!!!

  Also turns out ubuntu is not id10t proof,  read as idiot:D
  I was also told last Saturday that ubuntu assumes you know what you are doing. We know what assume spells RIGHT!!!

 Before I started this adventure I setup a ROOT password, just to be safer.

  FIRST ?? HOW DO I GET COMMAND LINE TO GO PAGE BY PAGE INSTEAD OF ALL AT ONCE TRIED /P, \P BEFORE COMMAND EXECUTION, NO JOY

  SECOND?? LOG IN AS ROOT, TYPE apt-get install jaunty, RESPONSE, could not find package jaunty. TYPE apt-get install karmic, same response as above.

 WHAT DO I DO NOW;):) NOW????:confused::confused::confused::confused::confused:

What is it you even want to do?
If you want to get OpenOffice for Hardy Heron you can do that by following [These Instructions](http://ubuntumanual.org/posts/175/upgrade-to-open-office-3-1-in-ubuntu-jaunty-intrepid-hardy)

---

### Post by Sealbhach on 2009-11-16
Hold on there... You want to get the latest Open Office? All you have to do, without changing anything else on your system, is to add the Open Office PPA to your software sources.

There's a how-to here: [http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

And if you want to upgrade your version of Ubuntu, I would recommend using a CD or a USB stick, upgrading over the internet usually does not work as well as it should.

.

---

### Post by cariboo on 2009-11-16
The first thing you need to do is disable the root account:

```
sudo usermod -p '!' root
```

The reason I say this is, right now with your knowledge level you are just plain dangerous to your self. Once you become more familiar with Ubuntu you can enable the root if you want.

Next make sure the version you are using is fully up-to-date, make sure you have any third party repositories and ppa's, disabled. Go to System-->Administration-->Software Sources and uncheck them.

Once you have done the above press Alt-F2 and type:

```
gksudo update-manager -d
```

This will will start the update process for you. Like you said you will have to upgrade from Hardy-->Intrepid-->Jaunty-->Karmic. It may be easier if you have a seperate /home partition to do a clean install.

---

### Post by manners2345 on 2009-11-16
Get some version of ubuntu back

---

### Post by manners2345 on 2009-11-16
right now running new computer, duo core, with 500gb hdd, windows vista, 19" monitor as opposed to  my R40 laptop with 10gb hdd

---

### Post by manners2345 on 2009-11-16
right now all I have is command line, no system as such

---

### Post by Sealbhach on 2009-11-17
> **manners2345 said:**
> right now all I have is command line, no system as such

OK, at the command line, re-install the desktop:

```

sudo apt-get install ubuntu-desktop

```Then to start the desktop:

```
sudo /etc/init.d/gdm start
```

or 
```

sudo reboot
```
.

---

### Post by manners2345 on 2009-11-17
Thank you many times over and over, doing first instruction now,downloading,100 some mb, i think it is jaunty

---

### Post by manners2345 on 2009-11-17
STILL DOWNLOADING, SAYS ABOUT ANOTHER 35 MINUTES, LOOKING AT WHAT IS EVERYTHING I SEE SAYS JAUNTY:popcorn::popcorn:

---

### Post by fromthehill on 2009-11-17
[IMG]http://www.352media.com/rantingandraving/CMFiles/Images/CapsLock.jpg[/IMG]

---

### Post by slakkie on 2009-11-17
See my sig for a HOWTO on upgrading Ubuntu.

---

### Post by manners2345 on 2009-11-17
JUST DID  sudo reboot, there is much joy in mudville, MIGHTY SEALBHACH HIT A GRAND SLAM HOMER!!!!


THANK YOU
MANNERS2345

---

