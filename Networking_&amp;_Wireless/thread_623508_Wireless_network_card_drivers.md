---
title: "Wireless network card drivers"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by topher123890 on 2007-11-25
I've read through some other threads but nothing that I've tried from those has worked so far..but I've basically deduced (mostly from looking [here](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys[/url) ) that if I use ndiswrapper that I should be good (mine is the WUSB54G V4).

So a little background to my situation: I just installed Ubuntu on this computer earlier tonight (dual boot system with XP, which I'm using for this post obviously). I was able to view wireless networks, but I couldn't connect to any. From a little bit of searching on here, I found someone that had a nice little step-by-step showing you how to get it working from the command line. So I started doing that, only to realize at the start of that (after running lshw) that there are no drivers, or at least none installed.

I searched around and kept hearing about ndiswrapper. But everything I read I couldn't figure out how to do it on my system, I must be missing something here. I'm running Ubuntu 7.10. I found on one site that there at least used to be a way to run ndiswrapper from system>administrator, but the icon that was present in that screenshot I saw was not on mine (I can't remember where I saw this screenshot though, I tried looking for it again but could not find it).

If anyone could help me out with this, I would greatly appreciate it. XP is getting slower by the day, and I can't take it anymore, this is the computer I use most so there's no reason it shouldn't have Linux on it too.

---

### Post by kevdog on 2007-11-25
You could use ndiswrapper or use the ra drivers (open source project known as serial monkey).  It kind of depends if you have the windows drivers available for the device since with ndiswrapper you are basically installing software that allows your linux OS to use windows drivers.  The serial monkey drivers you actually need to compile.  

As far as complexity, I'd say both are about equal to set up.  Neither is a walk in the park however.

---

### Post by topher123890 on 2007-11-25
The Windows drivers for the adapter are easily available from Linksys' website, I checked their first just to make sure that I wouldn't be extremely lucky and find that this adapter has Linux drivers already from them (wishful thinking, I know..). So it sounds like I should get those drivers and the ndiswrapper files and make it work that way?

It was your guide I used BTW for the command line method. :) Great guide.

Edit: Wow, somehow I missed the fact that you have a guide for ndiswrapper too. I'll read that now and see what all it entails, I might have to put this off until tomorrow so I can get some sleep.

---

### Post by kevdog on 2007-11-25
Thanks for the compliment.

Just a few words on ndiswrapper installation.  If you have a working wired connection on the computer I would install subversion and download the svn version of ndiswrapper and compile and install it this way.  If you dont have a wired connection, I would download the most recent beta release 1.50-rc2.  You still need to compile and install this, however this really isnt a big deal -- the compiled version is much more reliable than the synaptic provided version.

Here is another guide which you can take a look at.  There are a bunch of ndiswrapper guides -- this being one of the longest out there (which isnt necessarily a good thing).  Take a look at it and tell me what you think:
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by topher123890 on 2007-11-26
The router is across the hall, and unfortunately I no longer have an ethernet cable long enough to reach there. While I could take the computer across the hall, I'd rather not have to do that, so I'll just go with the "no wired connection" option for now.

I browsed through your ndiswrapper guide real quick and it doesn't seem like it'll take too long to at least try, so I'll give it shot right now. Just gotta find and bring the laptop up here so I can read the guide and do the steps at the same time :)

Thanks for the help so far, I don't get how you can deal with what I'm sure is an old question by now over and over again without coming off as aggravated (though I'm sure there's some hidden aggravation down there).

I'll give this a shot right now and come back here and let you know how it works for me. Hopefully, I'll be posting that update with Ubuntu :) But if not, I can always try again tomorrow.

---

### Post by kevdog on 2007-11-26
If you dont have a wired connection, then you will need the ubuntu installation cd to install the linux headers and build-essential package.  One thing that I didnt add to the guide (which maybe I should) would be at the end of the process when everything is up and running to manually edit your /etc/apt/sources.list and remove the line(s) that list your cd as a repository.  You do not want want the CD as an official repository for everyday purposes.

Good luck

Yeah and its not really all that hard.  I think Im down now to between 20-30 seconds for the complete svn download, compilation, and installation (of course Ive done this now about 100 times).  And if the svn connection is really slow, it would take me longer :)

---

### Post by topher123890 on 2007-11-26
One last quick question before I start: In your guide, when it talks about the Windows wireless drivers, it talks about .sys and .inf files...but all the drivers I'm finding for mine are just .exe's...Am I supposed to use the exe or should I look around for other drivers?

---

### Post by kevdog on 2007-11-26
The .exe file you have is either a cabinet file or self-extracting zip file.  There are utitlities on linux that can open these file types, however Ive found its probably easiest if you have a windows computer nearby to simply open up the exe file there, copy the windows xp directory -- specifically the .sys and .inf files (possibly the .cat file too) -- located inside this directory -- and then just burn a cd, use a flash usb stick, or something else and bring them over to the ubuntu box.

