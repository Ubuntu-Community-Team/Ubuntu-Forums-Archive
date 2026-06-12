---
title: "I wanna get rid of vista and run Ubuntu."
date: 2009-02-20
forum: New to Ubuntu
---

### Post by Split007 on 2009-02-20
Ok so right now im on a Dell inspiron 530s with a 1.60 ghz Pentium dual core and 3gbs of ram with Vista Basic. I have been wanting to Put ubuntu 8.10 on there the only big thing is I play world of warcraft and ive heard of problems but ive been reading it works great now. So all i do is play wow listen to music download **** from bittorrent and browse the net. So if ubuntu can do all this nice and easy tell me what i need to do.  I would like to get this done ASAP.

---

### Post by sandyd on 2009-02-20
ok, heres the deal

theirs several things i need tp know

whats your graphics card?

have time to try ubuntu out before attempting to wipe out your vista system and cry because something didn't work right?

are you ok with running Wow in a virtual machine?

read here for WoW:[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)

theirs also some other commercial programs that are designed for this purpose such as Cedega, Crossover .etc.etc.

---

### Post by chronographer on 2009-02-20
nono. Run WOW in wine. It is done, not by me, but by many others. [http://www.wowwiki.com/Wine](http://www.wowwiki.com/Wine)

but it is easier than the guide above says.

First. Install dual boot Ubuntu, either from within Vista (easy) or by booting from the live CD (pretty easy). Do guided partitioning to shrink your vista partition and make ~20 gig for Ubuntu. then install Ubuntu.

Now Ubuntu is installed, get connected to the internet, update your software, and install nvidia / ATI drivers. (nvidia is better, easier). Usually you can do this with the 'restricted drivers manager'.

ONce this is done open a terminal (applications : accessories : terminal) and install wine:

"sudo apt-get install wine"

then double click the warcraft installer. Or right click and choose "run with wine".

After this it should be easy. you will get a 5-10% performance penalty by running WOW in wine.

---

### Post by sandyd on 2009-02-20
i said it was possible for him to running in wine:o
i just listed out all his options, thats all

cedega, and crossover IS WINE after all..........

---

### Post by Split007 on 2009-02-20
Oh i know about Wine and its the stock graphics card that came in the comp how do i find out what it is?

---

### Post by epitaph on 2009-02-20
Try typing this in console:

```
lspci | grep VGA
```

Should tell you what VGA card you have.

---

### Post by Split007 on 2009-02-21
i m still on vista i havent even tried downloading ubuntu cuz i dont know what to do

---

### Post by sandyd on 2009-02-21
> **Split007 said:**
> i m still on vista i havent even tried downloading ubuntu cuz i dont know what to do
heres what you do

download ubuntu.

burn to a cd
pop the cd in while running windows
open the cd (autoplay should start now)

install ubuntu

then we can see weather your hardware is COMPLETELY compatible with linux or not

you can also easily try ubuntu without killing your vista by installing like that

---

### Post by lkraemer on 2009-02-21
Split007,
carlee, has it right, but you need a little more detail.

1. Download the Distro of your choice.  Go to:
   ww.distrowatch.com to view the choices......#1=Ubuntu
2. Burn the ISO to a CDR as Disk at Once (DAO) and 4x or 8x speed
   after you have VERIFIED the MD5SUM of the ISO.  There are Windows
   and Linux programs that do just that, or you can use K3B in
   Ubuntu to verify against the posted good MD5SUM.  Use GOOD Media!
3. Insert the LiveCD you just burned, and boot the LiveCD.  This will 
   allow you to test the distro you just selected to see if it will
   run properly on your machine.  (Wifi might not work initially!)
   Check the distro's fourms.....
4. If you are happy with that Distro you can install from the LivdCD.
5. If it doesn't run properly, or you don't like the distro, or you
   like KDE better than Gnome or XFCE, or Fluebox, or on and on... go to:
   [www.distrowatch.com](www.distrowatch.com) and select another one that more suits your fancy.
   Test several as you might not like the first one you pick.
   Ubuntu, PCLinuxOS, sidux, Damn Small Linux, are my choices.
   Mythbuntu, ArtistX, UBCD, Gparted, Clonezilla...LiveCD's are GREAT TOO!
6. The decision is going to be tough.
7. I wouldn't recommend installing inside Windows, but rather test with
   the LiveCD's to narrow down your choices.  Less chance of messing
   up a Picky Windows (YUK!) OS.  But, it's your choice.  If it were me,
   I'd much rather purchase another 2.5" Drive, and install it in the 
   lappy, and install the Distro of my choice...and save the Windows Drive
   for a Paperweight until you are satisfied.  And before I did anything
   I'd for sure export your Favorites, Print out any Registrations for
   Windows Software Installs, and back up all IMPORTANT files to an
   external drive that can be saved for future needs.  Later you may want
   to use VirtualBox and and install Windows inside VirtualBox as a
   Guest OS....ie. the need for Registration and favorites at this time. 


lkraemer

---

### Post by Split007 on 2009-02-21
I donhave any blank discs so can i download image to desktop and run daemon tools and run the image?

---

### Post by sandyd on 2009-02-21
> **Split007 said:**
> I donhave any blank discs so can i download image to desktop and run daemon tools and run the image?

yes, just mount it and youll see the autorun pop 
so thats for your test install....
(oh wait, quick reminder. installing inside of windows isn't considered to be installing on hard disk. remember that for later support requests)

meanwhile, go and buy some blank cds. Youll need those when you get everything running on your test platform and are ready to install ubuntu on hard disk.

---

### Post by sandyd on 2009-02-21
> **lkraemer said:**
> Split007,
carlee, has it right, but you need a little more detail.

1. Download the Distro of your choice.  Go to:
   ww.distrowatch.com to view the choices......#1=Ubuntu
2. Burn the ISO to a CDR as Disk at Once (DAO) and 4x or 8x speed
   after you have VERIFIED the MD5SUM of the ISO.  There are Windows
   and Linux programs that do just that, or you can use K3B in
   Ubuntu to verify against the posted good MD5SUM.  Use GOOD Media!
3. Insert the LiveCD you just burned, and boot the LiveCD.  This will 
   allow you to test the distro you just selected to see if it will
   run properly on your machine.  (Wifi might not work initially!)
   Check the distro's fourms.....
4. If you are happy with that Distro you can install from the LivdCD.
5. If it doesn't run properly, or you don't like the distro, or you
   like KDE better than Gnome or XFCE, or Fluebox, or on and on... go to:
   [www.distrowatch.com]("http://www.distrowatch.com") and select another one that more suits your fancy.
   Test several as you might not like the first one you pick.
   Ubuntu, PCLinuxOS, sidux, Damn Small Linux, are my choices.
   Mythbuntu, ArtistX, UBCD, Gparted, Clonezilla...LiveCD's are GREAT TOO!
6. The decision is going to be tough.
7. I wouldn't recommend installing inside Windows, but rather test with
   the LiveCD's to narrow down your choices.  Less chance of messing
   up a Picky Windows (YUK!) OS.  But, it's your choice.  If it were me,
   I'd much rather purchase another 2.5" Drive, and install it in the 
   lappy, and install the Distro of my choice...and save the Windows Drive
   for a Paperweight until you are satisfied.  And before I did anything
   I'd for sure export your Favorites, Print out any Registrations for
   Windows Software Installs, and back up all IMPORTANT files to an
   external drive that can be saved for future needs.  Later you may want
   to use VirtualBox and and install Windows inside VirtualBox as a
   Guest OS....ie. the need for Registration and favorites at this time. 


lkraemer

im thinking of letting him use WUBI b/c/ i want him to actually test everything out. and i mean EVERYTHING. Even WINE, virtual boxes, everything. you can't try everything on the RAM (livecd). and i also prefer to keep it as simple as possible at the start ( no going into BIOS........ yet)

---

### Post by glotz on 2009-02-21
> **Split007 said:**
> Ok so right now im on a Dell inspiron 530s with a 1.60 ghz Pentium dual core and 3gbs of ram with Vista Basic. I have been wanting to Put ubuntu 8.10 on there the only big thing is I play world of warcraft and ive heard of problems but ive been reading it works great now. So all i do is play wow listen to music download **** from bittorrent and browse the net. So if ubuntu can do all this nice and easy tell me what i need to do.  I would like to get this done ASAP.Smart move, welcome to the light side!

---

### Post by Split007 on 2009-02-23
So what do i do? cuz i dont have any disks?

---

### Post by yther on 2009-02-23
Won't Canonical mail people a free CD?  Hmmm.... why, [yes, they will]("https://shipit.ubuntu.com/"), but it could take *two months* to arrive?!?  :shock:

OK, so if you're not that laid-back, you could use Daemontools and install the WUBI thing from there.  Or... have any USB flash drives you don't mind erasing?

Yeah, I knew I remembered this from somewhere:  Unetbootin is a utility that lets you install an ISO image to a USB drive and boot it.  --> [HOWTO]("http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/") <--

So there are a couple of alternative ideas if you don't mind some fiddling around.  Hey, you got daemontools to work and that's more than most people have done!  ;)

---

### Post by Split007 on 2009-02-23
I found a blank cd so i wanna run the program and see if i likes my system cant i do that with out installing it?

---

### Post by uberg on 2009-02-23
*Yes. ;)*

