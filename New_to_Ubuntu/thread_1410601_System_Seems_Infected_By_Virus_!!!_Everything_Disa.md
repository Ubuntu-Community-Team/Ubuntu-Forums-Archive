---
title: "System Seems Infected By Virus !!! Everything Disappearing &amp; nothing works !!!"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by faron45 on 2010-02-18
Help !!!!!!!!!!!!!!!!!!!!! I just did an update of Firefox,shut it down,shut down the comp,turned it back on & over 25 files {pics etc} that I had on my desktop just disappeared before my eyes !!!!! 

This is not the first time that I have had files from my desktop disappear but,I didn't know why they disappeared or how to get them back & they weren't all that important.I just kind of forgot about them.But,when I see all the files on my desktop disappear before my eyes something tells me something is wrong.

Everything except {so far} "file sys","home","trash","floppy" & one called "funny pics" has disappeared Help !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! Also,NOTHINS on my system seems to work.......I've tried to load "Pidgin","system monitor" & "synaptic package manager" & NOTHING will load ?????????????????

This all happened after the Firefox update.After I "reloaded" Firefox,Firefox began to complete the update & seemed to have gotten stuck on checking add ons.So,Iclicked "close" & then Firefox just loaded up.So,I suppose I'm lucky I'm able to use it right now BUT-this page looks VERY plain !!

One of the other times I recently lost a file or two like this I was screwing around with the display settings.

---

### Post by faron45 on 2010-02-19
And,now...I had to restart the comp & now the whole OS is like brand new.It looks like a completely fresh install of Xubuntu ! I've lost all my bookmatrks,Pidgin thinks it's never been used & God knows what else  !!!!!
Someone PLEASE HELP !!!!!!!!!

---

### Post by QIII on 2010-02-19
Can you reach any of the files that have disappeared by going to Places | Desktop?

---

### Post by WubiNoob on 2010-02-19
Unfortunatly, I think this might not be a virus, because I have experianced the same thing before, and I was never even connected to the internet. If everything dissapered, besides a handful of folders, that means your programs cannot load because all the data would have been in one of those system folders. If you were using pidgin, like you said, as far as I know, the data might be erased. If you can get the file in your favorites, then you could copy them to your new install. And were you running this as a fresh install being the only OS on your computer, or Multibooting, with like Windows? I've had problems when multibooting with xubuntu and windows.
 
Sorry dude, but I dont know what to say, this might seem obvious, but you might want to try recovery mode, if you have a grub bootloader screen.

---

### Post by undecim on 2010-02-19
I see three possible causes:

1: You've run out of hard drive space. It's usually not pretty when that happens, but your files are still there.

2: You are using the home directory encryption (selected during installation) and something has gone wrong.

3: You are using a seperate home partition on which something has gone wrong.

Check case 1. If you still have space left, post here and I will help you diagnose the problem.

---

### Post by lavinog on 2010-02-19
Can you see them in the command line?

---

### Post by QIII on 2010-02-19
Possibility 4:  Thunar is borked?

---

### Post by undecim on 2010-02-19
Just to clarify: This is not a virus. If someone were to have put a virus on your computer, it would be using your computer to attack websites, or would be stealing your personal information; i.e. you wouldn't notice it.

@QIII:> **faron45 said:**
> I've tried to load "Pidgin","system monitor" & "synaptic package manager" & NOTHING will load

---

### Post by faron45 on 2010-02-19
QIII...As a matter of fact I can !! I found all those files

---

### Post by QIII on 2010-02-19
@undecim

> And,now...I had to restart the comp & now the whole OS is like brand new.It looks like a completely fresh install of Xubuntu ! I've lost all my bookmatrks,Pidgin thinks it's never been used & God knows what else !!!!!
Someone PLEASE HELP !!!!!!!!!One might assume that he is using Xubuntu right now to post, since he has not said otherwise.  He might even be using Firefox, which, as he mentioned, has lost all of his bookmarks.  And Pidgin is apparently getting to a point where he thinks it looks like it has never been used.

It appears that at least something is "loading"...

---

### Post by QIII on 2010-02-19
> **faron45 said:**
> QIII...As a matter of fact I can !! I found all those files

Then I think that Thunar may be your culprit.

