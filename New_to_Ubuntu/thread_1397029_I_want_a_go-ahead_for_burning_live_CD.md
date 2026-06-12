---
title: "I want a go-ahead for burning live CD"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by Chris Edgell on 2010-02-02
I must tell you I have spent at least 15 hours at the HarvardComputer1 classes online.  I'm getting the picture.

Now here I sit. I have downloaded XUbuntu 9.04 to my desktop.  i386.iso

How DO I burn the liveCD?  Here's a screenshot.  What directions can you give me?

I thank you.

---

### Post by tom.swartz07 on 2010-02-02
> **Chris Edgell said:**
> I must tell you I have spent at least 15 hours at the HarvardComputer1 classes online.  I'm getting the picture.

Now here I sit. I have downloaded XUbuntu 9.04 to my desktop.  i386.iso

How DO I burn the liveCD?  Here's a screenshot.  What directions can you impart?

I thank you.

Before you do anything, check the md5sum of the file: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Verify that it has the same number as the original file.


An md5sum is a number that verifies that you downloaded a complete file. Sometimes, small errors can occur when you get it, and it will cause problems. 

Next, after you checked that everything is clear- burn the image.
Looking at your screenshot, it looks like its the last one on that menu page. DO NOT BURN IT AS A DATA CD!!!! 

After that, you should be good as gold to install!

---

### Post by OrangeCrate on 2010-02-02
> **Chris Edgell said:**
> I must tell you I have spent at least 15 hours at the HarvardComputer1 classes online.  I'm getting the picture.

Now here I sit. I have downloaded XUbuntu 9.04 to my desktop.  i386.iso

**How DO I burn the liveCD?**  Here's a screenshot.  What directions can you give me?

I thank you.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by audiomick on 2010-02-02
> **Chris Edgell said:**
> I must tell you I have spent at least 15 hours at the HarvardComputer1 classes online.  I'm getting the picture.

good on you!

I agree with Tom.
Check the md5 sum as he suggested.
Choose "burn image"
use the slowest burn speed that is available.

When you get booted into the CD menu, let it run the "check CD" option out of the CD menu.

---

### Post by Chris Edgell on 2010-02-02
hi, all I can do is to persevere; hangup on first instruction shows in screenshot.

I did download to desktop.

---

### Post by warfacegod on 2010-02-02
> **Chris Edgell said:**
> hi, all I can do is to persevere; hangup on first instruction shows in screenshot.

I did download to desktop.

download_directory means: ```
cd /where/you/downloaded/disc/image
```

---

### Post by tom.swartz07 on 2010-02-02
> **Chris Edgell said:**
> hi, all I can do is to persevere; hangup on first instruction shows in screenshot.

I did download to desktop.

when they say download_directory, they mean the folder that you downloaded the .iso to.

for example, if you have it on your desktop it would be
```
cd ~/Desktop
```

then you could hit TAB to auto complete the file paths and names, rather than typing the whole long thing

```
md5sum xu<TAB>
```
will finish the command

---

### Post by tom.swartz07 on 2010-02-02
> **warfacegod said:**
> download_directory means: ```
cd /where/you/downloaded/disc/image
```

ARGH! Warface, we always do this! hahaha

Great minds think alike, i guess! :D

---

### Post by Chris Edgell on 2010-02-02
Since I have told you where I have downloaded the iso, can you simplify for me exactly what I am to type there?

I see our messages crossed.  Let me go see.

---

### Post by audiomick on 2010-02-02
> **Chris Edgell said:**
> Since I have told you where I have downloaded the iso, can you simplify for me exactly what I am to type there?

Tom's post. number #7.

---

### Post by warfacegod on 2010-02-02
Tom, audiomick beat us both!


Hi, Chris.

---

### Post by tom.swartz07 on 2010-02-02
> **warfacegod said:**
> Tom, audiomick beat us both!


Hi, Chris.

HAHA! its a race!



Hey Chris-

I found the list of md5 hashes;
7afaff09c4b192415bad703ee564cff8 xubuntu-9.04-desktop-i386.iso

