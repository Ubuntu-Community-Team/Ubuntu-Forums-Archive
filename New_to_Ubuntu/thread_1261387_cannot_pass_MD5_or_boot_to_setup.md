---
title: "cannot pass MD5 or boot to setup"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by banjolawyer on 2009-09-08
I'm a noob.  Last time I tried to transition to Linux was in 2002, and I failed to stick with it at the time.  This time, I'm committed.  So, I appreciate the help I know I'll be able to get here.

I downloaded ubuntu-9.04-desktop-i386.iso several times this weekend, from different mirrors (most via Chrome browser but once via CuteFTP)

I am using winMD5Sum for MD5 check sum.

WinMD5 calculates the MD5 sum as
66fa77789c7b8ff63130e5d5a272d67b

which is the same as [here]("https://help.ubuntu.com/community/UbuntuHashes").  However, each time I test, WinMD5sum says the "MD5 Check Sums are different" when I click compare.

Also, when starting computer (Dell Inspiron 6000) with ubuntu-9.04-desktop-i386.iso burned to CD, Ubuntu setup does not load.  Same result with ubuntu-9.04-desktop-i386.iso on USB drive.  And my boot order in BIOS is floppy, CD, USB, internal drive.

Any suggestions?  Thanks.

---

### Post by the.phantom on 2009-09-08
i'm no heavyweight on Ubuntu but a few ideas?

what software are you using to burn? and are you sure you burned a ISO and not just a data copy?
what burn speed? ( i recommend X4)

what error are you getting when trying to boot from a cd? ( or what happens)

and when you said you d/l ed several times, gotta ask did you try different sites?

---

### Post by LewRockwell on 2009-09-08
what are you burning it with?

you need to slow-burn it with something like isorecorder

for reference:
(for XP)

[http://download.cnet.com/ISO-Recorder-Windows-XP-2003-Server-32-bit/3000-2646_4-10628966.html](http://download.cnet.com/ISO-Recorder-Windows-XP-2003-Server-32-bit/3000-2646_4-10628966.html)

.

---

### Post by scrooge_74 on 2009-09-08
Also note what is your hardware specs? Some people are having issues with ATI cards and some other stuff with the latest Ubuntu.

Then you need to burn it at slowest speed possible to avoid errors, also burn it as iso image.

If you burn it ok, if you put the CD in the PC even with windows running it should start and give you menus. That should tell you how you doing.

Keep posting

---

### Post by jsoellner on 2009-09-08
if you can visually verify that the md5 hashes are the same then you should be ok.

To boot from the CD, you need to change the boot order in your BIOS settings.  Normally on a Dell (like mine) you need to hit F2 just after POST.  Or you can hit F12 and choose to boot from the CD drive.

If you're not sure when to press either F2 or F12 just tap it every second or so after you power on.

Once you manage to boot from the CD, you can use the built in utility from the main menu to check the integrity of the CD.

---

### Post by sandyd on 2009-09-08
its f12 on all dell computers (except for the reallly aold ones)

---

### Post by scrooge_74 on 2009-09-08
> **carlee said:**
> its f12 on all dell computers (except for the reallly aold ones)

Maybe he has a really old one :lolflag:

---

### Post by banjolawyer on 2009-09-11
Hey everyone.  Thank you for the suggestions.

This is a Dell Inspiron 6000.  I'm not sure what type of specific hardware information would be relevant.  If there's a utility I can run, please let me know if that is necessary.

I burned a new disk at 4x using InfraRecorder.  Maybe I should have used ISOrecorder instead.  InfraRecorder was ranked pretty high on sourceforge, and I had forgotten to check back here for what the recommendation for a burner was.

I can redo it if necessary.  Looks like I may still have a problem.

I was able to boot from the new CD.
However, the last % I saw was 63% complete and then I saw an error message saying that there was an error copying data from the CD to the hard drive.

Once I clicked out of that message, Ubuntu appeared to be running.  I'm not posting with Ubuntu running now because I'm gonna have to figure out how to get connected wirelessly after I get past my current problem.

Do I need to reburn another disc and try again?  One of the weired things that happened when the CD was being burned was that, even though I asked it to burn at 4x, the display said it was being burned at 28x

---

### Post by scrooge_74 on 2009-09-12
If you got it up and running you may not need to burn another CD unless that one starts to give problems.

Check the specs for the DELL specially for the wifi card, but in the last few versions of ubuntu if the wifi card or the video driver was a restricted model (no open source drivers) the system would tell you and in most cases go fetch them itself, a few drivers have their own isntall guides. So check what DELL says you have inside that PC so you can see if there are any restricted drivers.

Most likely after you install you are going to have to use the wired ethernet to download wifi drivers unless there are open source ones. So before you install hook the network it will be easy that way.

Good luck, have fun and keep posting

---

### Post by armandh on 2009-09-12
Bad CD drives are a big PITA
they may play songs just fine but crash the installs.
any over 2 years old are always suspect [IMHO]
I keep a known good cd/dvd drive to use as needed.

a scratch or a thumbprint can wreck havoc too

since you are booting from the cd this does not apply but some MOBOs will only boot from the primary ide, and of course the HDD is always inconvient to re routing cable. [another reason for the spare drive.]

---

### Post by scrooge_74 on 2009-09-12
Worst case take a usb drive, use usb drive instructions and boot from usb (if bios allows for it)

---

