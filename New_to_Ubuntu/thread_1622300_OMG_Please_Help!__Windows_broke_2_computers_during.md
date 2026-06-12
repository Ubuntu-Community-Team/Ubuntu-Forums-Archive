---
title: "OMG Please Help!  Windows broke 2 computers during install!!!  Need Ubuntu back!!!"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by luckylucky on 2010-11-15
OMG... I don't know whether to laugh or cry, but I'm close to tears.

2 computers broken in 2 days!!!!!!!

I'm a hard core ubuntu fan and use ubuntu exclusively.  However I've decided to install windows again because, well, to watch netflix I need to have the dual boot.

I installed windows (XP pro), and now machine #1 (laptop) won't get past that bios screen - you know that very first screen that appears when you just turn on your machine.  F2, esc, booting from disk / usb, nothing works.  Basically I thought it was a dead machine, said it's final prayers, and grabbed another machine.

With machine #2 (a desktop machine) I tried the same thing, this time trying to install XP home instead of pro, and I just bricked it exactly the same as above.

Bottom line is that obviously this is a windows problem, and the windows somehow bust both machines.  Why?  I don't know, but is it possible that it might have done so deliberately seeing that there are ext4 partitions with ubuntu?

Folks, PLEASE PLEASE PLEASE... how do I fix these machines now???  At this point I say screw it to windows... I'd be just happy to get my Ubuntu back.

---

### Post by Hippytaff on 2010-11-15
Can you do a fresh install of ubuntu from liveCD (if you have one handy), or are you trying to recover stuff first?

---

### Post by luckylucky on 2010-11-15
Dude, on neither computer am I even able to boot from a CD anymore.  

both computer hang on the bios splash screen.

I think I'm gonna cry now - for real.

---

### Post by Rushyang on 2010-11-15
You don't get pass through your bios screen seems weird... Generally if you install windows last.. Only windows boot loader will appear. ie you will be able to boot into windows only. 

Now, once you get to boot into windows only.. Use "Universal USB Installer" software (Google to get it) and get a ubuntu live usb stick through it... OR, get a ubuntu live cd. & then google "How to reinstall grub2" to get ubuntu grub back. (Grub2 for 9.10 and later version... grub for before it)

---

### Post by philinux on 2010-11-15
> **luckylucky said:**
> OMG... I don't know whether to laugh or cry, but I'm close to tears.

2 computers broken in 2 days!!!!!!!

I'm a hard core ubuntu fan and use ubuntu exclusively.  However I've decided to install windows again because, well, to watch netflix I need to have the dual boot.

I installed windows (XP pro), and now machine #1 (laptop) won't get past that bios screen - you know that very first screen that appears when you just turn on your machine.  F2, esc, booting from disk / usb, nothing works.  Basically I thought it was a dead machine, said it's final prayers, and grabbed another machine.

With machine #2 (a desktop machine) I tried the same thing, this time trying to install XP home instead of pro, and I just bricked it exactly the same as above.

Bottom line is that obviously this is a windows problem, and the windows somehow bust both machines.  Why?  I don't know, but is it possible that it might have done so deliberately seeing that there are ext4 partitions with ubuntu?

Folks, PLEASE PLEASE PLEASE... how do I fix these machines now???  At this point I say screw it to windows... I'd be just happy to get my Ubuntu back.

After the bios POST are there any beeps?

The beep codes can tell you the cause of problems.

---

### Post by C0derBear on 2010-11-15
Take a breath. I sincerely doubt you've lost anything but time at this point.

I'd guess that the MBR needs real repair work to make it MSWin-clean *cough* - neither install should have done *any* fussing with your BIOS settings - unless you're using a hacked MSWIn which in that case all bets are off.

You should be able to trap the BIOS before it goes to the drive to figure out booting, but on modern machines  you may need to be pretty quick. You may need to temporarily disconnect the internal drive in order to get to the BIOS and change a setting to slow it down - I've had to do that in the past. ;^(

