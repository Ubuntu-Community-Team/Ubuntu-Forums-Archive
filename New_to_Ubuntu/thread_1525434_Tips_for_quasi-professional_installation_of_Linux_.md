---
title: "Tips for quasi-professional installation of Linux for new clients?"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by Nick_Jinn on 2010-07-06
So it looks like I converted someone. I am charging a very small fee for installing Ubuntu on someones old Acer laptop. I am going to set it up nice, get all the drivers and programs he needs, make it pretty and make sure he can get online wirelessly.

       Yeah, so this guy is infected with a virus. He runs a business, but his computer is sending spam emails to all his clients. Its ruining his business, and I think he is finally fed up. He saw my add for Linux and tired of viruses, and I think he is convinced. This is exactly why Linux will keep growing as people become aware of it. He also has a Mac, so Linux should be a little more intuitive than it would be for a Windows only user. I guess his Mac laptop is for home, but the cheaper Windows computer is for work.

       This computer is 5 years old, so I am probably going to install a 32 bit version. Depending on the size of the hard drive we can discuss just using Linux or dual booting windows...I could devote 20gb to windows just in case he needs it for something.


       Anything you would suggest and recommend? This guy has used Mac but never used Linux before.


       This is basic stuff, and I think I can handle it, but getting second opinions never hurt.

---

### Post by warfacegod on 2010-07-06
Set up a separate /home partition. New guys seem to have a fondness for breaking stuff. If all of his business files are on a separate partition, they'll be relatively safe.

Also, test the install *thoroughly* before you give it back and accept payment. I've been down that road before in Windows and Linux and it's a LOOOONNGGGG one to crawl. Trust me, if something isn't quite right, you *will* be crawling. Squirming at the very least.

---

### Post by k3lt01 on 2010-07-06
Check out my signature to see my laptops specs. A word of warning if it is a low RAM system, mine has 256mb RAM, you may have some difficulty installing 10.04 (even off an AlternateCD).

If it is a low RAM system one thing I would do after installation is remove "ureadahead" because if your customer updates his system and it pulls a new kernel or anything that makes ureadahead reprofile the bootup sequence you may be getting some very angry telephone calls. This is because it can cause a ***_massive_*** slow down. Last time I had it on my Acer laptop it took 2 hours to get anywhere near a workable laptop and that was only because at 2 hours I pulled the power on the thing.

---

### Post by Nick_Jinn on 2010-07-06
I doubt the ram is that low, but if it is I have some RAM laying around that I could sell him as an upgrade. His laptop was new in 2005...its not THAT long ago. My laptop from 2005 had 2.2 ghrz Turion 64 processor in it, a dedicated ATI graphics card, and it was only $500. He picked up his Acer is Korea, so it was probably a bargain for good specs.

I guess its possible that this PC is older than he is claiming, but I doubt it has less than 512.

As long as it comes with DDR, I have some memory to upgrade with. Hopefully it comes with DDR2.....did they have DDR2 in 2005 laptops?

---

### Post by HermanAB on 2010-07-07
If the PC is old, then the disk is probably small.  So make a complete copy of the whole disk before you start.  

Better: Get him a new (or used) disk and keep the present one on your own desk for some time - since he may want to go back to his infested system, or may need a copy of last year's tax return or whatever.

---

### Post by Nick_Jinn on 2010-07-07
I think this guy picked me because I am cheap....Around these parts I am a total noob, but to my family I am the guy who fixes everyone's computer. I am somewhere inbetween this guy and most of the techs around here.

I am only charging $40 to help this guy out, save his files and install linux. He may or may not want to invest a bunch of money into the computer. If he does I want to give him a fair deal and only charge him for what I actually spend.


I am not really a computer tech, just someone who has troubled shooted their own problems a lot and can definitely do a linux installation with some customizations and introduce somebody, get their wireless working and all that. He isnt asking for anything too complicated, so its within my skill range....this is more of a hobby/experiment for me...but maybe it will go somewhere and I will end up getting good.

---

### Post by Paqman on 2010-07-07
> **Nick_Jinn said:**
> 
       Anything you would suggest and recommend?


