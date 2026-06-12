---
title: "[SOLVED] WPA wireless problems"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by Freiberg on 2008-08-18
Hi.  I installed ubuntu yesterday and have had no problems with it except for one:  I can´t connect to an encrypted wireless signal.  To cut to the chase, this is what it looks like:

[IMG]http://i276.photobucket.com/albums/kk6/htgnef/Screenshot.png[/IMG]

I can connect to regular, unencrypted networks just fine, but not this one.  Anyone have any idea?  Thank you.



EDIT: While, as I said in my final post, this problem was entirely my fault, if you, the person reading this, have a genuine problem, you may want to read on.

---

### Post by ajgreeny on 2008-08-18
Are you sure the password you typed is correct?  I know it seems like a silly question, but I know someone will ask so I got in first.

---

### Post by Xant on 2008-08-18
no, Im getting the same problems. and it asks for passwords too right? (after the initial attempt)

---

### Post by Freiberg on 2008-08-18
> **ajgreeny said:**
> Are you sure the password you typed is correct?  I know it seems like a silly question, but I know someone will ask so I got in first.

I am sure, but I don´t even get the chance to find out because the connect button is faded.

> **Xant said:**
> no, Im getting the same problems. and it asks for passwords too right? (after the initial attempt)

Yes, except it asked for the password on the initial attempt too.  I am currently connected to a wireless network that is unsecured.  I have no problem doing that, so it is not a problem with roaming or my wireless card.  I don´t know how to be more specific with my problem.

---

### Post by jimv on 2008-08-18
Try using WICD instead.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

(Make sure you get 1.5.1, not 1.4.2)

---

### Post by tl3000 on 2008-08-18
> **Freiberg said:**
> Hi.  I installed ubuntu yesterday and have had no problems with it except for one:  I can´t connect to an encrypted wireless signal.

I can connect to regular, unencrypted networks just fine, but not this one.  Anyone have any idea?  Thank you.

Checkout the following bug report, and if your situation is similar try the recently posted workaround near the end of the thread:

[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446)

---

### Post by Freiberg on 2008-08-18
> **tl3000 said:**
> Checkout the following bug report, and if your situation is similar try the recently posted workaround near the end of the thread:

[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446)

OK, but I do not know whether or not I am using ndiswrapper, which is what this bug is talking about.  Other than that the problems seems similar.  I will try it.

---

### Post by tl3000 on 2008-08-18
> **Freiberg said:**
> OK, but I do not know whether or not I am using ndiswrapper, which is what this bug is talking about.  Other than that the problems seems similar.  I will try it.

This WPA_Supplicant bug is mainly for wireless connections using NDISwrapper.  If you're not sure, then most likely you're not using NDISwrapper and just using the native wireless driver.

---

### Post by suprakid24 on 2008-08-18
I had a similar problem and this worked for me, maybe it will work for you. 

[http://ubuntuforums.org/showthread.php?t=892739](http://ubuntuforums.org/showthread.php?t=892739)

---

### Post by Freiberg on 2008-08-18
> **ajgreeny said:**
> Are you sure the password you typed is correct?  I know it seems like a silly question, but I know someone will ask so I got in first.

My deepest apologies to you all for wasting your time.  While I did do what you suggested, which may have indeed helped, it turns out that I MISSPELLED my password to make it one letter shorter, which means that it could not be a WPA password, which meant that the connect button would not activate.  Again, sorry.

---

### Post by ajgreeny on 2008-08-19
No problem.  It's always worth checking the obvious first, then moving on to the unlikely and finally to what nobody in their right mind would get wrong.  However, we've all done similar things at some time or another, I'm sure.

---

