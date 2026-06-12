---
title: "Quite a few questions here"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by sunrex on 2009-01-14
I've decided it's time to ditch XP-64bit (Been acting up recently) and I haven't done anything linux in a bit. And even then, I hardly knew much about it back then.

So here are a few questions I need answered before I do anything:

64bit - I need this because I have  4GB ram and a 512MB video card. And I'm considering another 4GB. What is not 64bit compatible (I hear they even have 64bit flash now) and how would I run a 32bit environment inside 64bit?.

Nvidia drivers - Is the 8800GT supported for linux?. How good are the drivers?.

Gaming - I don't game a lot right now. The only game I currently use anyway is a hl2mod (On the orange box engine - episode one) is Wine up for this yet, or does it still need a lot of development?.

Partitioning - I would like a setup that has little or no SWAP due to my ram, and would be able to last me through a second, third installation - My understanding is you can mount the /home on another partition?.

Security - I would like to lock this down as much as possible without a performance hit. Truecrypt would work well right?. Or would that be a huge performance hit. Also, how much extra space is needed for say a 15MB application in truecrypt.

Desktop - I've tried both gnome, and KDE. Last time I used gnome. Has KDE evolved much these days?.

Hardware: Is dual cores supported better then in XP?. Because I have a dual core in XP and when I game, it uses up a entire core but the other is hardly active. I know games have to support it but it still, to this day irritates me.

Distro: I'm  thinking about using Mint right now. Because it has everything, or mostly everything right out of the box. I also understand it has better 64bit support. No idea if that's correct.

Scripting: I do lua scripting on occasion, what sort of program would I need for this here?. Eclipse?.

Torrenting: What is the best torrent program in linux currently?.

Yeah, that's basically the sum of my questions. I did like vista to an extent, but I felt it was the worst OS I have ever encountered. And that's saying something because I remember working on DOS and Windows 3.1 when I was sixish.

---

### Post by pavel989 on 2009-01-14
> **sunrex said:**
> I've decided it's time to ditch XP-64bit (Been acting up recently) and I haven't done anything linux in a bit. And even then, I hardly knew much about it back then.

So here are a few questions I need answered before I do anything:

64bit - I need this because I have  4GB ram and a 512MB video card. And I'm considering another 4GB. What is not 64bit compatible (I hear they even have 64bit flash now) and how would I run a 32bit environment inside 64bit?.
-probably VMware. why would you need to?

> 
Nvidia drivers - Is the 8800GT supported for linux?. How good are the drivers?.
-most drivers ive heard about, which are recent, run quite well. id do a bit of googling, or just search around on the nvidia website to be sure,
> 
Gaming - I don't game a lot right now. The only game I currently use anyway is a hl2mod (On the orange box engine - episode one) is Wine up for this yet, or does it still need a lot of development?.

-wine seems to be able to do a lot of things with games, but again, google around. (or ask in the gaming or wine section of the forum)

> 
Partitioning - I would like a setup that has little or no SWAP due to my ram, and would be able to last me through a second, third installation - My understanding is you can mount the /home on another partition?.
-yes u can mount home on another partition, and if you do a custom table, u can ommit swap.

> 
Security - I would like to lock this down as much as possible without a performance hit. Truecrypt would work well right?. Or would that be a huge performance hit. Also, how much extra space is needed for say a 15MB application in truecrypt.
-if i have a right hold on truecrypt (use it myself sometimes), it doesn't change. after all, a byte is a byte, but the process of changing the numbers comes down to the cpu. But it seems as though that wont be a problem for u.
> 
Desktop - I've tried both gnome, and KDE. Last time I used gnome. Has KDE evolved much these days?.
-everything has, you can switch between both. in fact to my knowledge you can have both installed and have it specific to users.
> 
Hardware: Is dual cores supported better then in XP?. Because I have a dual core in XP and when I game, it uses up a entire core but the other is hardly active. I know games have to support it but it still, to this day irritates me. 
-For the most part, it should automatically try to split it all up, but there are options you can change for it(not recommended).
> 
Distro: I'm  thinking about using Mint right now. Because it has everything, or mostly everything right out of the box. I also understand it has better 64bit support. No idea if that's correct.

- no idea
> 
Scripting: I do lua scripting on occasion, what sort of program would I need for this here?. Eclipse?. 
-well Eclipse is awesome, but you can even use a text editor like gedit (which i think is totally awesome) or terminal things like vim or nano.
> 
Torrenting: What is the best torrent program in linux currently?.

- I always stuck with Azureus, but Ubuntu comes preinstalled with one. You should check the repos to find what you fancy

---

