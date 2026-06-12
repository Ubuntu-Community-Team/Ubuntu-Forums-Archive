---
title: "Omnikey card reader"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by woodseaves on 2009-11-11
Hi,
I have been trying to install an Omnikey reader to a usb port. To cut a very long story very short I am at a point where I am getting the message 'no reader control enabled' Now I appreciate that this is not a lot of info but at this hour I'm hoping that this rings a bell to someone. If not I will post again tomorrow with a lot more info.
 
Regards

---

### Post by ramjet_1953 on 2009-11-11
This may be worth a try.

For some unknown reason (probably political correctness) the boffins at Ubuntu have decided to enable the Brail TTY package by default.

This has been the case for ages.

Go into Synaptic package manager and search for [COLOR="Blue"]brltty[/COLOR] and [COLOR="Blue"]brltty-x11[/COLOR].
Remove both of these packages.

I am guessing that your reader, even though it is USB, probably is a psudo-serial device and brltty interferes with these devices.

Regards,
Roger :D

---

### Post by woodseaves on 2009-11-12
Thanks for your interest but none of the above are installed Ver. 9.10.
Regards

---

### Post by anewguy on 2009-11-12
Try running the application as super user (e.g, sudo ......) and see if it works - if so let me know.  I suspect you may have a little trouble getting the drivers to work for it, but it's worth digging for.

Dave :)

---

### Post by woodseaves on 2009-11-12
Thanks,
Here's the story so far.
I am attempting to setup a linux pc card server following a thread on satellites.co.uk. I have completed the following successfully on my computer which is a Sony vaio which is more than up to the job.
Installed PCSCD, PCSC tools and the latest omnikey 3121 cardreader drivers. I have the lates version of smartcards_list.txt installed.
 
I have setup a new directory called newcs and installed newcs.i686.pcsc (renamed to newcs_167) and newcs.xml
 
using the code ./pcsc_167 -c /home/username/newcs/newcs.xml )where username is a  named directory) I receive the following:
 
reader type 2 on node 0  (That's a zero)
opening device 0
could not get device 0
reset failed
 
and again and again and again etc.
 
In all the thread there is only one instance of this happening and I think it may have been sorted via PM exchange. I've tried to PM but no success.
 
I am running Ubuntu 9.10, I have tried 9.04, I have rebooted an reinstalled more times that you could shake a stick at.  Surely I can't be so stupid, as I have said only one other out of all the people following the thread has failed.
 
Any ideas?
 
Regards

---

### Post by woodseaves on 2009-11-12
Well I've reinstalled ubuntu and followed the thread to the letter with no result, it's good to know that I'm not the only one who doesn't know the answer.

I think I'll take a break then have another go, my problem has got to be a simple one.

 I need a mentor who will instruct me one step at a time so I can see where I am going wrong. A free reader is on offer. (tic)

Regards

---

### Post by woodseaves on 2009-11-12
Thanks to all who read and helped, I had the wrong newcs file, i.61 instead of 1.67.

I'm new.

Regards Mark as solved

---

