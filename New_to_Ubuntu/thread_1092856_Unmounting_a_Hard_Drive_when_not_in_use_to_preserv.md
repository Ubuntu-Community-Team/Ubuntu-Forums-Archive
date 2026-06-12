---
title: "Unmounting a Hard Drive when not in use to preserve integrity?"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by DBrocks on 2009-03-10
Well, at 15 years old, I have succeeded in becoming the Network Manager at my house :D I am running a file sharing server, and have 2 500 gig HDDs in it. One for file sharing, and one for backing up files on the family computer, which contains lots of critical information. This server runs 24/7, with both HDDs mounted 24/7. Currently, the family computer (Windowze) runs incremential backups via This nifty Rsync wrapper I found called DeltaCopy. every 24 hours. The drive hosting the shared files MUST be mounted 24/7. However, the backup HDD only needs to be mounted for about half an hour a day for the backups. Now, my question is: Is it better to leave the backup hard drive mounted all the time, or unmount it when not in use. It seems like un-mounting it when not in use, would preserve integrity in the HDD. However, I'm worried the constant mount/unmounts would cause excessive wear/tear on the drive. It's critical that that HDD keep in good condition. Thanks!

---

### Post by Defrector on 2009-03-10
In my sort-of-educated opinion, leaving it mounted is probably better *given that the drive is protected from overheating and vibration*.

I've had some drives which were securely installed into the machine run perfectly for a long time (7 years and still going, after bought refurbished- no bad blocks yet!) and others which got very hot, or were moved alot (including while running) which wore out very quickly (3 years, lots of lost data). It appears that physical stress and temperature is a bigger deal than the stable constant running of the drive. And like you suspect already, spin up/down can wear the drive.

Of course there's always the luck factor... some drives are going to junk out no matter what.:P

On a side note, you can probably set up the drives' power management capabilities to spin down automatically after X minutes of inactivity, without un-mounting them (they should automatically spin up when a request is received.)

EDIT: Another thing which can mess up drives is power outages, though some drives handle them better than they used to. The head inside the drive would go all crazy and sometimes would damage the surface of the drive.

---

### Post by kerry_s on 2009-03-10
in your fstab use the "noauto" for that drive. it will then become like a removable where you click to mount and right click> unmount when your done. i wouldn't worry about wear a tear, as you say it's only mounted once a day.

the best thing is to use a external for backups, inside the computer is just not as safe, it could short, power spikes, etc...
i use a external to back up once a week, i use a thumb drive in between.

---

### Post by DBrocks on 2009-03-11
> **Defrector said:**
> 
EDIT: Another thing which can mess up drives is power outages, though some drives handle them better than they used to. The head inside the drive would go all crazy and sometimes would damage the surface of the drive.

Well, that, I'm not too worried about. See, A few years back, my family picked up an APC UPS, which has USB support. I found a driver, and my server can monitor the battery level left in it via USB. It's pretty sweet. When it runs down to the last 5% of battery power, it sends me a text telling me its going down, then it sends out shutdown commands to all computers on the network, and shuts itself down safetly. Im not concerned about voltage spikes/surges/outages do to this high quality UPS.

---

### Post by SamNSane on 2009-03-11
Please take my word for it. No UPS (or any other kind of protection) will protect that system from lightning or strong EMF coupling which strikes the power supply chain anywhere near you. If such a thing happens then a "backup" drive that is connected internally OR externally to the same system will almost certainly be as cooked as the primary drive.

If data is truly critical, the admin has to make development of an appropriate backup strategy the highest priority consideration. A proper backup strategy for personal family data that is truly indispensible may involve various technologies, but it will always include backups to external media, copies of which will be kept in remote (from the server) locations. As in a different building / town / maybe even state / country. Really. Think lightning strike followed by fire. Are you safe? If not, do something about it. It's not really that hard, but it is probably one of the more boring features of systems administration. I imagine that's why it gets done so poorly so often.

If you analyze your data types you will find that some of the data is certainly not critical. But the subset of data that is crucial to the well-being of your family or "memories" type stuff is something that you want to protect to the best of your ability -- especially since computers make that so easy to do. Years ago, if the house burned it took all of your keepsakes with it. These days, at least the stuff you've scanned (or which was digital in the first place) can be almost impossible for fate to take from you.

Well, unless we have a nuke war or something.

;)

---

### Post by kerry_s on 2009-03-11
:lolflag:
a cup of soda got mine, went right down the blow hole fried it all.

just do your best, but backup your backup. if you have a dvd burner and rw dvd, you can use that to backup the drive. trust me having more than 1 backup can save you.

---

### Post by DBrocks on 2009-03-11
> **SamNSane said:**
> Please take my word for it. No UPS (or any other kind of protection) will protect that system from lightning or strong EMF coupling which strikes the power supply chain anywhere near you. If such a thing happens then a "backup" drive that is connected internally OR externally to the same system will almost certainly be as cooked as the primary drive.