When you run the commands

```
cd Desktop
md5sum xubu**<TAB>**
```

you should get the same number.


alternatively, you could just run this one command:

```
[ "7afaff09c4b192415bad703ee564cff8" = "$(md5sum ~/Desktop/xubuntu-9.04-desktop-i386.iso | cut -d' ' -f1)" ] && echo OK || echo FAIL
```

That should take care of it

---

### Post by Chris Edgell on 2010-02-02
> **tom.swartz07 said:**
> when they say download_directory, they mean the folder that you downloaded the .iso to.

for example, if you have it on your desktop it would be
```
cd ~/Desktop
```

then you could hit TAB to auto complete the file paths and names, rather than typing the whole long thing

```
md5sum xu<TAB>
```
will finish the command

When I type in:  cd ~/Desktop       nothing happens
your next instruction: hit TAB      I did hit TAB and heres shreenshot

Are you not being explicit or am I just too damned dense?

---

### Post by warfacegod on 2010-02-02
You're in the desktop folder now.

---

### Post by tom.swartz07 on 2010-02-02
> **Chris Edgell said:**
> When I type in:  cd ~/Desktop       nothing happens
your next instruction: hit TAB      I did hit TAB and heres shreenshot

Are you not being explicit or am I just too damned dense?

You changed the directory to the desktop, but you never entered the command for the md5sum?


Try this instead:

> **tom.swartz07 said:**
> 

```
[ "7afaff09c4b192415bad703ee564cff8" = "$(md5sum ~/Desktop/xubuntu-9.04-desktop-i386.iso | cut -d' ' -f1)" ] && echo OK || echo FAIL
```

That should take care of it

---

### Post by warfacegod on 2010-02-02
The line that says: [email]chris@computer...Deskto[/email]p$, indicates that you have entered the Desktop folder. Where as you were in the / folder in the line before it.

/ = root, top of the folder heiarchy

---

### Post by Chris Edgell on 2010-02-02
So that little OK ... must mean it's OK.

OK, thank you all.

OKAY...OKAY...OKAY

---

### Post by warfacegod on 2010-02-02
Sure.

---

### Post by audiomick on 2010-02-02
Chris, I often have the problem of not knowing for sure if I am in the directory where the file is that I am looking for.
What really helps me is the "ls" command. Just
```
ls
```
in a terminal (small L, not number one).
It lists the contents of the directory you are in.

---

### Post by tom.swartz07 on 2010-02-02
> **Chris Edgell said:**
> When I type in:  cd ~/Desktop       nothing happens
your next instruction: hit TAB      I did hit TAB and heres shreenshot

Are you not being explicit or am I just too damned dense?

I suppose I didnt specify that you had to enter the beginning of the command.


> **warfacegod said:**
> The line that says: [email]chris@computer...Deskto[/email]p$, indicates that you have entered the Desktop folder. Where as you were in the / folder in the line before it.

/ = root, top of the folder heiarchy

Chris, I honestly do not intend to sound rude, but perhaps it would be helpful to look into some command line basics? Ive been creeping on a few of your previous posts, and although you have a really good intuition about using computers, it seems that you are quite shaky about using the command line.

Here are some good guides that will help you get a foothold on whats going on:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)


