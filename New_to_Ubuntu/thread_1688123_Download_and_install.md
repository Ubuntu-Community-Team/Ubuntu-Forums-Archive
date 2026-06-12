---
title: "Download and install?"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by J-mz on 2011-02-15
Just made my first Linux installation - 10.10. Very glad to be getting away from Vista. However:

I'm confused as to why I can't seem to install Sunbird from the Mozilla website.  I happily clicked the link to download Sunbird for '[Linux x86, English]("http://download.mozilla.org/?product=sunbird-1.0b1&os=linux&lang=en-US")'.  Since then I've started dimly to become aware that it might not be installable on Ubuntu 10.10.

I know it's been removed from the repositories and that it's "the last public Sunbird release by the Calendar Project".  My point is not about that, but about why it doesn't seem to be installable when downloaded.

Short version:
a)  Can I download and install Sunbird from the Mozilla website (or other apps from elsewhere)?

b)  If not, then what is the purpose of the Linux x86 download provided on the Mozilla site?  

Advice appreciated!

Thanks.

---

### Post by wojox on 2011-02-15
Did you unpack the .tar.bz2 file?

Then move it to /opt?

Then create a menu item for it?

Do you need more help?

---

### Post by Paqman on 2011-02-15
IIRC Sunbird is just the Thunderbird email client plus the Lightning calender extension.

Both Thunderbird and Lightning are in the repos. The package for Lightning is xul-ext-lightning. Installing Lightning will automatically install Thunderbird too.

---

### Post by Old *ix Geek on 2011-02-15
> **J-mz said:**
> Just made my first Linux installation - 10.10. Very glad to be getting away from Vista.Glad to have you! :)
> I'm confused as to why I can't seem to install Sunbird from the Mozilla website.  I happily clicked the link to download Sunbird for '[Linux x86, English]("http://download.mozilla.org/?product=sunbird-1.0b1&os=linux&lang=en-US")'.  Since then I've started dimly to become aware that it might not be installable on Ubuntu 10.10.I'm not running 10.10 but that shouldn't matter--it works fine for me. I just followed the link you provided, downloaded the file, unpacked and ran it and it works fine.
> My point is not about that, but about why it doesn't seem to be installable when downloaded.After you downloaded it, what did you do next?
> Short version:
a)  Can I download and install Sunbird from the Mozilla website (or other apps from elsewhere)?Yes.

---

### Post by J-mz on 2011-02-15
Thank-you.

I did unpack the .tar.bz2 file, but I didn't know how to run it.  Does moving it to  /opt constitute running it?  

Cheers.

---

### Post by Paqman on 2011-02-15
> **J-mz said:**
> Thank-you.

I did unpack the .tar.bz2 file, but I didn't know how to run it.  Does moving it to  /opt constitute running it?  

Cheers.

I'd recommend against installing it from a tarball, as you won't get updates, which is not a great idea for an app that connects to the internet. Just open up Ubuntu Software Centre and install Lightning, which will install the rest of the Sunbird suite as well.

---

### Post by J-mz on 2011-02-15
> **Paqman said:**
> I'd recommend against installing it from a tarball, as you won't get updates, which is not a great idea for an app that connects to the internet. Just open up Ubuntu Software Centre and install Lightning, which will install the rest of the Sunbird suite as well.

There won't be any updates for Sunbird.  This was the final version, sadly.  I want to use it as-is.
There's no Sunbird suite; Lightning installs within Thunderbird.  I just don't want a calendar inside my email program - it's too much like Outlook.  (Not everyone wants a camera in their phone, right?  ;))

So, what's a tarball anyway, for future reference?  In Windows I'm used to simply downloading and installing at will...

Cheers and thanks.

---

### Post by oldos2er on 2011-02-15
A tarball is a tar.gz or tar.bz2 archive containing source code or precompiled code or something similar. Think of it as a zip file, basically.

You can download and install programs at will in Ubuntu too, but it's recommended you do so from the repositories.
 
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by J-mz on 2011-02-15
Ok, I've now properly extracted the files.  I tried to shift them to  /opt as suggested above, but couldn't get them to move there. 
Clicking on one of the unpacked files does run the program, and the program does save calendar entries, but I'm sure I haven't properly installed it - the unpacked files are all just sitting in the Downloads folder.

---

### Post by Paqman on 2011-02-15
> **J-mz said:**
> I just don't want a calendar inside my email program - it's too much like Outlook. 

Fair enough. Outlook sucks.

> 
So, what's a tarball anyway, for future reference?  In Windows I'm used to simply downloading and installing at will...


It's just an archive, like .zip for example. On Linux we generally don't have to go to sites and download files to install them. We just open up the package manager (eg: Ubuntu Software Centre, Synaptic or Update Manager) and all the software comes to us. Easy peasy.

