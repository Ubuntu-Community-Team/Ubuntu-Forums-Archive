---
title: "Ubiquity's &quot;Install Third-Party Software&quot; == &quot;ubuntu-restricted-extras&quot; Package?"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by Stisfa on 2011-05-01
Long story short, I let these lines scare me away when I initially installed:

"Ubuntu uses third party software to display Flash, MP3 and other media... The software is subject to the license terms included with the software's documentation."

After reading [[COLOR="DarkOrange"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=315886") and [[COLOR="DarkOrange"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=500018"), I now know that there's nothing wrong (legally) with me installing it, it's just so that Canonical doesn't have to pay out the nose to ship Ubuntu with Flash installed by default.

So I now want to install all this material without having to reinstall afresh (trying to avoid 11.04 for now, as I'm still new to 10.10; that and I don't want to reinstall Vim, Chromium, and all the other knick-knacks).  This leads me to the question, does the "Install this third-party software" check box run the command:
```
sudo apt-get install ubuntu-restricted-extras
```
?

I was also wondering, this "ubuntu-restricted-extras" package doesn't include the win32codecs or libdvdcss2, does it?  Nor anything in that vein?

I did read up on [[COLOR="DarkOrange"]"Playing Restricted Formats"[/COLOR]]("https://help.ubuntu.com/community/RestrictedFormats/#Playing Restricted Formats"), but I didn't see anything immediately strike out to me about the details of the package.  Maybe I'm looking in all the wrong places (tried Google, but I must be entering all the wrong search terms).

---

### Post by Quackers on 2011-05-01
I would think there is much more content in the ubuntu-restricted-extras than just Flash and some codecs. Certainly Microsoft fonts are included, for one thing.

---

### Post by Stisfa on 2011-05-01
> **Quackers said:**
> I would think there is much more content in the ubuntu-restricted-extras than just Flash and some codecs. Certainly Microsoft fonts are included, for one thing.

Hmm... [[COLOR="DarkOrange"]looks like it's legal[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1645960") to get those fonts; the more I read into this, it seems that the term "restricted" is more of a misnomer, at least from an end-user's standpoint, although, I guess it is appropriate from Canonical's position.  I did some more reading that lead me to this conclusion (please correct me if I've made a mistake in my analysis).

libdvdcss2 is not included, as brought out on [[COLOR="DarkOrange"]Maverick Meerkat's restricted packages page.[/COLOR]]("http://packages.ubuntu.com/maverick/ubuntu-restricted-extras")

I also read up on the [[COLOR="DarkOrange"]Licensing Page[/COLOR]]("http://www.ubuntu.com/project/about-ubuntu/licensing"), and the **"Ubuntu 'main' and 'restricted' component license policy"** subheading brings out several points that I *think* address my concerns.
[LIST]
[*]Must not require royalty payments or any other fee for redistribution or modification.It's important that you can exercise your rights to this software without having to pay for the privilege, and that you can pass these rights on to other people on exactly the same basis.
[*]Must not discriminate against persons, groups or against fields of endeavour. The licence of software included in Ubuntu can not discriminate against anyone or any group of users and cannot restrict users from using the software for a particular field of endeavour - a business for example. So we will not distribute software that is licensed "freely for non-commercial use".
[/LIST]

There's more under that subheading, but I *think* those I listed address my paranoia with the term "restricted" (again, I could be wrong, as I'm still a major n00b - any affirmation would be most appreciated =^D).

P.S. If the "ubuntu-restricted-extras" package isn't the match for Ubiquity's installation of third-party software, what is the correct invocation?  I'd take a look at the source code, but I'd be overwhelmed in trying to figure out the navigation to the correct file alone, lol.  Sorry for my lack in capability :redface:.

---

### Post by K_45 on 2011-05-01
What are you trying to do? That package may contain stuff you do not need or want, so do you want Flash, mp3 support . . . ?

---

### Post by Stisfa on 2011-05-01
> **K_45 said:**
> What are you trying to do? That package may contain stuff you do not need or want, so do you want Flash, mp3 support . . . ?

Flash and MP3 playback are part of the goal, but the greater part of this is to know what command(s) Ubiquity calls when the "Install Third-Party Software" checkbox is ticked at the time of install.

This has extended into an inquiry as to what "restricted" software/packages means for me, the end user, in it's legal aspect.  To put it plainly, **I want to get something done and learn about the fundamental reasons *why* I'm instructed to do it the way the [Ubuntu Documentation]("https://help.ubuntu.com/community/RestrictedFormats/") has directed.**

Here's another way to put it: why am I using the "restricted" post-install instructions listed in the Documentation versus Medibuntu?  Medibuntu readily acknowledges that it's "breaking" rules, but the material I've read on "ubuntu-restricted-extras" seems to indicate that I'm not at risk of a legal breach when installing the package, the only things to worry about are reading the EULAs for the individual components prior to install (as is usual for most software packages).  My current research has lead me to believe that Canonical can not, by default, include these "restricted" packages with their distribution of Ubuntu, lest licensing costs be passed from Canonical to the end-user, despite the fact that they are **free and legal** for the end-user to install in the USA.  I just need some feedback as to whether my assessment is accurate or skewed.

So to break it down:
[LIST=1]
[*]Does Ubiquity's "Install Third-Party Software" Check Box == "sudo apt-get install ubuntu-restricted-extras"?  If not, what does Ubiquity do?
[*]What does "restricted" formats/packages/software mean to the stupid end-user, alias Stisfa (in plain English, please)?
[/LIST]

Quackers answered the first part of Question 1, but I'm still curious as to the second part.  Question 2 is more pertinent to me, at least in this current hour (be careful, I'm sleep depraved - in fact, I believe there was a 3rd Question, but I'm too exhausted to muster up any more mental resources to retain or advance any further thought, so you'll have to forgive me for being somewhat disjointed).

