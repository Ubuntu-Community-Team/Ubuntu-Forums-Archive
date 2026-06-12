---
title: "[SOLVED] Put Ubuntu on Vista Machine?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Kellemora on 2008-12-07
Hi Gang

I've never used Vista ever!
My son picked up a new low end computer, seems decent enough for a store bought.

I shrunk the partition using Vista's own shrinker.  That went OK.

I have about 6 Ubuntu Live CD's here that work great on any computer I've ever tried them on, except this one.
I DID set it to boot from DVD in the bios.

This machines has a LightScribe SATA DVD and cannot read ANY Live CD, not gparted, not super grub, not even Knoppix.

The computer is a Presario SR5507F Desktop!

He doesn't want Vista Deleted!  But does want Ubuntu installed on it as the main boot.  It also does NOT come with Disks to restore, you have to rely on the Drive_D restore if I blow it.

Could it be that Mickey$oft has locked out non-Mickey$oft software?  Or perhaps this won't read CD's at all?

Any Ideas?  Took me forever to convince my son to try Ubuntu and he bought a new machine just so he could.  It's up to me to get it going and set up for him though.

Now, after all my bragging, I'm stuck!

TTUL
Gary

---

### Post by laffinet on 2008-12-07
What screen or error message do you get when booting the liveCD ?

---

### Post by cobra741 on 2008-12-07
wow that's an odd one.... did you try kicking it? :) 

Have you tried using different blank media for the CD? I did the whole store purchase thing about 1yr ago and it's drive refused to use about 5 different brands of disks. 

The other thing you can try is putting it on a USB stick and see if it can boot form that. I'm pretty sure you'll need a 2GB stick

