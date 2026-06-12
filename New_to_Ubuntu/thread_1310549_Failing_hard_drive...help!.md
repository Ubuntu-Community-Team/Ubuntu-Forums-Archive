---
title: "Failing hard drive...help!"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by mollydoggy1971 on 2009-11-01
Today I upgraded to Karmic Koala.  I don't know if it's a coincidence or not, but it now tells me my hard drive is failing...it has bad sectors.  I will be buying a new hard drive Wednesday.  Where I need help is this...I am a major newbie at Linux.  Please assume I know NOTHING.  I want to know how to put the new drive in the system (hardware-wise, I'm fine), make Ubuntu recognize it, then copy 100% of the old drive to the new one, so that I can then remove the bad drive, place the new one as primary, and not lose any information in the process.  If someone could tell me how to do this, I would be very grateful.  Again, I must stress, I know virtually NOTHING about Linux, so I'll need VERY detailed, simple steps to follow.  Pretend you're asking a 5 year old child to perform the steps.  I promise not to feel slighted or insulted.  Thanks in advance for your help!

---

### Post by benj1 on 2009-11-01
just plug the new drive it, (you may have to mess with the switches on the back to sort out the master and the slave). install ubuntu on your new drive and transfer over your data from you old drive.
thats the easiest way, you could clone it, i dont know if thats a good idea if the hard drive has issues tho.

---

### Post by peculiar penguin on 2009-11-01
You probably want to run your hard disk manufacturer's diagnostic software before spending money, there has been some discussion about Palimpsest misinterpreting certain disks' health data (i.e. complaining about healthy disks). Usually this is available as an .ISO image you can burn to CD and boot your computer from, so if you managed to install Ubuntu this shouldn't be a challenge for you. Now if the manufacturer's diagnostic says the drive is bad then you'll definitely want to get it replaced as soon as possible.

---

### Post by mollydoggy1971 on 2009-11-02
> **benj1 said:**
> just plug the new drive it, (you may have to mess with the switches on the back to sort out the master and the slave). install ubuntu on your new drive and transfer over your data from you old drive.
thats the easiest way, you could clone it, i dont know if thats a good idea if the hard drive has issues tho.

I will try this.  Two questions though...How do I know what data to transfer?  Also, How do I clone the drive?  That sounds like what I'm looking for, but I don't know how to do it.

---

### Post by mollydoggy1971 on 2009-11-02
> **peculiar penguin said:**
> You probably want to run your hard disk manufacturer's diagnostic software before spending money, there has been some discussion about Palimpsest misinterpreting certain disks' health data (i.e. complaining about healthy disks). Usually this is available as an .ISO image you can burn to CD and boot your computer from, so if you managed to install Ubuntu this shouldn't be a challenge for you. Now if the manufacturer's diagnostic says the drive is bad then you'll definitely want to get it replaced as soon as possible.

I have a Maxtor drive.  They're Seagate now.  I tried installing their diagnostic software under WINE, but it wouldn't run.  In order to test it, I'd have to put it in my Windows machine, and I don't think it will read it correctly, as it's Linux formatted.

---

### Post by TheForumTroll on 2009-11-02
Cloning a bad drive sounds like a bad idea as it would also copy over any files corrupted by the bad drive with their errors :(

You could however install on the new drive and then mount the old drive. Then you could copy the stuff over you want (or keep using the old drive if you want) :)
Also I think seagate has a tool you can boot into and then test.

---

### Post by inspiteofmyself on 2009-11-02
i bought a brand new 500g drive not long ago, and it reported bad sectors on it as well. funny thing was that i couldnt find them with anything but palimpsest. it was brand new though, so i wasnt going to take the risk of having a new drive come out of the box with bad sectors...these arent the MFM/RLL days! :P

i wondered though, nothing that i tested the drive with complained. SMART error table was empty, but palimpsest reported SMART having bad sector errors.

after reading this, ill trust my instincts a little better on old drives, but if they are new...ill return them every time ;)

as for your problems...if the drive is failing...it is coincidence that it happened when you installed linux. the drive was likely like that before you installed linux.

if palimpsest is what told you the drive was failing, there is a good chance it may not be. id get something else to test with.

---

