---
title: "ventrilo"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by F@#k WINDOWS!! on 2009-02-22
i am a total noob. im here because as you can porobably tell ive had it with windows. ive had some problems that i will probably bring up later but my main concern right now is ventrilo. i have read threads all over the web and i just cant get it to work. it says it cant find the specified codec. i have no sound whatsoever. ive repeatedly reied to follow other threads and i cant seem to fix the problem...maybe someone can give me a plain talk walkthrough on getting vent to work.

---

### Post by Zoquara on 2009-02-22
Install WINE (not sure what version of Ubuntu you're running)
If you're running 8.04 (and it might work in later, I really have NO idea) go to Applications> Add/Remove... In that, Show: All available and do a Search for : Wine
Select it (Should say Wine Windows Emulator) and install.
Next, download, and install the Windows version of Ventrilo, and install it. I've had no problem getting mine to work that way, other than a few sound issues.

---

### Post by F@#k WINDOWS!! on 2009-02-22
hmmm i have wine ill try downloading vent again though  thanks

---

### Post by Zoquara on 2009-02-22
Not a problem... try not to get frustrated while learning Ubuntu... I have to keep reminding myself that!

---

### Post by F@#k WINDOWS!! on 2009-02-22
I reinstalled it im still getting the same -cant find specified codec- message thanks for trying to help though and yeah learning ubuntu is a little frustrating but not nearly as bad as just using vista!!!! Lmfao

---

### Post by raydeen on 2009-02-22
This is just a guess, but do you know that the server you're connecting to supports the Linux client? Case in point: The WoW guild I'm in rents a Vent server in Va. but only the most basic Vent setup. If I or another of our members attempts to connect with a Mac Vent client, it won't work because the server doesn't support the codec uesd by the Mac (or the Mac doesn't support the codec used by the server - not sure which). I'm not very familiar with Vent but this was the explanation given by our guild leader. Hope this helps you track down the problem.

Edit: Nevermind all that. I just looked and there doesn't seem to be a Linux client yet. Something else to try: 

[http://www.codeweavers.com/compatibility/browse/name/?app_id=413;tips=1](http://www.codeweavers.com/compatibility/browse/name/?app_id=413;tips=1)

Apparently there's some luck getting Vent to run in Crossover (commerical offshoot of WINE). You'll have to pay for Crossover after the trial period, but it might be worth it if it works.

---

### Post by F@#k WINDOWS!! on 2009-02-22
thanks but no its a windows based server im the only one who switched to linux   vent seems to be dragging their heals with making the lunux based client although they have the server...although being the guild leader i suppose i could talk to our it person and get them to try the linux server and see what kind of issues arrise...i hadnt thought of that thank you...enjoy wow i play guild wars you should check it out sometime

---

### Post by F@#k WINDOWS!! on 2009-02-22
i will check out codeweavers thanks im desperate at this point ive been working on this for a week and im sure the members of my guild are missing my voice lol   thanks again

---

### Post by Zoquara on 2009-02-22
Someone else set up my guild's Vent server, but they set it up a certain way so that Mac users could use it too... It's using the Speex codec, if I remember correctly, and I haven't had a problem with it telling me I was missing a codec... so maybe look into reconfiguring the server?

---

### Post by raydeen on 2009-02-23
Yeah, I play GW now and again. :) In any event, try Crossover (it's free to try at any rate - [http://www.codeweavers.com/products/](http://www.codeweavers.com/products/)). The page I linked was for the Mac version, but I'd think the Linux version of Crossover should work as well. You're still basically tricking Vent into thinking it's on a Windows machine, but it might be more compatible than WINE atm for this app.

---

