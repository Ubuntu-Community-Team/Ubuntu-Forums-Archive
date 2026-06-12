---
title: "I'm not sure if I've updated to Ubuntu 8.10"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by projecthikari on 2009-03-27
And, If I have, how would I know?
My computer certainly hasn't gone through any major updates. I want to go to 8.10, so how would I go about doing that? I never figured it out.

---

### Post by drs305 on 2009-03-27
run these commands to learn about your installed system. It provides the version number/release, code name and kernel:
```
lsb_release -a && uname -r
```

---

### Post by rburkartjo on 2009-03-27
drs tks for the useful info

---

### Post by projecthikari on 2009-03-28
I still have 8.04, just as I suspected in the first place.
How do I go about upgrading?

---

### Post by SunnyRabbiera on 2009-03-28
Truth be told if hardy works for you I say stick with it, Intrepid really doesn't offer much in my opinion and is quite unstable.
Is there anything of real value you see in intrepid?
really other then a updated gnome and other apps I personally dont think intrepid is worthy if hardy works for you.

---

### Post by drs305 on 2009-03-28
> **projecthikari said:**
> I still have 8.04, just as I suspected in the first place.
How do I go about upgrading?

If you decide to upgrade, here is the official "how to":
[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

I was pretty happy with Intrepid but have now moved on to Jaunty beta.

---

### Post by sasquatch74 on 2009-03-28
I would agree with the post above, if Hardy works for you, it might be better to stick with it.
However, if you still want to upgrade to 8.10:
Go to System>Administration>Software Sources, then click on the Update tab.  Then look at the bottom where it says,"Release Upgrade."  Select "Normal Releases."  Close the dialog.
Now go to System>Adminstration>Update Manager.  There should now be "New Distribution release '8.10' available."  Click the Upgrade button.  
A dialog will open to upgrade.

---

### Post by projecthikari on 2009-03-28
Are there any cons to upgrading? What about Pros?

---

### Post by SunnyRabbiera on 2009-03-28
For me here are the pros and cons for the common user:

Pros:
More "up to date" software, newer gnome, newer GIMP, newer KDE
Better hardware support with a newer kernel
easier to update to jaunty if desired

Cons:
Unstable at least for me
segmentation faults are waaay too common
offers little improvement in the long run for the average user.

---

### Post by mcduck on 2009-03-28
> **projecthikari said:**
> Are there any cons to upgrading? What about Pros?
Pros: 
- New versions of everything, both the system itself and all available programs which means more features, and also often better performance.

- Support for more hardware, and new devices.

- More support time (you'll *have* to upgrade to some new Ubuntu version, sooner or later).

Cons:
- Some people always have troubles with new Ubuntu versions, or during the update. Of course things work just fine for most of us.

I don't really see any reason to *not* upgrade. If you happen to be very unlucky and the latest version doesn't work for you, you can always reinstall the old one and stay with that until another Ubuntu version is released (or support for your current version ends..).

---

### Post by peakshysteria on 2009-03-28
8.10 is more stable. At least on our housholds machines. Also I guess if you want Jaunty later you first have to upgrade to Intrepid anyway. If you don't want a clean install. My advic is clear. Go for Ubuntu 8.10 Intrepid Ibex. The best Ubuntu for me so far.

---

### Post by Claus7 on 2009-03-28
Hello,

I relied on dapper for three consecutive years. I was pretty pleased and happy. One of the best versions ever for the time it was out. I tried to switch version after everything was working really well to experiment with new libraries and new environment and also be up to date. There were things that I was slightly missing, so I had to see how these changes are working (printer issues e.t.c.). 
Long Term Support versions are really nice and they give you the advantage not to change all the time versions. Now I can see that ubuntu makes big improvements in covering new hardware and be a very descent os. The bad thing is that tweaking is still needed at least in my case. Yet, sooner or later you will cover your needs. 

I would advice you, as I think most users here, to do a fresh install and not an update. Hardy is working nice, yet I miss some things, which should not missing. Even though most of my configurations were untouched after upgrading. In Jaunty I made a fresh install, a lot of things to prepare, yet here I face other problems. 

I like to experiment (in a specific version). The thing is that linux users in my humble experience do not change (easily) version very often. That is because they give a lot of time to adjust the os to their needs, whereas in windows there is not so much freedom to do so. Upgrading keep some things untouched, yet some things might not work as expected. Experiment. See for yourself. There are so many architectures and the problems you might face might be unique for your case. That way you will be able to learn. That is because I said a lot.

My kindest regards!

---

### Post by TheLoneHoot on 2009-04-06
> **drs305 said:**
> run these commands to learn about your installed system. It provides the version number/release, code name and kernel:
```
lsb_release -a && uname -r
```

Okay, I like that - a quick and to-the-point reply... but I can't understand it.  Where does one type in that command?  Is there a program one is supposed to automatically know about, or is there a command prompt window to open?


This is supposed to be "Aboslute Beginner Talk", right?  I'm assuming I must be something along the lines of primative user level.  I have actually had Ubuntu for over a year, but I only use my PC to check my e-mail and surf the web, so I really don't know anything about Linux (in any form).  So I'm trying to figure out what version I have... I THINK it's 8.04 - there are a lot of things hinting at that being the case.  (A lot of what are probably very obvious things to you folks.)  But I don't see anything definitive.  Here's what I know:

- When I type Ubuntu.org, I get a "Welcome to Ubuntu 8.04!" message
- The background of that page has a heron (and I'm sure it's hearty)

and that's about it.  Is there some place I can click and choose "About" to find out what version I have?  Obviously I'm a pathetic Windows user by habit, so I don't know how else to be sure.

I have frequently been told that Ubuntu is the best version (er, "distro" I guess), of Linux for Windows users to transition with...  if that's the case I think I'm probably more suited for a life among the masses of clueless point and clickers.  But as much as people trash talk Windows, at least it's ridiculously easy to use.  I don't mean to complain or illicit any "get lost" replies, but it's extremely frustrating, so please understand the level of ignorance I'm operating with.

I don't need any reassurances or sympathy, just a few words to point me in the right direction.  I'm trying to make sure I'm up to date on things, and I want to make sure I have the right version of Ubuntu.

Sorry for venting.

---

### Post by pbpersson on 2009-04-06
> **TheLoneHoot said:**
> Okay, I like that - a quick and to-the-point reply... but I can't understand it.  Where does one type in that command?  Is there a program one is supposed to automatically know about, or is there a command prompt window to open?


Well.....if your version looks like my version you could get to the command prompt by going to Applications-->Accessories-->Terminal

---

### Post by pbpersson on 2009-04-06
> **TheLoneHoot said:**
> 
I have frequently been told that Ubuntu is the best version (er, "distro" I guess), of Linux for Windows users to transition with...  if that's the case I think I'm probably more suited for a life among the masses of clueless point and clickers.  

Now that you have the command to type to discover the OS version, how would you discover information about your hard drives or your graphics card or your installed printers?

I'll bet you are thinking that you would need to memorize a hundred different command-line things that make no sense to get anything at all accomplished in Ubuntu.

No, in fact you really don't need the command line at all.  People use it as a shortcut to get you the information you want in a hurry.

In Windows if you want to graphically view all the details of your system in one easy-to-use point-and-click window you would go to:
Start-->Programs-->Accessories-->System Tools-->System Information

I have this memorized because I have spent too many years in Windows.

Ubuntu has the very same thing but it is not installed by default.  You can make Ubuntu as easy to use as Windows using graphical applications, so please don't be scared by the command line.

---

### Post by pbpersson on 2009-04-06
> **TheLoneHoot said:**
>  Is there some place I can click and choose "About" to find out what version I have?  Obviously I'm a pathetic Windows user by habit, so I don't know how else to be sure.


In order to make Ubuntu lean and mean, a whole lot of applications are not installed by default.

If you wanted to install something like "System Information" on your computer (and I just tried this on 8.04 so I know it works):

1.  Go to System-->Administration-->Synaptic Package Manger (my favorite)
2.  Search for HardInfo
3.  Install it (along with dependencies)
4.  After installation, go to System-->Preferences-->System Profiler and Benchmark

:)

---

### Post by lhb1142 on 2009-04-07
> **TheLoneHoot said:**
> Okay, I like that - a quick and to-the-point reply... but I can't understand it.  Where does one type in that command?  Is there a program one is supposed to automatically know about, or is there a command prompt window to open?


This is supposed to be "Aboslute Beginner Talk", right?  I'm assuming I must be something along the lines of primative user level.  I have actually had Ubuntu for over a year, but I only use my PC to check my e-mail and surf the web, so I really don't know anything about Linux (in any form).  So I'm trying to figure out what version I have... I THINK it's 8.04 - there are a lot of things hinting at that being the case.  (A lot of what are probably very obvious things to you folks.)  But I don't see anything definitive.  Here's what I know:

- When I type Ubuntu.org, I get a "Welcome to Ubuntu 8.04!" message
- The background of that page has a heron (and I'm sure it's hearty)

and that's about it.  Is there some place I can click and choose "About" to find out what version I have?  Obviously I'm a pathetic Windows user by habit, so I don't know how else to be sure.

I have frequently been told that Ubuntu is the best version (er, "distro" I guess), of Linux for Windows users to transition with...  if that's the case I think I'm probably more suited for a life among the masses of clueless point and clickers.  But as much as people trash talk Windows, at least it's ridiculously easy to use.  I don't mean to complain or illicit any "get lost" replies, but it's extremely frustrating, so please understand the level of ignorance I'm operating with.

I don't need any reassurances or sympathy, just a few words to point me in the right direction.  I'm trying to make sure I'm up to date on things, and I want to make sure I have the right version of Ubuntu.

Sorry for venting.

:KS  Try this: go to Systems->Administration->Software Sources and click on the Third-party Sources tab. In that section, look at the name(s) of the repositories; if they have 'hardy' in their name, you have 8.04; if they have 'intrepid,' you have 8.10. ):P

