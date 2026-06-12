---
title: "starting from scratch"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by norm_56 on 2010-05-23
can you point me to the tutorial to install ubuntu after formatting a hard drive?
My daughter sent me her Dell laptop lattitude 505 with a virus. After too many hours of examining processes and stopping them, removing them, the virus persists.
I can not copy from the cd to the desktop any solutions. it blocks the copy. It blocks the DOS copy command, it blocks pslist, I can't boot ubuntu from the cd. I can get to the help files, and tried all the F6 options for booting.

How do I reformat the hard drive, and install ubuntu without re-installing windows? I have no reinstall cd that came with the laptop.  

She thinks I am the dad that can fix all her problems. I scanned the tutorial on installing a new hard drive, FAT, partitioning, lots of sodo commands. Is that what I need to do?

Give me 3 days and I can learn it.

Thanks.

---

### Post by CharlesA on 2010-05-23
Why can't you boot off the livecd and install it from there?

---

### Post by ubudog on 2010-05-23
First of all, it will not take 3 days to learn everything.  But anyway, you need to get an Ubuntu CD from []("http://www.ubuntu.com") and burn it as a .iso.  After that, boot into it.  Follow the on-screen instructions to install Ubuntu.  When it gets to the partitioning part, make sure you select the guided install format "use entire disk" option.  After that, you will no longer have Windows, and you will be able to restart your computer into Ubuntu.  Good luck.

---

### Post by ubudog on 2010-05-23
Oh, and if you can't burn a .iso or anything, just request one for free from here: [http://www.ubuntu.com/shipit]("http://www.ubuntu.com/shipit")  It may take a while though.

---

### Post by alphacrucis2 on 2010-05-23
> **norm_56 said:**
> can you point me to the tutorial to install ubuntu after formatting a hard drive?
My daughter sent me her Dell laptop lattitude 505 with a virus. After too many hours of examining processes and stopping them, removing them, the virus persists.
I can not copy from the cd to the desktop any solutions. it blocks the copy. It blocks the DOS copy command, it blocks pslist, I can't boot ubuntu from the cd. I can get to the help files, and tried all the F6 options for booting.

How do I reformat the hard drive, and install ubuntu without re-installing windows? I have no reinstall cd that came with the laptop.  

She thinks I am the dad that can fix all her problems. I scanned the tutorial on installing a new hard drive, FAT, partitioning, lots of sodo commands. Is that what I need to do?

Give me 3 days and I can learn it.

Thanks.

Just as an aside. Have you tried using malwarebytes? I find that to be one of the more effective tools for sorting out Windows malware issues. Too late if you have already wiped the disk and installed Ubuntu. In that case: Welcome to the light side :P.

---

### Post by norm_56 on 2010-05-23
Thank you so much for replying.
I figured out how to burn the cd.
I put it in 
I get two little icon on a black screen. a keyboard and a circle with a figure in it
I hit Enter
I get the menu
I try install
A stupid looking red box comes up with an error message. ( i figure it is the virus)

I go to the help file and try all the options - i don't remember- no adad or something like that using F6 and still that stupid error box comes up.

---

