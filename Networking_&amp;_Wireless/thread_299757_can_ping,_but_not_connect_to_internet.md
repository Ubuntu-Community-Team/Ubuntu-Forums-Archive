---
title: "can ping, but not connect to internet"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by UpsideDownFace on 2006-11-14
I have an IBM R50e laptop with only ubuntu installed (i.e NO MSWindows)
I also have dual booted desktops with windoze 2000 ubuntu dapper, suse 9.1.
I can ping any computer on any operating system from any other.

I use ThunderBird / FireFox under windoze via a wireless ADSL modem /router.

 I can't get e-mail or browsing to work with any of my linux machines,
 but I can ping [www.google.com](www.google.com) and FireFox will then connect to the 4-number address the ping returns, but it will not transfer to what I select on a google page. I can also ping any other site to get its address and connect just to the first page.

---

### Post by Verbatim9 on 2006-11-15
I've been having exactly the same problem, though my equipment is rather different (you can see some details of my struggles against the bug in [this thread](http://www.ubuntuforums.org/showthread.php?t=299770)).

I have no idea what's causing the problem, but I can recommend a temporary workaround...try installing another browser, I've had luck with Konqueror. I recommend installing it with aptitude, since it has so many dependencies (if you install with aptitude, and uninstall later with aptitude, it will remove the unnecessary dependencies, rather than leaving them cluttering your disk).

I suspect this is a very common problem at the moment, so I'll give thorough instructions from a fresh install, in case there are linux noobs reading: in Dapper, you'll need to run Synaptic first (System->Administration->Synaptic), and add the official web-based repositories (Settings->Repositories->Add button->check "officially supported" and "restricted copyright" (these repositories were pre-selected in Edgy with a fresh install, so this first step is not necessary in Edgy). Close Synaptic.

Next open a termial (applications->accessories->terminal) type in "sudo aptitude update", and give it the root password. When it's finished updating, type "sudo aptitude install konqueror". It will ask you to confirm before installing, type "y" and hit enter. When it's finished installing, Konqueror should appear under Applications->Internet...and if your problem is the same as mine, it should work beautifully, no idea what it is that's so different about it.

I've also read on the forums that if you re-build Firefox and install it yourself (not from the repositories or from the CD, but by downloading the Linux version from Mozilla) it will work correctly, haven't gotten around to trying it myself.

---

### Post by stream303 on 2006-11-18
Quickie tip:  Place your isp's dns nameservers into your router's setup page and restart networking.

You may want to look at this response to a similar question I wrote:

[http://www.ubuntuforums.org/showthread.php?t=300518](http://www.ubuntuforums.org/showthread.php?t=300518)

Inside is another reference to dns material that might help you.  Being able to ping but not browse is a classic dns symptom which should be easy to resolve.

Unfortunately we have to sometimes tickle linux into submission. :)

---