If data is truly critical, the admin has to make development of an appropriate backup strategy the highest priority consideration. A proper backup strategy for personal family data that is truly indispensible may involve various technologies, but it will always include backups to external media, copies of which will be kept in remote (from the server) locations. As in a different building / town / maybe even state / country. Really. Think lightning strike followed by fire. Are you safe? If not, do something about it. It's not really that hard, but it is probably one of the more boring features of systems administration. I imagine that's why it gets done so poorly so often.

If you analyze your data types you will find that some of the data is certainly not critical. But the subset of data that is crucial to the well-being of your family or "memories" type stuff is something that you want to protect to the best of your ability -- especially since computers make that so easy to do. Years ago, if the house burned it took all of your keepsakes with it. These days, at least the stuff you've scanned (or which was digital in the first place) can be almost impossible for fate to take from you.

Well, unless we have a nuke war or something.

;)

Hey, thanks. Well, this is what I've been looking at: Hot-Swapable drive bay from newegg for about $20. For $20, I can push the drive in when I need it, remove it when I dont, and ship it out to a safe location when not in use. I think this is a much better tactic. And thank's alot for your concern.

---

### Post by SamNSane on 2009-03-11
> **DBrocks said:**
> Hey, thanks. Well, this is what I've been looking at: Hot-Swapable drive bay from newegg for about $20. For $20, I can push the drive in when I need it, remove it when I dont, and ship it out to a safe location when not in use. I think this is a much better tactic. And thank's alot for your concern.

Sounds like a plan.

Some folks think I'm paranoid, but I could tell you some stories about several months' worth of data loss in a hospital back in the days of the Jerusalem B virus. (I'm delighted to say I had warned them about "rotating" backups. I'm sorry to say they didn't listen.)

Plus, the lightning is definitely out to get me and my whole family.
1. One of my uncles was killed by a lightning strike while riding his horse.
2. I was in a pickup that was struck directly by lightning, causing the rear axle to actually become embedded in the asphalt -- not to mention what it did to my hearing.
3. I've been involved in three forced landings due to lightning strikes on aircraft.
4. A medical data center I ran years ago got creamed by a direct lightning strike, despite the best protection we could get installed.

I spend a lot of time crawling on my belly and looking up at the sky.

Well, not really. But I do try to be careful.

---

### Post by LowSky on 2009-03-11
SamNSane is a human lightning rod... lol

Ok for Personal stuuf get a fireproof safe and make copies to DVD's or CD's. this is family stuff not government secrets dont go overboard! Unless your the Royal family to some nation...LOL

I dont really recommend using a hard drvie or flash as a storage method, they can be wiped or damage much easier than DVD type media. a Tape Drive back up would be ideal, but is very time consuming especially looking for data.

So I say do DVD back-ups of important pictures, documents, and music, or videos maybe once a month or a week if your over zealous. 

In my house we like to live on the edge, No backups, No surrender!

---

### Post by DBrocks on 2009-03-11
Lol. But the thing is, is that my dad is a photographer. And he uses that computer for storing all his pictures. If we were to loose this, then one of our sources of income is down for the count. Now, what you said about CDs/DVDs. Since he's a professional photographer, most of the data on our computer is pictures. (250-270 gigs). Thus, DVDs are out of the question, and tapes are def out because of their high starting cost. Rotating backups with HDDs may be the only way to go at my house.

---

### Post by SamNSane on 2009-03-11
> **DBrocks said:**
> Lol. But the thing is, is that my dad is a photographer. And he uses that computer for storing all his pictures. If we were to loose this, then one of our sources of income is down for the count. Now, what you said about CDs/DVDs. Since he's a professional photographer, most of the data on our computer is pictures. (250-270 gigs). Thus, DVDs are out of the question, and tapes are def out because of their high starting cost. Rotating backups with HDDs may be the only way to go at my house.

Yup, you need off site storage. I use a combination of safety deposit boxes for physical media and online storage (commercial, but free is available).

As for fire protection within the home. "Fireproof" safes aren't really fireproof. I have a couple of reasonably high quality ones, and they'll do a decent job of saving documents on paper -- but only up to a point. Will they keep data on optical media or removable hard drives safe in a serious fire? Maybe, if you're lucky. If you read the information provided by those who produce these safes they tell you how hot they get inside with a given type and duration of fire exposure. Many of the best-performing ones release moisture into the interior of the safe as an added protection measure. Between the heat and the moisture, the medium which stands the best chance of surviving would probably be DVD or Blue Ray. Tape would be the worst. I'm thinking 400 degrees F on a hard drive would probably not be okay. Controller failure at the very least.

Speaking of which, Blue Ray would appear to be the most cost-effective answer for you. At 50 gigs, give or take, per disc, you're talking about a reasonable backup effort and cost when done once-in-a-while. That small investment will provide for maximum data safety if copies are kept off site as well as on. The discs themselves are also supposed to be pretty reliable. (Obviously, I haven't had to pull data off of any 10 year old BD discs yet.)

---

### Post by SamNSane on 2009-03-11
> **LowSky said:**
> SamNSane is a human lightning rod... lol

The combination of that droll comment plus your nickname is making the hair stand up on my neck.

;)

> 
In my house we like to live on the edge, No backups, No surrender!
[/QUOTE]

I admire your sense of adventure, sir. I'll probably emulate you -- once I retire -- which should have been 20 years ago!

---