Once you can get to the BIOS and configure the boot order, using either a CD-ROM or USB stick to boot from to begin the MBR/GRUB/whatever repair as the other poster said should be straight-forward.

---

### Post by Rushyang on 2010-11-15
> **C0derBear said:**
> Take a breath. I sincerely doubt you've lost anything but time at this point.

I'd guess that the MBR needs real repair work to make it MSWin-clean *cough* - neither install should have done *any* fussing with your BIOS settings - unless you're using a hacked MSWIn which in that case all bets are off.

You should be able to trap the BIOS before it goes to the drive to figure out booting, but on modern machines  you may need to be pretty quick. You may need to temporarily disconnect the internal drive in order to get to the BIOS and change a setting to slow it down - I've had to do that in the past. ;^(

Once you can get to the BIOS and configure the boot order, using either a CD-ROM or USB stick to boot from to begin the MBR/GRUB/whatever repair as the other poster said should be straight-forward.

Nice.

---

### Post by luckylucky on 2010-11-15
First of all I am currently in an unusual mental state right now - my head is swooning and I don't even know how to describe the emotion I'm feeling... kinda like a sense of desperation.  

I kid you not, the desire to cry is real... and I'm a "guy".  Having these two machines down is a serious blow to me - one was bad enough, but both "oh dear God".  Thank goodness for this wimpy machine to be able to at least communicate with you guys.

C0derBear, thanks for your thoughts.  Honestly I can't even wrap my head around what you just said.

I fear that I may have to do something to the guts of the machine.  Is there something I can do to somehow manually reset the machine cmos/bios/whatever?

Please treat me like an idiot - this is unfamiliar territory now doing whatever needs to be done now, and my head is far from being most resourceful.  Thanks for understanding.

---

### Post by qyot27 on 2010-11-15
That splash screen isn't the BIOS (it's the POST, rather), but that's inconsequential.

Since you're talking about XP here, there is no 'deliberate' screwing up because of ext4 partitions that the disk may have on it.  **However**, XP (nor Vista or Win7, I'd presume) can't even *identify* such partitions, and thus might have trouble recognizing them far enough to be able to format over them, as it definitely cannot resize them.

The following is really last-ditch compared to the previous answers, but here goes:

If you can, physically remove the hard drives and put them in USB/Firewire/eSATA/whatever drive enclosures.  Hook these up to a *working* Ubuntu machine, recover any data still on them, and then use GParted to wipe the partitions from the enclosured disks.  Do not create new partitions, leave them unallocated.  Then put the drives back in the machines they came from and try to start over - Windows first, then Ubuntu.

Windows should not have done anything to the BIOS (any OS is pretty much relegated to the HDD, the BIOS resides on the motherboard), and if it did, then my guess is that these aren't legitimate Windows install discs, or that you did something else to the firmware to make the mobo spazz out.

---

### Post by Rushyang on 2010-11-15
There is a trick of resetting CMOS to the factory's default settings.. But as assume you need to follow CoderBear's instructions first.. you won't need to reset CMOS.

---

### Post by luckylucky on 2010-11-15
> **C0derBear said:**
> - unless you're using a hacked MSWIn which in that case all bets are off.


No, I bought it from a major retailer store.  The disk has that holographic shiny look all over.  It is legit, so there shouldn't be any malware crap to think about.

---

### Post by jwbrase on 2010-11-15
> **luckylucky said:**
> Dude, on neither computer am I even able to boot from a CD anymore.  

both computer hang on the bios splash screen.

I think I'm gonna cry now - for real.