### Post by sunrex on 2009-01-14
My understanding was wine needed 32bit, but I wasn't talking about VMWare.

---

### Post by hyper_ch on 2009-01-14
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by 3rdalbum on 2009-01-14
> **sunrex said:**
> 
64bit - I need this because I have  4GB ram and a 512MB video card. And I'm considering another 4GB. What is not 64bit compatible (I hear they even have 64bit flash now) and how would I run a 32bit environment inside 64bit?.

I honestly don't think there's anything on Linux these days that is not 64-bit compatible. Running a 32-bit environment is easy - just install the "ia32libs" package and all your 32-bit programs will run.

> Nvidia drivers - Is the 8800GT supported for linux?. How good are the drivers?.

The 8800GT is well supported. Nvidia's drivers are high performance fortunately. Not sure on the comparison between Windows and Linux drivers and their performance, as I don't use Windows. There is one issue with video playback that you might come across (wrong colours in some video players) but this can be worked around very easily.

If you encounter the problem, please e-mail Nvidia and hassle them to fix it - they know it exists but haven't done anything concrete about it. I guess they figure that everyone just uses the workaround.

> Partitioning - I would like a setup that has little or no SWAP due to my ram, and would be able to last me through a second, third installation - My understanding is you can mount the /home on another partition?.

You can choose to have no swap partition, and you can choose to mount the /home on another partition. You will need to use the "Manual" partitioning option of the installer. If you want an encrypted filesystem, you will want to use the "Alternate CD" installer. It's a bit uglier, a tiny bit more difficult to use, but can set up the encryption for you.

As for your encryption, I can't really comment on performance or anything - I don't use encryption. However I believe some forms of encryption that you can use on Ubuntu add about 12kb to each encrypted file. A program will consist of lots of smaller files, but then do you want your whole filesystem encrypted, or just your important data? (/home)?

> Desktop - I've tried both gnome, and KDE. Last time I used gnome. Has KDE evolved much these days?.

KDE 4 is pretty much a complete rewrite from KDE 3.5. So yes, it's evolved a lot. I used to always use Gnome but I do quite like KDE 4 now, so try both of them if you can.

> Hardware: Is dual cores supported better then in XP?. Because I have a dual core in XP and when I game, it uses up a entire core but the other is hardly active. I know games have to support it but it still, to this day irritates me.

SMP (multi-processing and multi-threading) works better on Linux than on XP, but in order for an individual program to scale across your cores it needs to be written to do so. You will notice your programs being more responsive on Linux, especially when your system is under load. But games still tend to use a single thread, which means they use a single core.

> Distro: I'm  thinking about using Mint right now. Because it has everything, or mostly everything right out of the box. I also understand it has better 64bit support. No idea if that's correct.

Mint has exactly the same 64-bit support as Ubuntu. I can't imagine how you could do better than Ubuntu's, to be honest :-)  Mint does come with codecs, DVD playback and Flash Player, but all this is trivial to install on Ubuntu anyway.

> Torrenting: What is the best torrent program in linux currently?.

I like Transmission - that's the default client in Ubuntu. Some people use various Windows-based torrent programs in Wine but I think that's a bit odd.[/QUOTE]

---

### Post by MikeSz on 2009-01-14
"64bit - I need this because I have 4GB ram and a 512MB video card. And I'm considering another 4GB. What is not 64bit compatible (I hear they even have 64bit flash now) and how would I run a 32bit environment inside 64bit?."

Think you may be getting a little confused here - if I read that correctly - you dont need "64 bit" ram to run ubuntu in 64 bit mode.  Its your processor's instruction set that does all the work from what I know and the software that is used to support it.  In terms of memory, it really shouldnt matter as long as you simply add memory that is of a compatibile speed with your existing module and motherboard etc.  

"Gaming - I don't game a lot right now. The only game I currently use anyway is a hl2mod (On the orange box engine - episode one) is Wine up for this yet, or does it still need a lot of development?."

I struggled with this one sorry - Wine will do the job and there are plenty of ways to make things work, but for me it was laborious and I never really got anything working.  you can by all means put the effort in if you want but for me it was just far easier to get an Xbox - the PC for me is now a work horse with the odd game of Championship manager.  

"Distro: I'm thinking about using Mint right now. Because it has everything, or mostly everything right out of the box. I also understand it has better 64bit support. No idea if that's correct."

Nothing wrong at all with Mint - I've used it and liked it, but I have since gone back to using normal Ubuntu for no particular reason than I liked the native feel of it.  

As for security, from what I know Ubuntu is pretty secure already but there are plenty of answers in here if you have more specific concerns.  