On the rare occasions that a package isn't available from the repositories, what you want is either:
[LIST=1]
[*]A .deb file, which works roughly the same as a Windows .exe installer
[*]A repository provided by a third party (eg: Google and Virtualbox both have Linux repos available)
[*]A Personal Package Archive (PPA), which is a sort of mini-repo created by a individual or a project to push software out to Ubuntu users.
[/LIST]

Installing from tarballs is really a last resort. They're pretty unpredictable, and can contain anything from fully ready-t-run apps, to custom install scripts, and even raw source code that you have to compile yourself. You have to figure each one out on its own.

---

### Post by J-mz on 2011-02-15
Thanks Ann.

---

### Post by J-mz on 2011-02-15
Thanks Paqman, and others above too!

---

### Post by Old *ix Geek on 2011-02-15
> **J-mz said:**
> I did unpack the .tar.bz2 file, but I didn't know how to run it.  Does moving it to  /opt constitute running it?No. And I want to expand a little on some of the other comments.

As you now know, a tar.bz2 file is a compressed archive containing other files. After unpacking it, its files can be used. How the files are used depends on WHAT they are. In your case, with Sunbird, they're the actual program files.

Unlike windows, *nix programs may or may not need an installation process, but that info is generally available from wherever you're obtaining programs. In this case, Sunbird doesn't need any installation other than simply moving it to its desired location. So after unpacking its tarball, moving the entire **sunbird** directory to its new location is all that's needed.

As you saw, some people place user-installed programs in /opt. That's fine--if that's where YOU want to put them. This is Linux--in other words, FREEDOM! You can put your programs wherever you like [within reason]. I prefer to put my user-installed programs in /usr/local, so when I installed Sunbird last night I put it in /usr/local/sunbird.
> In Windows I'm used to simply downloading and installing at will...As you can in Linux. :)
> I've now properly extracted the files.  I tried to shift them to  /opt as suggested above, but couldn't get them to move there.That would be a permissions issue--and it's what makes *nix inherently safer than windoze will ever be, so don't think of it as a nuisance or hindrance, think of it as part of what makes Linux secure. If you really want Sunbird to reside in /opt, then you're going to have to move it there using root's power. If you need help with that, post again!

---

### Post by J-mz on 2011-02-16
That's very helpful.
Many thanks.

---

### Post by decopeland on 2011-03-02
As I have little experience (but some luck) with Ubuntu, I would like help in moving (or installing) Sunbird.  I have downloaded file sunbird-1.0b1.tar.bz2  to Downloads folder.  I then extracted (clicked on the file and selected Extract option) it to a folder called Sunbird.  To see if it runs I clicked on Sunbird file (message says it is executable) but when I click on "Run" option, nothing happens.  I don't want to go any further until I am certain that the program is working.  If/when it does I don't know what to do next?

---

### Post by decopeland on 2011-03-17
Although I am not running Ubuntu I am running Linux Mint (which I understand is built on Ubuntu).  As I mentioned I extracted the Sunbird files (just as J-mz) but it won't launch.  I click on the Sunbird launcher and get a message with 4 options-one of which is Run- but nothing happens.  Any idea why?  I really would like to get this version of Linux to run.

---

### Post by oldos2er on 2011-03-17
Run it from a terminal, so you can see if there's any output that will point to the problem.

---

### Post by decopeland on 2011-03-23
command not found

---

### Post by Old *ix Geek on 2011-03-23
> **decopeland said:**
> command not foundWhere are you when you issue the command? In what directory? While you're there, please do this and post its output:
```
pwd
```

and then this:
```
ls -l
```

---

### Post by decopeland on 2011-03-24
I am in home/dael.  I then change directory to sunbird.  Entering pwd yields 
/home/dael/sunbird

Entering ls -1 yields
?,???4
application.ini
calendar-js
chrome
components
defaults
dependentlibs.list
dictionaries
extensions
greprefs
icons
libfreel3.chk
libfreel3.so
libmozjs.so
libnspr4.so
libnss3
libnssckbi.so
libnssdm3.chk
libnssdm3.so
libnssutil3.so
libplc4.so
libdls4.so
libsmime3
libsoftokn3.chk
libsoftokn3.so
libsqlite3.so
libssl3.so
libxpcom_core.so
libxpcom.so
LICENSE
modules
mozilla-xremote-client
?P?D@??
platform.ini
plugins
README.txt
removed-files
res
run-mozilla.sh
sunbird
sunbird.bin
update.locale
updater
undater.ini

There are three different colors for the entries-black, blue, and green.

---

### Post by oldos2er on 2011-03-24
When you're in the sunbird directory, run **./sunbird**