Can you get into BIOS setup from the splash screen? (usually something like F2, F12, ESC, or DEL while the splash screen is up, depending on your manufacturer. Sometimes the splash screen will say, sometimes it won't). That should tell us if BIOS is at least halfways working

Do you have a spare (preferably blank) hard drive? If so, try taking the drive with the botched Windows install out and putting the blank drive in, then try booting from a CD. (If you don't, you could even try disconnecting the offending HD and leaving just the CD drive connected). That should also tell us if it's just a disk problem or if it's affected the BIOS.

---

### Post by luckylucky on 2010-11-15
Folks, I need to go freak out for a bit.  I am stepping away from my machines for a while to clear my head before proceeding with anything.  I won't be here to reply to any posts for a while, but please continue posting in the meantime any solutions you might have.  You could bet your life's savings that I'll be back here to read what you wrote.

I quit smoking some time ago... I'm having an intense craving :(

---

### Post by jwbrase on 2010-11-15
> **qyot27 said:**
> That splash screen isn't the BIOS (it's the POST, rather), but that's inconsequential.

Well, POST is done by BIOS and option ROM's called by BIOS, but yes, it's inconsequential.

---

### Post by ivarn on 2010-11-15
Yea I don't think you are talking about Bios either.
Could you film the whole process with your mobile and upload it?
It will be easier to help you if we can see what bios version you have and all that stuff.

---

### Post by C0derBear on 2010-11-15
(un)Lucky,

Good idea to take a break and get some air. I know I've been where you are (okay, it's been a while, but still...).

Like jwb said, the BIOS has a keypress that it'll respond to while it is going through it's paces. If you've not been into your BIOS before it may be a wee tricky to find ... often varies by hardware vendor.

A related shortcut is that in many machines there's a keypress to make during POST/BIOS boot-up that will let you select what device to boot your machine from. On Dell machines for example this is usually F12 ... so gently tapping F12 during machine boot will present you with a list of bootable devices ( CD-ROM, hard drive, USB device, etc. ).

Sounds like you don't have the basics of what is going on during boot in your head, here's the off-the-cuff version to help you understand BUT keep in mind I'm rapping this in manually so I may have something wildly off for your machines ... or just forget something...

Basically, the steps your machine goes through could look like this:
1. Power up

2. Power On Self Tests execute ( POST ), this is done by the BIOS and used to determine which peripherals are connected, what boot volumes there are, how much ram, etc.

3. BIOS picks a boot volume, loads the Master Boot Record ( MBR ) and hands-off control.

4. The MBR code basically leverages a larger operation system loader (in the example of Windows this is named NTLDR ) which can know a lot more about the hardware and stuff and which actually starts the real operating system boot process.

There's lots of little niggly bits that can be screwed up and break the sequence, and it's usually completely NON-DESTRUCTIVE to any data or operating system on the machine ... you just need to proceed calmly and without hurrying so that you properly identify and fix the real problem(s).