That really depends on exactly what your client needs. What kind of an environment is the machine operating in? Do they need something like Zimbra to replace Outlook? Or is this just a standalone machine for a sole trader? What apps is he going to need, and what sort of documents are they likely to be handling from their clients? And who is going to be providing support for this? You? Them?

The more info you can give us, the better advice we can give you.

---

### Post by Nick_Jinn on 2010-07-07
Sounds like he uses it for email and web surfing and keeping in touch with his clients, and anything intensive he is using his newer Mac for. I guess his current PC has a virus and is sending malicious spam through a POP client or something.


Sounds pretty straight forward, but I want to make it nice for him with as few hiccups as possible.

---

### Post by Paqman on 2010-07-07
> **Nick_Jinn said:**
> 
Sounds pretty straight forward

Indeed it does. You might want to ask if he has any preference about what browser and email apps he wants to use.

Email-wise you've got a few options. The default is Evolution, which has the advantage of having a calendar. The main alternative is Thunderbird, which you can add a calendar to if you want. If he uses webmail then install the package desktop-webmail, which helps to integrate Gmail/Hotmail/Yahoo/whatever into the desktop a bit better.

He's also likely to need word processing/spreadsheets (at least so he can open attachments). By default this will be Open Office, which should be fine.

You could Mac-ify the desktop a little to make it a bit easier to switch between the two machines. Mac-style docks like Avant Window Navigator are very popular, and extremely useful. Just remove the bottom panel and install AWN. You might want to install something like Dropbox or sort out folder sharing across the network between the two machines.

---

### Post by Nick_Jinn on 2010-07-07
Sounds good.


I am thinking I should download some introduction to Ubuntu and Linux books and leave them conveniently on his desktop, along with a link to this place. 


I was considering giving him something with the Enlightenment desktop, since he seems to prefer mac, though I hear Enlightenment is still buggy.

Does anyone like GOS? I prefer Ubuntu of course, but I think Gnome is more functional as a desktop for standard computers, while E17 will excel when it gets touch screen support.

---

### Post by philinux on 2010-07-07
> **Nick_Jinn said:**
> Sounds good.


I am thinking I should download some introduction to Ubuntu and Linux books and leave them conveniently on his desktop, along with a link to this place. 


I was considering giving him something with the Enlightenment desktop, since he seems to prefer mac, though I hear Enlightenment is still buggy.

Does anyone like GOS? I prefer Ubuntu of course, but I think Gnome is more functional as a desktop for standard computers, while E17 will excel when it gets touch screen support.

I reckon this guy will be phoning you a lot. ;)

---

### Post by k3lt01 on 2010-07-07
> **philinux said:**
> I reckon this guy will be phoning you a lot. ;) I agree.

It may be a idea, and yes I realise you are only charging $40 for this entire service, to spend some time with him showing him around his "new" system. Show him things like the email program, web browser, relevant links, Office applications etc. Help him migrate his email and other net settings like bookmarks etc. I think that you will gain alot of customer goodwill by doing this and also you will have personal peace of mind because you will know he has seen his system working and has used it with you there.

---

### Post by Nick_Jinn on 2010-07-07
Totally. I am going to spend a whole hour with him when I get his laptop fixed up and show him around.

---

### Post by Paqman on 2010-07-07
> **Nick_Jinn said:**
> 
I am thinking I should download some introduction to Ubuntu and Linux books and leave them conveniently on his desktop, along with a link to this place. 


He's probably got better things to do than rummage around in manuals. Set it up to be 100%, then back up what you've done yourself. If this guy is paying to not have to sort it out himself, then don't expect him to. If you're worried about committing to a lot of work for your $40, then tell him you'll provide a certain amount of free support, but after that you'll have to charge him. The software is under a free licence, but that doesn't mean he should expect infinite amounts of skilled technical help for nothing.

> 
I was considering giving him something with the Enlightenment desktop, since he seems to prefer mac, though I hear Enlightenment is still buggy.


This is a production machine, be _very_ conservative in your choice of software. The primary consideration should be stability, not features.

