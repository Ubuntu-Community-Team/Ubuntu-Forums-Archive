---
title: "Could not download all repository indexes"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by Reljoy on 2009-10-14
I thought I would see if there were any updates to Ubuntu as I hadn't done any for a while.
So I went System, Administrator, Update Manager
and it worked perfectly for my second computer --- but ---
it did not work properly for my main computer which is a windows xp / Ubuntu dual boot system.

It told me that there were things that would not update.

So I went to this forum and did some reading and it seems to be a common problem with lots of variations.

I went to Synaptic Package Manager and it says it Could not download all repository indexes.

Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

Does this mean my Ubuntu is "broken" in some way that is significant?
Or will it fix itself if I wait a day or two?

I tried changing the server that I was downloading the repositories from but it made no difference. I tried several.
Maybe there is a problem at Ubuntu's end and it is not a problem at my end???

What should I do?

---

### Post by SkyNet2029 on 2009-10-14
The error you speak of is actually aptitude (synaptic is a front-end for apt) telling you that it was unable to scan the repository on your original install media, not on the network. You could always go into synaptic and remove the entry for the cdrom from your /etc/apt/sources.list file.
At any rate, no your ubuntu is not broken, in fact it is onl doing what it can to tell you that it did not find removable medium with a repository on it in the specified location.

---

### Post by Reljoy on 2009-10-15
That's really strange. I've had Ubuntu on this computer for some months and I've never seen this message before.

I'll need explicit instructions on how to remove the entry for the cdrom from my /etc/apt/sources.list file, please.

---

### Post by Reljoy on 2009-10-15
I figured it out - I unticked a checkbox in Synaptic Package Manager and the error did not happen this time. 
Thanks for your help.

---

### Post by SkyNet2029 on 2009-10-15
```
sudo gedit /etc/apt/sources.list
```
place a comment (#) 
in front of the listing that says CDROM
 
save then run
```
sudo apt-get update
```

---

