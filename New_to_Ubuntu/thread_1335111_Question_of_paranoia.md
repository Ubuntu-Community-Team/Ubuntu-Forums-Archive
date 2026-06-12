---
title: "Question of paranoia"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by Tycoon timbo on 2009-11-23
Hello to all you happy ubuntu users.  I want to migrate from windows ( not a Gates fan anymore) BUT:

Will I still be able to access all my information on the hard drive?
Will ubuntu overwrite windows?
If I install ubuntu on my slave hard drive, how do I get it to boot instead of windows and will it be able to access the folders on the C drive.
How do0 I get rid of windows and have only ubuntu without re-formatting the HD?
Do any commercial games run on ubuntu?

Do I come across as a little nervous?:o

---

### Post by Tycoon timbo on 2009-11-23
seems to me that I should just shove it in and pray as there is no better advice

---

### Post by MrReaper on 2009-11-23
Will I still be able to access all my information on the hard drive? - Depends on how you plan to install.
Will ubuntu overwrite windows? - No it will not. You can make windows not accessible but it will not be gone until you delete it.
If I install ubuntu on my slave hard drive, how do I get it to boot instead of windows and will it be able to access the folders on the C drive. - wubi install - google it
How do I get rid of windows and have only ubuntu without re-formatting the HD? I assume you could install Ubuntu on your slave and still access files on your master BUT - read ADVICE.
Do any commercial games run on ubuntu? - Check AppDB at [http://www.winehq.org](http://www.winehq.org) there are all the games supported by wine.

Do I come across as a little nervous?:eek: - A lot actually :)

ADVICE: Make backup of all your important files (iow - the ones you need to have in ubuntu as well) and make clean install of Ubuntu partitioning either:
1) Your MR as '/' and swap (not needed if you create swap-file later) and your SL '/home'
2) Your MR as '/' and leave SL not formatted, this way it will mount as new filesystem everytime you start your PC (external HDD-like)
Choosing the option depends on sizes of your drives. I presonally have 10G drive as '/' and 50G drive as '/home'.

Sorry if it's not technically precise, it's based on my personal experience (only year and a bit so not much).

edit: Yes, just shove Windows, you don't need it! Search your feelings timbo, you know this to be true :)

---

### Post by coffeecat on 2009-11-23
> **Tycoon timbo said:**
> Do I come across as a little nervous?:o

> **Tycoon timbo said:**
> seems to me that I should just shove it in and pray as there is no better advice

You come over as a little bit impatient. :wink: Waiting only 11 minutes before bumping a post is poor forum etiquette.

However, you are new here, so welcome. :)

What do you want to do? Completely replace Windows or have a Windows/Ubuntu dual-boot? It sounds as though you haven't made up your mind. Tell us which you want, post a bit of information about your hardware - the sizes of your two hard drives - and you will get plenty of advice...

... if you are patient. :p

---

### Post by Tycoon timbo on 2009-11-23
Thankyou MrReaper.  I have printed your reply and will give it a try.

---

### Post by MrReaper on 2009-11-23
> **Tycoon timbo said:**
> Thankyou MrReaper.  I have printed your reply and will give it a try.

First check the winehq database so that you dont miss your favourite game (in my case it was Diablo II :) ). Then make liveUSB using unetbootin (just google it) and TRY Ubuntu for a while to see if there are any major problems with your PC running it. Check how it looks with accessing NFTS or FAT partitions as well (that's option 2 of my previous post). And then if everything looks fine - Just install from that liveUSB (and don't forget to backup your data before you go :D ).

---

### Post by themusicalduck on 2009-11-23
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Have a look through here and it'll answer many of your questions.

---

### Post by Tycoon timbo on 2009-11-23
Coffeecat, please accept my apologies for being so hasty.  I am new to forums in general and my experience with computers and operating systems more so.

I will introduce my computer (Orac):

chip is AMD 64 Athlon 3200

1.5 gig ram

75 gig C drive

37 gig D drive

Radeon X 1800 256 meg graphics card

Soundblaster Audigy 2 sound card

