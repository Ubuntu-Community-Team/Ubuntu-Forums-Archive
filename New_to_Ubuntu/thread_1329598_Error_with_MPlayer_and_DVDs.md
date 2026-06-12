---
title: "Error with MPlayer and DVDs"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by KarmicKlot on 2009-11-17
When I insert a DVD and try to play it with Movie Player in Karmic Koala, the following message appears "An error occurred - No URI handler implemented for "dvd"."
 
Is there a solution for this?
 
This is unfortunately one of a raft of problems I have with Ubuntu, the worst of which is that Evolution Mail will not let me access my e-mail, but continually asks for a password for the "Default Keyring". As I have never set up any password this is impossible, but equally it is impossible to stop the pop-up re-appearing. The only way out of the situation is to press and hold the power button to turn off the computer.
 
I installed Ubuntu 9.10 in dual boot with Vista. In the install it partitioned the hard drive. Can I uninstall Ubuntu and recover the partioned disc space without destroying my Windows installation? If so, How?

---

### Post by quinnten83 on 2009-11-17
**[SIZE="7"]YES![/SIZE]**

but seriously?
have you installed ubuntu-restricted-extras and the medibuntu repositories and then installed the libdvd codecs so you can play encrypted DVD's?

you don't have to turn off the entire computer just to use evolution, you can open terminal and then type: 
```
killall evolution
```
That should kill evolution and stop the popup.
I would go about creating a keyring to see if that solves the problem.

---

### Post by volodymyr on 2009-11-17
You can boot with Windows recovery disk, in recovery mode, and when you will see a command line do a fixmbr. The following article explains this in details: [http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

After you will fix your mbr, the Windows will normally boot and you would not see a grub menu. After you can reformat partition which you used to install ubuntu on, and merge it into another partition if needed. You can use Paragon Partition Magic for that.

---

### Post by Old *ix Geek on 2009-11-17
> **KarmicKlot said:**
> When I insert a DVD and try to play it with Movie Player in Karmic Koala, the following message appears "An error occurred - No URI handler implemented for "dvd"."
 
Is there a solution for this?Yes, but I don't know what it is offhand, so someone else will answer.
> Evolution Mail will not let me access my e-mail, but continually asks for a password for the "Default Keyring". As I have never set up any password this is impossible, but equally it is impossible to stop the pop-up re-appearing. The only way out of the situation is to press and hold the power button to turn off the computer.You really MUST get out of the windoze mindset of rebooting/shutting down to fix every problem. Thank goodness this isn't windoze.  Just enter your password when you're prompted for the default keyring's password. It's been a while but I think that's all that's necessary.  If there's more to it than that, it should prompt you after you enter your password.

I don't use Evolution for mail (I use SeaMonkey's e-mail client), but I'm curious now as to why it's prompting for the default keyring's password. I know I've tried it in the past and it didn't do that for me.  Is it some kind of permission problem?

---

### Post by t0p on 2009-11-17
> **KarmicKlot said:**
> When I insert a DVD and try to play it with Movie Player in Karmic Koala, the following message appears "An error occurred - No URI handler implemented for "dvd"."
 
Is there a solution for this?
 
Of course.  Lots of useful info [here]("https://help.ubuntu.com/community/RestrictedFormats").  If you don't understand something, come back and ask.

> **KarmicKlot said:**
> 
This is unfortunately one of a raft of problems I have with Ubuntu, the worst of which is that Evolution Mail will not let me access my e-mail, but continually asks for a password for the "Default Keyring". As I have never set up any password this is impossible, but equally it is impossible to stop the pop-up re-appearing. The only way out of the situation is to press and hold the power button to turn off the computer.


What do you mean, you "never set up any password"?  When you install Ubuntu, the installer asks you to set a password.  Have you tried using that password?
 
> **KarmicKlot said:**
> 
I installed Ubuntu 9.10 in dual boot with Vista. In the install it partitioned the hard drive. Can I uninstall Ubuntu and recover the partioned disc space without destroying my Windows installation? If so, How?

If you really want to give up on Ubuntu because of a few problems, go ahead.  But don't you think it might be better to try and *solve* the "raft of problems"?  Users of these forums will be only too happy to help.

Start a new thread for each problem.  Explain exactly what's wrong.  You will get help.

Alternatively, give up.  But first, answer me this: Why did you install Ubuntu in the first place?  Has that reason gone away?

Whatever you decide: good luck.

---

### Post by KarmicKlot on 2009-11-17
Unfortunately the only password I have set is the Administrator Password, and it does not accept that. The only way that I could find to get out of the loop in which the password box popup came back immediately it was cleared, and nothing, repeat nothing, else would work, was to switch off. 
 
I would love to get out of the Windows mindset, provided that does not also mean getting out of the mindset of having programs that actually work. I don't find having to use a terminal every time I want to do something very appealing. I tried Ubuntu, after a gap of several years since my first attempt to escape from Microsoft, but sadly I am finding that things don't seem to have improved very much. I dare not try messing about with partitions at the moment as I have to take the laptop on a trip, and need Windows working. I will use my spare time to see if I can sort out the problems with Ubuntu. I installed the libdvd codecs yesterday, but still no luck with the dvd player.
 
P.S. Reason for intalling Ubuntu was to have a more secure laptop for the internet when overseas, and Firefox is working OK, but without my ISP based e-mail, and only web based mail (Yahoo) working I remain forced to rely on Windows.

---