That about sums it up, unless there's another factor that I've neglected in this discussion?

---

### Post by K_45 on 2011-05-01
No 2 means that there are certain formats restricted to end users because of licensing concerns. To install what you want I'd:

```
sudo apt-get install gstreamer0.10-fluendo-mp3
```

```
sudo apt-get install flashplugin-nonfree
```

If Flash is still screwing around, install FLashAid, which is a FIrefox extension that should fix you up.

---

### Post by Stisfa on 2011-05-04
> **K_45 said:**
> ```
sudo apt-get install flashplugin-nonfree
```
 
Slight clarification for installing Flash on Ubuntu:

[[COLOR=DarkOrange]For 9.04 and Later[/COLOR]]("https://help.ubuntu.com/community/RestrictedFormats/Flash#Ubuntu%209.04%20%28Jaunty%20Jackalope%29%20and%20later") (10.10 in My Case)
```
sudo apt-get install flashplugin-installer
```[[COLOR=DarkOrange]For 8.04 LTS[/COLOR]]("https://help.ubuntu.com/community/RestrictedFormats/Flash#Ubuntu%208.04%20LTS%20%28Hardy%20Heron%29")
```
sudo apt-get install flashplugin-nonfree
```It took me awhile to figure out the difference between the "flashplugin-installer" package vs the "flashplugin-nonfree" package; it's just a difference of which version of Ubuntu you're using, apparently.  I didn't realize this fully until I read the properties on the package, which brought out that it was designated to replace the "flashplugin-nonfree" package, at least in 10.10.

> **K_45 said:**
> No 2 means that there are certain formats restricted to end users because of licensing concerns.

This was far too ambiguous for my liking, especially since it was basically a paraphrase of the "RestrictedFormats" page in the Official Ubuntu Documentation, so I did some more research in this manner and found that this is a topic can't help but be obfuscated!

