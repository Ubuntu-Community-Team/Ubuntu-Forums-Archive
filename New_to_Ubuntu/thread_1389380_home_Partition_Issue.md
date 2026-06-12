---
title: "/home Partition Issue"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by Wataru8675 on 2010-01-24
Hi folks,

I decided yesterday to create a /home partition as per recommended by another user, and I found and used the psychocats guide ([http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)).

I finished all the steps and then rebooted.  I got some scary-looking error messages after logging in, but eventually, my desktop and taskbars all loaded and everything seemed at place.  I restarted and got the same messages.  This one I got immediately after logging in:

```
User's $Home/.dmrc file is being ignored.  This prevents the default session and
 language from being saved.  File should be owned by user and have 644 permissions.  
User's $Home directory must be owned by user and not writable by other users.
```
Then my screen went blank (except my cursor) for an uncomfortable amount of time before this appeared:
```
Could not update ICEauthority file /home/kyle/.ICEauthority
```Then my screen stayed blank for another uncomfortable amount of time, and then my desktop and taskbars slowly filled in.  Now everything seems completely at place and usable.

Can someone translate these error messages for me and let me know if I did something wrong?

Thanks,
Wataru8675

---

### Post by cosine352 on 2010-01-24
have you tried the 
> What if it doesn't work?
solution in your link (neaar the end)?

---

### Post by Wataru8675 on 2010-01-24
Yes, but it says "if you're unable to log in."  I AM able to log in.  And I don't know what those commands do, and I didn't want to mess things up even more since it "kind-of" works, and not flat out "doesn't" work as they seem to be helping with.

---

### Post by lotharmat on 2010-01-24
----snip ----

What if it doesn't work?
If you reboot and are unable to log in because of some errors having to do with the $HOME/.dmrc file and/or .ICEauthority file, this may help.

Boot into recovery mode (if you don't know how to do this, go to this section of another tutorial). 

----snip ----


I think this may be the problem you are having...

---

### Post by philinux on 2010-01-24
> **Wataru8675 said:**
> Hi folks,

I decided yesterday to create a /home partition as per recommended by another user, and I found and used the psychocats guide ([http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)).

I finished all the steps and then rebooted.  I got some scary-looking error messages after logging in, but eventually, my desktop and taskbars all loaded and everything seemed at place.  I restarted and got the same messages.  This one I got immediately after logging in:

```
User's $Home/.dmrc file is being ignored.  This prevents the default session and
 language from being saved.  File should be owned by user and have 644 permissions.  
User's $Home directory must be owned by user and not writable by other users.
```
Then my screen went blank (except my cursor) for an uncomfortable amount of time before this appeared:
```
Could not update ICEauthority file /home/kyle/.ICEauthority
```Then my screen stayed blank for another uncomfortable amount of time, and then my desktop and taskbars slowly filled in.  Now everything seems completely at place and usable.

Can someone translate these error messages for me and let me know if I did something wrong?

Thanks,
Wataru8675

Those two errors are fairly minor to fix.

To fix the first one follow this.

[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

Then reboot and lets see where that gets you.

Main thing is now you have home on its own partition is all your stuff there as expected?

---

### Post by Wataru8675 on 2010-01-24
Ahh, thank you very much philinux!  The errors are now gone.

However, the appearance of my desktop is now much slower than it was before...is this normal when /home is in another partition?  Makes sense that it would slow it down a touch, but I just want to make sure.

And, also, just to make sure I know what I just did to my computer...my original /home folder (which started on the same partition as from where Linux booted) has now been...transfered(?)...to another partition, from which Ubuntu now reads exclusively from?  Or have I simply made a backup of my current /home folder, and all new info will be saved to the same partition from which Ubuntu is booted, like usual?  And, be this case, will I have to backup my /home folder regularly to the extra partition?

---

### Post by nothingspecial on 2010-01-24
There should be no noticable performance lag as long as the partitions are on the same hard disk.

As long as you got those errors then your /home is on the new partition (unless you made some really weirdly coincidental mistakes, of which there is very little chance)

Therefore everything will be saved to your new home, on the new partition.

If you followed those directions to the letter then you should have a directory on your computer /home_backup which is effectively a backup of your home directory at the moment you carried out the instructions.

It is not necessary to keep it, although aslong as you have enough free space it will do no harm, and backups are good things to have.

---

### Post by Wataru8675 on 2010-01-24
Okay, that makes sense.

Now, sorry to keep dragging this out...but this opens a new question for me:  Should I then make my /home partition as large as possible, and put the partition Linux boots from at the minimum required space?  And, if so, how much room should I allot for Linux to boot from?

---

### Post by nothingspecial on 2010-01-24
Not unless you really need the space.

Resizing partitions carries a small risk of data loss.

I use about  6 gigs for my / partition.

If you have backups, and you are comfortable with linux then you could (probably should). But I think you might need a bit more experience first.

This is opinion only. You are using linux - you are free to do as you choose.

---

