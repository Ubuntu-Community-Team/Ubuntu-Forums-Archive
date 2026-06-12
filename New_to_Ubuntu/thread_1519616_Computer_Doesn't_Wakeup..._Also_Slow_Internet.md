---
title: "Computer Doesn't Wakeup... Also Slow Internet"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by DTHCND on 2010-06-28
Ok I recently started using Ubuntu A LOT! I like 10.04 but I got a few problems... When I suspend Ubuntu then wake it up, it works but the screen remains off... (I am using a laptop)... Also I find the Internet is a lot slower when I'm going to a new URL (Example: Google.ca to ubuntuforums.org) but is normal speed when I go to another link with the same URL(?) but is still sometimes slow (Example: ubuntuforums.org to ubuntuforums.org/newthread)...

---

### Post by DTHCND on 2010-06-28
Bump

---

### Post by Metrop021 on 2010-06-28
the reason it's a lot slower when going to a new link is because an old link is cached (saved on your hard disk (or sometimes ram)) so for most of the things on the webpage the browser doesn't even have to go to the internet.

and for the suspend problem: i have it too, its a rather common problem with 10.04 i'm afraid. your best bet (for now) is to just disable suspend in system > preferences> energy manager (not sure what its called in english)

---

### Post by texla on 2010-06-29
@ [DTHCND ]("http://ubuntuforums.org/member.php?u=977760")I'm kind of new to all this, too but I do know that ipv6 seems to be the culprit for most of the internet trouble in Lucid and you may want to try one of these methods to get your internet up to speed - See if either method works for you, they both worked for me - and I had slow as molasses net speed with lucid before this... first I used the opendns method but I just tried the firefox method and that seems to be just as fast so try either one you want:

First for both options, you will need to go to 
system > preferences > network connections 
 then click on the name of your dsl (autoEth0 or whatever) and then click edit
go to ipv6 methods and choose **ignore** (if it's not already chosen)
(master password needed for this change)

then you have two choices:

1. you can go to  [URL="https://store.opendns.com/setup/device/ubuntu/"]https://store.opendns.com/setup/device/ubuntu/
[/URL] and follow the directions

**or **

2. (and I am quoting dixiedancer from this thread here: [URL="http://ubuntuforums.org/showthread.php?t=1479682%29"]http://ubuntuforums.org/showthread.php?t=1479682)

[/URL]then, in Firefox, you need to do the following:
Open your Firefox browser, and in the field where you would normally  type a web address (like [http://www.ubuntu.com]("http://www.ubuntu.com/")),  type

**about:config**

It'll display a warning about messing around with the configuration.  Answer by clicking on the button that says, "I'll be carefull, I  promise!"

Now scroll down that list of settings until you find the one that says, 

"network.dns.disableIPv6 = false" and just double click on that line. It  will darken and then read,

"**network.dns.disableIPv6 = true.**"

Do the same thing on the lines that say

"network.http.pipelining = false" and
"network.http.proxy.pipelining = false."

That will convert those settings to "true."

Then lastly, find the line that says

"network.http.pipelining.maxrequest" and set that number to 8.

Good luck!

---

### Post by DTHCND on 2010-06-29
Thanks! It was already set to ignore but I did the next the in firefox... Super fast now! :D

---

