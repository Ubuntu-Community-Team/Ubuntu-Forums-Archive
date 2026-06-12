---
title: "How do I uninstall ATI Catalyst Driver?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by bamend on 2009-01-31
I just installed the catalyst driver from ATI and now I can't boot up my computer.  It tries to boot up in low graphics mode and then just dies.  How can I uninstall the catalyst driver and go back to what I had?

---

### Post by balcis on 2009-04-09
> **bamend said:**
> I just installed the catalyst driver from ATI and now I can't boot up my computer.  It tries to boot up in low graphics mode and then just dies.  How can I uninstall the catalyst driver and go back to what I had?

try to backup and then remove xorg.conf in /etc/X11/ directory. you can do it by booting up from livecd etc. try this.

---

### Post by markbuntu on 2009-04-09
There is directions for uninstalling the driver in the installation instructions and/or release notes at the page you got the driver from.

People should really read those things.

---

### Post by Scott M. Sanders on 2009-04-28
> **markbuntu said:**
> There is directions for uninstalling the driver in the installation instructions and/or release notes at the page you got the driver from.

People should really read those things.
You know what, I had the exact same problem, Windows was never as difficult, and your response was completely false and unhelpful.

Anyway, boot Ubuntu in recovery mode, drop to terminal, login to root, and type in "aptitude." This will give you a text-based package manager like the Synaptic GUI. From here, the offending ATI packages can be found and removed from under Misc. Press ? for help. This should ultimately get you back; it did me anyway after days of guessing. Reply with any questions.

---

### Post by rcayea on 2009-04-28
Hopefully this helps:

With super user permissions, enter the command "sh./fglrx-uninstall.sh

R.

---

### Post by asuastrophysics on 2009-04-28
> **markbuntu said:**
> There is directions for uninstalling the driver in the installation instructions and/or release notes at the page you got the driver from.

People should really read those things.

it's really hard to do that when you have no display. 

so what you're saying is, unless there's an uninstall script, i'm screwed.

i really hate ATI. 

btw. there is another way of doing it, i'm just not 100% sure if this is right

sudo apt-get remove --purge all fglrx-xorg-xserver

or something like that.

---

### Post by asuastrophysics on 2009-04-28
> **Scott M. Sanders said:**
> You know what, I had the exact same problem, Windows was never as difficult, and your response was completely false and unhelpful.

Anyway, boot Ubuntu in recovery mode, drop to terminal, login to root, and type in "aptitude." This will give you a text-based package manager like the Synaptic GUI. From here, the offending ATI packages can be found and removed from under Misc. Press ? for help. This should ultimately get you back; it did me anyway after days of guessing. Reply with any questions.

thank you so much, that really helped me :popcorn:
your answer was straight and to the point, and it worked. 

just so everyone knows, DO NOT try to install ATI catalyst 9.4. you will be disappointed.

---

### Post by markbuntu on 2009-04-29
> **Scott M. Sanders said:**
> You know what, I had the exact same problem, Windows was never as difficult, and your response was completely false and unhelpful.

Anyway, boot Ubuntu in recovery mode, drop to terminal, login to root, and type in "aptitude." This will give you a text-based package manager like the Synaptic GUI. From here, the offending ATI packages can be found and removed from under Misc. Press ? for help. This should ultimately get you back; it did me anyway after days of guessing. Reply with any questions.

This is taken directly from the driver installer instructions at the ati web site:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)


> 

Note: ATI recommends you uninstall the ATI Proprietary Linux
Driver before installing a newer version.

......

1 Launch the Terminal Application/Window and navigate to the /usr/share/ati
     folder
2 With superuser permissions, enter the command "sh ./fglrx-uninstall.sh"
You have now successfully uninstalled the ATI Linux Proprietary Driver.



Failure to read the release notes and installer instructions does not constitute false and unhelpful information or any failure by ati or linux or ubuntu but it does show that many people have never bothered to even read these things and so are also unaware of other important information that may prove helpful and instead clog up the forums with questions that they do not need to ask if they would have taken a few minutes and read these things.

---

