---
title: "Medibuntu failed to fetch"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-12-24
On running

sudo apt-get update

the terminal returned:

N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/Release.gpg)  Something wicked happened resolving 'archive.getdeb.net:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/Release.gpg](http://packages.medibuntu.org/dists/maverick/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

What went wrong?
How do I fix this?
How do I prevent this from happening in the future?

Merry Christmas.

---

### Post by Sef on 2010-12-24
What version of Ubuntu are you running?

---

### Post by ajgreeny on 2010-12-24
Have you updated your version of Ubuntu from 10.04 to 10.10, as that may account for these two repos not now working.  You will need to update the repos for both medibuntu and getdeb again, I think.

---

### Post by sandyd on 2010-12-24
> **Mark_in_Hollywood said:**
> On running

sudo apt-get update

the terminal returned:

N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/Release.gpg)  Something wicked happened resolving 'archive.getdeb.net:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/Release.gpg](http://packages.medibuntu.org/dists/maverick/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

What went wrong?
How do I fix this?
How do I prevent this from happening in the future?

Merry Christmas.
For some users, theirs some issues with their DNS resolvers.

Check out the tutorial here -> [http://openubuntu.com/index.php/topic,230.0.html](http://openubuntu.com/index.php/topic,230.0.html)
to set alternate DNS servers (level 3 is really fast btw)

---

### Post by Mark_in_Hollywood on 2010-12-24
> **Sef said:**
> What version of Ubuntu are you running?

Per my signature on this bb

Maverick Meerkat 10.10.

---

### Post by Mark_in_Hollywood on 2010-12-24
> **ajgreeny said:**
> Have you updated your version of Ubuntu from 10.04 to 10.10, as that may account for these two repos not now working.  You will need to update the repos for both medibuntu and getdeb again, I think.

OK, but how do I do the Update? I ran Update Manager to get the errors I posted. I have previously run: sudo apt-get update. Thanks.

---

### Post by Mark_in_Hollywood on 2010-12-24
> **sandyd said:**
> For some users, theirs some issues with their DNS resolvers.

Check out the tutorial here -> [http://openubuntu.com/index.php/topic,230.0.html](http://openubuntu.com/index.php/topic,230.0.html)
to set alternate DNS servers (level 3 is really fast btw)

I'm using OpenDNS already. I'm not well versed in computer, but I am fairly sure this problem isn't about speed or access. Something is crossed up in the package management area. Thanks.

---

### Post by ajgreeny on 2010-12-25
> **Mark_in_Hollywood said:**
> OK, but how do I do the Update? I ran Update Manager to get the errors I posted. I have previously run: sudo apt-get update. Thanks.
Just re-run the commands you ran before to enable the repos again; that should make sure that everything is set for the correct Ubuntu version.

---

### Post by Mark_in_Hollywood on 2010-12-26
> **ajgreeny said:**
> Just re-run the commands you ran before to enable the repos again; that should make sure that everything is set for the correct Ubuntu version.

I tried that, as you say, but apt-get returned the same errors.

---

### Post by oldos2er on 2010-12-26
Can you post the output of **ls /etc/apt/sources.list.d/** ?

---

### Post by Mark_in_Hollywood on 2010-12-27
> **oldos2er said:**
> Can you post the output of **ls /etc/apt/sources.list.d/** ?

I sure can, Phyllis:


mark@Lexington-19-Karmic:~$ ls /etc/apt/sources.list.d/
cairo-dock-team-ppa-maverick.list
cairo-dock-team-ppa-maverick.list.save
deja-dup-team-ppa-karmic.list
deja-dup-team-ppa-karmic.list.save
deja-dup-team-ppa-maverick.list
deja-dup-team-ppa-maverick.list.save
docky-core-ppa-maverick.list
docky-core-ppa-maverick.list.save
ferramroberto-extra-lucid.list
ferramroberto-extra-lucid.list.distUpgrade
ferramroberto-extra-lucid.list.save
getdeb.list
getdeb.list.bck
getdeb.list.distUpgrade
getdeb.list.save
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
google-talkplugin.list
google-talkplugin.list.distUpgrade
google-talkplugin.list.save
jonls-redshift-ppa-lucid.list
jonls-redshift-ppa-lucid.list.distUpgrade
jonls-redshift-ppa-lucid.list.save
kilian-f.lux-lucid.list
kilian-f.lux-lucid.list.distUpgrade
kilian-f.lux-lucid.list.save
loneowais-ppa-karmic.list
loneowais-ppa-karmic.list.distUpgrade
loneowais-ppa-karmic.list.save
medibuntu.list
medibuntu.list.save
opera.list
opera.list.distUpgrade
opera.list.save
playonlinux.list
playonlinux.list.distUpgrade
playonlinux.list.save
robert-ancell-simple-scan-karmic.list
robert-ancell-simple-scan-karmic.list.distUpgrade
robert-ancell-simple-scan-karmic.list.save
super_os_respository.list
super_os_respository.list.save
tualatrix-ppa-maverick.list.save
ubuntu-audio-dev-ppa-lucid.list
ubuntu-audio-dev-ppa-lucid.list.distUpgrade
ubuntu-audio-dev-ppa-lucid.list.save
ubuntu-tweak-stable.list
ubuntu-tweak-stable.list.distUpgrade
ubuntu-tweak-stable.list.save
ubuntu-wine-ppa-karmic.list
ubuntu-wine-ppa-karmic.list.distUpgrade
ubuntu-wine-ppa-karmic.list.save
winehq.list
winehq.list.distUpgrade
winehq.list.save

Your avatar is Phyllis Diller, right?

---

### Post by davidmohammed on 2010-12-27
your sources list contains stuff from karmic, lucid and maverick...

This probably will cause you all sorts of issues.

Go to Update Manager - Settings.  Disable all the ppa's you are using.

Or edit each ppa and make sure the Distribution field says "maverick"

---

### Post by oldos2er on 2010-12-27
> **Mark_in_Hollywood said:**
> Your avatar is Phyllis Diller, right?

Yes, it is.

+1 to what davidmohammed said.

---

### Post by Mark_in_Hollywood on 2010-12-28
> **davidmohammed said:**
> your sources list contains stuff from karmic, lucid and maverick...

Go to Update Manager - Settings.  Disable all the ppa's you are using.

Or edit each ppa and make sure the Distribution field says "maverick"

I opened Up Mgr. - Settings - and much to my surprise, all the ppa:'s had the word: maverick associated with their respective "check-marks". 

So, I unchecked EVERY ppa: with a check-mark in it, ran the "check for updates" and now MediBuntu does not show the extra fonts it was trying to install.

How do I FIX this problem. Your solution seems to ignore it.

---

### Post by davidmohammed on 2010-12-28
ok - just to confirm the current state - please reply with the contents of the following file

/etc/apt/sources.list

---

### Post by Mark_in_Hollywood on 2010-12-29
David:

Thank you for sticking with me in this problem. I have looked at my ~sources.list and have found the problems. Or at least I believe I have found them.

I'm posting an example, here, for others who may find themselves with a similar problem. Again, thanks. I think I have it licked. If I don't I'll post here again and PM you to get your attention.

## 2 lines below added by mp 29-may-2010. Update Mgr returned 2 'getdeb' errors today. I saw a
## story about different mirrors at: [http://www.webupd8.org/2010/05/getdeb-playdeb-repositories-##down-what.html](http://www.webupd8.org/2010/05/getdeb-playdeb-repositories-##down-what.html) and found that my sources-dot-list has no reference to 'getdeb'.
# deb [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) lucid-getdeb games # disabled on upgrade to maverick
# deb-src [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) lucid-getdeb games # disabled on upgrade to maverick
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports restricted main multiverse universe

---