Some other expert should kick in (I've only been using Linux at home full time for a couple weeks, and off and on since '91 or '92) but the primary boot loader for Linux is GRUB.

Part of GRUB sits in the MBR and hands off to a larger bit, which in turn get's the Linux kernel up and running which in turn can get the rest of the system going. GRUB is the counterpart to the Windows NTLDR. GRUB is so smart it also understands handing off the machine to NTLDR so that you can setup a GRUB boot menu to pick which operating system you want to boot. Not to get distracted but this GRUB boot menu is also the easy way to play around with different kernels on one machine.

WHAT I'M GUESSING is messed up by the MSWin installation is that low-level bit of the boot-loader support within the MBR ... or there's a configuration issue ... which I'll post in a new message.

---

### Post by C0derBear on 2010-11-15
Okay, so the configuration item that I just thought of which may be "in the way" is that you installed your 2nd OS (Windows?) onto the system, targeting a (new) partition that is pretty high up on the hard drive.

For many of the OS loaders, their basic stuff needs to be in the first 1k cylinders of the hard drive. It's a painful/insane limitation, but a REAL HONEST technical limitation no matter. If your machines are trying to boot into windows, and the windows bootstrap stuff is at > 1k cylinders, I don't think it'll work. I think it COULD manifest in precisely the behavior you are seeing.

It's a theory any way.

Add that to the situation that your CD/USB is "lower" in the boot priority than the hard drive and you could easily be in the situation you're talking about.

Again, this is CONJECTURE, but very plausible I think.

Again, we get back to just needing to get control of the boot sequence and you'll be okay. I've yet to hear of a machine that you can't do that to - it just takes some fiddling.

Good luck!

---

### Post by ppv on 2010-11-15
The next suggestion after trying what others have suggested would be to simply remove and re-insert the cmos battery on the motherboard...easier to do on the desktop. This would reset the bios settings and may bring your usb device to a higher boot priority which is generally the case now-a-days.

---

### Post by luckylucky on 2010-11-15
> **ppv said:**
> The next suggestion after trying what others have suggested would be to simply remove and re-insert the cmos battery on the motherboard...easier to do on the desktop. This would reset the bios settings and may bring your usb device to a higher boot priority which is generally the case now-a-days.

Around the time you posted this I was doing exactly that... on the desktop.  Because it's a slimline machine I had to move things, like the cd/dvd drive & fan, to get to the battery.  I also took the time to take a good look around within.

I removed the battery - looks like a silver coin - left it out for about 20 minutes, reinserted it, put humpty dumpty together again, plugged it in, turned it on, and watched breathlessly before my heart sank... no change.


I have this sick feeling in my gut... an no, it is not a (human) virus.  FWIW, I didn't actually shed a tear (yet), but I am sure not happy.  I soooooo miss seeing ubuntu happily booting on those machines.  ::sniff::

I'm at a loss with what to do now.  Will be carefully re-reading everyone's posts for further ideas.

---

### Post by Golem XIV on 2010-11-15
There are several things you may want to do in order to help us help you:

- The exact make & model of your computer(s).  If not available (i.e. if it's not a brand-name system but rather put together form separately bought components) then exact make/model of the motherboard;
- Are there any beeps coming out of the computer (two, three, four, long, short, continuous or any combination);
- What does exactly appear on the screen (blank screen with or without cursor, BIOS POST screem, "No OS Found", etc.);
- If the screen is completely blank, is the monitor on? If it doesn't receive a signal from the graphic card then will be in power save mode (either a flashing LED or a different coulour LED);
- What happens with the disk activity LEDs while powering on? They blink, they stay on, they don't light up at all?

---

### Post by jwbrase on 2010-11-15
> **C0derBear said:**
> (un)Lucky,

Good idea to take a break and get some air. I know I've been where you are (okay, it's been a while, but still...).

Like jwb said, the BIOS has a keypress that it'll respond to while it is going through it's paces. If you've not been into your BIOS before it may be a wee tricky to find ... often varies by hardware vendor.

Not to mention that the timing of *when* you need to hit it can be tricky.

---

### Post by dFlyer on 2010-11-15
> **jwbrase said:**
> Can you get into BIOS setup from the splash screen? (usually something like F2, F12, ESC, or DEL while the splash screen is up, depending on your manufacturer. Sometimes the splash screen will say, sometimes it won't). That should tell us if BIOS is at least halfways working

Do you have a spare (preferably blank) hard drive? If so, try taking the drive with the botched Windows install out and putting the blank drive in, then try booting from a CD. (If you don't, you could even try disconnecting the offending HD and leaving just the CD drive connected). That should also tell us if it's just a disk problem or if it's affected the BIOS.

I have not seen any answer to this question. Are you able to access your BIOS?

---

### Post by luckylucky on 2010-11-15
> **dFlyer said:**
> I have not seen any answer to this question. Are you able to access your BIOS?

No.  :(


I found someone else with a similar computer to my desktop:
[http://www.daniweb.com/forums/thread34017.html](http://www.daniweb.com/forums/thread34017.html)
Basically I could just say "ditto" to his posts

Honestly, I feel so sick (physically) thinking that I might have lost these two machines.  This could be a major setback in my life.  I'm taking another little break.  Will be back @ the forum soon though.

---

### Post by dFlyer on 2010-11-15
If your unable to access your BIOS - that is not good. Just strange that it would happen to two computers at about the same time. Is there any chance you may have had a power surge recently (ie electrical storm, power failure etc)?

---

### Post by luckylucky on 2010-11-15
OMG I might be onto something... but I definetely need advice before proceeding.


I found on the motherboard something that says clear cmos.  Next to it are some metal pins, 6 in all.  next to it it says "1-2 clear" and "2-3 default".

There are two little plastic things - I guess they are jumpers.  Image two rows of three pins - three on top 123, and three below abc.  One plastic jumper is on 2&3, the other is on b&c.

[COLOR="Red"]**I speculate that I can somehow clear the cmos with this thing.  Am I right?  What do I do?  how do I proceed?**[/COLOR]

Somehow a sense of hope has replaced that dread of earlier in my gut.  :)

---

### Post by luckylucky on 2010-11-15
> **dFlyer said:**
> If your unable to access your BIOS - that is not good. Just strange that it would happen to two computers at about the same time. Is there any chance you may have had a power surge recently (ie electrical storm, power failure etc)?

The thought had temporarily crossed my mind, but I ruled that out.  A) Two separate days.  B) Other machines at the time unaffected.  C) Unseasonably pleasant weather outside throughout whole time.  


Separate note - I just wanted to express how grateful I am to all of you who have jumped in to offer suggestions!  This ubuntu community is just great!!!

---

### Post by dFlyer on 2010-11-15
If 1-2 clears your BIOS place the jumpers on them. That might help for your Desktop, for the laptop I'm not sure.

---

### Post by dFlyer on 2010-11-15
I should also say that after you clear the bios return jumpers to 2-3.

---

### Post by tad1073 on 2010-11-15
where did you obtain the copies of windows xp?

---

### Post by luckylucky on 2010-11-15
> **tad1073 said:**
> where did you obtain the copies of windows xp?

A computer store.

---

### Post by luckylucky on 2010-11-15
Do I move those plastic things to cover 1/2 and a/b? 
Do I then boot it up like that?  How do I actually do this?
Please, talk to me like a complete noob.  thanks

---

### Post by dFlyer on 2010-11-15
> **luckylucky said:**
> The thought had temporarily crossed my mind, but I ruled that out.  A) Two separate days.  B) Other machines at the time unaffected.  C) Unseasonably pleasant weather outside throughout whole time.  


