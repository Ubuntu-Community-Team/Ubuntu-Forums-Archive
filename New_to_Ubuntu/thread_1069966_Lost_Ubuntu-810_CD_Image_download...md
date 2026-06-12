---
title: "Lost Ubuntu-810 CD Image download..?"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by DonaldJ on 2009-02-14
I downloaded the latest Ubuntu-810 disk image CD, set to "save to desktop", but it didn't save to the desktop, and I can't find it in the OS..?  
A search finds it in the items to search-in,  but it isn't in my files anywhere.. I just can't get the package to the desktop, to do the CD copy..?   How do I find and get that huge download onto the desktop from where ever it's hiding?..  All other downloads go to the desktop as requested, all but this one..?

---

### Post by mikewhatever on 2009-02-14
Can you post the output of <ls ~/Desktop>, and perhaps also of <locate *.iso>.

---

### Post by hyperyoda on 2009-02-14
> **DonaldJ said:**
> I downloaded the latest Ubuntu-810 disk image CD, set to "save to desktop", but it didn't save to the desktop, and I can't find it in the OS..?  
A search finds it in the items to search-in,  but it isn't in my files anywhere.. I just can't get the package to the desktop, to do the CD copy..?   How do I find and get that huge download onto the desktop from where ever it's hiding?..  All other downloads go to the desktop as requested, all but this one..?

You saved it to your MS Windows desktop or Ubuntu desktop?

If Ubuntu do this:
$ updatedb
$ locate <name of file>

Zach

---

### Post by DonaldJ on 2009-02-14
I searched for it, in everything I could.. It seems to be gone...
Probably it got trashed when I uninstalled "Gnome Apt Software Manager" and rebooted..?  Double Ouch!..
I'll do another download...
I'll start by doing a little download to desktop, to test it...

---

### Post by DonaldJ on 2009-02-14
> **mikewhatever said:**
> Can you post the output of <ls ~/Desktop>, and perhaps also of <locate *.iso>.


 <ls ~/Desktop>
bash: syntax error near unexpected token `newline'



 <locate *.iso>
bash: syntax error near unexpected token `newline'

---

### Post by mikewhatever on 2009-02-15
Brackets are only there to indicate where the command starts and ends in the text, you don't need to type them.

---

### Post by DonaldJ on 2009-02-15
oops...

---

