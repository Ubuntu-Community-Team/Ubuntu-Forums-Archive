---
title: "This is really weird....partition issue....."
date: 2009-12-06
forum: New to Ubuntu
---

### Post by listerdl on 2009-12-06
Hi, I spent at least six hours yesterday creating partitions to dual boot Windows 7 and Ubuntu 9.04 and allowing them to share the same NTFS data storage.

Everything worked well and everything seems to work 100% in that if I boot into windows I have access to my documents - and if I boot into ubuntu I also have access to the same documents.

The documents are all located in a very large 100 NTFS gig partition called storage - on the E:/ drive.

Now - having downloaded about 3 gig from dropbox to the allocated E:/ drive - it now says that the drive is 100% empty. (The data is all there....but windows and ubuntu say that that partition is empty.....)

What is going on?

If view properties in either system it clearly states that the E Drive contains all the data - so how come it says that it is empty?

Very odd....

Any ideas what happened?

My suspicion is that for some very odd reason, although the E:/ Storage drive was allocated the data storage task it just ignored and slapped the storage in the windows 7 installation.

Any ideas?

Thanks!

---

### Post by Bölvaður on 2009-12-06
try reformat it again as NTFS from within ubuntu.
I am not familiar with windows but I would guess the problem might partly be because of it.

---

### Post by bumanie on 2009-12-06
Please post the output of terminal command > df -hThat will state your partitions, their sizes and how much of each partition is used.

---

### Post by listerdl on 2009-12-06
> **bumanie said:**
> Please post the output of terminal command That will state your partitions, their sizes and how much of each partition is used.

Thats really good advice thanks.

[COLOR="DarkRed"]This is what happened:

henry@Toshiba:~$ df -h 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              15G  3.0G   12G  21% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M   92K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M  160K 1003M   1% /dev
tmpfs                1003M   76K 1003M   1% /dev/shm
lrm                  1003M  2.2M 1001M   1% /lib/modules/2.6.28-17-generic/volatile
[COLOR="SeaGreen"]/dev/sda4             119G  475M  119G   1% /media/storage[/COLOR][/COLOR]

I downloaded a lot of files from dropbox that actually only came to 367 MB. That is reflected in the green color right? if it is then all is good....just seems weird that windows lists that partition as having 100% availability when it ought to be 99% -

any thoughts very appreciated - im just keen to see that i have installed correctly. It all works I guess I just want peace of mind before I make lots more tweaks - thansk very much!

---