Separate note - I just wanted to express how grateful I am to all of you who have jumped in to offer suggestions!  This ubuntu community is just great!!!

It wouldn't be strange at all. Back in 89 or 90, my son-in-law was at our home during a thunder storm on one computer while I was on another. My motherboard got fried, his didn't

---

### Post by tad1073 on 2010-11-15
> **luckylucky said:**
> A computer store.

ok, just trying to rule out a nasty bios killing virus.

---

### Post by dFlyer on 2010-11-15
> **luckylucky said:**
> Do I move those plastic things to cover 1/2 and a/b? 
Do I then boot it up like that?  How do I actually do this?
Please, talk to me like a complete noob.  thanks

Never had a computer with the abc post just the 123 post. I would try the 1-2 alone first. Just put the plastic covers over 1-2, leave it there for a few seconds. Replace plastic post covers to 2-3 and try a reboot. Hopefully it will take you to bios setup.

---

### Post by C0derBear on 2010-11-15
Lucky,

Did I miss something, or did you post the make/model numbers of your two computers?

---

### Post by luckylucky on 2010-11-15
> **C0derBear said:**
> Lucky,

Did I miss something, or did you post the make/model numbers of your two computers?

No, sorry I didn't.

Desktop = HP Pavilion Slimline s7421c PC
Notebook = (from memory) averatec 1050