---

### Post by 3rdalbum on 2009-02-23
Burn Ubuntu to a CD, **using your software's "Burn Image to Disc" function**.

Then boot up from the CD. You might need to change your BIOS settings to tell the computer to boot from CD before trying to boot from hard disk.

Ubuntu will boot up from the CD. If you like it, you can double-click the "Install" icon on the Ubuntu desktop, which runs the installer.

---

### Post by Split007 on 2009-02-23
ok um should i partition my drive before the install or during and do i need to back up my data? i can get a external hard drive and how would i back it up just put my  c drive on it?

---

### Post by beju0506 on 2009-02-23
Honestly, if it were me, I'd wait until the weekend, make sure I have my system restore CDs that originally came with my laptop, backup all of my stuff and then format and install Ubuntu. Try out everything and see if it works the way you want. If you don't like it, format and reinstall Windows using your original restore CDs and reinstall your proggies, etc. I know it's a pain, but sometimes it's the best way to learn... and its nice to have a fresh install now and then anyway.

Or buy a whole 'nother computer to use for Ubuntu... that's what I did ;)

:D

---

### Post by sandyd on 2009-02-23
> **Split007 said:**
> ok um should i partition my drive before the install or during and do i need to back up my data? i can get a external hard drive and how would i back it up just put my  c drive on it?