This entire book is a really great read, but Chapter 5 in particular is really informative.
[http://books.google.com/books?id=kHLlJzI6L20C&lpg=PP1&pg=PA67#v=onepage&q=&f=false](http://books.google.com/books?id=kHLlJzI6L20C&lpg=PP1&pg=PA67#v=onepage&q=&f=false)

---

### Post by tom.swartz07 on 2010-02-02
> **Chris Edgell said:**
> So that little OK ... must mean it's OK.

OK, thank you all.

OKAY...OKAY...OKAY

Yeppers! youre all set to burn the image. You like that little code? I love home-brewed commands with nice output. :D
I got that one from commandlinefu.com 




Remember, burn the image, not a data cd.

Let us know if it works!

---

### Post by Chris Edgell on 2010-02-02
[QUOTE=tom.swartz07;8766238]I suppose I didnt specify that you had to enter the beginning of the command.


Chris, I honestly do not intend to sound rude, but perhaps it would be helpful to look into some command line basics? Ive been creeping on a few of your previous posts, and although you have a really good intuition about using computers, it seems that you are quite shaky about using the command line.


LOL  Why does this remind me of the line, "The rumors of my death have been greatly exaggerated."  

I am studying for hours on end now; it's only by the forbearance of people like you all that I get anything done...sometimes I'm surprised people still come to my aid.  Again I thank you all.  

With such a beginner, I can really only follow explicit instructions, thank you for seeing my point on that matter.

Now I have the burned liveCD and I have put it into my "Machine #3".  As of right now, the icon of a disk sits on the desktop with the title, "XUbuntu 9.04 I386".

What I want to do is to catch the moment where the machine offers me the option of replacing ALL with this distro -- no partitions, no old OS left on it.  (Well, there was Windows AND Hardy, before now.)

What new advice, what next step?  I want this to replace all.

---

### Post by warfacegod on 2010-02-02
It sounds like you want to do away with everything on that computer. You need to restart the computer and let it boot into the disc. Select "Try without installing". When you click install and it gets to the which hard drive part, select "Use Entire Disk".

---

### Post by tom.swartz07 on 2010-02-02
> **Chris Edgell said:**
> So that little OK ... must mean it's OK.

OK, thank you all.

OKAY...OKAY...OKAY

> **Chris Edgell said:**
> [QUOTE=tom.swartz07;8766238]I suppose I didnt specify that you had to enter the beginning of the command.


Chris, I honestly do not intend to sound rude, but perhaps it would be helpful to look into some command line basics? Ive been creeping on a few of your previous posts, and although you have a really good intuition about using computers, it seems that you are quite shaky about using the command line.


LOL  Why does this remind me of the line, "The rumors of my death have been greatly exaggerated."  

I am studying for hours on end now; it's only by the forbearance of people like you all that I get anything done...sometimes I'm surprised people still come to my aid.  Again I thank you all.  

With such a beginner, I can really only follow explicit instructions, thank you for seeing my point on that matter.

Now I have the burned liveCD and I have put it into my "Machine #3".  As of right now, the icon of a disk sits on the desktop with the title, "XUbuntu 9.04 I386".

What I want to do is to catch the moment where the machine offers me the option of replacing ALL with this distro -- no partitions, no old OS left on it.  (Well, there was Windows AND Hardy, before now.)

What new advice, what next step?  I want this to replace all.

Im not quite sure what you mean- you want to install Xubuntu on the entire drive, deleting everything that was on it originally?



If thats the case, you just have to say "use entire drive" when installing.

---

### Post by audiomick on 2010-02-02
you need to go into the bios (oh my god! again!) and put the cd drive first in the boot sequence.

---

### Post by Chris Edgell on 2010-02-02
How IS it going to boot into the disc?  The first screen I get is the one that says Press F1 to continue, DEL to enter SETUP.

This gives me my old startup screen, with a Disc Icon labeled with the name of THIS new distro.

You remember, audiomick, but I studied a lot since then, I'm pretty sure I can go in and get the CD boot first.  That's it, anything else have to be changed there?

---

### Post by warfacegod on 2010-02-02
> **audiomick said:**
> you need to go into the bios (oh my god! again!) and put the cd drive first in the boot sequence.

If the BIOS has never been changed, CD-ROM should already be first.

---

### Post by Chris Edgell on 2010-02-02
Tell me where to look.  

When I look at CMOS Setup Utility it says:  First Boot Device    Floppy.  Is that it?

---

### Post by audiomick on 2010-02-02
Thats the right place. Floppy can be first, the important thing is that the cd drive is before any hard drives.

---

### Post by Chris Edgell on 2010-02-02
"As far as viruses and firewalls are concerned, they won't make a bit of difference once you install Ubuntu. The installation program will ask you whether you want to use the whole disk, or just the largest block of free space. Selecting "whole disk" will wipe everything off." 

This was written by Jim Kyle on another thread....What I want to know is:  WHERE IS the installation program.

Now a few days ago, when I stuck in the liveCD that I'd ordered some time back, it DID give me the options try it out or install.  This time it doesn't seem to be booting off the liveCD, does it?

---

### Post by warfacegod on 2010-02-02
> **Chris Edgell said:**
> "As far as viruses and firewalls are concerned, they won't make a bit of difference once you install Ubuntu. The installation program will ask you whether you want to use the whole disk, or just the largest block of free space. Selecting "whole disk" will wipe everything off." 

This was written by Jim Kyle on another thread....What I want to know is:  WHERE IS the installation program.

Now a few days ago, when I stuck in the liveCD that I'd ordered some time back, it DID give me the options try it out or install.  This time it doesn't seem to be booting off the liveCD, does it?

It should. As long as "Boot from CD-ROM" is before "Boot from hard drive" in the BIOS. You can change the order by highlighting the appropriate item and hitting something like F6. There should be a legend on the BIOS screen indicating which button is correct.

---

### Post by warfacegod on 2010-02-02
Another option would be to go into the BIOS and in the "Save Changes" screen select "Restore Defaults". That will almost certainly set CD in fro=nt of hard drive. In every BIOS (in your case, CMOS setup utility) I've ever seen, Boot from CD..." has always been before the hard drive.

---

### Post by Chris Edgell on 2010-02-03
Well, I've been fooling around with this for an hour.  I'll say one thing, when I said that about floppy being the "First Boot Device"...that wasn't good.  I did go in there and found another menu that offered CDROM as First Boot Device.  I click enter and escape and then the outer chart says CDROM.  Now I see F10 : Save and Exit Setup; when I press F10 I get a red box that says "Save to CMOS and EXIT (Y/N)? Y   and the final "Y" there is flashing; I press the capital Y and nothing changes there: my next and only way out is to press ESC.  I look back and it still says CDROM.  However, when I reboot, it has not been saved -- it has gone back to saying floppy.

I must give up on this. I'll have to leave it alone until another day.  Thanks for trying....well, we did burn the LiveCD, that WAS my original aim.

---

### Post by nhasian on 2010-02-03
instead of ls, use the *print working directory* command.

```
pwd
```

> **audiomick said:**
> Chris, I often have the problem of not knowing for sure if I am in the directory where the file is that I am looking for.
What really helps me is the "ls" command.

---

### Post by nhasian on 2010-02-03
yes it sounds like you did not save the changes you made in the bios.  did you see if your computer has boot options during startup?  hit the PAUSE button on your keyboard during the post screen so you can read all the options.  i know they can flash by pretty quickly.  pressing the SPACE key resumes the bootup process.  Sometimes the one-time boot options are F10 or F12 or something similar.  Then you can tell it to boot from the CDrom for this one boot.  Otherwise you will need to set it in your bios to always boot from CDRom until you tell it otherwise.  at the bottom of the bios screen it will tell you how to save and exit.  sometimes you have to press F10 for save & exit.

On another note, have you discovered IRC yet?  If you connect to irc.freenode.net and join the #ubuntu channel we can help you in realtime chatting instead of waiting for responses on the message forum.  I think you would benefit from that :)

> **Chris Edgell said:**
> Well, I've been fooling around with this for an hour.  I'll say one thing, when I said that about floppy being the "First Boot Device"...that wasn't good.  I did go in there and found another menu that offered CDROM as First Boot Device.  I click enter and escape and then the outer chart says CDROM.  Now I see F10 : Save and Exit Setup; when I press F10 I get a red box that says "Save to CMOS and EXIT (Y/N)? Y   and the final "Y" there is flashing; I press the capital Y and nothing changes there: my next and only way out is to press ESC.  I look back and it still says CDROM.  However, when I reboot, it has not been saved -- it has gone back to saying floppy.

I must give up on this. I'll have to leave it alone until another day.  Thanks for trying....well, we did burn the LiveCD, that WAS my original aim.

---

### Post by audiomick on 2010-02-03
@ chris: I think saving will work if you press small y instead of capital Y.

@ nhasian : "pwd" is a good tip, thanks. I often need ls to see exactly what the file is called that I am aiming for. I know it is cumbersome, bit I  am prone to being over precise...;)