Hope that helps.

---

### Post by Paqman on 2009-01-14
> **sunrex said:**
> 
64bit - I need this because I have  4GB ram and a 512MB video card. And I'm considering another 4GB. What is not 64bit compatible (I hear they even have 64bit flash now) and how would I run a 32bit environment inside 64bit?.


There's no need to run 32-bit apps like browsers on 64-bit any more. You can either get 64-bit plugins, or Ubuntu will install the right wrapper for you automatically.

To avoid any hassles, simply install ubuntu-restricted-extras, which will install Flash, Java, etc in one step.

> 
Nvidia drivers - Is the 8800GT supported for linux?. How good are the drivers?.
The Nvidia drivers are good, especially the latest 180 series, which should be hitting the repos soonish.

> 
Gaming - I don't game a lot right now. The only game I currently use anyway is a hl2mod (On the orange box engine - episode one) is Wine up for this yet, or does it still need a lot of development?.
The [Wine App DB]("http://appdb.winehq.org/") is the best place to lok for WIne info.

> 
Partitioning - I would like a setup that has little or no SWAP due to my ram, and would be able to last me through a second, third installation - My understanding is you can mount the /home on another partition?.
You could skip swap, but it wouldn't hurt to have some as a backup. Storage is cheap.

To be honest, even 4GB is way more than you'll need on Ubuntu for anything except the most unbelievably RAM-intensive apps. You'll probably stay under 1GB most of the time.

> 
Security - I would like to lock this down as much as possible without a performance hit. Truecrypt would work well right?. Or would that be a huge performance hit. Also, how much extra space is needed for say a 15MB application in truecrypt.
Are you looking to encrypt the whole partition, or just create an encrypted vault? For the latter, Truecrypt works nicely. For whole-disk, Ubuntu can do this itself (IIRC you'll need to install from the Alternate LiveCD)

> 
Desktop - I've tried both gnome, and KDE. Last time I used gnome. Has KDE evolved much these days?.


KDE 4 is becoming a bit more usable i'm told. Early versions of it were a mess, but you can always use 3.5

> 
Hardware: Is dual cores supported better then in XP?. Because I have a dual core in XP and when I game, it uses up a entire core but the other is hardly active. I know games have to support it but it still, to this day irritates me.
That's really down to the app, not the OS. If something is written single-threaded then there's nothing the OS can do to make it use both cores.

> 
Distro: I'm  thinking about using Mint right now. Because it has everything, or mostly everything right out of the box. I also understand it has better 64bit support. No idea if that's correct.
Nope. 64-bit is fine in vanilla Ubuntu as well. Mint is just Ubuntu with a different menu and some codecs pre-installed. The actual system is the same.

> 
Torrenting: What is the best torrent program in linux currently?.
Personal preference really. I like the bundled client Transmission, but everybody has their own favourite.

---

### Post by meindian523 on 2009-01-14
> **sunrex said:**
> My understanding was wine needed 32bit, but I wasn't talking about VMWare.
non,wine is available for 64 bit too.I use it.
Transmission is just fine.Azureus is now known as just Vuze.And you used GNOME last time,but when was that?

---

### Post by sunrex on 2009-01-14
It seems most of you misunderstood what I said about needing 64bit. I need it because of ram limitations on 32bit, simple as that. I was concerned about the compatibility of some 32bit applications though.

Alright, thanks for the help!.

Can you give me some install tips so I don't make a boo-boo somewhere?. I'm talking about partitioning and filesystems. What would be best for 4GB ram (Might be 8GB) and a SATA hard drive?.

---

### Post by Paqman on 2009-01-14
> **sunrex said:**
> 
Can you give me some install tips so I don't make a boo-boo somewhere?. I'm talking about partitioning and filesystems. What would be best for 4GB ram (Might be 8GB) and a SATA hard drive?.

There's a million different ways to partition, it depends on what you want to do.

Since you mention gaming i'm assuming you're going to dual-boot. Where do you want to keep your data? On the Win partition? A separate data partition? In your /home?

Generally speaking, i'd go for:

Swap = max 1GB due to tons of RAM
/ = 10GB (maybe 20GB if you want to do anything that makes massive temp files like authoring DVDs)
/home = As much of the disk as you can spare. Wine installs Windows apps to a fake C drive in your /home, and you might also want to keep other stuff there like VMs, plus any data you want to keep there.

I just use ext3 for both partitions. A shared data partition can be NTFS (or FAT if you're feeling old-fashioned). Either way you'll need to defrag it from Windows once in a while, since Ubuntu can't defrag Microsoft filesystems.

---