just back up ALL the data you need, such as My Documents, Desktop

simply, just back up **WHAT YOU CANNOT LOSE**, for example, if you were a university student, you would probably NOT want to lose the course notes you just typed up during class would you?

the poster before me is right. 

Theirs ALWAYS weird things that pop up and a million questions you will probably will have some problems on the way, so start when you have a LOT of time, and i mean A LOT, and you don't need to use your computer for that day.

---

### Post by Split007 on 2009-02-23
ok i on ubuntu now and im thinkin about clicking install with out backing up

---

### Post by yther on 2009-02-24
Congratulations, you had us going there for a while!

I no longer believe this is a genuine request for help, but it was creative.  Good job.

---

### Post by BruisedQuasar07 on 2009-02-24
I would not do that. Get a few blank CDs or blank DVDs and download a live CD copy of Ubuntu. You can safely run a live CD version of any major home use Linux version (Distribution) and not damage your Vista installation. The entire Ubuntu will run from CD (or DVD) and RAM. 

I would not dual boot either. I haven't had much luck with dual boot on any Dell I own. It works for a while (couple months) and then the entire system crashes. Unless you want to invest the time into mastering Grep, I'd stay away from dual boot of Vista and Linux anything. Vista Basic presents enough headaches by itself! For some reason, I have an IBM Thinkpad (T-23) that I've run Xubuntu and Windows 2000 Pro (in my opinion, the best O/S Microsofthead ever released) for over 2 years with no problems. Were it not for the Microsoft Monopoly cartel the O/S today would be a version of 2000 Pro. 

I find that it's best to have a Windows PC around. Due to Microsoft monopoly practices, there are some things than you simply need Windows for. 

You have a Dell which means you can install any Dell disc version of Windows. They are also much cheaper than OEM versions. I'd get a Dell disc with Windows 2000 Pro SP3 or XP Pro SP2 and install that over your Vista. Then, I would install Ubuntu on a second INTERNAL hard drive. That works out much better than dual boot.Dell discs are sold on eBay. 

You may want to burn an ISO of Puppy Linux. Its very small (made to run off a CD and to run from RAM) and a great way to ease into Linux. I have a Puppy CD and pen drive for each of my PCs. I often surf the Net with Puppy. Its sleek and very fast as it auto loads into RAM and runs from there!

--Bruised

---

### Post by Split007 on 2009-02-24
Ok well i realy hate vista right now and the only things i do on my comp is play wow download using bittorrent and listen to music so if i can do those with ubuntu then screw vista.  Oh um 1 thing i noticed while on ubuntu that its kinda flat compared to vista  Vista is kinda round and more 3d  u get what i am saying?

---

### Post by Split007 on 2009-02-24
Anyone?

---

### Post by ulfj on 2009-02-24
make good backups of everything and go ahead. Did I mention make good backups of everything.

---

### Post by Split007 on 2009-02-24
can i just copy my whole c drive on a external hard drive and should i partition during my install of ubuntu and how many gigs 20?

---

### Post by MasterNetra on 2009-02-24
> **u.lover said:**
> how can i run Age Of Empires III & Rise of Nations in Ubuntu 8.10?

use wine, cedgea or VM it.

---

### Post by sandyd on 2009-02-24
Age of Empires: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795)
Rise of Nations: [http://appdb.winehq.org/appview.php?iAppId=3017](http://appdb.winehq.org/appview.php?iAppId=3017)

read that buddy

---

### Post by Split007 on 2009-02-24
?

---

### Post by Split007 on 2009-02-25
Um anyone?

---

### Post by sailthesea on 2009-02-25
Hi split007
 Your questions have all been answered you know. All you have to do is decide which advice to take and try things out. If you don't no one will be able to help you. 
 Personally, I think you should try 8.10 on a live cd and get used to the way it works, it isn't vista and won't try to be, if it isn't for you try something else the choice is wide and varied 
 The point is you aren't forced to use microsoft  there are alternatives but you have make that choice
 Its up to you now friend

---

### Post by uberg on 2009-02-25
Split, 
     Did you download the CD image and burn a CD yet?

---

### Post by Split007 on 2009-03-02
ya its on a disk

---

### Post by Bradtek on 2009-03-02
If you want a better looking desktop & 3D effects etc. you will have to actually install Ubuntu, then if your video card is good enough you can enable effects (compiz)

Edit:

And then you can go to gnome-look.org and choose from hundreds of themes, download & install them.
Possibilities are almost endless for customisation.

---