### Post by thelonelysoulX9 on 2009-05-01
Why some people are so mean. Just answer a question does not take much time. Well, if you said it is wasting your time then why you still spend time on replying it.
We don't know that why we ask. That's why the forum is built for. Check your dictionary ! :p :lolflag:

---

### Post by Biohmmwv on 2009-05-02
Thanks for the help. The dangers of this program were not listed in the add/remove menu.

---

### Post by astriemer on 2009-06-22
That worked perfectly for the uninstall, thanks for the tip!

I agree with Biohmmwv and wonder why it would be included in the add/remove listing if it seems to be so crippling to some users.

I'm a newbie to linux and ubuntu but am an experienced windows guru and I'd much rather have not had the package listed in the add/remove and had to go to the manufacturer's website to get the drivers and program so that I'd be more inclined to read the warnings and disclaimers as markbuntu suggested.

Anyway, thanks for the instructions on removing the offending drivers once the gui display stopped working.

---

### Post by raymondvillain on 2009-06-22
You folks are fantastic!

Many thanks, this helped me in a BIG way.

---

### Post by ripley609 on 2009-06-28
Thanx a million. Got stuck with a messed up screen after installing ati catalyst. A quick search with my other machine, and the answer popped right up

/rip

---

### Post by agst on 2009-07-27
damn...I wish I'd seen this earlier.  I had to reinstall ubuntu 9.04 after I added that application from the add/remove programs menu.  And I totally agree with Astreimer!
 
After reinstalling I added this and again it messed things up.  I will now try this.  Thanks!

---

### Post by BillybobT on 2009-08-13
> **markbuntu said:**
> This is taken directly from the driver installer instructions at the ati web site:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)




Failure to read the release notes and installer instructions does not constitute false and unhelpful information or any failure by ati or linux or ubuntu but it does show that many people have never bothered to even read these things and so are also unaware of other important information that may prove helpful and instead clog up the forums with questions that they do not need to ask if they would have taken a few minutes and read these things.


I made the mistake of installing the Catalyst drivers using either the synaptics package manger or add applications. Unfortunately, there are no release notes to read, and after rebooting, I too had a completely unusable Jaunty. Thanks Scott, for your concise, easy to use info on how to recover from what I thought was a hopeless situation.

---

### Post by QIII on 2009-08-13
> **asuastrophysics said:**
> 
just so everyone knows, DO NOT try to install ATI catalyst 9.4. you will be disappointed.

I've used Catalyst on my machine with an ATI card for quite some time without the slightest difficulty.

While it is clear that you had issues, which is terribly unfortunate and very frustrating for you, it is not true that all will be disappointed.

You have chosen a sample size of 1 on which to base a representation of a very large population.  What you have not seen, because it is invisible, is the sampling of the population where all went well.  People do not come to forums for help when things go right.

That being said, I hope that you will not abandon Catalyst outright, because it gives you some tools which can be very helpful.

It is NOT helpful for people on a forum to blurt out "RTFM" dismissively, and for that I apologize on behalf of the forum community.

This should be a place where people can come for help and answers, not disparaging remarks.

---

### Post by Mark Phelps on 2009-08-14
> **QIII said:**
> I've used Catalyst on my machine with an ATI card for quite some time without the slightest difficulty.
 Same here, in fact, since 7.04 -- which came to a sudden halt with 9.04, since I'm one of the hundreds of folks that has one of those "legacy" (read that, 3-years old) cards.
> 
That being said, I hope that you will not abandon Catalyst outright, because it gives you some tools which can be very helpful.
Ironically, I'm NOT abandoning Catalyst -- at least, not on my MS Windows installs.  Catalyst 9.3 not only works just fine in Vista, it also CONTINUES to work just fine in Windows 7 -- due to Win 7 compatibility mode.  It's only Ubuntu 9.04 and newer in which Catalyst does not work for me. I'm not pointing the finger her, but of the three OS environments I use daily, Ubuntu is the only one that has forced me to abandon the use of Catalyst.

> This should be a place where people can come for help and answers, not disparaging remarks.

Agree ... but the situation would be vastly improved if there was a tutorial that we could simply point to, preferably one in the tutorials subforum, that provided step-by-step instructions for folks who unfortunately forced the installation of the fglrx driver on their machine.