---

### Post by Chris Edgell on 2010-02-03
Better overly than underly precise, Michael.

(I also tried the small y, neither shows any sign of acceptance, and still the only action available to me at that point is Esc.)

I MUST start a new thread.
Bye for now.

---

### Post by tom.swartz07 on 2010-02-03
> **Chris Edgell said:**
> Better overly than underly precise, Michael.

(I also tried the small y, neither shows any sign of acceptance, and still the only action available to me at that point is Esc.)

I MUST start a new thread.
Bye for now.

Not to beat a dead horse, but did you try just hitting ENTER?

---

### Post by warfacegod on 2010-02-03
> **Chris Edgell said:**
> Well, I've been fooling around with this for an hour.  I'll say one thing, when I said that about floppy being the "First Boot Device"...that wasn't good.  I did go in there and found another menu that offered CDROM as First Boot Device.  I click enter and escape and then the outer chart says CDROM.  Now I see F10 : Save and Exit Setup; when I press F10 I get a red box that says "Save to CMOS and EXIT (Y/N)? Y   and the final "Y" there is flashing; I press the capital Y and nothing changes there: my next and only way out is to press ESC.  I look back and it still says CDROM.  However, when I reboot, it has not been saved -- it has gone back to saying floppy.

I must give up on this. I'll have to leave it alone until another day.  Thanks for trying....well, we did burn the LiveCD, that WAS my original aim.

