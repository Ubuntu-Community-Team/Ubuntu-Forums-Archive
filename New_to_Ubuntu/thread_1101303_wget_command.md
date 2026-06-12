---
title: "wget command"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by Grendel336 on 2009-03-20
I am running through a tutorial for installing a driver and the instruction tell me to type: 

wget [http://ftp](http://ftp)........

If I have the file I need on a USB stick should I still use the [COLOR="Red"]wget[/COLOR] command or would it be more appropriate, and/or faster to use some other command for loading the file I need?

I can't access the internet so going to a web site to get the file is not an option right now. 

Thanks for helping a newb.

---

### Post by t0p on 2009-03-20
wget would fetch the file from the ftp site you mentioned.  If you have got the required file on a usb drive, it would be easier to transfer it from that.  And if you don't have internet access, you don't have any choice anyway.  You need internet connection to use wget.

If you're following a command line tutorial, you need to use the **cd** command to move the file from your usb drive (/media/disk or something similar) to wherever you need it.  Or you can use the graphical file manager to drag it over or cut and paste.  wget is an internet utility.

---

### Post by Grendel336 on 2009-03-20
Thanks...that's what I was wondering.

---

### Post by mikechant on 2009-03-20
> If you're following a command line tutorial, you need to use the cd command to move the file from your usb drive (/media/disk or something similar) to wherever you need it. 

I think you mean the 'cp' (copy) command not 'cd' (change directory), although of course you might want to do a 'cd' to the correct directory before doing a 'cp'.

---

