---
title: "Out on the Street"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by Langstracht on 2009-10-08
I think this belongs here (i.e. that this is an OS problem) but, if not, if someone can suggest a more appropriate place ...

I am having a problem with Google Streetview.

It seems that everything "works" except for the street view image itself.  The moving box works (zooms and moves around). The box goes half screen or disappears.

But the street view image is steadfastly black.

I've been all over Google help sites and have deleted cookies and emptied caches and tried to put the view on a different page than the map ... all to no avail.

Does anyone have a solution? (ubuntu 8.04, Firefox 3.0, Flash 10.0)

---

### Post by lavinog on 2009-10-08
What video card are you using?

---

### Post by Langstracht on 2009-10-08
I guess I should have said that I am using a Toshiba Satellite lap top - sorry for the omission.  So it does not have a video card per se.  It "runs" with an ATI Radeon Mobility 7000 IGP chip off the motherboard.

Perhaps I should add I have no other video issues at all.  Far as I know everything runs/displays properly regardless of file type.

---

### Post by starcannon on 2009-10-08
That is now a legacy card, and ATi has dropped support for it. That said, the default drivers in Ubuntu work pretty good, as you have mentioned. It may be possible to tweak your xorg.conf file to get that working; I'll try doing a little googling and see if I come up with anything in direct regards to ATI 7000 igp, Ubuntu, and Google Maps Streetview.

GL

P.S.
This is all I was able to dig up, though it may be of value: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Langstracht on 2009-10-08
Yeah I'm aware of it's, well, limitations (like no Boxee for me!) but, that aside and as I said, no probs with anything else.

Appreciate you looking into this.

Thanks so much.

---

### Post by Langstracht on 2009-10-12
This message intended for starcannon.

I was going on the basis that, despite your "p.s.", you were going to trawl the 'net and see if you could find anything helpful to my situation.

Seeing it's been a number of days, I'm wondering "did I get that wrong?"

Help would be wonderful if you can find me any ...

---

### Post by lavinog on 2009-10-12
[s]Have you tried empting your cache?[/s]
Edit:  oops missed that part in your first thread.

What is the full version number of flash?

Also since you are using hardy, you should be able to update the proprietary fglrx driver to 9-3 (The last version to support your card.)  Or you might want to update to a more recent version of ubuntu.

---

### Post by Langstracht on 2009-10-12
Thanks for picking up on the thread.

Flash version is 10.0.32.18-1hardy1.

I didn't know about fglrx.  But having "checked it out" I am wondering if maybe that is my problem.  Synaptic "report" attached.

As for upgrading, I've had good success sticking with LTS releases and was intending continuing that practice.  Probably for no other good reason than fear.  Stupidity.  Whatever.

Then again if the answer is in fglrx!  I gotta dsay though it's not even clear to me which of the six files I "need".

Thanks in advance for much appreciated help.

---

### Post by lavinog on 2009-10-12
I think you can use the hardware manager in the system, administration menu

---

### Post by Langstracht on 2009-10-12
Well, based on the attached, I'm not sure ... I don't see any place to add "new" ones ...

---

### Post by lavinog on 2009-10-13
I apologize, the fglrx driver never supported the 7000 series.

---

### Post by Langstracht on 2009-10-13
Pity.  But no problem.

Any other action that you think I might be able to take?

Is there reason to believe that 8.04 is in fact the cause of the problem?

---

### Post by lavinog on 2009-10-13
Maybe you can try a live cd of karmic to see.

---

