---
title: "Ubuntu Studio - issues"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by texla on 2009-09-16
Just installed Ubuntu Studio in Jaunty and having some strange issues. 
 
Jack seems very flawed - won't open in default without an error and doesn't do anything to aid a usb device for Ardour either.  Been racking the forums at Ardour with this to no luck.  Also, various sound programs don't seem to open at all (don't know if this is because of Jack):
Meter Bridge, Patchage, Jack Time Machine and others (Audacity, Hydrogen and Ardour do open)

And the Real Time Kernel is very slow... but that could be because of my 512 MB RAM 
(but Jaunty in the vanilla kernel is lightning fast with same RAM) - will be upgrading RAM shortly but just testing out apps until I do with this...

OK just wondering if anyone has any experience with these issues - seems I've been striking out with my questions now for a while, tons of looks and no replies - hope this breaks the trend!

---

### Post by Mike_IronFist on 2009-09-16
> **texla said:**
> Just installed Ubuntu Studio in Jaunty and having some strange issues. 
 
Jack seems very flawed - won't open in default without an error and doesn't do anything to aid a usb device for Ardour either.  Been racking the forums at Ardour with this to no luck.
That's an unusual problem and one that I've never had with Jack. It might be a problem that runs so deep in your system that you have to reinstall.

But, you should explain what error Jack is opening with. If you did, perhaps someone could help find an answer to what the error's from.

> **texla said:**
> 
Also, various sound programs don't seem to open at all (don't know if this is because of Jack):
Meter Bridge, Patchage, Jack Time Machine and others (Audacity, Hydrogen and Ardour do open)

Some sound programs must have Jack running in order to function at all. Jack is, after all, a sound server.

> **texla said:**
> 
And the Real Time Kernel is very slow... but that could be because of my 512 MB RAM 
(but Jaunty in the vanilla kernel is lightning fast with same RAM) - will be upgrading RAM shortly but just testing out apps until I do with this...

I recommend looking up a How-To on using a realtime kernel with Ubuntu Studio. Following the directions for that kind of documentation will allow you to get the performance you're supposed to get with an RT kernel. I found this little article, it might or might not help:
[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted]("https://help.ubuntu.com/community/UbuntuStudio/GettingStarted")

> **texla said:**
> 
OK just wondering if anyone has any experience with these issues - seems I've been striking out with my questions now for a while, tons of looks and no replies - hope this breaks the trend!

---

### Post by texla on 2009-09-16
> **Mike_IronFist said:**
> That's an unusual problem and one that I've never had with Jack.

[quote=
I found this little article, it might or might not help:
[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)[/quote]


Thanks a lot Mike for your reply - I found the page you referenced earlier today and the fix needed was indeed inside.  It had to do with the permissions that had to be added to the audio user so you we're on the right track.  

Jack seems to be running like it should now but it's not liking the realtime option much and the rt kernel is slow as molasses for now - I'll keep pouring through info pages and sites when I can for a while and see if I can crack this thing open a bit more.   I Heard some complaints about this version of Ubuntu Studio  though and the next advice I keep reading is to install an earlier kernel or downgrade jaunty to hardy and I'm not sure I have the time to do all that - I'll see what I can fix from here.

Anyways, appreciate  your input!

---