In that case "Solving" this thread would be appropriate.

I would still try resetting the BIOS to default.

---

### Post by Chris Edgell on 2010-02-03
Thank you guys, you've been great.

Tom, I went there and pressed Y and hit enter and the screen has gone black.  (It makes me realize that I had NOT hit enter.  And now it reboots with that: First boot device CDROM saved.)

Thank God Tom. that you persevered with beating that dead horse. That did the trick.  All that long sad tale in other post is moot...XUbuntu 9.04 that I burned IS NOW being downloaded.

TA-DA

I'll wait for the install to complete before I mark this solved.

Thanks warfacegod and audiomick and especially tom.swartz for hanging in there...I'm truly elated , I can't believe how my mood has brightened...it just shows how nothing feels better than a success.  To tom especially because some people would not have WANTED to ask if I had hit enter...in case I might take offense that you would think I was THAT dumb.  And even YOU backed away from it a little by the "dead horse" approach...thankyouthankyouthankyou!

It almost illustrates a couple of times here that you can't take anything for granted with someone who ACTUALLY IS an absolute beginner.

---

### Post by warfacegod on 2010-02-03
If it all works out, I suppose you'll need to mark your other one as solved too! It's like hitting two birds with one computer.

---

### Post by audiomick on 2010-02-03
> **Chris Edgell said:**
> 
It almost illustrates a couple of times here that you can't take anything for granted with someone who ACTUALLY IS an absolute beginner.

Good point, and one that is not always easy to keep in mind.;)

---

### Post by warfacegod on 2010-02-03
So the moral of the story is: When in doubt, grind some of your beans to make digital coffee?

---

### Post by tom.swartz07 on 2010-02-03
> **warfacegod said:**
> If it all works out, I suppose you'll need to mark your other one as solved too! It's like hitting two birds with one computer.

HAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHHHAHAHA!


Quote. of. the. year.

---

### Post by tom.swartz07 on 2010-02-03
Oh, and Chris- Im really glad that it worked out! :D


I guess it helps to say some dumb things sometimes! :popcorn:



Anywho- I hope that you get everything sorted out. Dont forget to read up on those few links that we posted, especially the Pocket Guide link. They will do wonders.

---