Install an LTS release, set it to show LTS updates only and have the security updates install automatically. Maybe enable backports. You want this machine to be stable and reliable with minimal fuss for several years.

---

### Post by kevinatkins on 2010-07-07
> **Paqman said:**
> This is a production machine, be _very_ conservative in your choice of software. The primary consideration should be stability, not features.

Install an LTS release, set it to show LTS updates only and have the security updates install automatically. Maybe enable backports. You want this machine to be stable and reliable with minimal fuss for several years.
Couldn't agree more here. I'd be inclined to limit any sort of customization attempts - leave the stock Ubuntu desktop as it is, perhaps just adding a few links on the desktop to useful information.

You mention that your client has suffered a virus and he is 'spamming' clients from his email account. It's also quite possible that it isn't a virus as such and that his email address has simply been harvested - it's quite a common technique of spammers to use lists of harvested emails from which to 'send' junk (ie, to masquerade as your client). So do be aware that simply installing Linux may not stop the spam from happening...

On the subject of emails, I have found Evolution to be a touch unstable / buggy over the last couple of releases and it doesn't seem any better in 10.04LTS.. I'm looking at Thunderbird instead, with the Lightning calendar extension - you might want to consider doing the same if ultimate reliability is a concern (which I think it should be here!)

---

### Post by Nick_Jinn on 2010-07-07
I appreciate all of the advice and I will consider all of it.

---

### Post by k3lt01 on 2010-07-07
Nick, it is good to see you making such a concerted effort and also that you asked here for advice. Good luck in your venture.

---

### Post by Nick_Jinn on 2010-07-07
The only thing I am currently stuck on is that he wants me to save his photoshop....which could be a bootleg or maybe not, but it came with the computer and he doesnt want to lose it if he goes back to Windows. He doesnt have a disk for it. 

Is there a way (besides just giving him a pirated copy) of backing up his PROGRAMS on a DVD?

I guess its possible to just get a cracked version of photoshop, but I would rather save the authenticated one he has in a way that does not require re-authentication, because it came with the laptop.

---

### Post by k3lt01 on 2010-07-07
> **Nick_Jinn said:**
> The only thing I am currently stuck on is that he wants me to save his photoshop....which could be a bootleg or maybe not, but it came with the computer and he doesnt want to lose it if he goes back to Windows. He doesnt have a disk for it. I'll refrain from judgement on photoshop except to say if it isn't a bootleg he should know where the details are for it.

> **Nick_Jinn said:**
> Is there a way (besides just giving him a pirated copy) of backing up his PROGRAMS on a DVD?Don't even think about the bracketed option. You could always Ghost his system for him using programs like Nortons/Symantec Ghost. There are others but I don't remember what they are called, I myself have Nortons Ghost.

> **Nick_Jinn said:**
> I guess its possible to just get a cracked version of photoshop, but I would rather save the authenticated one he has in a way that does not require re-authentication, because it came with the laptop.Be very careful, in Common Law jurisdictions Ignorance is not a defensible position. In other words you cannot just say to a judge "oh sorry I didn't know" and expect to get off. You are working on the machine so if you put a bootleg back on it you could get in trouble.

---

### Post by Nick_Jinn on 2010-07-08
> **k3lt01 said:**
> I'll refrain from judgement on photoshop except to say if it isn't a bootleg he should know where the details are for it.


Thats a big assumption. People lose their disks. Thats a fact. It might not be a bootleg because this laptop says that this PC has a full multimedia suite. However, if he cant find the disks or box for it, that is proof of nothing. It could still be a legitimate copy that came with the PC just like he claims.


> **k3lt01 said:**
> Be very careful, in Common Law jurisdictions Ignorance is not a  defensible position. In other words you cannot just say to a judge "oh  sorry I didn't know" and expect to get off. You are working on the  machine so if you put a bootleg back on it you could get in  trouble.

lol. I guess I like to live dangerously. Even if its technically illegal, I doubt they would prosecute if he could prove that he owned a legitimate copy (included in his multimedia suite) before doing so....A lot of things are technically illegal, like growing a few poppies in your garden, but unlikely to be an issue unless you score them (or sell them as new copies).

