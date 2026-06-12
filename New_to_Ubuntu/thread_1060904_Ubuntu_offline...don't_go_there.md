---
title: "Ubuntu offline...don't go there"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by longtom on 2009-02-05
I am afraid I am learning the hard way, tha Ubuntu is a system which doesn't work well at all on offline machines.  

Don't get me wrong, it's a nice little OS out of the box (from the cd), but as soon as you get to upgrading or installing an additional program, you are buggered.

Every program I installed on this machine was getting additional downloads from somewhere.  The last one was VirtualBox, which I'm busy installing (well, trying to) as I write.  After I downloaded the allocated deb file and started the installation, I considerable download followed before the installation was finished.  

And so it appears to be the case with all installations.  Now - I would have liked to get Ubuntu out there into areas, where online is not a given and won't be for quite some time...

Is there a chance I can "compile from source" (whatever that means) and be more successful?  Given my success with normal deb installs and actually get it going, I'm busy losing heart....

Not a huge fan of MS, I still believe the system of downloading a complete program and install it anywhere, on- or offline, would work better for me...

I was kind of hoping, with somebody like Mark Shuttleworth connected to the project, the problematic in Africa would be more considered.

I probably had the wrong expectations and it is just expected that everybody has an uncapped 4000 connection and of you go....

Oh, I'm still having fun with Ubuntu here on my online machine...but the reason I started out to get into this was not fun alone...it is now for the time being.

Thank you for all your help so far - more simple questions will be coming up...shortly.

longtom

---

### Post by wilbbe01 on 2009-02-05
You could download .deb files and install them manually if that is what you really wanted.  There are instructions out there to build your own repositories on say an external hard disk which you could move to the computer when you needed to install something.  I do have a question for you though...if you don't download the applications from the internet how else do you expect to get them?  With any operating system you need to either go buy the software at a store, order it in the mail, or download it.  I'm not sure I'm seeing where that makes Ubuntu unworthy of being used somewhere where an internet connection is not readily available.  You need to get the software somewhere, and I think in 99% of cases it is faster for someone to download software from the internet than it is to drive to a store or wait for the mail (even if that internet connection is not right where the computer sits.)

---

### Post by longtom on 2009-02-05
> **wilbbe01 said:**
>  I do have a question for you though...if you don't download the applications from the internet how else do you expect to get them?  With any operating system you need to either go buy the software at a store, order it in the mail, or download it.  I'm not sure I'm seeing where that makes Ubuntu unworthy of being used somewhere where an internet connection is not readily available.  You need to get the software somewhere, and I think in 99% of cases it is faster for someone to download software from the internet than it is to drive to a store or wait for the mail (even if that internet connection is not right where the computer sits.)

I assumed that the original idea was to get the open source software and distribute it.  Now, that's what I wanted to do:  

Dl additional software and distribute it (on a cd, dvd, whatever) and have it installed somewhere, where PCs are offline.

>  think in 99% of cases it is faster for someone to download software from the internet

well - if you have internet available, which appears to be a concept not well understood in so called developped countries.

longtom

---

### Post by Flimm on 2009-02-05
Compiling from source is not the solution. You would need more software just to compile source code, such as make.
Here's a tip, open synaptic manager, tick the packages you want to install, and then click File, Generate package download script. You can take that script to a linux computer with an Internet connection and get all the .deb packages that way.
You might also want to consider [APTonCD](http://aptoncd.sourceforge.net/). It lets you create a small repository on a CD with all the .debs on them, for Ubuntu or Debian.
You might want to vote on this idea too:
[[IMG]http://brainstorm.ubuntu.com/idea/13/image/2/[/IMG]](http://brainstorm.ubuntu.com/idea/13/)

---

### Post by kansasnoob on 2009-02-05
I've used "aptoncd" (Apt on CD) which is available in Synaptic to create an installation CD for machines that are still on dial-up.

Here's Synaptics brief description:

> Installation disc creator for packages downloaded via APT
APT removable repository creator and package backup tool for Debian based
systems.

This tool will allow you to create a media (CD or DVD) to use to install
software via APT in a non-connected machine, as well upgrade and install
the same set of softwares in several machines with no need to re-download
the packages again.

For more information, visit [http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)

---

### Post by longtom on 2009-02-05
Thank you everybody for your tips.

I'll attempt to get my head arround APTonCD.

Will advise about success and will certainly shout, when and if failure is imminent...:p

longtom

Edit:  Once reading through the manual, this might actually work.  Thank you again....

---

### Post by carml on 2009-02-05
Of course the machine where you install APTonCD should have (a Debian distro as prerequisite), a fast internet connection.:)

---

### Post by Kellemora on 2009-02-05
Hi Longtom

I used to do some overseas missionary work a number of years ago!
But still after the internet was popular, so most installs required an internet connection to get drivers and updates, etc.

Because we were going into areas that had no phones at all, and few even had electric.  We had to pack with us two sets of 134 floppies each, to insure we could install the programs, drivers and upgrades for all of the old systems we would encounter.

All I'm saying is it could be done, but was a royal pain without an internet connection.

Today it's much easier as you just need to build a repository to carry with you.  But one thing I have not figured out yet is how to activate some programs that require on-line activation!  Most places still use The Doze, and we have to comply with what THEY use, not what we prefer, hi hi..........

TTUL
Gary

---

### Post by steveneddy on 2009-02-05
Just make or buy an Ubuntu Repo DVD and you are all set.

[http://ubuntuforums.org/showthread.php?t=352460](http://ubuntuforums.org/showthread.php?t=352460)

---

### Post by shauvik on 2009-02-05
Another way would be to get the repo on a USB.
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

Or if there is an online server on the network; one could setup a proxy or a mirror there:
[http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror](http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror)

---

### Post by longtom on 2009-02-06
Thank you so much for all your tips.

The philsophy is still ... foreign to me though.  You need at least one "mother machine" with a decent connection.  Going into town, see an Internet Cafe and get what you need, is not an option.  Since the theory is to learn people to fish and not just give them fish, this is not ideal.  They will always be dependent on me (or somebody) to send or bring them updates, programs etc.  Kellemora knows what I'm talking abaout.  
Getting 40GB or even "only" 5 DVDs of Repository is not an option really, since any halfway affordable dsl is capped.

APTonCD appears to be the interim solution for me.  Here I can choose the programs I want from my "mother machine", put them on a cd and go.  I have put them on a cd and will run a test tonight on a fresh 8.10 offline installation.  If this works, that will be the way I'll be going for the time being.

I just wish I could print all your tips on a printer commected to a WinXP simple network.  I can see the machine, can't see the attached and shared printer so.  see also here:

[http://ubuntuforums.org/showthread.php?t=1058720](http://ubuntuforums.org/showthread.php?t=1058720)

If that is working and the WinXP machines can see my Ubuntu machine (which they can't because my machine refuses to share folders...), I am a huge step closer to achieving what I set out to do.  
However, this appears to be a more complicated matter considering my extreme small knowledge and experience with Linux in general and Ubuntu in particular.

If anybody has any tips, which might even be understood by me, answers on a postcard....or maybe rather here...:p

greetings

longtom

---

### Post by igknighted on 2009-02-06
If you have an Ubuntu system online, simply use the command 'apt-get -d <packagename>' to download the packages you need and all dependencies.  Should solve those dependency problems you are having.

---