---

### Post by decopeland on 2011-03-24
That yielded 15 lines of what looks like corrupted files
The first 10 lines start with ./sunbird-bin: 10: and "gibberish" followed by not found
The next line starts with ./sunbird-bin: 11: 0: not found
The next line starts with ./sunbird-bin: 12: and nonsense followed by not found.
The next line starts with ./sunbird-bin: 12: w: not found
The next line starts with ./sunbird-bin 13: $: not found
Then ./sunbird-bin 14:  Syntax error: ")" unexpected

Several files in the Sunbird folder now have the same gibberish as their names.  That was not the case before I ran ./sunbird

---

### Post by Old *ix Geek on 2011-03-24
> Entering ls -1 yields
**[color="red"]?,???4  <-- NOT GOOD[/color]**
application.ini
calendar-js
chrome
components
defaults
dependentlibs.list
dictionaries
extensions
greprefs
icons
libfreel3.chk
libfreel3.so
libmozjs.so
libnspr4.so
libnss3
libnssckbi.so
libnssdm3.chk
libnssdm3.so
libnssutil3.so
libplc4.so
libdls4.so
libsmime3
libsoftokn3.chk
libsoftokn3.so
libsqlite3.so
libssl3.so
libxpcom_core.so
libxpcom.so
LICENSE
modules
mozilla-xremote-client
**[color="red"]?P?D@??  <-- NOT GOOD[/color]**
platform.ini
plugins
README.txt
removed-files
res
run-mozilla.sh
sunbird
sunbird.bin
update.locale
updater
undater.ini

There's something wrong with your Sunbird directory.

> That yielded 15 lines of what looks like corrupted files
The first 10 lines start with ./sunbird-bin: 10: and "gibberish" followed by not found
The next line starts with ./sunbird-bin: 11: 0: not found
The next line starts with ./sunbird-bin: 12: and nonsense followed by not found.
The next line starts with ./sunbird-bin: 12: w: not found
The next line starts with ./sunbird-bin 13: $: not found
Then ./sunbird-bin 14:  Syntax error: ")" unexpected

Several files in the Sunbird folder now have the same gibberish as their names.  That was not the case before I ran ./sunbird

Yep, there's just something wrong there. Can you start fresh? Either delete the entire directory and recreate it, or try again in a different location. Like I said way back when, for me it was a simple matter of downloading the tarball, unpacking it in its desired location, and that was that. Sunbird ran fine.

---

### Post by oldos2er on 2011-03-24
If you're running 64-bit Ubuntu, did you download 64-bit Sunbird? I don't really know what else to suggest based on the odd terminal output you posted.

---

### Post by decopeland on 2011-03-25
Not running 64-bit Ubuntu but I believe I did download the 64-bit Sunbird.  I will start over later today and post results.

---

### Post by decopeland on 2011-03-25
I removed the original downloads and downloaded the 32-bit version and extracted the files.  Following the suggestions on this thread I managed to get Sunbird to launch.  Now for a follow-up:  I keep a copy of my calendar on a network drive.  Is there some way to get Network listed under Places as a source for Import or Export or can someone suggest a way of importing the calendar from my network source?
I really appreciate the help on this site.

---

### Post by oldos2er on 2011-03-25
> **decopeland said:**
> I keep a copy of my calendar on a network drive.  Is there some way to get Network listed under Places as a source for Import or Export or can someone suggest a way of importing the calendar from my network source?

Can't help you with that, other than to suggest you start a new thread for this question. You're more likely to get meaningful answers by doing so.

---

### Post by Old *ix Geek on 2011-03-25
> **decopeland said:**
> I removed the original downloads and downloaded the 32-bit version and extracted the files.  Following the suggestions on this thread I managed to get Sunbird to launch.Good to hear the problem's fixed. So it was something wrong with the directory's files.
> I keep a copy of my calendar on a network drive.  Is there some way to get Network listed under Places as a source for Import or Export or can someone suggest a way of importing the calendar from my network source?This being *nix, there are multiple ways to do what you're after. The best, in my opinion, is to mount your network drive(s) so they're always accessible--just as if they're part of your local computer's directory structure. This is in contrast to having them only show up under "Network" (which you can accomplish using Samba).

I agree with another comment that you should start a new thread, or--better yet!--search the forums and/or Google for info on how to do these. To permanently mount your drives you'll need info on **/etc/fstab**.

---

### Post by decopeland on 2011-03-25
Actually it turned out to be pretty simple (at least for my network).  I clicked on the Network tab, then Windows Network (sorry about that but I set up the network from a Windows machine), then Home (the name of my network), then the NAS device, and when I click on the drive, it mounts automatically and remains on my desktop and is one of the options for importing.

---