[http://www.pendrivelinux.com/2008/11/15/usb-boot-cd-for-ubuntu-810/]("http://www.pendrivelinux.com/2008/11/15/usb-boot-cd-for-ubuntu-810/")

Good luck!

---

### Post by jimmy the saint on 2008-12-07
Another option is to do a Wubi install.  I have never done one, but it basically installs Ubuntu from inside windows.  You end up with a dual boot machine from what I understand.
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Kellemora on 2008-12-07
Hi Gang

No error messages at all!

The DVD drive runs for awhile, then Vista will boot up.

I tested several Live CDs in other machines to make sure they were OK and they were.  They all came up on a restart on other machines, just not on this new machine.

Unfortunately Everything in it is SATA including the DVD, so I have no way of dropping another CD into it.

In fact, since I posted this a few minutes ago, I have tried everything in it from music CD's to Device Driver CD's and it flat out won't read a single CD of any type.

I don't have any DVD's here in the office, I can bring one tomorrow to see if it reads DVD's and perhaps burn an Ubuntu Live CD on a DVD.

I've also found a few other things not exactly kosher with this machine.  Only 2 SATA plugs, both used, one for the drive and one for the DVD, does have 3 gigs of memory.
But I'm thinking of telling him to take it back from whence it came.  Because I can pick him up a much better machine for about the same price.  It's useless if it can't read ANY CDs!

TTUL
Gary

---

### Post by handydan918 on 2008-12-07
I believe the sata-boot issue is not uncommon, and certainly not unique to Ubu. I would consider trying to get it to boot from a flash drive with Ubu on it.

---

### Post by theozzlives on 2008-12-07
Might be a bad drive.

---

### Post by laffinet on 2008-12-07
> In fact, since I posted this a few minutes ago, I have tried everything in it from music CD's to Device Driver CD's and it flat out won't read a single CD of any type.

Sounds like a bad drive, not an Ubuntu issue. 

Since it's a new computer I would take it back to the shop !

---

### Post by crazyness003 on 2008-12-07
> **Kellemora said:**
> Hi Gang

No error messages at all!

The DVD drive runs for awhile, then Vista will boot up.

I tested several Live CDs in other machines to make sure they were OK and they were.  They all came up on a restart on other machines, just not on this new machine.

Unfortunately Everything in it is SATA including the DVD, so I have no way of dropping another CD into it.

In fact, since I posted this a few minutes ago, I have tried everything in it from music CD's to Device Driver CD's and it flat out won't read a single CD of any type.

I don't have any DVD's here in the office, I can bring one tomorrow to see if it reads DVD's and perhaps burn an Ubuntu Live CD on a DVD.

I've also found a few other things not exactly kosher with this machine.  Only 2 SATA plugs, both used, one for the drive and one for the DVD, does have 3 gigs of memory.
But I'm thinking of telling him to take it back from whence it came.  Because I can pick him up a much better machine for about the same price.  It's useless if it can't read ANY CDs!

TTUL
Gary
its not even worth buying pre-made computers now. If you have the know-how, do-it-your-self is the best route (plus you avoid paying an arm and a leg for viztas! I can build a mid ranged setup (tower) for under $400 (about $80 for mobo, $120 for CPU, $70 for ram, $100 for GPU, $70 for PSU and whatever for drives and such) . Im betting you have something less than expected for the same, if not more money.

Anyway, back to the problem at hand: 
options: Wubi, Flash-Boot, Try DVD-media, replace sata-DVD drive with a pata one (if possible).

The Drive_D things is garbage. You need to use the built-in Recovery Drive software to make the recovery disk. and you can ONLY run it ONCE! So, if it fails (like it did for me), you are sol since you cant re-run it.

All in all, i'd get rid of Vista altogether and find an XP cd somewhere and use that in a VM inside of Ubuntu (or dualboot if necessary).

Anyway, keep us posted on what routes you take.

---

### Post by Kellemora on 2008-12-08
Hi C

Most of my OWN computers are built ups!

In any case, this one is back in the box and going back to wherever he got it from.

Having a Vista machine on my side of the property line gave me the creeps as is was!  Get Cooties just touching the box it came in, hi hi........

Don't know how anybody can stand to be around a Vista machine?

So marking this nightmare solved!

TTUL
Gary

---

### Post by detroit/zero on 2008-12-08
> **Kellemora said:**
> Hi Gang

No error messages at all!

The DVD drive runs for awhile, then Vista will boot up.
I have a HP desktop with one of those LightScribe drives in it. Even on my Toshiba laptop (which is also set to boot from CD/DVD if present) I have to hit F12 to select my boot device and choose the DVD drive.

Try doing that. While your POSTs run, there should be a message somewhere on the screen that says something like (Hit F2 to enter setup, hit F12 to select boot device) or something similar. Then just select the DVD drive.

If that doesn't work, I'd verify that the drive does or doesn't work from inside whatever functional OS you have on the computer before you go lugging the thing back to the store to complain.

EDIT: Didn't see the part where you said you tested the drive from inside windows. Scratch my post then.

---

### Post by crazyness003 on 2008-12-08
> **Kellemora said:**
> Hi C

Most of my OWN computers are built ups!

In any case, this one is back in the box and going back to wherever he got it from.

Having a Vista machine on my side of the property line gave me the creeps as is was!  Get Cooties just touching the box it came in, hi hi........

Don't know how anybody can stand to be around a Vista machine?

So marking this nightmare solved!

TTUL
Gary
nice. you should teach your boy to build. its so much better (in terms of creativity and the fact that you're not constricted by the proprietary garbage they throw in there)

Its nice to hear the 'solution' you came up with. But it still didnt solve the problem (what if someone else runs into this).

Possible causes (IMO): Bad Drive. Not that its incompatable, but it appeared you had faulty hardware. It woulda been a good idea to try and test the drive in another machine, or test a new drive in that machine. But dont sweat it.

If anyone else runs into a problem like this, make sure you have spare drives laying around (if you're a geek, this wont be a problem). If not a geek, then find a geek to do it for you (also, remember local computer shops, they may be helpful).

Well, happy hunting.

---

### Post by Kellemora on 2008-12-08
Hi Crazy

Well my son took the computer back and got his money back.

On the way home he stopped and picked up a used Dell OptiPlexGX270 with XP Pro in it on a small 40 gig hard drive, for less than 1/3 the price.  The former owner added quite a few bits of hardware to it but apparently cobbed the original hard drive and did a reinstall of XP Pro, plus all the drivers for the hardware.  Everything worked fine that we could test!

I dropped a 60 gig EXT3 hard drive in it for Ubuntu Hardy and set the bios to boot from the second hard drive, which is also where I installed Grub so he can still boot into the Doze if he ever needs to.  I made / root and swap partitions at the top, but put /home on a separate 15 gig partition and also made a /data partition from the rest of the drive that's divided up into Music, Images, Documents & Personal folders.

He took to Ubuntu like a duck to water.  1000 times faster than I did!  And even installed wine on his own while here in order to install some program he needed for work to try out.  It to worked perfectly, so he's a happy camper!

The Ubuntu install found ALL but one piece of hardware he will probably never use (a TV tuner?) and installed the drivers for them without a hitch.  It's a 2.4 gig Pentium 4 with 1024 megs of Ram and a 650 watt power supply.

Almost the moment he got the machine home and set up, he installed Compiz and a few other programs like OOo.  And set up the other Repositories just by looking on line to see how to do it.  Took me like 4 days of studying to figure out how to do it!

I really expected my phone to be ringing off the hook with how do I do this and how do I do that, but he only called once later to say every things working GREAT!

TTUL
Gary

---

### Post by crazyness003 on 2008-12-08
> **Kellemora said:**
> ...I really expected my phone to be ringing off the hook with how do I do this and how do I do that, but he only called once later to say every things working GREAT!...
nice. I'm betting hes hooked now. If you mention VirtualBox to him, he'll probably never dual-boot into windows again.

The way i 'forced' Ubuntu on my family was with the "this is the last straw" technique. Our windows install went sour for some reason (itkept asking for activation, even after re-activating). So is said wtf, might as well do something drastic. and drastic it was.

Unfortunately, I needed IE since some construction websites DEMAND it. Enter VirtualBox. I did a quick insgtall of the same xp cd (hopefully it dosnt screw around again) and installed all necessary programs (FF, Thunderbird, Zonealarm, AVG, Sysinternals). Now i only boot it when i need a windows-only program to run, like ie or live messenger. No gaming here tho. The vBox can almost handle OpenGL, but not that well.

Okay. Well, another day, another one saved :D

---

### Post by Kellemora on 2008-12-09
Hi CN

I haven't even tried Virtual Box myself yet!

My primary goal after finding out I liked Ubuntu was to convert my entire office over to it.  Smartest move I ever made too!  After a very short learning curve for everyone, production is up considerably.

I installed wine on my personal machine, but wine didn't work for the front office programs that interface with commercial hardware.  So, front office still has an XP machine for that.

Actually, the only reason I have wine right now is to handle my e-mail program and it does that perfectly.

Once I get things working right, I don't like to mess with those machines, so I have an older machine I test things out on and was planning on seeing what this Virtual Box stuff was all about.
But I need to pick up some XP Home and XP Pro disks that take valid License numbers, not the OEM install disks I have that only do a new install to the same machine it came with, it checks something on the MOBO to make sure you're not trying to install it somewhere else, hi hi.........
I have tons of licenses here I can use, just no open type disks to use them from.  But I do have a repair shop that will gladly give them to me since I buy so much stuff there!

My son called last night after work to tell me how much faster and easier Ubuntu is than the Doze for almost everything he uses a computer for.  He's obviously smarter with these computin' contraptions than I am, hi hi.........

Have a nice day there CN!

TTUL
Gary

---

### Post by crazyness003 on 2008-12-10
thanks. I just wanna let you know a little 'secret' about VirtualBox. Sun Microsystems released 2 versions. The OSE (open source edition) and the PUEL (personal use and evaluation license). 
Its still the same program, but the PUEL has some features that were not included with OSE (although if you knew how to, you could just recompile the OSE version to overcome these obsacles. I dont know how to tho). Heres a list of the differences :[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)
The OSE verison is included in the Ubuntu repos. A quick synaptic search should hook you up. The PUEL can be downloaded from here: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

But even with the PUEL edition, it takes some work to get usb to work in the VM (its not the VM's fault tho, its the say linux security is set up. USB bus is allowed only by the user and root, nothign else, no even the VM).
Just some info for you. If you need assistance, we'll be more than happy to help.

---

### Post by Kellemora on 2008-12-11
Hi CN

Thanks for the tip!  
I jotted it down in my notebook in case I do try VM.

The only reason I installed WINE was so I could run Eudora, my e-mail program I've used for decades, hi hi.......

Plus some old win3.11 document utilities and converters I find useful at times, like GraphicsWorkshop95, hi hi.....

What I wish I could get working would be QuickBooksPro but I haven't found anything it would run under yet.

I downloaded PostBooks for Linux to give it a try, but then got swamped with work and never got back to studying it to see if I wanted to buy it or not.

Since I'm in the process of dumbing down the company as it is, I don't really need a program as powerful as QuickBooks, but I have years of data in QuickBooks that I have to refer to every quarter.

Unless I'm seeing it the wrong way, Virtual Box or VMware are similar to Wine, in that they let you run Windows Programs.  The difference being, if I"m correct that is, is that in Virtual Box you can install Windows itself, like Windows XP.

By my way of thinking, doing so could be self-defeating!
I moved to Ubuntu to get away from XP and Mickey$oft and to get things up and humming independent of them, so that when XP is no longer supported, I'm not left out there in the cold.  Because I will never use Vista for anything.  It's Mickey$ofts ultimate Spyware OS and they are trying to emulate Unix in a way with it too.  I saw that right off when I looked at my sons machine.  Many of the underpinnings are exactly like they are in Unix, not like the msDOS or Windows I had moved into.

Again, thanks for the tip!
I wish I had more playing around time than I do!
Hmmmm, perhaps it's good I don't, as I'm trying to learn Ubuntu, Edubuntu and studying how to build a file server.  All would be GREAT if I didn't need to keep a couple of XP machines for the time being.  And then their is the frau and her Adventure Games.
So far I have not been able to get a single one of them to run in Wine as they make API calls to function.  I did get one of her downloaded Big Fish games to run, but it stopped at like level 16 of 18 levels.  That's one of the reasons I may try Virtual Box to see if it will fix some of those things.  But NOT on this machine I need for work, hi hi..........

I'm going to be swamped the next few days, I'll still be on but not much.  Have a rush order to get out that I didn't think I could do as the particular packaging required I was short of.  But luck of the Irish, a tractor trailer pulled up a little while ago with exactly what I needed on board.  And of course it was pouring down rain when they arrived.  Part of Murphy's law I imagine, hi hi........  So I have a crew coming in on Saturday to knock this order out.  Then comes the bookwork!

You and yours have a Very Merry Christmas!

TTUL
Gary

---

### Post by crazyness003 on 2008-12-13
wine and a Vm are different.
Wine is an API layer that tricks the software running to think its a windows OS.
VirtualBox (or any other VM) emulates a hypothetical machine insode a hot OS. In the machine, you can install any OS you wish (did I mention ANY os? like oldschool win3.11 or even osx(question of legality))
And unfortuanately, as of right now, its nearly impossible to completely push away from mswin right from the getgo. And its all because the software company only wants to support win. 
You may find a replacement software here: [http://linuxappfinder.com/alternatives](http://linuxappfinder.com/alternatives)
Or even start some sort of movement and demand a FOSS replacement (i dont know where tho)

Good luck

---

### Post by chris062689 on 2008-12-13
Another great solution is to use a spare usb flash drive you have laying around.  You never have to burn another CD again!
Just simply run this program, and select the ISO.
Easy as pie...   [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Kellemora on 2008-12-13
Thanks CN!

Hi Chris
I'm OLDE now, my stash that's laying around consists of things like, Apple Disk II, 8 inch floppy drives, lot's of 5-1/4 inch drives, 1 and 4 gig hard drives abound, a few 10 gig ones also.
Power supplies for Doze 95 and 98 machines, etc.

But I have been upgrading a little!
A picture would be worth a thousand words, hi hi......
Sitting here at my desk, right in front of me, I see the backside of 5 computers, all blowing hot air onto me, 4 are through a KVM switch, monitor and keybaord above my desk and one is tied directly to my desk monitor, keyboard and mouse.  These are all fairly NEW machines, mostly built ups using cases or Mobo's from store bought machines.  Most have new 650 watt power supplies and at least 4 hard drives each, 2 internal and 2 external, plus an off-site hard drive for off-site backups (actually mirrors)  I hate backups as backups, prefer direct copy of everything.  This is my office!

Now, down at the house I have a near similar situation.
The Frau has the newest computer (don't she always!) and I have a small office down there with one antique and one new machine.
The antique was used as a print server, now it's just used for off-site data storage (meaning off-site from my office).
Front office has two Doze machines mainly to run the sales hardware and programs.

In the process of trying to downsize, I keep ending up with MORE instead!  You may have seen one of my beefs on another post!
Had to ADD another Doze machine in order to USE Ubuntu!

Have a Merry Christmas all!

TTUL
Gary

---