### Post by Old *ix Geek on 2009-11-17
> **KarmicKlot said:**
> I would love to get out of the Windows mindset, provided that does not also mean getting out of the mindset of having programs that actually work.  I don't find having to use a terminal every time I want to do something very appealing.I understand that you're having problems and that you're frustrated as a result, but it's unfair to generalize and act as if nothing works on Linux.  Simply not true.  I use nothing but Linux.  The only time I see windoze is when I buy a new computer that comes with it pre-installed, and I can't wipe it off the hard drive fast enough.  EVERYTHING works for me.  That's right.  Everything I want to use works for me--all the graphics programs, all the office programs, all the multimedia programs, and so on, without ever needing to do anything at a command line. I even play my favorite game, Roller Coaster Tycoon, on Linux by using wine and it runs/plays better than it does on windoze boxes I've seen it on.  I run my business on Linux.  I do everything on Linux. If it were as fraught with problems as you're suggesting, how would this be possible?

Over the years when I had the displeasure of using windoze boxes (at my last job [programmer/sysadmin] we had some 'doze desktops...that were the bane of my existence with their constant crashing, their RIDICULOUS slowness, etc.), I've practically gone bald from pulling out my hair in frustration. I honestly have no idea how anyone can use anything so bloated, slow, uncustomizable, etc.

I'm not trying to diminish the frustration you're feeling due to the problems you're experiencing, just pointing out that your experience is NOT typical.  For every post you see on this forum complaining about a problem, there are probably a thousand other people out there using Ubuntu WITHOUT problems...so they're not posting here.  People only post when they need help.  So don't let the number of problems on this board color your thinking about Ubuntu.

Have you thought about switching to KDE?  It's so much nicer--in my humble opinion--than GNOME, and in my experience everything just works with it.  Perhaps give it a try.  You can either burn a Kubuntu CD or you can go to [KDE.org](http://www.kde.org) and download the latest version there (I think you can also install it via Synaptic).

---

### Post by KarmicKlot on 2009-11-17
Evolution problem solved.  I followed the suggestion to create a keyring password, and created one called "default".  Then I went back to Evolution, and it did not ask for it!
 
Now I am working on the dvd issue.  My first thought was that perhaps it was the dvd, but the same thing happens with others.
 
If I can get that going then I have to tacle the BIG ONE!  I have used Quicken for many years to keep some very complex and extensive accounts.  No way could I transfer all the data to another program, so it looks as if I will need a windows emulator, is that wine?

---

### Post by mivo on 2009-11-17
> **KarmicKlot said:**
> I have used Quicken for many years to keep some very complex and extensive accounts.  No way could I transfer all the data to another program, so it looks as if I will need a windows emulator, is that wine?

That would be Wine, but there are money management programs for Linux that can import Quicken files. You'll have to look around. I believe KMyMoney can do this, but as I said, you'll have to google a bit.

---

### Post by Old *ix Geek on 2009-11-17
> **KarmicKlot said:**
> Evolution problem solved.  I followed the suggestion to create a keyring password, and created one called "default".  Then I went back to Evolution, and it did not ask for it!Great! Glad to see some progress. :)

---

### Post by alicemoon on 2009-11-17
[QUOTE=]If I can get that going then I have to tacle the BIG ONE!  I have used Quicken for many years to keep some very complex and extensive accounts.  No way could I transfer all the data to another program, so it looks as if I will need a windows emulator, is that wine?[/QUOTE]

Gnucash is what I use - and you can import quicken files in it - don't give up on Ubuntu - I made the decision a year ago to switch completely out of windows and have not looked back. Sometimes it is a bit of a learning curve but I know there is lots of support out there when I need it. Take it slowly and keep the dual boot until you are happy everything is fixed - once you start using ubuntu regularly you will find the positives outway the odd problems you come up against.

---

### Post by Cityscape on 2009-11-17
> **KarmicKlot said:**
> No way could I transfer all the data to another program, so it looks as if I will need a windows emulator, is that wine?
WINE is by far the best free program there is for running Windows programs on Linux. However your program may not run well on WINE so check the program database for WINE at [http://appdb.winehq.org](http://appdb.winehq.org). However WINE is not an emulator, the name WINE even stands for *"**W**ine **I**s **N**ot an **E**mulator"*. Wine simply converts the programs commands for Windows programs to commands that Linux understands. If you can find a Linux program that'll do the same thing for you that would be much better though.

I'm glad to see that your starting to get stuff figured out. With the help of the guys on this forum there should be no problem that you can't overcome.

---

### Post by KarmicKlot on 2009-11-17
I have reinstalled libdvdread4 and still cannot play any DVD. Can anyone point me to which of the huge number of Gstreamer add ins listed in Synaptic I need to install, or are the things I want elsewhere.
 
On the other issue I have looked at Gnucash, but it would take weeks to copy all my data from Quicken, one account at a time, and even the I just don't like the way it works.  Kmymoney needs me to have Kubuntu, by the look of it, so I guess its wine for me.

---

### Post by mc4man on 2009-11-17
> I have reinstalled libdvdread4 and still cannot play any DVD
In all likelihood the ugly plugin (1st. listed), is the one you want in addition to the ffmpeg plugin

If you  to try just those search in synaptic or go in a terminal
```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg
```

if you wish to get most of the useful ones then 
```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse \
gstreamer0.10-ffmpeg

```

To ck. on or install libdvdcss2 

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by KarmicKlot on 2009-11-18
Thank you very much for those codes.  I ran all three in a terminal, and a DVD still did not play, but then I tried the Windoze trick of re-booting, and it is now working!
HOORAY!

---