I have loved both machines for a good time.  Infact the averatec was my first dance with ubuntu ::sniff::


******************************* 

BTW, I attempted many runs (desktop).  shifted jumper pins.  ran both ways, with/without batter, even tried without the ram (computer didn't like that at all).  Returned everything back the way it was and still same result - that splash screen telling me to push esc for boot, f1 for options, f10 for recovery (unfortunately deleted the recovery partition long ago due to my love affair with ubuntu, divorcing win... regret deleting it).

My desktop is beginning to look 6 feet deep.

---

### Post by dFlyer on 2010-11-15
> **luckylucky said:**
> No, sorry I didn't.

Desktop = HP Pavilion Slimline s7421c PC
Notebook = (from memory) averatec 1050

I have loved both machines for a good time.  Infact the averatec was my first dance with ubuntu ::sniff::


******************************* 

BTW, I attempted many runs (desktop).  shifted jumper pins.  ran both ways, with/without batter, even tried without the ram (computer didn't like that at all).  Returned everything back the way it was and still same result - that splash screen telling me to push esc for boot, f1 for options, f10 for recovery (unfortunately deleted the recovery partition long ago due to my love affair with ubuntu, divorcing win... regret deleting it).

My desktop is beginning to look 6 feet deep.

what happens when you press f1?

---

### Post by dFlyer on 2010-11-15
> **dFlyer said:**
> what happens when you press f1?


Desktop = HP Pavilion Slimline s7421c PC - This is the same model my son-in-law had. He ended up sending it back to the company for a new video card within 60 days of his purchase. I'm not suggesting that is your problem because you have video on boot. It's just something to think about.

---

### Post by ppv on 2010-11-15
> **luckylucky said:**
> No, sorry I didn't.

Desktop = HP Pavilion Slimline s7421c PC
Notebook = (from memory) averatec 1050

I have loved both machines for a good time.  Infact the averatec was my first dance with ubuntu ::sniff::


******************************* 

BTW, I attempted many runs (desktop).  shifted jumper pins.  ran both ways, with/without batter, even tried without the ram (computer didn't like that at all).  Returned everything back the way it was and still same result - that splash screen telling me to push esc for boot, f1 for options, f10 for recovery (unfortunately deleted the recovery partition long ago due to my love affair with ubuntu, divorcing win... regret deleting it).

My desktop is beginning to look 6 feet deep.



press f1 here...that should take you into the bios settings

---

### Post by luckylucky on 2010-11-15
> **ppv said:**
> press f1 here...that should take you into the bios settings

Oh how I wish it were just that easy...






Something that has worked, sometimes, is ctrl alt del.  It just rebooted to bring me back to square one within exactly three seconds.

---

### Post by ppv on 2010-11-15
> **luckylucky said:**
> Oh how I wish it were just that easy...






Something that has worked, sometimes, is ctrl alt del.  It just rebooted to bring me back to square one within exactly three seconds.

why....what happens when you try to press F1 here ...does it not register the keystroke and just continues as if nothing was pressed....

---

### Post by luckylucky on 2010-11-15
> **ppv said:**
> why....what happens when you try to press F1 here ...does it not register the keystroke and just continues as if nothing was pressed....

It behaves as though nothing happened.  I've also tried every Fx button, Esc, and some others too.  It's like the keyboard isn't pluggged in (of course it is)

::groan::  so sad :(

---

### Post by migs73 on 2010-11-15
Lucky,

I think in your heightened emotional state you are missing the actions people are asking you to perform.!!

Take a deep breath and relax.........

With your computer off...... press the on button..... now gently start tapping the f1 key once or twice a second........... Hopefully now as you get to the BIOS/POST screen (keep pressing tha key though!)this will enter you into the BIOS set-up.

If this works, post back here and people will tell you what to look for in the BIOS settings.

---

### Post by C0derBear on 2010-11-15
FYI, the manuals for the desktop are [over here](http://h10025.www1.hp.com/ewfrf/wc/manualCategory?cc=us&lc=en&dlc=en&document=&product=1849529) if anyone wants them.

---

### Post by C0derBear on 2010-11-15
Lucky, Are you using a wireless keyboard?

When you went to reset the BIOS and removed the battery, did you also disconnect the power cable?

---

### Post by dFlyer on 2010-11-15
If you have another keyboard, you might want to try that????

---

### Post by jwbrase on 2010-11-15
> **luckylucky said:**
> It behaves as though nothing happened.  I've also tried every Fx button, Esc, and some others too.  It's like the keyboard isn't pluggged in (of course it is)

::groan::  so sad :(

Have you tried DEL?

---

### Post by luckylucky on 2010-11-15
I'm back from a few hour absence - had to take kids somewhere.

Being gone I've had a chance to calm down.  I am a bit more level headed now.

I will be going through all the posts again, and will compose a bit of a longer reply to address all the fine points people raised.

BTW, thank you all for your caring support :)  You are all greatly appreciated!

---

### Post by ironic.demise on 2010-11-16
Some BIOS have a keyboard support option
"from bios
or
from os"
 
If it's set to from bios you use your keyboard until in Windows or Ubuntu, I had to get a PS/2 to correct it on mine.

---

### Post by Golem XIV on 2010-11-16
Also some BIOSes will not work with USB keyboards (most keyboards are USB these days).  If your keyboard is USB (rectangular wide flat connector) get a keyboard with a PS/2 plug (small round green one) or an adapter, they should be available in any specialized store and shouldn't be expensive.

Also, what happens if you remove just one memory card (if you have more than one)?  Usually if the amount of memory changes the system goes to BIOS automatically so you can confirm that the new amount of memory is correct and not due to a malfunction.

---

### Post by C0derBear on 2010-11-16
> **Golem XIV said:**
> Also some BIOSes will not work with USB keyboards (most keyboards are USB these days).  If your keyboard is USB (rectangular wide flat connector) get a keyboard with a PS/2 plug (small round green one) or an adapter, they should be available in any specialized store and shouldn't be expensive.

From looking at the service manual for his machine it came as either wireless- or PS2 keyboard ... so I'd suggest he find a PS2 keyboard if he doesn't have one.

Considering the machine worked fine and went through installs, I'd suggest he stay away from mucking around inside as much as possible. That only increases the likelihood of hardware problem from jangled cables, etc., on these snap-together machine.

---

### Post by luckylucky on 2010-11-16
Hi folks, just a quick little update.  Due to being effectively like "without an arm", I needed to quickly setup a new computer - this is my current A+++ top priority.  I got an old machine from someone (it'll do) and am currently building it.  

I have to take 24 hours off to fix my main problem - not having a suitable machine - and once that is done then I'm returning here to continue to figure out how to fix the broken machines.

Furthermore, I mentally reviewed the situation and will provide some more, hopefully relevant, details.

Please note that I am not inactive today in this forum due to lack of interest, just I must scratch the greater itch - get a functional computer to work (gotta make a few bucks for the bills).

I *WILL* be back very soon

---

### Post by luckylucky on 2010-11-24
Now that a week has passed I feel compelled to provide an update for anyone who cares.

I have gone through the 5 stages of grief and have come to accept the situation.  Bad things happen.  Things die.  I am definitely not happy about it, and it is a significant setback to me.

Currently I am making do with a netbook. I've added a new OS (triple boot) that is light weight to allow me a bit more flexibility with software.  

I am marking this thread as "solved", not because it is, but rather as a courtesy so that others don't try to read through this long thread to discover that the computers are 6 feet deep.

Thank you everyone who tried to help.

---

### Post by ironic.demise on 2010-11-24
May they rest in peace.
Sorry to hear the news.

---