I am not familiar enough with Xfce any longer (it's been a long time since I used it), but you may need to reinstall it.  Thunar, that is.

That might be advice someone else is better prepared to give.

Notice that nobody panicked and said "Oh, crap! faron45 got a virus!"  That is incredibly unlikely given the nature of Linux (although you certainly may encounter malicious code).  And it is possible that some PFY in Des Moines, Iowa, is even now launching a Linux killing virus that will catch us all by surprise.

Have a cold one and calm down.  This is probably a relatively easy fix.

---

### Post by faron45 on 2010-02-19
> **WubiNoob said:**
> Unfortunatly, I think this might not be a virus, because I have experianced the same thing before, and I was never even connected to the internet. If everything dissapered, besides a handful of folders, that means your programs cannot load because all the data would have been in one of those system folders. If you were using pidgin, like you said, as far as I know, the data might be erased. If you can get the file in your favorites, then you could copy them to your new install. And were you running this as a fresh install being the only OS on your computer, or Multibooting, with like Windows? I've had problems when multibooting with xubuntu and windows.
 
Sorry dude, but I dont know what to say, this might seem obvious, but you might want to try recovery mode, if you have a grub bootloader screen.
 wubi........I wasn't using pidgin at the time.What do you mean by the "file in my favorites" ? And,yes this is the only OS on my sys. WHY though has my system seemed to do a fresh install without my permission ?

---

### Post by faron45 on 2010-02-19
> **undecim said:**
> I see three possible causes:

1: You've run out of hard drive space. It's usually not pretty when that happens, but your files are still there.

2: You are using the home directory encryption (selected during installation) and something has gone wrong.

3: You are using a seperate home partition on which something has gone wrong.

Check case 1. If you still have space left, post here and I will help you diagnose the problem.

PLENTY of hard drive space avail still.Thanks.

---

### Post by faron45 on 2010-02-19
> **lavinog said:**
> Can you see them in the command line?

Sorry lavinog...pretty unfamiliar with the command line thing.

---

### Post by QIII on 2010-02-19
> **faron45 said:**
> wubi........I wasn't using pidgin at the time.What do you mean by the "file in my favorites" ? And,yes this is the only OS on my sys. WHY though has my system seemed to do a fresh install without my permission ?

I don't think your system did a fresh install on its own.  That would have been painfully obvious -- and would have taken some time.

---

### Post by undecim on 2010-02-19
> **QIII said:**
> I am not familiar enough with Xfce any longer (it's been a long time since I used it), but you may need to reinstall it.  Thunar, that is.

Actually, if it is thunar, reinstallation won't do anything because the only files that change are in the home directory, which isn't touch in install or uninstallation.

There is either a ".thunar" folder or a ".config/thunar" folder that you can rename (to something like "xthunar"), and see if that fixes it.

[s]I still would check the drive-space thing if I were you though. I've run out of drive space before and had VERY similar problems.[/s] nvm

---

### Post by faron45 on 2010-02-19
> **QIII said:**
> @undecim

One might assume that he is using Xubuntu right now to post, since he has not said otherwise.  He might even be using Firefox, which, as he mentioned, has lost all of his bookmarks.  And Pidgin is apparently getting to a point where he thinks it looks like it has never been used.

It appears that at least something is "loading"...

Yes QIII I am using Xubuntu & Firefox.An,dyes Pidgin is freshly installed to.

---

### Post by QIII on 2010-02-19
> **undecim said:**
> Actually, if it is thunar, reinstallation won't do anything because the only files that change are in the home directory, which isn't touch in install or uninstallation.

Ah.  Thunar is the file manager that finds the files in the /home partition and everywhere else.  It is installed/uninstalled/reinstalled as is any other application.  I didn't say that it is itself associated with the /home partition in any other way than some profile settings.  Most likely the hidden file in /home will be empty.  If the installed application package is corrupt, however, thunar will not work.

The same symptoms he has described occur in Gnome when Nautilus fails.

Which, of course, was why I asked him if he could use Places | Desktop to see the files.  It is diagnostic.

---

### Post by faron45 on 2010-02-19
undecim...{evreybody} sorry it's taken me so long but,I've been trying to reply to everybody.Can you tell me how to rename that folder ?? And,will that put everything back the way it was ?? If not...IS there a way that I coould maybe do this thing called a recovery mode ? Specifically back to a certain date ??

---

### Post by QIII on 2010-02-19
> **faron45 said:**
> An,dyes Pidgin is freshly installed to.

What I am saying is that it likely is not "freshly installed" unless you deliberately reinstalled it.  It may simply not be able to find its profile files, so it appears as though you have lost everything.

---

### Post by faron45 on 2010-02-19
Now THAT sounds likely ! But,HOW do I fix that ? Heh heh

---

### Post by QIII on 2010-02-19
First.

While I do not think undecim is on the right track, I do not dispute that he may be.  After 35 years in the gee whiz world of computers, I have found that this old dog can be peed on by a pup.

Using Places again, go to Places | Home (may be Home Folder).  When you get there, click Control + H.  That will unhide the hidden files.  Look for a folder like .thunar(blah blah).

I suspect it will be empty, because I doubt you have done any fancy stuff in configuring thunar.

If that is the case, then sit tight until someone can tell you for sure how to reinstall thunar to see if that rectifies the problem.

I suspect that is as simple as the following (BUT DON'T DO IT UNTIL SOMEONE CONFIRMS!!!)

```
sudo apt-get install --reinstall thunar
```

---

### Post by faron45 on 2010-02-19
QIII I DO find all those files in places/desktop.Now IS there a way to put my system back the way it was ??? PLEASE !!! Thank you

---

### Post by QIII on 2010-02-19
Yes.  I do believe there is a way.  I believe you will need to reinstall thunar.

But like I have said, my recollection of Xfce is rusty, and I would ask you to wait until some kind soul with fresher experience can step in tell you "QIII is right" or "QIII needs to take his geritol and go to bed."

---

### Post by faron45 on 2010-02-19
> **QIII said:**
> Yes.  I do believe there is a way.  I believe you will need to reinstall thunar.

But like I have said, my recollection of Xfce is rusty, and I would ask you to wait until some kind soul with fresher experience can step in tell you "QIII is right" or "QIII needs to take his geritol and go to bed."

Okay QIII Thanks very much...I'm tired.Going to bed for now.Hopefully I have internet tomaorrow too.Supposed to be shut off today !! Heh,heh.Oops !

---

### Post by undecim on 2010-02-19
There is certainly no harm in reinstalling Thunar, but there is no reason for it to be corrupt. That file should never be so much as opened in write mode.

The fact we still have file sys, home and floppy icons indicates that Thunar is indeed running. The chance that a corrupt system file would cause this kind of behaviour without causing a segfault is next to nothing.

If it is a system-wide problem, it is likely due to an error in packaging (since this problem appeared after an upgrade), but could also be the result of old Thunar settings being used with an upgraded version.

I have a simple test to determine if this is a system-wide problem:

Create a new user, and log in as that user. Create a new file on the desktop, then log out, and log back in.

If the file still shows up on the desktop, this is a user-wide problem in the /home/ directory.

If the file does not show on the desktop after logging out and back, then this is a system-wide issue.

---

### Post by airtonix on 2010-02-19
> **faron45 said:**
> [SIZE="5"][COLOR="Red"]wubi[/COLOR][/SIZE]
I think this is your intial problem... the sanity of everything in a wubi install relies on the health and stability of the ntfs partition it is installed on.

> **faron45 said:**
> 
.....And,yes this is the only OS on my sys.

You just said you installed ubuntu via wubi, which means it's not the only operating system on your computer.

> **faron45 said:**
> 
WHY though has my system seemed to do a fresh install without my permission ?

see above : re > wubi = fail

---

### Post by undecim on 2010-02-19
@airtonix: I think he was referring to wubi as in the forum user WubiNoob, who had replied earlier in the thread, and not to the windows ubuntu installer.

---

### Post by lavinog on 2010-02-19
> **undecim said:**
> @airtonix: I think he was referring to wubi as in the forum user WubiNoob, who had replied earlier in the thread, and not to the windows ubuntu installer.

Almost thought airtonix solved the issue there.

To anyone that has used xubuntu lately:  Wasn't there an option in thunar to show/hide desktop icons?

---

