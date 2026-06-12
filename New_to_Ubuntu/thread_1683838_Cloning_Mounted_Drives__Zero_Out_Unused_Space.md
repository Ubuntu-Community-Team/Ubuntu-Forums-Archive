---
title: "Cloning Mounted Drives | Zero Out Unused Space"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by mitch:) on 2011-02-08
New to UNIX, Sorry if this thread exists some where else; the solution I want is to do is the following:

[LIST=1]
[*]Clone a mounted drive
[*]Prepare the drive before cloning, zeroing out unused space, making an image of a drive of its actually size being used.
[*]Is compression achievable using gzip?  (will just be a plus if number 2 is achievable).
[*]Mount the drive virtually after running dd.
[/LIST]
There is method in my madness; instead of copying the data, it is vital to keep the drives content intact and mount it with its original structured content, this is because inside it has a xml asset map.  This map is used to map UUID's to an asset.  One asset is transferred across via FTP and the associated UUID's follow.

Have been reading into dd and running CloneZilla.  But CloneZilla misses out on a few things like the limit of the image format - being able to select individual files and cloning mounted drives.

Running a line of dd seems like the ideal option, and prior to that creating a redundant file that creates binary zeros on those regions which are not being used, and is then deleted.

Being able to prep the drive is important otherwise the cloned imaged would take up more than the actual data that is required.

Before I persevere with this does any one else have an opinion or has made progress with this.  Any feedback would appreciated

Cheers

---

### Post by mitch:) on 2011-02-09
[http://www.linuxquestions.org/questions/linux-general-1/how-to-create-disk-image-of-actual-data-844474/](http://www.linuxquestions.org/questions/linux-general-1/how-to-create-disk-image-of-actual-data-844474/)

This link is on the right track.  Going to experiment with the idea and see how I get on.

---

