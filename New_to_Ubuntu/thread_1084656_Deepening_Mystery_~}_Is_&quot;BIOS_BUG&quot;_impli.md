---
title: "Deepening Mystery ~} Is &quot;BIOS BUG&quot; implicated?"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by Andavane on 2009-03-02
My Ubuntu on an old IBM Think-Centre has been behaving strangely, beginning last year. To recap on the symptoms:

1) Latter quartile of 2008: Gutsy Gibbon not updating properly. i posted the problem and some users had the same thing happen.
2) When using grsynch to backup my files to an external hard drive, masses of errors came from this machine. (But worked fine from my laptop, and worked fine to my colleagues Windows laptop, so I assumed it must be this machine, and quarantined it. If I wanted to move files, they were sent to my gmail, and then downloaded to my laptop.)
3) Installed Intrepid 8.10 (Ubuntu Gutsy is still there)
4) Now (Feb--March 2009) when I boot this machine I sometimes see "BIOS BUG"* flashing*before my eyes, and then it is gone.

These things are mysteries way beyond my comprehension, and I thought that a clever detective might know what the problem could be.

Apart from this, the machine appears to be working well, but I don't transfer data off it physically.

Will happily "Open the bonnet" for anyone who wants to try to diagnose.

Regards

John

*I can't read those opening messages quick enough as they flash in front of my eyes. If we could read what it says fully, we might get some more clues.

PS: One "symptom" which has mysteriously disappeared: The machine has its Ubuntu installed on a hard drive which sits in the DVD drive bay. Windows XP is installed on the "C" drive (Main Drive) called IBM Preload. Until last week when I went to mount it, it said somewthing like "Unable to Mount: Mount Point not assigned". And then it went and mounted it anyway.
Now, that symptom has disappeared. It no longer says "Unable to Mount", and it appears to be mounting normally. But "BIOS BUG" has crept in.

---

### Post by HavocXphere on 2009-03-02
Unlikely that the bug is the cause. One of the later updates probably just added code to detect the existing bug. Usually it also means that the OS is working around the bug, so it shouldn't cause a problem.

On the whole it sounds more like a collection of unrelated issues not one thing causing it.

I'd guess
1) -> Some package dependency problem/synaptic bug.
2) Would be helpful to know what those errors said that came up...

Not sure what the mount thing is, but if its mounting OK then why worry.

---

### Post by Andavane on 2009-03-03
> **HavocXphere said:**
> .......
2) Would be helpful to know what those errors said that came up...

...
Indeed it would.
I will try to catch those words when next they flash up (they don't always come)... when they appear it seems to say "....timer..."

Regards

John

---

### Post by handy on 2009-03-03
Wouldn't they be logged in a file?

I've not used Ubuntu for a long time, so I can't go looking at the logs.  On Arch it would definitely be logged.

Perhaps someone who knows can tell us?

---

### Post by Andavane on 2009-03-04
> **handy said:**
> Wouldn't they be logged in a file?

I've not used Ubuntu for a long time, so I can't go looking at the logs.  On Arch it would definitely be logged.

Perhaps someone who knows can tell us?
Indeed... You'd think that there would be  a way of recalling this info ;)

Regds

john

---

### Post by handy on 2009-03-04
Have you had a ferret around in /var/log/ , that is where you should find the log you require.

In Arch I'd be looking at the *everything.log* though it is a monster. 

You only need to look at the relevant time span of whatever log you need to be looking into.

---

### Post by Andavane on 2009-03-04
> **handy said:**
> Have you had a ferret around in /var/log/ , that is where you should find the log you require.

In Arch I'd be looking at the *everything.log* though it is a monster. 

You only need to look at the relevant time span of whatever log you need to be looking into.

Well I'll have a ferret there next time I see it: I didn't see it on this boot.

my HawkEye will be pinned extra wide from now on ! :-|

Rgds

John

---

### Post by albinootje on 2009-03-04
> **Andavane said:**
> 
4) Now (Feb--March 2009) when I boot this machine I sometimes see "BIOS BUG"* flashing*before my eyes, and then it is gone.

After a fresh reboot you can do the following :
```

dmesg

```
One other, perhaps better, option is to boot into "recovery mode", and then scroll back with the shift-page-up key combination.

---

### Post by handy on 2009-03-04
> **Andavane said:**
> Well I'll have a ferret there next time I see it: I didn't see it on this boot.

my HawkEye will be pinned extra wide from now on ! :-|

Rgds

John

Sorry if my suggestions are too loose for you. 

I'm just giving you the best I've got.  

Which will find the answer you are looking for as far as logs are concerned, if you spend a little time.

Whilst spending that time you will learn some more about your system, which (if your memory is superior to mine) will serve you well in the future. :P

---

### Post by albinootje on 2009-03-04
> **Andavane said:**
> 
*I can't read those opening messages quick enough as they flash in front of my eyes. If we could read what it says fully, we might get some more clues.

Years ago it was possible to hit the scroll-lock key, (right after Linux would boot,) and then booting of Linux (in text-mode) would pause. 
Not sure whether this is still possible, but if it is then it's easier to scroll back with shift + page-up.

---