---

### Post by thraxsa on 2009-04-07
Without learning to use the command line, you really are limiting the potential Ubuntu or Linux in general has to offer.

GUI is great to use by all means, and do a substancial amount of it myself.  

I am far far from being a linux guru, but I have found that experimenting with command line procedures certainly enhances my knowledge.

---

### Post by Claus7 on 2009-04-13
Hello,

> **TheLoneHoot said:**
> Okay, I like that - a quick and to-the-point reply... but I can't understand it.  Where does one type in that command?  Is there a program one is supposed to automatically know about, or is there a command prompt window to open?

If you want to find out about your release of ubuntu without even touching the command line you can simply find out by two clicks away:
System -> About Ubuntu 
and you are almost done (it is written in the third or so line). 

Regards!

---

### Post by TheLoneHoot on 2009-04-14
Thanks to everybody who answered.  I genuinely appreciate all the help.  I have 8.04 as it turns out.

With regard to learning the command line, sure, I'd like to do that sometime, but honestly I just don't have the time or patience at this point.  I work a lot, have a family, and because I'm on a PC all day long at work, I really don't relish the idea of "working" on a computer when I get home.  So for me, and the limited things I need to do, GUI is the way to go.

Nonetheless, I'm sure I'll need to learn to use it some as I run into compatibility issues, etc.  So I'll take your advice and learn to use it, I just can't say it's going to be any time soon. ;)

Claus7, your advice was EXACTLY what I was looking for.  (I could have sworn I had tried that, but I guess I hadn't.)  THANKS A MILLION! :D

---