---

### Post by topher123890 on 2007-11-26
Well, what just happened is not good at all...after restarting the computer in order to switch over to Ubuntu, I got an error while GRUB was loading (error 22 to be specific). I turned the computer off, tried again, and got another error (21 this time), and this is the error that I keep getting everytime I try. I can load up a live CD fine, but I can't boot from my HDD into either Ubuntu or XP anymore :( So for now I'll be more worried about getting my computer back to a usable state.

Edit: OK, figured out that 21 means it's a problem with finding the disk, which made sense when I looked down and saw that the external HDD that it's installed on was turned off...so I got in there, started doing everything, but when I went to compile and install ndiswrapper things started not going right. I copied and pasted what I got on my terminal screen, so that maybe someone can make some sense out of it, because I can't..I copied and pasted it into Open Office, and since I'm now on Windows I can't view the .odt file, so I've uploaded it [_**here**_](http://topher123890.bemaniso.ws/errors.odt) if you want to look at it and try to diagnose the problem. It seems that my problems begin with the "make" command (in between "make distclean" and "sudo make install"), as most of the errors that come after the "sudo make install" command came up after the "make" command as well.

I'm clueless as to why this happens, but I definitely know that something is wrong, because in the next step where I verify the installation, it says something to the effect of "no utils exist for ndiswrapper". Could this possibly just be in issue with the version I'm using (1.50 instead of the 1.48 that is described in your guide)?

It's getting late now and I need to be up a little earlier in the morning than usual, so I'm going to call it a night now. But when I get home tomorrow I'll be going at this until I get it working, because I'm fed up with Windows.

---

### Post by kevdog on 2007-11-26
Looks like you didnt install the linux-header files.

loadndisdriver.c:15:20: error: stdlib.h: No such file or directory 
loadndisdriver.c:16:19: error: stdio.h: No such file or directory 
loadndisdriver.c:17:19: error: errno.h: No such file or directory 
loadndisdriver.c:18:20: error: string.h: No such file or directory 
loadndisdriver.c:19:20: error: libgen.h: No such file or directory 
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory 
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory 
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory 
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory 
loadndisdriver.c:26:20: error: unistd.h: No such file or directory 
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory

---

### Post by topher123890 on 2007-11-26
That's what gets done at the beginning with the CD, right? I'm almost positive I did that, I remember using the little backquotes, and nothing came up after that saying "this didn't work" so I just assumed it worked however it was supposed to..When I get home today I'll start it again from scratch, and I'll copy and paste what comes up after what I do with the CD, maybe there's some problem when I go to install the headers.

---

### Post by kevdog on 2007-11-26
sudo aptitude install linux-headers-`uname -r`

Those are backticks

I think
sudo aptitude install linux-headers-$(uname -r)

will also work

---

### Post by topher123890 on 2007-11-26
Alright, gave it another shot, but it looks like I'm getting the same problems. I gathered a little more information from earlier commands, maybe they have some information in them that'll point to what's going wrong. I didn't realize these forums had an attachment thing before...so this time I just put the stuff in an attachment.

Edit: Note that what I copied and pasted there is not every command I entered, just the ones that I felt would most likely be the source of the problem.

---

### Post by rustybronco on 2007-11-26
> **topher123890 said:**
> I've read through some other threads but nothing that I've tried from those has worked so far...Nothing against Kevdog, his help is among the best out there, but have you looked at this thread? [http://ubuntuforums.org/showthread.php?t=588045&highlight=WUSB54GV4](http://ubuntuforums.org/showthread.php?t=588045&highlight=WUSB54GV4)
maybe you can give it a try, i worked on mine with wep.
or possibly try Kevdogs trouble shooting guide in his signature.

---

### Post by kevdog on 2007-11-26
rustybronco

That guide looks like a good one to me if you want the native linux driver.

---

### Post by topher123890 on 2007-11-26
That looks like a fairly straightforward method, I'll give that a shot when I'm more awake, just woke up from a nice long nap :)

---

### Post by kevdog on 2007-11-26
> **topher123890 said:**
> That looks like a fairly straightforward method, I'll give that a shot when I'm more awake, just woke up from a nice long nap :)

Must be nice!

---

### Post by topher123890 on 2007-11-26
Oh trust me, it was :)

Alright, after looking through that WUSB54G V4 thread, I found out that the linux-headers need to be downloaded, which would explain why I didn't install them when I was trying it before...so since I'm already generally familiar with how ndiswrapper gets set-up, I'm going to download the header package and give it one last shot, it seems like it should work now, but anything can happen I guess.