But, as has been said before, with power comes responsibility.  While the power of being able to do nearly anything you want in Linux is awesome at times, it also carries the risk that you can completely trash your installation -- if (1) you don't know what you're doing, and (2) you're either too lazy or stupid to check first.

And, I think the latter is becoming an increasing problem in our "community".  We started out as a bunch of geeks (and some of us are still that), but as time goes on, we get more and more of the one-click-solution folks.  So, the old adage of "check first, then do" may need to be replaced with more controls in place to PREVENT folks from damaging their systems.  

Thus, it would be good if BOTH the envy program and the ATI installer would first verify that the video chip/card version and the XServer version were compatible -- before installing the driver.  I think that might have saved nearly ALL the folks from trashing their displays.  But, I haven't read or seen anything happening along these lines.

---

### Post by AstroPhysik on 2009-08-22
[php] Anyway, boot Ubuntu in recovery mode, drop to terminal, login to root, and type in "aptitude." This will give you a text-based package manager like the Synaptic GUI. From here, the offending ATI packages can be found and removed from under Misc. Press ? for help. This should ultimately get you back; it did me anyway after days of guessing. Reply with any questions.[/quote]
[/php]
[Scott M. Sanders]("http://ubuntuforums.org/member.php?u=652364")
Thank you so much, i had exact the same problem.
I've read  [http://wiki.ubuntuusers.de/Grafikkarten/ATI](http://wiki.ubuntuusers.de/Grafikkarten/ATI)   so i wanted to install the ATI Catalyst Control Center first, with hopes to see further information without changing anything. But it installed the fglrx drivers and the screen went black...


 thanx a lot, AstroPhysik!!!  :popcorn:

---

### Post by mayur_rathi90 on 2010-02-21
sh./fglrx-uninstall.sh
this command is not working it says
 bash: sh./fglrx-uninstall.sh: No such file or directory

---

### Post by mayur_rathi90 on 2010-02-21
go to this page 
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
and follow the instructions provided there for removing the drivers
and you will actually love it it worked for me

---

### Post by halitech on 2010-02-21
> **mayur_rathi90 said:**
> sh./fglrx-uninstall.sh
this command is not working it says
 bash: sh./fglrx-uninstall.sh: No such file or directory

you need to cd to /etc/ati before running the command or it won't find the script. I just upgraded to the latest Catalyst (10.4 I believe) and it works fine as long as you have a supported card (HD2400 or better) after uninstalling the old version of Catalyst.


One of the main problems I see is that everyone says install the ATI drivers without asking what card people have or what version they are running. This is what leads to systems getting borked, not the driver itself so we need to start asking people the right questions before giving advice.

---

### Post by vinan on 2010-03-18
if you have a onboard vga, 
remove PCI video card and boot up.
synaptic->Installed-> find the pkg.->fglrx-amdccle and complete remove

all done

hopes it will be usefull

cheers

---

### Post by bcooperb on 2010-06-21
@mayur_rathi90

did you make sure you are in the directory where the file is located?

Also you'll need to run it as SuperUser

***sudo sh ./FileToInstall.run***

---

### Post by a_flj_ on 2012-02-02
> **markbuntu said:**
> Failure to read the release notes and installer instructions does not constitute false and unhelpful information or any failure by ati or linux or ubuntu ... .

Excluse me please for putting it that bluntly, but you're gratuitously a smartass.

I had a similar problem with uninstalling, and I *knew* what I had to do, since I did it repeatedly in the past. Only, after an upgrade from lucid to maverick the ATI uninstall script was gone, so the instructions provided by ATI were useless.

Your way of answering questions assumes you know everything that happens on someone else's computer. Which may at least occasionally not be the case.

THe only advice that helped was to use aptitude in a console - for some reason kubuntu's default package manager doesn't find the packages to be uninstalled, and synaptic was no longer in the start menu after the upgrade (although I just discovered it's still installed).

Posting this only so googling for "maverick luxid ati driver fglrx uninstall" (which is what I did) should find this solution.

---

