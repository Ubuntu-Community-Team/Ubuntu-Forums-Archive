---
title: "Burning a Disc and Installing"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by Tethryn on 2010-10-22
Ok. I am completley new to Ubuntu, and here is my situation. My previous computer broke, so my mother gave me her old compaq that she bought refurbished. It came with Windows XP Home, but no discs, so she made repair disks for it. When I went to reformat the computer the discs were missing a file and now it has no OS at all. 
 
Someone suggested I use Ubuntu, but I am confused on how to burn and install it. Right now I am using my mothers new laptop with Windows 7.
 
Do I have to download ubuntu-10.10-desktop-i386.iso to my mothers desktop, or can I save it to the disc and then put that in the compaq?
 
Can I just use the cd/dvd burner/program that comes with my mothers computer?
 
I'm sorry if I'm being dumb, but the download page for such things is not very clear in what to do...

---

### Post by JustinR on 2010-10-22
> **Tethryn said:**
> Ok. I am completley new to Ubuntu, and here is my situation. My previous computer broke, so my mother gave me her old compaq that she bought refurbished. It came with Windows XP Home, but no discs, so she made repair disks for it. When I went to reformat the computer the discs were missing a file and now it has no OS at all. 
 
Someone suggested I use Ubuntu, but I am confused on how to burn and install it. Right now I am using my mothers new laptop with Windows 7.
 
Do I have to download ubuntu-10.10-desktop-i386.iso to my mothers desktop, or can I save it to the disc and then put that in the compaq?
 
Can I just use the cd/dvd burner/program that comes with my mothers computer?
 
I'm sorry if I'm being dumb, but the download page for such things is not very clear in what to do...

Hi,

In Windows 7, find the '.iso' file, right click it, and press 'Burn Image' (make sure a blank CD is in the computer). Burn the ISO image. Then pop the cd into your Compaq and it should boot up just fine - I recommend using the 'Try Ubuntu before Installing' option just to see if everything on the computer works okay with Ubuntu. If you have any problems - don't hesitate to ask!

---

### Post by Tethryn on 2010-10-22
So I DO have to save the file onto my mothers computer first?

---

### Post by JustinR on 2010-10-22
> **Tethryn said:**
> So I DO have to save the file onto my mothers computer first?

Yep - '.iso' files are special files that expand to a bunch of different files - so you need to use the 'Burn Image' menu on Windows 7 to expand the file onto the CD.

---

### Post by sikander3786 on 2010-10-22
Welcome to the forums :popcorn:

> Do I have to download ubuntu-10.10-desktop-i386.iso to my mothers desktop, or can I save it to the disc and then put that in the compaq?

You can download it anywhere, on any PC and then burn a disc and use for installation on any PC.

> Can I just use the cd/dvd burner/program that comes with my mothers computer?

You can use and CD/DVD burning app as far as it supports burning image to disc.

I will recommend that after download, you verify the integrity of the downloaded image. It will save you lots of hard work later. See here for details.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And burn the disc at lowest possible speeds if there is an option in the CD burning app.

Welcome for any further queries :-)

---

### Post by Tethryn on 2010-10-24
I burned ubuntu-10.10-desktop-i386.iso to a disc, and put it in the compaq, restarted it, and nothing happened even though the cd was spinning. Instead it told me NTLDR missing. I dont thing this has anything to do with the disc though since it comes up even when there is no disc in the drive. Also, when I right click the file on my moms laptop I don't see a"Burn Image" command... Should I open it first?

---

### Post by JustinR on 2010-10-24
> **Tethryn said:**
> I burned ubuntu-10.10-desktop-i386.iso to a disc, and put it in the compaq, restarted it, and nothing happened even though the cd was spinning. Instead it told me NTLDR missing. I dont thing this has anything to do with the disc though since it comes up even when there is no disc in the drive. Also, when I right click the file on my moms laptop I don't see a"Burn Image" command... Should I open it first?

It might have burned correcly - on your computer - when the HP logo first starts up when you start your computer, does it list any buttons you can press to get to a boot menu? It should be something like F12, ESC, etc. If you get to it, select CD-ROM or Multibay drive with the keyboard arrow keys and press enter - Ubuntu should boot up then.

---