To illustrate, the threads listed below don't really clarify much, rather, they seem to further cloud what is and isn't legally appropriate in the USA:
[[COLOR=DarkOrange]ubuntu-restricted-extras legal?[/COLOR]]("http://ubuntuforums.org/showthread.php?t=607112")
[[COLOR=DarkOrange]Are Ubuntu restricted extras legal in the USA?[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1363643")
[[COLOR=DarkOrange]Microsoft Fonts in Restricted Extras[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1645960")

After reading through these, I really can't tell if the "ubuntu-restricted-extras" package is legally *gratis* (as you can tell, I'm not too concerned about the packages being *libre*; don't get me wrong, I prefer transparency of code, but it doesn't supersede my desire for a $0 OS - I know, I'm cheap).  The first two threads show varying differences of opinions, the third one seems pretty straight-forward.  It was the third thread that lead me to believe that the whole package is just a matter of reading EULAs and conforming to them, even though they're free software.  The first two threads undermined that belief, so I'm left to assume that this is another topic that's encumbered by a legal quagmire.  Oh well, at least I don't have to worry too much about the Fonts :P.

---

### Post by Stisfa on 2011-05-04
> **Stisfa said:**
> 
I also read up on the [[COLOR=DarkOrange]Licensing Page[/COLOR]]("http://www.ubuntu.com/project/about-ubuntu/licensing"), and the **"Ubuntu 'main' and 'restricted' component license policy"** subheading brings out several points that I *think* address my concerns.
[LIST]
[*]Must not require royalty payments or any other fee for redistribution or modification.It's important that you can exercise your rights to this software without having to pay for the privilege, and that you can pass these rights on to other people on exactly the same basis.
[*]Must not discriminate against persons, groups or against fields of endeavour. The licence of software included in Ubuntu can not discriminate against anyone or any group of users and cannot restrict users from using the software for a particular field of endeavour - a business for example. So we will not distribute software that is licensed "freely for non-commercial use".
[/LIST]

There's more under that subheading, but I *think* those I listed address my paranoia with the term "restricted" (again, I could be wrong, as I'm still a major n00b - any affirmation would be most appreciated =^D).

Looks like I need to correct this:
Under the subheading "**Categories of software in Ubuntu**" on the [[COLOR=DarkOrange]Licensing page[/COLOR]]("http://www.ubuntu.com/project/about-ubuntu/licensing"), it states this: 

"The thousands of software packages available for Ubuntu are organised  into four key groups or components: main, restricted, universe and  multiverse. Software is published in one of these components based on  whether or not it meets our free software philosophy, and the level of  support we can provide for it.
 
**   This policy only addresses the software that you will find in main  and restricted**, which contain software that is fully supported by the  Ubuntu team and must comply with this policy."

The [[COLOR=DarkOrange]package's page[/COLOR]]("http://packages.ubuntu.com/maverick/ubuntu-restricted-extras") clearly shows, at the top, that it's in the Multiverse repository, which means that it is [[COLOR=DarkOrange]classified as "software that is not free"[/COLOR]]("https://help.ubuntu.com/community/Repositories/Ubuntu#What%20are%20Repositories?") or [[COLOR=DarkOrange]"software restricted by copyright or legal issues"[/COLOR]]("https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Ubuntu%20Software%20Repositories").  I guess this is where I got caught up; the software in the Multiverse repository can be either priced or unpriced, such as unrar (which starts out as a trial license that will lead to a paid license, if memory serves correctly), but that's not the main reason why it's in the Multiverse repository, it's there because the software packaged within can't be freely distributed, hacked, improved, and customized without breaking the license terms.  Please correct me if I'm wrong (ugh, it's unfortunate that [[COLOR=DarkOrange]the English word "free" can be loosely applied to the concept of both *libre* and *gratis*[/COLOR]]("http://en.wikipedia.org/wiki/Gratis_versus_libre")).

---

### Post by beew on 2011-05-04
If you are worried about legality then don't use them. It doesn't bother me the least bit.

---

### Post by Stisfa on 2011-05-04
> **beew said:**
> If you are worried about legality then don't use them. It doesn't bother me the least bit.

That's why I haven't installed them yet and that's exactly why I opened this thread to gain more insight into this; unfortunately, as all things legal are, unreasonable amounts of resources have to be poured in to get any semblance of a legible answer to one's specific inquiry :P.

If somebody could tell me what packages Ubiquity brings in when checking the "Install Third-Party Software" checkbox, I'd be up to researching the legality/EULA behind the individual packages on my own.  Since we've established it's not the same thing as the "ubuntu-restricted-extras", I'm not going to go through each sub-package in that package.

Basically, in line with K_45's thoughts, I'm only going to select the packages that I need amidst what Ubiquity's brings in at install time.

---

### Post by fremantle on 2011-05-04
If you just want to play mp3 files, gstreamer plugin should be good for you. But if you want to play xvid, avi files, watch divx videos online and play different kind of media files, you should go with restricted-extras. however, it also installs java and flash.

i my self just like to install mp3 plugin, gecko-mediaplayer, mplayer and vlc media player. and also flash. i dont need java that much or play dvds, so res-extras is pointless to me.

ps: ubuntu's install thrid party codecs is not restricted-extras.

---

### Post by fremantle on 2011-05-04
i myself really dont care about legality when it comes to using plugins for my computer. theres more important legal things to worry about in this world, like getting rid of terrorism.

---

### Post by Stisfa on 2011-05-04
> **fremantle said:**
> i myself really dont care about legality when it comes to using plugins for my computer. theres more important legal things to worry about in this world, like getting rid of terrorism.

Mmm, I'm not going to get into an ethical and legal discussion about Terrorism, but I do know that joking "I'm going to bomb xyz" can land you in prison, even though you had no real intention to do that (it happened to a truck driver in my area, all but a few weeks ago).  Regardless of this, I'm an individual that does his best to respect all laws, even if they are [[COLOR=DarkOrange]unreasonable, facetious, and petty[/COLOR]]("http://www.dumblaws.com/"); well, up to a certain point, but I'll not get into that :).

I've already taken care of my Flash needs and will soon take care of my MP3 needs, but I still want to **learn **what's behind Ubiquity's installer.  A moment less ignorant is a moment more informed.

Really, I was hoping somebody who's already had their hands in the code (maintainer/co-maintainer) or somebody who knows the maintainer would be able to provide a list of the packages, but it looks like I'll need to pursue my answer by going directly to [[COLOR=DarkOrange]the source[/COLOR]]("https://wiki.ubuntu.com/Ubiquity"). Once I get my answer, I'll post the list of packages and mark this thread solved once I get my answer; thanks for all the feedback everyone ):P

---