Edit: Alrightt, I feel really stupid because I can't figure anything out..I'm pretty sure I installed the headers the right way, I looked in /usr/src and I saw stuff in there. So I figured I'd start your's (kevdog's) guide again from the top. When I went to install the build-essential from the CD, I saw something on my terminal that doesn't look right, I can't remember exactly what it says, but I've got it [here](http://topher123890.bemaniso.ws/cdproblem.odt) (apparently you can't add an attachment when you edit a post?). Does this look like something is wrong with the installation of that, or am I just missing something completely here?

---

### Post by rustybronco on 2007-11-27
> E: Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.46_i386.deb: Hash Sum mismatch  There is a defect in that file on your cd rom (or a possible bug). you can go to your sources list and un-check the cd-rom "source" and it should down load the required file from the server

Hash sum... [http://en.wikipedia.org/wiki/Cryptographic_hash_function](http://en.wikipedia.org/wiki/Cryptographic_hash_function)

---

### Post by kevdog on 2007-11-27
Rusty is right on the mark

Use the CD only if you dont have an internet connection.  If you do not have an internet connection -- then you will need the disk -- it looks like your disk is bad -- may need to burn another copy!

---

### Post by topher123890 on 2007-11-27
That's frustrating, I thought about hitting the "check disc" or whatever is on the menu before installing Ubuntu, but I figured "nah, there's a pretty low chance something is wrong with it", and then when it installed fine I didn't even think twice about that at all...but I guess I'll run that check thing, and then if it says something's wrong I'll reburn it. If it says something's not wrong, I'll try reburning the iso and burning that, maybe that would remedy the situation.

And as always, I'll edit the results into this post once I do all of that.

Edit: Sure enough, 3 errors on the disc. I'm about to reburn now, I'll try a slower speed.

---

### Post by rustybronco on 2007-11-27
> **topher123890 said:**
> That's frustrating, I thought about hitting the "check disc" or whatever is on the menu before installing Ubuntu, but I figured "nah, there's a pretty low chance something is wrong with it
Edit: Sure enough, 3 errors on the disc. I'm about to reburn now, I'll try a slower speed.Use to think that way also, now I check 'em all.

---

### Post by topher123890 on 2007-11-27
Mkay, so I reburned an install disc, checked this one and it had no errors. Went through basically all of the ndiswrapper stuff fine, but for some reason when I would run ```
lshw -C network
``` to see if the drivers were listed under the wireless device, nothing would be listed...so I think I'm going to give the other method a shot now, see how it works. It looks fairly short and to the point, so if it doesn't work for whatever reason then it's not like it'll take too much time.

---

### Post by kevdog on 2007-11-27
Your device is a USB wireless dongle correct??? USB device to the best of my knowledge do not show up with lshw -C network.  It should show with lsusb, however the driver used will not be shown.  That is kind of the problem with USB devices --- they work well, however installation of drivers is painful since there are not as many troubleshooting steps along the way.

---

### Post by topher123890 on 2007-11-27
Yeah it's from a dongle.

I don't know if it was the first method or the second, but I'm connected now, posting this from Ubuntu. :) Thanks so much for the help, it's so nice to only have to deal with Windows now when I absolutely have to :)

---

### Post by rustybronco on 2007-11-27
one down, a hundred more to go.... glad you have you around.

---

### Post by kevdog on 2007-11-27
In order to determine which driver is loaded:

lsmod | egrep '(ndis | rt)'

This should show either ndiswrapper or an rt module.  That way you will know what is working!!

---

### Post by topher123890 on 2007-11-27
> **kevdog said:**
> In order to determine which driver is loaded:

lsmod | egrep '(ndis | rt)'

This should show either ndiswrapper or an rt module.  That way you will know what is working!!

Nothing shows after I run that...that doesn't mean neither of them got installed, does it? :P

Edit: Nothing shows up after running that, but I just ran lsmod and looked through it real quick and it looks like it's the rt drivers:

> rt2570                189888  1 

ndiswrapper has a line in there too (which may be why nothing showed up with the original command?) but in the "used by" column it has a 0, so I guess that means it's not being used.

---

### Post by kevdog on 2007-11-28
Why dont you remove ndiswrapper from the /etc/modules file to prevent it loading on boot.  No use having the OS load a kernel module for something you are not going to use.

---

### Post by topher123890 on 2007-11-28
Probably a good idea. Just removed it. For some reason it was listed in there twice..? I guess I probably added it in twice somehow...I'm gonna have to remember to edit files like that with gksu gedit instead of just going into vi..though that doesn't make sense to me that it says I can use ! to override the readonly, but then when I do x! it says it's readonly...oh well, got it all working great now :)

And I got my package manager working (before it wouldn't install things when I told it to, it would just reload the list of packages), so now I really don't have to use Windows unless there's an application I need it for, and even then I'll probably see how it works with WINE before I reboot into Windows.

Though I am having some trouble mounting my Windows partition in Linux, whenever I try it says the drive is busy..I found a command to use and figured out which disk was my Windows partition, and typed it in, but it says the drive is busy and can't be mounted. This isn't the right place to ask about that though, and I'm not really too worried about it for the moment, because most of the files (videos, music, etc.) are on my external drive, which came up right away, I guess since it's USB.

---

