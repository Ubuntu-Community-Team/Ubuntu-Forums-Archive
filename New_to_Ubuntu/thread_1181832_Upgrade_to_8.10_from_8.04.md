---
title: "Upgrade to 8.10 from 8.04"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by newport_j on 2009-06-08
I am trying to upgrade my Linux Ubuntu to 8.10 from 8.04. I believe the 8.04 version is LTS. I forget what that means, but I believe it is long term support. I do not know if Ubuntu 8.10 is LTS. so this may not be a wise move. I just think it is time to upgrade to 8.10. 

Anyway, it has problems with my graphics card and driver. It says that there is no driver for my card in 8.10. Is there a way around this? Is this even a problem? What can I, should I do?

My graphics card is :
 
Geforce4 MX440 with AGP8X.

The monitor is Dell E207WFP.
 
Any help appreciated.


Respectfully,

Newport_j

---

### Post by Celauran on 2009-06-08
Having 8.04 on my laptop (which sees the most use) and 8.10 on my desktop, I'd strongly advise sticking with 8.04. Moreso because 8.04 is LTS.

---

### Post by reeseslover531 on 2009-06-08
well 9.04 is out as well, have you tried booting the live cd of 9.04 to see if things work?  Hopefully they will.  In all honesty unless there is a major thing not working in 8.04, there isn't much of a reason to update.  OpenOffice is updated to 3.0 in 9.04, which might be nice but you can get that from a [PPA]("http://ubuntu-snippets.blogspot.com/2008/10/ppa-for-openofficeorg-30.html").

---

### Post by 123456789123456789123456 on 2009-06-08
Last report was that 9.04 was out, and it works great, on most machines i have installed it on.  The next LTS version is 10.04 I believe.  which comes out next year.  You can stick with 8.04 and upgrade directly to 10.04 I understand, but that usually causes problems for some reason, possible due to the amount of files that needs to be removed.
Best option is to keep 8.04 as a backup, use a utility like ghost boot, to create a complete backup, upgrade to 8.10, which will soon be taken away, as it's support is comming to an end, after sucessful upgrade to 8.10, upgrade to 9.04.  You can upgrade to 9.10 when it comes out in october.  The next LTS version will be released 6 months after that, which would be april, close to the end of april 2010.

---

### Post by Umang on 2009-06-08
I don't think you can upgrade to a not LTS from an LTS out of line. (As in from 8.04 to 9.10). From 8.04 you may only go from 8.10 or 10.04 (which is not yet released).

If you want to go from 8.04 to 9.04, then you will have to go "via" 8.10.

---

### Post by niteshifter on 2009-06-08
Hi,

For some additional info on release timing, see Shuttleworth's [blog post]("http://www.markshuttleworth.com/archives/146").

Just a suggestion here: I'd stay with 8.04. 8.10 has less than a year to live. This month should see the release of 8.04.3 which might be of use to you.

---

### Post by UbuntuNerd on 2009-06-08
LTS is an abbreviation for “Long Term Support”

---

### Post by Umang on 2009-06-12
No, 8.04.3 is not actually an upgrade. If someone has installed 8.04, they do need need to upgrade. It is just that 8.04 has the new packages that 8.04 has been getting and for someone who wants to do a fresh install of 8.04 they should not have to download the full CD and then have to get all the packages upgraded. 

8.04.3 is just 8.04 with the new packages that 8.04 has got. You never need to upgrade from 8.04 to 8.04.3. 8.04.3 is just for fresh instals.

---

### Post by oxf on 2009-06-12
> **Umang said:**
> No, 8.04.3 is not actually an upgrade. If someone has installed 8.04, they do need need to upgrade. It is just that 8.04 has the new packages that 8.04 has been getting and for someone who wants to do a fresh install of 8.04 they should not have to download the full CD and then have to get all the packages upgraded. 

8.04.3 is just 8.04 with the new packages that 8.04 has got. You never need to upgrade from 8.04 to 8.04.3. 8.04.3 is just for fresh instals.

So does 8.04.3 fix any of the querks that one finds in 8.04? For example it took a bit of fidling to get my wireless card (BC43xx) to work under 8.04. I understand this is much improved in 9.04.

---

### Post by Umang on 2009-06-12
If the issue still exists in a completely up-to-date 8.04, I believe 8.04.3 will still suffer from the same problem.


8.04.3, as I said before, is simply released so that people don't have to upgrade the packages using package manager as soon as they install 8.04. To simplify:

Apr 08: 8.04 Released
Apr 08 to now - 8.04 users are provided with upgrades through upgrade manager

If someone installs 8.04 now, then they will have to run the many many upgrades (~200MB) that have been provided, after downloading 700MB and installing 8.04.

8.04.x is released now

If someone wants to download 8.04 they can download 8.04.x which is 8.04 with the new packages that 8.04 users have recieved **after** they installed 8.04 (between Apr 08 to now). So the new user will have the new packages, so will old 8.04 users.

A 8.04.x install is equal to an 8.04 install that has been regularly upgraded using upgrade manager.

---

