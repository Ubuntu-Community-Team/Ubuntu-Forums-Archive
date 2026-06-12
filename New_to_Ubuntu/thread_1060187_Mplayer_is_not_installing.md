---
title: "Mplayer is not installing"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-02-04
Im on my customization for a live cd and when i type apt-get install mplayer it saids that 10 of its depends are not installable including the mplayer-skins package

---

### Post by ericeclifford on 2009-02-04
HELP! I did the search and couldnt find anything that helped me.

---

### Post by taurus on 2009-02-04
Maybe the LiveCD doesn't contain enough repos to install some extra stuff!  What does the /etc/apt/sources.list look like?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by ericeclifford on 2009-02-04
root@ericeclifford:/# cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security universe

---

### Post by taurus on 2009-02-04
Edit /etc/apt/sources.list and remove the **#** in front of the last 6 lines.  Then see if you can install mplayer now.

```
sudo apt-get update
sudo apt-get install mplayer
```

---

### Post by ericeclifford on 2009-02-04
WELL WELL WELL . it went from 10 packages not installable to only 5 you must be on the right track :) Ill show you the errors.

root@ericeclifford:/# apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libdvdnav4 (>= 0.1.10) but it is not installable
           Depends: libenca0 (>= 1.9) but it is not installable
           Depends: libfaac0 (>= 1.26) but it is not installable
           Depends: libggi2 (>= 1:2.2.1) but it is not installable
           Depends: libjack0 (>= 0.109.2) but it is not installable
           Depends: liblame0 (>= 3.97) but it is not installable
           Depends: libsvga1 but it is not installable
           Depends: libx264-57 (>= 1:0.svn20071224) but it is not installable
           Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
           Depends: mplayer-skins but it is not installable
E: Broken packages




 THEN AFTER I DID WHAT YOU SAID IT DID THIS




root@ericeclifford:/etc/apt# sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libfaac0 (>= 1.26) but it is not installable
           Depends: liblame0 (>= 3.97) but it is not installable
           Depends: libx264-57 (>= 1:0.svn20071224) but it is not installable
           Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
           Depends: mplayer-skins but it is not installable
E: Broken packages
root@ericeclifford:/etc/apt# 


Any other tips brother? :)

---

### Post by ericeclifford on 2009-02-04
Should I do the same to the respos addresses in the medibuntu.list (theres 1 address that has a # and then do a apt-get update and then try to install it?

---

### Post by mc4man on 2009-02-04
You're missing the multiverse source (all those remaining packages are from there.

---

### Post by ericeclifford on 2009-02-05
Ahh so do I just copy the multiverse source into the source.list ?

---

### Post by taurus on 2009-02-05
You could just add this line to the end of your /etc/apt/sources.list.

```
deb http://archive.ubuntu.com/ubuntu hardy multiverse
```
Save it and then run

```
sudo apt-get update
sudo apt-get install mplayer
```

---

### Post by ericeclifford on 2009-02-05
Yo it worked let me tell you what I did, I just copied the source.list from my external harddrive OS to the live cd edit folder source.list, is this gunna be ok? or should I justadd in the previous source.list of the edit folder(live cd customization) and add that line, everything seems to be working now, the  mplayer installed as well as other things i couldnt install before and the update and upgrade looks good as well.

---

### Post by NoBugs! on 2010-03-13
I had this same error, disabling some repositories in the "Other Software" tab and reloading and installing with synaptic fixed it.

---

