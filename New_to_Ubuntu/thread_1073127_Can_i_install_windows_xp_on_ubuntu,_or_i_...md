---
title: "Can i install windows xp on ubuntu, or i ..?"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by LastWho on 2009-02-18
hi,
or i **lost my ubuntu cd**
can't offer more than 5 GB of disk space
and my RAM is only 757 MB

I need to install windows urgently, can i do it with this system configuration, by using virtualbox? and will windows run smoothly?

many thanks for ur help

---

### Post by SunnyRabbiera on 2009-02-18
well with space like that a dual boot is out of the question and a virtual machine will be too big.
What do you need XP for?
How big is your hard drive?

---

### Post by dabomb1022 on 2009-02-18
If you had windows on it before you might have a restore option on boot up. Mine has it because my pc is fairly new but look for something like: Press F2 for system recovery. By the way this will format your hdd

---

### Post by LastWho on 2009-02-18
i need to scan a book in pdf format with selectable text and images, which is praticlly impossible under linux :( 
       
[Scanning document (img and text) in Pdf format with selectable text?]("http://ubuntuforums.org/showthread.php?t=1064371")

[Can i make "WINE" recognise my hp printer 1100?]("http://ubuntuforums.org/showthread.php?t=1067369")
[B]
[COLOR=#980101]****[/COLOR][/B][Convert Image-Only Pdfs to Image-over-text Pdfs?]("http://ubuntuforums.org/showthread.php?t=836120")


> If you had windows on it before you might have a restore option on boot up. Mine has it because my pc is fairly new but look for something like: Press F2 for system recovery. By the way this will format your hdd
thx, but formating my hdd is not an option lol

---

### Post by SunnyRabbiera on 2009-02-18
> **LastWho said:**
> i need to scan a book in pdf format with selectable text and images, which is praticlly impossible under linux :( 
       
[Scanning document (img and text) in Pdf format with selectable text?]("http://ubuntuforums.org/showthread.php?t=1064371")

[Can i make "WINE" recognise my hp printer 1100?]("http://ubuntuforums.org/showthread.php?t=1067369")
[B]
[COLOR=#980101]****[/COLOR][/B][Convert Image-Only Pdfs to Image-over-text Pdfs?]("http://ubuntuforums.org/showthread.php?t=836120")

Its not impossible until you try.
Your HP printer might be able to work without WINE though as HP usally gives us drivers.
Again I ask how much space you have on your computer, RAM you covered but how much hard drive space you have?

---

### Post by LastWho on 2009-02-18
> **SunnyRabbiera said:**
> Its not impossible until you try.
Your HP printer might be able to work without WINE though as HP usally gives us drivers.
my HP printer work fine, the problem is with xscan and OCR software on linux
the native software of my hp has the option to scan docments and images in image over text pdfs

> Again I ask how much space you have on your computer, RAM you covered but how much hard drive space you have?
my free space = less than 9 GB :(
so i want to offer only 5 or 6 GB to windows xp sp2

---

### Post by SunnyRabbiera on 2009-02-18
I am not talking about free space I am talking about how much space overall you have not what you have left.
But I will tell you right now XP needs way more then 8GB...
If you have a small hard drive I suggest saving up for a larger one.

---

### Post by LastWho on 2009-02-18
my hard drive is only 40 GB

should i give it a try with virtualbox? what do u think plz?
thx

---

### Post by SunnyRabbiera on 2009-02-18
Yeh 40GB is kinda small nowadays, especially if you have a lot of media on your computer.
There is not a lot you can do, I mean for now if you are having too many issues just use XP if you need it so bad but later with a higher capacity hard drive you can set a dual boot.
Good news is that you can find a good capacity HD for real cheap now, I found many 300GB hard drives for under $80
XP under vitrualbox is not a good idea with space that small, for now you are better off backing up and installing XP in full until you get a better HD.

---

### Post by LastWho on 2009-02-18
ok i ll try with virtualbox only to run the hp software 
and next week i ll get a new hard drive
thank u Sunny!

---

### Post by theozzlives on 2009-02-18
I have one computer that had a 20 GB hard drive. The recovery partition was 9 GB. So I deleted the recovery partition as I don't need it and freed up the space. Is this the case in your senerio?

---

### Post by Kain000 on 2009-02-18
You may want to peruse ebay or newegg for a deal, I've seen 1TB drives on both for 90-120 dollars.   sufficed to say > then 40GB eh!

---

### Post by LastWho on 2009-02-18
@theozzlives, no i don't think it is

@Kain000 thx lol i ll check it out :p

---

### Post by sazan on 2009-02-18
u can use vmware workstation for windows if u want...

---

### Post by prshah on 2009-02-18
> **LastWho said:**
> 
can't offer more than 5 GB of disk space
and my RAM is only 757 MB

Sure you can, but don't expect to win any speed records. I use XP in virtualbox to run an investment (securities) program; it works fine off 2Gb (dynamically expanding) of HDD space, and only 192 Mb RAM (allocated off 1Gb of total system RAM).

You can perform a whole host of optimizations to reduce XP's load. To start with, I'd suggest XP Home instead of XP Professional.

---

### Post by LastWho on 2009-02-18
i intalled it this morning & the result is just great, only i wish if give it more memory (only 200 MB) 
thanks guys

---

### Post by LastWho on 2009-02-18
Hi, i need ur help please,
Is there a way to access to my documents on windows-virtualbox from ubuntu the host?

thanks

---

### Post by Kain000 on 2009-02-18
> **LastWho said:**
> Hi, i need ur help please,
Is there a way to access to my documents on windows-virtualbox from ubuntu the host?

thanks

yes, I believe that you must enable file sharing on the host menu (screen where you configure your virtural system and shows what systems you can boot)

once you click on the shared folders text you can direct it to a folder or file on your host (ubuntu) to view form your guest (windows)

---

### Post by wiseheart on 2009-02-18
Just wanted to add that I also used VirtualBox with a 2 GB dynamically expanding drive for XP and this worked fine.

---

### Post by LastWho on 2009-02-18
> Just wanted to add that I also used VirtualBox with a 2 GB dynamically expanding drive for XP and this worked fine. 
this dynamically expanding drive is just a great option, at first i thought all the 6 GB will be gone, but no! only 1.85 GB used by xp today.. 



> yes, I believe that you must enable file sharing on the host menu (screen where you configure your virtural system and shows what systems you can boot)

once you click on the shared folders text you can direct it to a folder or file on your host (ubuntu) to view form your guest (windows)
thanks Kain000,
so i did, but i couldn't find the shared files under xp, 
also i installed "ext2 IFS for windows xp" to allow it reading from ext2 and 3 .. but without a result

---

### Post by ZhuaSD on 2009-02-18
This problem of shared files in Virtualbox I also encountered.  I could not see my other discs from within.

For me, I had internet capability on the XP, (didn't realize it until I saw the windows pop-up about updates, lol first time I was glad to see that stupid balloon), and I just needed a couple of files, so I just emailed them to myself and downloaded them directly to the Virtualbox.

I don't know how big or how many files you need, and its not the greatest work around, but it might work for you in a pinch.

Good luck@!  :D

(P.S. I also have the 2 gig xp on Virtualbox, its a bit small but works fine.  Its just for one game, and I can't keep a lot of saves on the machine, but it works great otherwise, especially love the seamless mode)

---

### Post by LastWho on 2009-02-18
Hi zhuaSD, i found a better solution on another thread with some edition :p
[INDENT]1. Run Virtualbox 

2. Open Settings --> click on the Network. --> make sure that the Enable Network Adaptor and Cable Connected are checked.
(of course u ve to share the folder: Settings --> share)

3. log into your guest (XP) --> click on devices --> Install the guest additions

4. On ur guest: Open Explorer --> Click Tools | Map Network Drive (or connect a network drive .. = connecter un lecteur reseau :p) --> Then Click Browse --> Virtualbox shared folders --> choose the folder u ve shared[/INDENT]

---

### Post by ZhuaSD on 2009-02-18
Ha ok great news!  I tried it out for fun, but it wasn't easy enough and I don't really need it, so I gave up  ;)

So is your problem solved?  You might want to use the thread tools to mark it solved if so.

Nice working with you!  Congrats on a successful solution!

---

### Post by LastWho on 2009-02-18
unfortunatly this option is disabled now
if u wanna give it another try (only for fun) here a link with images, it is for vista but the only difference is in the 4th step i described above
[How To Share Files In VirtualBox With Vista Guest And Ubuntu Host]("http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12")

---

### Post by ZhuaSD on 2009-02-19
Ok, thanks a lot~!

---