### Post by wojox on 2010-05-23
You could try downloading [Darik's Boot and Nuke]("http://www.dban.org/")

---

### Post by ubudog on 2010-05-23
> **norm_56 said:**
> Thank you so much for replying.
I figured out how to burn the cd.
I put it in 
I get two little icon on a black screen. a keyboard and a circle with a figure in it
I hit Enter
I get the menu
I try install
A stupid looking red box comes up with an error message. ( i figure it is the virus)

I go to the help file and try all the options - i don't remember- no adad or something like that using F6 and still that stupid error box comes up.

Restart your computer and put in the cd. Press either ESC F10 or maybe F12.  And select the CD.  Then, it will boot.

---

### Post by Bradtek on 2010-05-23
Are you trying to use the Install CD in Windows ?

You need to Restart the computer with the Install CD in the drive
You may need to go into the BIOS and set CD/DVD Drive as first the Boot Order.

Once you can Boot from the Install CD things should be much clearer.

---

### Post by 2hot6ft2 on 2010-05-23
At the manufacturers screen when it first starts there are options usually at the bottom of the screen choose the Boot Priority one and select the cd drive. That's what they are trying to say. The key can be any number of possibilities but is usually the esc key or one of the F# keys above the keyboard.
You'll have to read fast. If you have to use Ctrl+Alt+Del to see it again. And you have to press the key while it's on that screen.
:popcorn:

---

### Post by norm_56 on 2010-05-23
I am sorry- I must be real thick
I do all that F12 
a quick line about ISOL Linux goes by.
I get the black screen, two small icons at the bottom, a small keyboard and a circle with a guy in it.
I hit enter,
I get the Ubuntu menu
I choose English
Try Ubuntu without installing
Install Ubuntu
Check disk
Test memory
I don' try "boot from first hard disk"

F1 Help, f2 Lnguage, F3 kemap, f4 modes, f5 accessability, f6 other options

what ever I do I get a crude looking box 
"I/O error"
Error reading boot CD
Reboot

---

### Post by UnknownFear on 2010-05-23
> **norm_56 said:**
> 
what ever I do I get a crude looking box 
"I/O error"
Error reading boot CD
Reboot

Seems like the burn process failed. When you burn the .iso, always make sure to verify the integrity of the burn process. Burn the .iso again, but this time, make sure that the option to verify the disk is checked.

---

### Post by CharlesA on 2010-05-23
> **UnknownFear said:**
> Seems like the burn process failed. When you burn the .iso, always make sure to verify the integrity of the burn process. Burn the .iso again, but this time, make sure that the option to verify the disk is checked.

The OP can select "check disk for defects" first, but I have a feeling it was a bad burn. Verify the MD5SUM of the ISO before burning it to cd.

---

### Post by Scarfnoogan on 2010-05-23
Burning at the slowest speed apparently helps too, though to be fair, I've never done that :P

---

### Post by wojox on 2010-05-23
When you download an ISO there is usually a hash5 or shm1 value to compare your iso file to.

Here's the numbers to compare them to if your running Lucid [http://noncdn.releases.ubuntu.com/releases/10.04/MD5SUMS](http://noncdn.releases.ubuntu.com/releases/10.04/MD5SUMS)

---

### Post by norm_56 on 2010-05-23
Thank you!
I will re-burn a new cd and verify it tomorrow at work, during lunch. I have a dissel connection at home.


Oh, that dban suggestion seemed quite drastic. Now I know why they changed all the computers in the student lab to not execute anything that in put in the cd drive.

And this virus re-directs everything, I can start malware bites, spyware doc, I can't get to ms update, I can't copy rootkit revealer over, it is just madness.

on the morrow.

---

### Post by ubudog on 2010-05-24
> **norm_56 said:**
> Thank you!
I will re-burn a new cd and verify it tomorrow at work, during lunch. I have a dissel connection at home.


Oh, that dban suggestion seemed quite drastic. Now I know why they changed all the computers in the student lab to not execute anything that in put in the cd drive.

And this virus re-directs everything, I can start malware bites, spyware doc, I can't get to ms update, I can't copy rootkit revealer over, it is just madness.

on the morrow.

Yeah I know what you mean.  Windows sucks.

---

### Post by norm_56 on 2010-05-31
The CD works in my newer laptop.
After trying no less than 8 time, and gettng the black screen, I opened windows. Got all kinds of error messages about corrupt files (from the virus) but! I could get to the cd and install ubuntu. Still got the black screen.
Some how found my to a place that ran a script. it said my wireless driver was not up to date and go get the new one. and to follow instructions carefully. Yeah right. 
Got this idea. hooked up an eithernet cable, found my way to dpkg. It uploaded 178 ms. of stuff. then something about I chose not to load a grub, but the "no" answer just sat there. So I said "yes" now I am back to the screen, i click resume, i get rc-sysint start/running, proces 10054 
a bunch of lines enabling addintonsl executable binary formats..
 
Then- - ubuntu login:  
Last time i logged in, i got stuck in some dos type window. exit did not work.
 
How do i run ubuntu from here?

---

### Post by saakeman on 2010-05-31
listen to what I am gona say 

You are going to need a usb (3-4 GB or 2 )
** 1st you extract that iso file in a folder 
** 2 : you download linux  live usb creator 
** 3 : run it  
** 4 : follow the steps ... 
** 5 : once done go to bios 
** 6 : select the hard drives 
** 7 : then set it to your usb 
** 8 : and reboot !

---

### Post by norm_56 on 2010-06-01
thanks for your help.
Did all that you requested.
 
had to enter a boot param- live vga=771 noapic nolapic
get red waning about a wireless kernel needed.
 
find my way to the $ubuntu prompt, plug in a eithernet cable directly to the router.
type in command: sudo apt-get install b43fwcutter
 
all sorts of stuff loads and updates- real sweet!
I am now stuck at the $ prompt again.
I can't figure out how to get out, so I hold the power button down.
 
Restart- use the same boot param- get the same red message about
b43/ucode5.fw not found
b43/-pem/ucode5.fw not found (mis typed, and turned off laptop) 
go to the website and download it.
Is it because I did not properly exit that the driver did not update?

---

### Post by norm_56 on 2010-06-02
I knew it was going to take at least 5 days to lean this thing.
One week later and I am still at the black screen of death.
I get there two ways- running ubuntu from the installed version- this just gets me to a ubuntu logon screen. I will try running sudo apt-get install b43 fwcutter again.
 
(I plug the laptop into the wireless router)
I boot from a memory stick, go straight to help, then use the boot prompt with the following parameters:
vga=772 aic7xxx.aic7xxx=no_probe netcfg/disable_dhcp=true noapic nolapic
 
still get b43/ucode5.fw not found
           b43/-open/ucode5.fw not found
 
when I run the get install b43, does it automatically update or do I have to do something else?
 
somewhere in my many hours on the site I saw something about having to disable wireless protection until a connection is established.
 
I will give it two more weeks and then call it quits. I may be that the laptop is just too old. I ran it on this laptop- the one without the virus, and wow- fast and sharp looking.
I see the value in learning ubuntu. Its harder than learing php and way harder than installing modx on a server to run websites.

---