### Post by Iowan on 2010-10-24
> **Tethryn said:**
> I burned ubuntu-10.10-desktop-i386.iso to a disc, and put it in the compaq, restarted it, and nothing happened even though the cd was spinning. If you open the CD (view it's contents), does it show a single .iso file? (That would make it a coaster instead of a bootable CD)

---

### Post by Tethryn on 2010-10-24
When I press ESC to enter the boot menu a screen comes up with...
 
Boot Menu
 
Select a Boot First device
 
>HDD Group
 -3rd Master: Maxtor 6L100M0
>CD-ROM Group
 -2nd Slave: GCR-8481B
 
I'm not sure exactley what to do, but I tried opening and closing each of them and the same error message came up when I hit ENTER.
 
NTLDR is missing (It tells me to Ctrl-Alt-Del to restart, if I just let things be the same message always comes up...)

---

### Post by Tethryn on 2010-10-24
> **Iowan said:**
> If you open the CD (view it's contents), does it show a single .iso file? (That would make it a coaster instead of a bootable CD)
 
Yes on my mothers computer that is the only file I see on it...

---

### Post by RJARRRPCGP on 2010-10-24
You need to have the BIOS have the CD as the first in the boot sequence. And that error is from the Microsoft bootloader being unable to find XP.

---

### Post by SuaSwe on 2010-10-24
If you're only seeing a single file with an .iso extension when exploring the CD, you'll need to burn a new one and ensure that it is burnt as a bootable image. Last I used Windows to do this I believe I used PowerISO (free, afaik).

---

### Post by Tethryn on 2010-10-24
I think I got it working now, thanks for putting up with me everyone! XD

---

### Post by Tethryn on 2010-10-24
Not sure if I have yet ANOTHER problem, but when I click Install Ubuntu it just sits there "thinking" (The little circle thing is spinning). So far nothing has happened...

---

### Post by SuaSwe on 2010-10-25
How long have you given it? I remember on my ancient Dell Latitude laptop, it took 15+ minutes for the setup stage to initialise!

Also, once the issue has been resolved it would be great if you described what steps you took/advice you followed and marked the thread as "solved" using Thread Tools, just for the sake of anyone coming after you with a similar problem. :)

---

### Post by Tethryn on 2010-10-27
Well, I've left it on all night. (I havent been able to get back in a while, so I've tried everything I could all this time). I've tried both Installing Ubuntu and Trying It Out. Neither seem to want to work (just sits there thinking, sometimes freezes).
 
Sometimes it will come up with a message that says "The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again."
 
Then it switches to a black screen that I think tells about some errors but all I have been able to make out (the text is really small and darka nd the first bunch of times I missed it) is "failed due to unknown user id."
 
It comes up with some applet errors, asking me if I want to delete them. Depending on what I do I may or may not get options (Support etc.).
 
Then if I'm lucky it goes to what I am assuming is the desktop. There is usually two Icons, sometimes they look different, some options at the top on both corners, and the same on the 
bottom.
 
If I try to select anything it just sits there and "thinks". Then if I leave it be, all night for instance (even if I havent tried to do anything), and come back to check on it later I will only see the background of the desktop, and the computer may or may not be frozen.
 
Is there anything wrong with my disc? It looks fine. The computer isn't new, but it's not THAT old (I think... It had XP Home edition on it before now).
 
I have two blank discs left that I can burn if I have to. The one that I have been trying to use I burned using Cyber Link Power2Go (I'm assuming it came with my Mothers laptop).
 
Should I do this [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) ?
 
I'm trying not to download anything onto my Mothers laptop, she gets worried about it because some things end up changing stuff on her laptop (one time something deleted all of her passwords and user ids).

---

### Post by johnnie1uk on 2010-10-28
I had similar problems yesterday, ended up using a CDRW.. the first time i did a burn i got the coaster, so cleaned disc and when Cyber Link Power2Go  asked me to format i did.
did another burn from the download and it worked O.K looking at the disc there is a list of folders and files.
Took 3 or 4 minutes to load off boot on laptop, so that i could try out.
Persevere and it works.

---

### Post by ArgusVision on 2010-10-28
I wanted to offer another suggestion. You should be able to fix your windows boot and still install ubuntu afterwards. 
Take a look at this thread. [http://ubuntuforums.org/showthread.php?t=1603143&highlight=ntldr](http://ubuntuforums.org/showthread.php?t=1603143&highlight=ntldr) Scroll down until you see [COLOR="Red"]ntldr[/COLOR] highlighted in red
 Follow the fix that was given to that user, and it should fix the "missing ntldr" error you're getting. 
Then we can walk you through getting both Operating Systems on your PC.
If you have any trouble or need more details just give a shout.
   Hope this helps.:)

---

