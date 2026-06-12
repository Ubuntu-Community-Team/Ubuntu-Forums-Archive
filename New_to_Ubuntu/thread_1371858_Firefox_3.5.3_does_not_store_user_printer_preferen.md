---
title: "Firefox 3.5.3 does not store user printer preferences"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by DocDanW on 2010-01-03
Firefox 3.5.3 in my new installation of Ubuntu 9.10 64-bit edition is not storing my user printer preferences between launches or even from print job to print job.

When I try to print in Firefox, printing defaults to the 300x300 Draft setting unless I manually reset it before each attempt.  Even the "Automatic" resolution setting does not hold.

This is a new problem to me...this is my first installation of Ubuntu to a dedicated partition in a tri-boot (Windows 7/Windows XP Pro/Ubuntu 9.10) installation; previously, I had 9.10 installed via Wubi in Vista and all worked well with that earlier version of Firefox.  I experienced this same problem on a second, similarly-configured computer.

My printer is a Canon MP600, which works fine printing in all other applications using the MP500 driver from the default repository.  This printer is set as my default printer and works properly via either USB or Bluetooth for everything but Firefox.

I scoured the forum archives and tried deleting the jacascript firefox preferences file but this did not solve the problem; print preferences still do not hold between print jobs.

I have used and enjoyed Ubuntu previously, but am a newbie when it comes to working on the foundations of the OS or solving problems, and am grateful for any help you might provide.  Thanks in advance for all efforts.

---

### Post by pcm_man on 2010-01-16
I am having the exact same problem.   Everything I print from within Firefox is now too light unless for every print job I specifically set the print resolution manually.

What is the fix for this!  It is driving me crazy.

---

### Post by adusty on 2010-01-26
I suffer the same problem! :icon_frown:

Do you know if there already is a bug report for that issue?

---

### Post by Merk42 on 2010-01-26
First thing I would do is make sure you have all your updates.  If you're running 3.5.3 you clearly don't as currently the most recent in the default repos is 3.5.7

---

### Post by adusty on 2010-01-27
Of course I run version 3.5.7+nobinonly-0ubuntu0.9.10.1 which is the latest official in (k)ubuntu.

Don't you suffer the same problem?

---

### Post by DocDanW on 2010-01-28
Yep; updated to Firefox 3.5.7 and the problem persists as noted in my initial post.  I do so wish I could resolve this problem; it is terribly frustrating when it is the sole flaw in an otherwise great OS experience.  I use my Linux partition on this machine primarily for web-surfing (I have to use Windows for some proprietary software that will not run under Wine), and that is effectively no longer possible with Firefox, since printing has become such a hassle.  Invariably, I will forget to reset my preferences *every* time I print, and so I end up cursing as I mis-print and re-print.    What's worse, it also affects three other computers in my care that are used by newbies who basically just want Ubuntu for surfing.  It is hard to explain to them why they can no longer "print as they used to".  They want me to "make it better" and in this case I cannot (yet).  This does indeed seem to be a problem (for me) specific to using Firefox 3.5x or greater with Ubuntu, and the problem is the same when running from a Live disk as from a dedicated partition.  All other applications work fine with the same print driver.  Only in Firefox do changes in print settings fail to hold past the present print session and default (in my case) to the draft setting of the print driver.  For that matter, changes I make to the print settings in about:config also do not "take" and reset themselves after one go.  I've tried everything to troubleshoot and address the problem from the Linux/Ubuntu and Firefox end of things, with no luck from support files or forums. It doesn't appear as if a user-preference file, numbered.js file, or bad prefs.js file are responsible, and I am baffled as well as frustrated.  This seems to be a problem that affects other users similarly.  I hope we can find a resolution soon!

---

