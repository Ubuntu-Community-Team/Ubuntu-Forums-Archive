---
title: "&quot;Could not download all repository indexes&quot; error..apt-cdrom issue??"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by sleepee on 2010-02-10
hey all...
so i've had this problem with the update manager/synaptic package manager for a while now.
every time i try to check for new updates, update manager seems to do its thing just fine... but it always gives me an error every time...
this is what it says:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
 
[B]GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)/dists/karmic/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)/dists/karmic/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.[/B]

i think the bold part is the important part.
now from what i understand from reading the man page for apt-cdrom, i get that it's basically like apt-get, but the sources come from a cd instead of some source over the internet..
if that's right, then i really don't understand why i'm getting this error, because i've never told synaptic to use the cdrom to get any packages from it..

but this is interesting, because i also have another problem that relates to cd's...
i can't burn any...  i've tried brasero, k3b, gnomebaker, and i always get an error that prevents me from burning...  can't burn iso's, data, music.. nothing.
the apps don't even start burning. as soon as i hit the "record" button, i get the error.
which is weird, because i can read cd's/dvd's just fine..and on Windows 7, i can burn and read cd's/dvd's just fine too.

they probably have nothing to do with each other and might be two separate issues (i have the same cd burning problem on my desktop with 9.04, but i don't have the repository index error on the desktop) but i thought i might throw that out there on the off chance that it might be related..
but now that i re-read the error, i see it could easily be that i'm missing some public key.  i really don't know the process of how to get that public key though..
actually, i really just don't even know what the problem is..

anyway, any help would be appreciated in deciphering and fixing that error message..
and if i could get my cd burning to work, i'd love that too..  thanx...
just in case, here's my specs:
i'm running 64-bit karmic (as you can probably already tell by reading the error) on an hp dv7, with a blu-ray/dvd-rw dl

---

### Post by nhasian on 2010-02-10
in System->Administration->Software Sources, under the first tab labeled Software Sources, at the bottom, untick the box for Cdrom with Ubuntu 9.10 Karmic Koala Officially supported Restricted copyright

---

### Post by sleepee on 2010-02-10
wow.. thanks for the fast response.. especially this late (or this early??)
anyway.. i unchecked the boxed, hit close, and got this error:

"An error occurred

The following details are provided:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
"

so apparently, the apt-cdrom issue was almost embarrassingly easy to fix.  but how exactly do i get this public key??
if i'm not mistaken, i got to type in some wget command in the terminal, am i right??

---

### Post by k3lt01 on 2010-02-10
Go to the medibuntu page and follow the instructions on the repository page. It will fix your problem.

---

### Post by nhasian on 2010-02-10
you can fix the 2nd error with this terminal command:

```
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

### Post by sleepee on 2010-02-10
thanks....  i found the key i needed in the medibuntu.org page.
i had been going to the packages.medibuntu.org page looking for something that wasn't there like an idiot  lol!!

anyway, thanks for the really quick response..  that was a lot faster than i expected..

---

