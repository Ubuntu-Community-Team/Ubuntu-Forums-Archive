---
title: "Firefox not online on start with dialup - solution"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by anewguy on 2009-10-01
I forgot to post this back in my thread about getting a program to "talk" to a serial modem so I could converse with the modem (see current settings, etc.).

Some of the replies I got in that thread indicated problems with Firefox starting off-line when using a dialup connection.  I know it's been mentioned in threads before, but there is a solution:

- networkmanager doesn't recognize a good dialup connection as a valid network, and Firefox (and pidgen also, I think) gets it's online/offline signal from networkmanager.

The solution:

- via synaptics package manager, install wicd.  This will remove networkmanager and use wicd in it's place.  Wicd seems to pass the online status of a dialup network fine, so Firefox starts in online mode.

I hope this is helpful to someone.

Dave :)

---

### Post by pj_kare on 2009-10-02
Typing about:config into firefox address bar and changing toolkit.networkmanager.disable from false to true (just by double clicking that line) also fixes offline issue. :)

---

### Post by anewguy on 2009-10-03
> **pj_kare said:**
> Typing about:config into firefox address bar and changing toolkit.networkmanager.disable from false to true (just by double clicking that line) also fixes offline issue. :)

Hey, thanks!!  I never knew about that!

Have a good one!

Dave :)

---

### Post by pj_kare on 2009-10-03
> **anewguy said:**
> Hey, thanks!!  I never knew about that!

Have a good one!

Dave :)

You're welcome Dave. Though I don't claim the fix as my own, I found it doing a google search for a fix myself. It was annoying the heck outta me.](*,) Not sure how/if it affects Network though, I don't use a network.:P

---

### Post by theozzlives on 2009-10-03
Who uses dialup nowdays?

---

### Post by pj_kare on 2009-10-03
> **theozzlives said:**
> Who uses dialup nowdays?

We have to! Simply because of where we live. Crappy phoneline means we cant get adsl, (it barely carries dialup) and we can only get wireless through one carrier, who are really expensive. Moving back into town would solve this, but until we do move we have to use dialup.

---

### Post by anewguy on 2009-10-03
> **theozzlives said:**
> Who uses dialup nowdays?

[He gulps, then a small pause] I do......don't have much choice right now as I'm living with my sister and brother in law right now until I get some of my life straightened out.  So, can't afford to get cable broadband now (I *REALLY* miss it!!) so I had to try using my brother in laws' Juno, but I can't it to actually work in Linux, and the machine they have it on for me to use is extremely archaic.  So......I was stuck with the cheapest I could get with no adds, etc. - so I got BasicISP at $6.95/mo.  Obviously it's not what I was used to, but dialup is far better than none at all.  The automatic updates that come out for Ubuntu kill me, however.  What used to be just a couple of minutes on cable broadband is now several hours on dialup, and the connection normally won't stay up that long.  Oh well.

Dave :)

---

### Post by pj_kare on 2010-02-02
Since recently updating to Karmic (Clean Install after creating disc from magazine dvd iso) I no longer have the "Offline" issue with Firefox. HOORAH!!!!!
 
I now have the problem with Evolution, I have to connect manually every time I start it. ](*,)

---

