---
title: "Firefox page display problem for some pages."
date: 2009-08-18
forum: New to Ubuntu
---

### Post by Duncan Hollands on 2009-08-18
Howdy people, any help would be very appreciated. 
For quite some time, my firefox has been displaying the occasional web page incorrectly. I'm afraid that I can't remember any settings that I changed when it first started to happen as it was a couple of years ago, and up until recently I've just put up with it. 
This is an example of a page which displays with error: [IMG]http://fc00.deviantart.com/fs49/i/2009/230/7/5/FF_error_by_shellat.png[/IMG]

Here is a similar page from the same site, which displays without error: 
[IMG]http://fc00.deviantart.com/fs46/i/2009/230/d/f/ff_no_error_by_shellat.png[/IMG]

I have tried moving the ~/mozilla/firefox/ directory, but it doesn't help. 
Neither did using synaptic to 'Completely Remove' the firefox meta package, neither seems to help :(   (both of these ideas came from searching the forums).
Any help would be appreciated.

---

### Post by Penguin Guy on 2009-08-18
This happens on some pages for me as well but [Planet Renders]("http://planetrenders.net/renders/") displays just fine.

---

### Post by y-lee on 2009-08-18
Try clearing your recent history, esp cache and history. And the restart firefox. that usually works for me. Also i have noted firefox sometimes acts strange when my system is low on memory. This happens to me in both windows and linux, so i monitor memory useage and if necessary close apps i may have open and or close some tabs or windows in firefox. Hope that helps :)

---

### Post by Duncan Hollands on 2009-08-18
Thanks for the cache clearing tip, but I just tried it and its still the same, and Mem Usage is at 36%.

---

### Post by y-lee on 2009-08-18
> **Duncan Hollands said:**
> Thanks for the cache clearing tip, but I just tried it and its still the same, and Mem Usage is at 36%.

have you tried creating a new firefox profile? And have you considered the possibility that it may be an error not on your end but on the web server you are visiting? Does the page display correctly in another browser when it doesn't in FF? if it does then it is obviously a FF error, if not then it most likely is an error coming from the site.

---

### Post by superprash2003 on 2009-08-18
does this happen with opera or any other browser?

---

### Post by Duncan Hollands on 2009-08-18
> have you tried creating a new firefox profile?
Wouldn't moving the ~/.mozilla/firefox/ directory to ~/.mozilla/firefox_back/ be the equivalent of trying a new profile? Actually  now that I think about it, I have tried it by running ...
```
firefox -p
``` ... so yes I have tried it with a new profile and it is still the same.

> And have you considered the possibility that it may be an error not on your end but on the web server you are visiting? Does the page display correctly in another browser when it doesn't in FF? if it does then it is obviously a FF error, if not then it most likely is an error coming from the site.
I can access the same page in Opera just fine, and it displays completely normally. So it does seem to be an ff error. 
I could just switch to Opera, but I do prefer ff (not to mention all my bookmarks). 

Thanks for the suggestions guys, its kind of you to help when you don't really get much for it.

---

### Post by ssdt on 2009-08-18
It might be caused by Firefox extensions. You might want to check those

---