### Post by mollydoggy1971 on 2009-11-02
> **TheForumTroll said:**
> Cloning a bad drive sounds like a bad idea as it would also copy over any files corrupted by the bad drive with their errors :(

You could however install on the new drive and then mount the old drive. Then you could copy the stuff over you want (or keep using the old drive if you want) :)
Also I think seagate has a tool you can boot into and then test.

You assume I know how to do that.  Mount the old drive?  I don't know how.  Also, how do I know what to copy over and what not to?  I don't know where programs are located, and I don't know where personal data is located.  When I want to save something I download, for example, I save it to a folder on my desktop, because I don't know where anything else is.

---

### Post by TheForumTroll on 2009-11-02
You could just install and then return back here and get help to mount the old drive. But you would lose installed applications this way though.

---

### Post by mollydoggy1971 on 2009-11-02
> **TheForumTroll said:**
> 
Also I think seagate has a tool you can boot into and then test.

I've looked and am not seeing anything like that on their website.  They offer SeaTools, but it's for Windows or DOS, and it doesn't run under WINE.  They have a command line program for Linux, but, again, I know nothing about command line.

---

### Post by mollydoggy1971 on 2009-11-02
> **TheForumTroll said:**
> You could just install and then return back here and get help to mount the old drive. But you would lose installed applications this way though.

See, that's what I want to avoid.  If it were a Windows thing, I'd know where my data and such is located.  I'd also know what programs I need, and where to find them.  I know I've added a couple of programs on this install with some help from other forum members, and I don't know if I can do it again on my own.

---

### Post by TheForumTroll on 2009-11-02
Ah I see. Well there is a [guide here]("http://ubuntuforums.org/showthread.php?t=261366") that will tell you how to make a list of what you have installed now and how to install it again in a fresh install. Remember everything will still be there when you re-mount the old drive though. So you could always get help to get data and such back.

---

### Post by peculiar penguin on 2009-11-02
You're not supposed to run it in WINE... that wouldn't work anyway due to the lack of direct hardware access.

Scroll down on the SeaTools page, you want "SeaTools for DOS". They claim you have to register, just make up an e-mail address (or use [Mailinator]("http://www.mailinator.com/")), leave everything else empty. Download the ISO image file (SeaToolsDOS213bEURO.ISO), burn it to a CD-R(W) using the "burn image" feature (name varies) of your favorite burning app. It's similar to a LiveCD in that it contains a very basic operating system and the diagnostic software, you just need to tell your computer to boot from this CD instead of the hard disk. It may attempt to do this automatically (just leave the CD in the drive and restart your computer), you may have to press a key to get a "boot menu" and select the CD-ROM drive, or you may have to change the boot order in the BIOS (a bit more complicated yet still not rocket science, but try the easier options mentioned before first).

[Here]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=201271")'s Seagate's tutorial for the diagnostic software. Basically you'll have to accept a license agreement, then you'll want to run the "Short test" and "Long test" found in the "Basic Tests" menu.

---

### Post by TheForumTroll on 2009-11-02
Running it in Windows should work too. I would guess it reads at a lower level than the file-system anyway.

---

### Post by danastasio on 2009-11-02
alright, well to get a couple of things out of the way, basic filesystem setup:
/                 <-this is the entire directory, everything that exists as far as your computer is concerned exists under this directory, it is similar to the C:\ directory in windows.

/home             <- this is where user files are located, NOTE: files are not located in this exact directory, rather, in a folder named after the user.

/home/philip      <-now here are your user files, philip being the username.

Within the above directory:
Documents, Music, Desktop, Video, and Downloads are all folders within the /home/USERNAME directory. by default they are all empty because they dont have anything in them! You can remove them if you want, but they are there to keep your file system nice and organized. With the exception of the desktop. The desktop folder is not a folder, but contains everything that appears on your desktop.

the /home/USERNAME directory is the only directory that you can write to by default. this is done for security purposes, in that if you want/need to write to any other part of the file system, you need to input your password.

The simplest way to backup your pictures, downloads, videos etc. is to copy the /home/USERNAME folder, but this is quite large. (mine currently clocks in at 46 Gigabytes, and is growing, but i have a plethora of video) This will NOT copy the programs that you have installed, just your documents pictures etc. you could consider UbuntuOne or dropbox to backup your files if you dont have any way to store that much data.