Anyway, I found the key by searching the files for it from Linux. I didnt actually say I was going to pirate anything. I was just wondering about the copy that was on there, but it looks like its a real copy that came with the PC, which explains the lack of disk....and some people are not that careful with their stuff, so I wouldnt doubt someone even if they said they lost the box for some expensive software.






One stumbling block so far. After restarting, the broadcom drivers seem to disable the internet. When I get rid of the broadcom drivers and restart the internet reappears (but not connects for some reason that could be on my end), but I cant get it to work with the internal drivers enabled and I dont think he wants to sacrifice 1 of his 2 only usb ports for a wireless card.

Broadcom sucks.

Anyway, I want to get him back online with his native broadcom drivers, but the the optional ones under "Drivers" dont seem to be working right. Any suggestions.


This is what he is paying me for (besides saving his files from Linux). A lot of people get frustrated when things dont work and they are not familiar with linux.

---

### Post by k3lt01 on 2010-07-08
> **Nick_Jinn said:**
> One stumbling block so far. After restarting, the broadcom drivers seem to disable the internet. When I get rid of the broadcom drivers and restart the internet reappears (but not connects for some reason that could be on my end), but I cant get it to work with the internal drivers enabled and I dont think he wants to sacrifice 1 of his 2 only usb ports for a wireless card.

Try [this]("http://ubuntuforums.org/showpost.php?p=3996845&postcount=5").

> **Nick_Jinn said:**
> Thats a big assumption.No it isn't actually and you didn't understand my point anyway as is evidenced by the quote below.

> **Nick_Jinn said:**
> People lose their disks. Thats a fact. It might not be a bootleg because this laptop says that this PC has a full multimedia suite. However, if he cant find the disks or box for it, that is proof of nothing. It could still be a legitimate copy that came with the PC just like he claims.I didn't say it wasn't legitimate, I said he should know where the details are for it. I didn't mention disks, nor did I suggest it was a bootleg you did that. If I assumed anything it was because of the information you supplied.

My laptop come with a "full multimedia suite" as well but I didn't have Photoshop.

> **Nick_Jinn said:**
> lol. I guess I like to live dangerously. Even if its technically illegal, I doubt they would prosecute if he could prove that he owned a legitimate copy (included in his multimedia suite) before doing so....A lot of things are technically illegal, like growing a few poppies in your garden, but unlikely to be an issue unless you score them (or sell them as new copies).It is a pity you have such a frivolous attitude towards the law. I don't know where your from, I guessed it would be a Common Law country based on your use of English, what we are talking about here is the possibility of theft, yes bootlegging is theft. Theft of such things is illegal in ALL Common Law countries, Growing Poppies isn't. You are obligated to notify the relevant authorities IF you know something is pirated. If you suspect it which you must because you brought it up in the discussion you should make sure nothing you do can come back at you. It is as simple as that.

> **Nick_Jinn said:**
> Anyway, I found the key by searching the files for it from Linux. I didnt actually say I was going to pirate anything. I was just wondering about the copy that was on there, but it looks like its a real copy that came with the PC, which explains the lack of disk....and some people are not that careful with their stuff, so I wouldnt doubt someone even if they said they lost the box for some expensive software.Again you have missed the point, it isn't whether I doubt someone, you asked for advice and you got it, you brought up about bootleg I gave you a little advice about it. Take it or leave it, that's up to you but don't go making a joke of it. Piracy is a serious matter and if you are going to make money out of this, which you will be because you are going to charge $40 for your services, you need to be aware of your legal obligations. If you have no concern or doubts about it that is good, all I would wonder is why bring it up in the first place.

---

### Post by Nick_Jinn on 2010-07-09
I dont want to argue about the law, but I will say that much of the younger generation has a very difficult attitude than the older generation does concerning intellectual property and respect for large corporations. What seems like common courtesy and basic decency to one person might seem like irrational shilling for the bad guy to someone else.

It doesnt matter though because this person does have a legitimate legally owned version it turns out.





I do appreciate you helping me solve this guys wireless issue though. I will check out that link.

---

