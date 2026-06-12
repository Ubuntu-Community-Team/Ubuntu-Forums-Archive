---
title: "confusing terminal message"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by vikigal on 2009-04-17
or maybe it's not, maybe it's just me. Anyway; My beloved firefox has went off the deep end. After spending much time and effort I finally found the an answer, create a new profile. After using incorrect terminal commands given at the firefox forum, I found the correct one here: firefox -P. I got my little box to create a profile, did it, and opened firefox. BUT when I went to close the terminal window I found the following:

oldgal1@user-desktop:~$ firefox -P
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)


Does this mean anything important? Can I ignore it and safely close the window?

I have not seen anything like this before so please excuse me if this is dumb. Thank you for any help.

---

### Post by Michael.Godawski on 2009-04-17
hi, 
seems to be a bug:


[LIST]
[*][https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/162976](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/162976)
[/LIST]
Does Firefox crash?
Or are you just curious what the mysterious message means?:D

---

### Post by vikigal on 2009-04-17
Firefox is/was dead. After creating a new profile it seems to be working. I think it is a bad bug. All the Firefox site commands are wrong so I have been beating my head over the computer for two solid days before I finally found the correct commands to find the profile manager here. I just have never seen this particular message, at least without a lot more info following it. It threw me as I do not use the terminal very often, and not without having read to find out what to expect.
I don't know if there is anything else I need to do before I close the terminal.

P.S. Thanks to this problem I have discovered Seamonkey, which I think I may keep using as with each update Firefox is behaving more like I.E. so I may have to flush it...

---

### Post by llamabr on 2009-04-17
Seamonkey is nice, based on a more original port of netscape.  But it's an enormous program, running lots of stuff in the background that you're probably not using.  It's simultaneously running a web browser, an email reader, a news reader, an html editor, and others.

Firefox broke each of those off into their own constituent programs, so you can run each as you want.

Sometimes when I've sufficiently broken firefox, I just rm my ~/.mozilla/ folder, and let firefox create a new one.  It'll solve whatever I broke.

The message you see in a terminal is probably nothing interesting, unless you're continuing to have trouble.

---

### Post by vikigal on 2009-04-17
Thanks you for the info. I did not know there was that much "stuff" in seamonkey. And thanks also for the terminal info. I panic easily when I am tired and confused anyway.

---

