---
title: "Should I Ubuntu-up my PC too??"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by FuneralQueen on 2009-07-25
Hi there :)

I recently installed Ubuntu onto my laptop (after removing windows completely) and I'm absolutely loving it!

I also have a PC (which I like to consider my power pc heh) which i use to record music and occasionally game. I've played around with the Linux sound software packages (adour, etc) but I'm still much more fond of Adobe Audition.

So my question is - would I be able to use Audition with Wine on my PC? Or would it lag?
It's got 4gigs of RAM and a quadcore 2.4GHz (32 bit system).

Any help would be appreciated :)

Thanks!

---

### Post by nmaster on 2009-07-25
check at [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by Commisar Jimp on 2009-07-25
As long as you've got the memory for it I don't see a reason not to just set up a partition and run both, at least until you've made sure everything works out.

---

### Post by philcamlin on 2009-07-25
i got this from a site 


I have been successfully using Adobe Audition 1.5 in Ubuntu 7.04 with Wine 0.9.40 and now, 0.9.41. The only problem is that all tool bar buttons are vertically squished.... but all of the equivalent menu functions work just fine. :smile:

---

### Post by nmaster on 2009-07-25
> **Commisar Jimp said:**
> As long as you've got the memory for it I don't see a reason not to just set up a partition and run both, at least until you've made sure everything works out.

you could also try wubi to check if "everything works" . wubi would be easier that setting up a new partition.

---

### Post by llamabr on 2009-07-25
Wine is very rarely the solution.  If there's some MS application you depend on, then you need to run a MS OS.

Rather, for whatever you want, there's likely some native GNU application.  If you tell us exactly what you want to do, we could help you find it.  Otherwise, I'd keep your PPC.

---

### Post by Zero++ on 2009-07-25
Back up your files and duel boot! Ubuntu talks very nicely with NTFS so you could make a minimal Ubuntu Partition and use your NTFS drive for music and video storage

---

### Post by FuneralQueen on 2009-07-25
Wow!
I never knew about this Wubi thing (I'm new after all heh)
Thank you guys, so much. This forum is so helpful :)

---

### Post by deadspider187 on 2009-07-25
> **llamabr said:**
> Wine is very rarely the solution.  If there's some MS application you depend on, then you need to run a MS OS.

Rather, for whatever you want, there's likely some native GNU application.  If you tell us exactly what you want to do, we could help you find it.  Otherwise, I'd keep your PPC.

I agree with you on this one.  I use my laptop running Linux parallel to my work laptop with Windows, and even though I rarely use the windows box, I don't go anywhere work-related without it.  You just can't put all your eggs in the Linux basket when everything you work with depends on Windows.

---

### Post by ssdt on 2009-07-25
You can also try vitrualbox which will have Windows right inside your Ubuntu. So that would not be any problem to run Windows applications.

---

### Post by Matthewthegreat on 2009-07-25
Sorry, but I don't think audition will work with Wine unless you have version 1.5.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2538]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2538")

---

### Post by Garrovick on 2009-07-25
If one already has Windows and needs to run a Windows app or two, just keep a small Windows partition.  Unless one only has Linux, Wine is about useless.

---

### Post by k3lt01 on 2009-07-25
> **Garrovick said:**
> If one already has Windows and needs to run a Windows app or two, just keep a small Windows partition.  Unless one only has Linux, Wine is about useless.
A small Windows partition? From my experience Windows has great difficulty with anything less than 15GB while my Ubuntu is on a 10GB partition and has 6GB of free space to expand.

WINE is ok for some things and not for others. It is really on a band-aid fix unfortunately and any upgrade in WINE can break a program that was working with a previous version.

It may be a good idea to ask or search, in one of the 2 Multimedia sections of the Main Support Category what program others use and why do they use it? They may be able to give you some tips on how to work your way around things you have difficulty with so the native Linux program behaves just as Adobe Audition does in Windows.

---