Mostly I use the computer for single player games (not online mmorpg), online poker, emails and some document work.

your reccomendations would be most welcome:D

---

### Post by random turnip on 2009-11-23
UBuntu won't overwrite or do anything at all to Windows unless you tell it to, and i would advise that you keep windows for the time being as a few things could go wrong if this is your first time.

First make the CD, then re-boot with it in the drive.  It will load a screen with a few options, i would go on the "try ubuntu without any changes to my computer" option first, this will boot ubuntu right from the disc.  This will look weird at first as it doens't know your screen res or drivers yet, but you can change these yourself now.  This will also run much slower than when Ubuntu is actually installed.

If you like what you see then go to the desktop and there should be an install icon, double click it.  Go through the instal guide, it's a really simple GUI, anyone can do it, then only thing that causes most people trouble is the partitions, but it's easier than it sounds.  Just make sure you slide the slider thing along to make sure you give UBuntu enough space, or you will find that your Ubuntu partition is full before you've even used it.  Next, let it install, should take 20-40 mins at most and then you have you ubuntu.

---

### Post by BFG on 2009-11-23
> **Tycoon timbo said:**
> 
Will I still be able to access all my information on the hard drive?
Yes.  BUT. You would be very foolish to attempt anything like this without making a separate backup of your data.  

More info.  A common strategy on windows is to not put your data on the C drive in with the windows OS, but to have a separate partition (D: or other).  Many big name PCs are like this from the store. However, Microsoft default is to mash all your data in with the OS.

I would recommend:

1. Make a backup.  Put it to one side.
2. PLan to have a new "Data" partition on your existing hard drive.  You can do this in windows with a tool like Acronis, or you can do it during the Ubuntu install (advanced)
3. Move all your data into this partition.  You can reconfigure windows easily to make use of this.  (E.g. just "move" my documents.
4. When you boot either windows or Ubuntu, they can both see the "Data" partition.  THis works well.

A tip.  If you split your hard drive, don't split it 50%/50%, it can make it hard to identify which is which as boot level tools often ignore partition labels or report them incorrectly.



> **Tycoon timbo said:**
> 
Will ubuntu overwrite windows?
No. The standard install will create a dual boot, and install a tool called grub which will give you an option at boot time.

You can tell it to overwrite if you want (but backup your data first)

> **Tycoon timbo said:**
> 
If I install ubuntu on my slave hard drive, how do I get it to boot instead of windows and will it be able to access the folders on the C drive.
It will work via grub, but why?  If you just want to try ubuntu use a CD or a flash drive to do a live demo.
If you;re serious about using it properly, put your data on the slave drive (but also have SEPARATE backup! ) and have the OSs on the internal drive.  It will run faster and avoids problems.



> **Tycoon timbo said:**
> 
How do0 I get rid of windows and have only ubuntu without re-formatting the HD?
You just wipe the partition when you don;t need it any more.  It's really easy.

> **Tycoon timbo said:**
> 
Do any commercial games run on ubuntu?

I'm not a gamer, but from reading up then running Windows PC games on a Ubuntu machine is a lot harder than installing on windows.

---

### Post by Tycoon timbo on 2009-11-23
Many thanks for all your help and advice people.  I am now happily playing with the ubuntu cd and checking it all out on my laptop.  I am sure I will convert my PC as well soon.;)

---

### Post by halitech on 2009-11-23
> **Tycoon timbo said:**
> Coffeecat, please accept my apologies for being so hasty.  I am new to forums in general and my experience with computers and operating systems more so.

I will introduce my computer (Orac):

chip is AMD 64 Athlon 3200

1.5 gig ram

75 gig C drive

37 gig D drive

Radeon X 1800 256 meg graphics card

Soundblaster Audigy 2 sound card

Mostly I use the computer for single player games (not online mmorpg), online poker, emails and some document work.

your reccomendations would be most welcome:D

With having an ATI X1800 video card, I would use 8.04 or 8.10 unless the open source drivers have come along well as the ATI drivers don't support the X series of cards in 9.04 or 9.10.

---

