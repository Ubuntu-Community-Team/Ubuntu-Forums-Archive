---
title: "laptop indicates critical battery and suspends. why is it lying to me?"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by SebSmith on 2011-03-02
hi i am a novice ubuntu user. 

my brand new envy 14 with 10.04 LTS tells me my battery is at a critical level and suspends even when i click cancel. this happens no matter what capacity my battery is, even freshly charged.

how i can i fix this?

thanks in advance

---

### Post by FoxEWolf on 2011-03-02
My thoughts are that the battery is improperly calibrated. my other thought is that the battery is failing in general.

---

### Post by matt_symes on 2011-03-02
Hi

> my brand new envy 14 with 10.04 LTS tells me my battery is at a critical level and suspends even when i click cancel. this happens no matter what capacity my battery is, even freshly charged.

Did you buy it with Ubuntu installed ? If you did and it is still under warranty then take it back and let them do the hard work.

Kind regards

---

### Post by SebSmith on 2011-03-02
> **FoxEWolf said:**
> My thoughts are that the battery is improperly calibrated. my other thought is that the battery is failing in general.

the battery is not broken. it works fine on win 7. the problem seems to be ubuntu causing a problem when the laptop gets plugged in.

---

### Post by FoxEWolf on 2011-03-02
well then I would return the laptop to whomever you got it and let them diagnose it. Was this laptop equipped with Ubuntu before you touched it?

If not then re-install ubuntu and see what that does, but this time use a new disc.

---

### Post by SebSmith on 2011-03-02
> **FoxEWolf said:**
> well then I would return the laptop to whomever you got it and let them diagnose it. Was this laptop equipped with Ubuntu before you touched it?

If not then re-install ubuntu and see what that does, but this time use a new disc.

i just did a fresh reinstall yesterday with a new disc. 

no it came with win 7. i did dual boot install

---

### Post by Vi3tHoneyX on 2011-03-02
[COLOR=darkred]Maybe [/COLOR][[COLOR=darkred]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1631980")[COLOR=darkred] will help?[/COLOR]

---

### Post by pieisgood4589 on 2011-03-02
> **FoxEWolf said:**
> well then I would return the laptop to whomever you got it and let them diagnose it. Was this laptop equipped with Ubuntu before you touched it?

If not then re-install ubuntu and see what that does, but this time use a new disc.

The problem isn't with the physical machine, only with Ubuntu misdiagnosing the battery condition. 

I'm going to assume that you checked the MD5 on your .iso and burned it properly. 

A bit of Googling brought me to this thread which could shed light on your issue-
[http://ubuntuforums.org/showthread.php?t=1543467](http://ubuntuforums.org/showthread.php?t=1543467)

---

### Post by mikewhatever on 2011-03-02
> **SebSmith said:**
> the battery is not broken. it works fine on win 7. the problem seems to be ubuntu causing a problem when the laptop gets plugged in.

So, when you plug in the power cord the laptop suspends?
What's envy 14?

---

### Post by SebSmith on 2011-03-02
> **mikewhatever said:**
> So, when you plug in the power cord the laptop suspends?
What's envy 14?

hp envy 14 beats edition laptop

---

### Post by pieisgood4589 on 2011-03-02
> **Vi3tHoneyX said:**
> [COLOR=darkred]Maybe [/COLOR][[COLOR=darkred]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1631980")[COLOR=darkred] will help?[/COLOR]

> **pieisgood4589 said:**
> The problem isn't with the physical machine, only with Ubuntu misdiagnosing the battery condition. 

I'm going to assume that you checked the MD5 on your .iso and burned it properly. 

A bit of Googling brought me to this thread which could shed light on your issue-
[http://ubuntuforums.org/showthread.php?t=1543467](http://ubuntuforums.org/showthread.php?t=1543467)

Have you checked out these two forum links yet? They might provide you with an answer.

---

### Post by SebSmith on 2011-03-02
> **pieisgood4589 said:**
> The problem isn't with the physical machine, only with Ubuntu misdiagnosing the battery condition. 

I'm going to assume that you checked the MD5 on your .iso and burned it properly. 

A bit of Googling brought me to this thread which could shed light on your issue-
[http://ubuntuforums.org/showthread.php?t=1543467](http://ubuntuforums.org/showthread.php?t=1543467)

as i have indicated, i am a novice so i dont know what md5 is.

perhaps i am describing the issue wrong.

HERE: my battery charges and discharges fine. however, everytime  i plug in my ac adapter (regardless of battery level) i get a pop up saying the battery is at a critical level as is suspending. this causes me to have to close the lid and unsuspend every single time i decide to recharge my battery (even if the level is at lets say 80%).

---

### Post by SebSmith on 2011-03-02
> **pieisgood4589 said:**
> Have you checked out these two forum links yet? They might provide you with an answer.


the first one is a completely a different issue and helps me in a different way.

the second is an issue that i am not having.

---

### Post by pieisgood4589 on 2011-03-02
Ah, after describing the issue again, I think I understand.

I had a client with a MSI Wind u100 netbook loaded with Ubuntu that had this exact problem. Even with a fully charged battery, once you unplug it from the power source, Ubuntu displays a popup warning that the battery level is critical, and the computer suspends/hibernates.

If you want to circumvent the problem for now, you can run System->Preferences->Power Management and go to the On Battery Power tab.

The entry for 'When laptop lid is closed' is the behaviour that gets acted when you remove your AC cable. I've changed it to 'Blank Screen' for now, as I can live with that. It seems that to my knowledge and to Google's that this is a bug that is currently being worked on.

Some reported success with updating the GNOME Power Manager tool, but that was around 8.04, and might not work with the newer versions of Ubuntu.

---

### Post by SebSmith on 2011-03-20
the problem is when is that ubuntu gives a pop up message that battery level is critical when i PLUG-IN the ac adapter. unplugging doesnt give me a problem. everytime i PLUG IN to recharge, my computer suspends. how can i fix this?

---

### Post by SebSmith on 2011-03-27
bump


problem is still persisting

---