so far as i know, there is no easy way to backup the programs that you have installed (however i consider myself to still be new) so there might be a way that i have not found yet. i'll keep an eye out for how to back up your programs (i think i already know, but i really dont want to say anything if it turns out to be terribly wrong.) and will post back here if i find an answer.

Hope this helped!

---

### Post by TheForumTroll on 2009-11-02
The guide I linked to will create a file with all installed packages listed and then reinstall them all on a new system. It is a rather easy guide to follow once the drive is re-mounted :)

---

### Post by danastasio on 2009-11-02
> **TheForumTroll said:**
> The guide I linked to will create a file with all installed packages listed and then reinstall them all on a new system. It is a rather easy guide to follow once the drive is re-mounted :)

awesome!!

also, here's a free guide to ubuntu to help you get to learn your new system!

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by Elfy on 2009-11-02
I am _not_ saying that there is nothing wrong with the drive, but it is _possible_ that you have this issue.

[http://ubuntuforums.org/showthread.php?t=1291998](http://ubuntuforums.org/showthread.php?t=1291998)

---

### Post by darksideforge on 2009-11-02
Did I miss something or is there a reason no one suggested System-->Administration-->USB Startup Disk Creator....?

He'd get the base .iso plus any programs he wanted to include and it wouldn't affect bad sectors.  If he was worried that the HDD was being
mis-read on startup he could burn the resultant .iso to a flash
drive or he could change options and burn it to a DVD...

Or did I miss something?

---

### Post by mollydoggy1971 on 2009-11-02
OK.  I got the SeaTools for DOS to run and, after the long test, my drive is indeed failing.  Over 90 errors.  I have the guide that was linked a bit back, and will be reading it tomorrow.  I'll be back here with any new questions I may have after reading it.  Could someone please explain why cloning the bad drive is not a good idea?  I'm under the impression that it would not make bad secotrs on the new drive.  Of course, I could be wrong.

---

### Post by Gorlist on 2009-11-02
moving onto a new harddrive is fairly easy as you don't need to shunt any backups around :)

If you think your hard drive is faulty, then I would just replace it - is it worth the risk of loosing your data? you can pickup WD 500gig sata drives for little over £40 quid from OC. 

You may be running IDE then you will need to fiddle with the jumpers, make your new harddrive the master and set your old one to slave (or set your bios to use the IDE channel and plug in accordingly). 

If your using SATA then its even easier as the order doesn't really matter as you can select which one to boot from first in BIOS (and can change the plugs around at a later date) - or just swap your existing drive and plug the older one into channel 2. 

Install ubuntu (make sure you use the same username) onto your new drive (recommend keeping your old drive unplugged, accidents do happen :)), then when your in, update, install the programs you normally use and then finially plug in your old drive. 

In Nautilus browse and mount your original drive, go to "/home/yourusername", then select all of the files and folders, copy (not cut) and paste into your fresh new drive user directory, so again browse your file system and go to "home/yourusername" (make sure you merge all).

Lastly to transfer application data (if you want to), go back to your original home/user directory, go "View/Show hidden files" and you will notice loads of new directories beginning with "." appear. Simply copy the folders you want and again paste into your new fresh user directory. 

So for example I take:

.mozilla 
.mozilla-thunderbird
.skype
.purple
.glabels
.gnome2/stickynotes_applet

(delete the existing .mozilla directory first to make sure it uses your old profile)

Nice and straight forward, and if you make a mistake or find your missing something then you can just plugin in your old drive and copy over the files. Reason I don't like copying all of the old home directory overwriting everything is I tend prefer nice clean new configs where possible.

---

### Post by danastasio on 2009-11-02
> **darksideforge said:**
> Did I miss something or is there a reason no one suggested System-->Administration-->USB Startup Disk Creator....?

He'd get the base .iso plus any programs he wanted to include and it wouldn't affect bad sectors.  If he was worried that the HDD was being
mis-read on startup he could burn the resultant .iso to a flash
drive or he could change options and burn it to a DVD...

Or did I miss something?

I didnt know that, thank you for edubacating me!!

---

### Post by darksideforge on 2009-11-02
> **mollydoggy1971 said:**
> OK.  I got the SeaTools for DOS to run and, after the long test, my drive is indeed failing.  Over 90 errors.  I have the guide that was linked a bit back, and will be reading it tomorrow.  I'll be back here with any new questions I may have after reading it.  Could someone please explain why cloning the bad drive is not a good idea?  I'm under the impression that it would not make bad secotrs on the new drive.  Of course, I could be wrong.

Cloning the drive is just that: making an exact duplicate. If your HDD is failing purely for technical reasons, cloning wouldn't hurt you from the mechanical standpoint, but there is reason to believe that with your drive already failing, some of your programs are already going to be failing as well (if any parts of them are located in bad blocks or sectors).  Cloning those failing/subpar programs would give you a brand new disk that was, for all intents and purposes, just as *broken* as your old disk...or at least, the behavior would be the same.

So, to answer your question: no, it wouldn't *make bad sectors* on the new disk, but it would be recreating any errors that are already present in your old disk.

I'm sure there's someone lurking who can give you a better explanation, but that should suffice until then.

---

### Post by mollydoggy1971 on 2009-11-03
> **Gorlist said:**
> 
In Nautilus browse and mount your original drive, go to "/home/yourusername", then select all of the files and folders, copy (not cut) and paste into your fresh new drive user directory, so again browse your file system and go to "home/yourusername" (make sure you merge all).

Lastly to transfer application data (if you want to), go back to your original home/user directory, go "View/Show hidden files" and you will notice loads of new directories beginning with "." appear. Simply copy the folders you want and again paste into your new fresh user directory. 

So for example I take:

.mozilla 
.mozilla-thunderbird
.skype
.purple
.glabels
.gnome2/stickynotes_applet

(delete the existing .mozilla directory first to make sure it uses your old profile)

Nice and straight forward, and if you make a mistake or find your missing something then you can just plugin in your old drive and copy over the files. Reason I don't like copying all of the old home directory overwriting everything is I tend prefer nice clean new configs where possible.

I thank you for the advice, but you're assuming I know too much.  I have no clue how to mount a hard drive, and the .mozilla, etc. list is confusing.  I don't know what or where those things are.

---

### Post by TheForumTroll on 2009-11-03
Just ask when you are ready ;)

---

### Post by darksideforge on 2009-11-03
> **mollydoggy1971 said:**
> I thank you for the advice, but you're assuming I know too much.  I have no clue how to mount a hard drive, and the .mozilla, etc. list is confusing.  I don't know what or where those things are.

In your old Windows system, have you ever inserted a CD disk and you get a pop-up menu item that gives you a choice similar to "View Files", "Copy to Hard Drive", "Open Files to View", or something similar?

"Mounting" a hard drive is very similar..."mounting" basically means the same thing as putting a CD in your CD-R and closing the door and waiting.  "Mounting" is sort of the same thing as "initializing" in Windows-speak.

What's unique/great about Linux is that you can actually command your computer to "mount" or "unmount" your CD/DVD drive depending on your specific needs.  The same holds true with your Hard Drive (HDD).

Have you ever opened your Windows Places or "Windows Network" folder?  If you do/have and you see a network "place" like a printer or a drive on another computer in your network that isn't physically attached to your own computer, and you then double-click on that particular icon (for example, the icon for a printer that is attached to your desktop computer downstairs while you're upstairs in the bedroom on your laptop), then you have effectively "mounted" that printer to your system.

Oh boy...I have the feeling that I may have just confused the living crap out of you....

There is no Windows-equivalent of "mounting" in that particular term. If you insert a CD disk into your CD-Rom drive, you have just "mounted" your CD.  Does that make any sense whatsoever?

I'm sorry that I'm not a better instructor/professor where this is concerned.

Keep asking questions or keep asking for clarification and we'll keep trying to get you where you want to be.  If we're lucky, one of the Moderators who's been around a while will pick up the slack and remind the rest of us goof-balls why they're moderators in the first place and the rest of us aren't!

~dsf

---

### Post by jmore9 on 2009-11-03
I was using a 40 gig seagate for my ubuntu machine.  It started to die so i bought a 80 gig WD.  I did a new install and then used the backup i made from the previous install to get the stuff off the old one.

I used the 40 until it died a horrible death by grinding to a halt.  Took about 1.5 months later .

---

