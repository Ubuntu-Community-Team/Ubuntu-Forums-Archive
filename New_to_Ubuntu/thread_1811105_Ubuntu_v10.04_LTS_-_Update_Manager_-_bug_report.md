---
title: "Ubuntu v10.04 LTS - Update Manager - bug report?"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by scruffyeagle on 2011-07-24
I've started 3 different installations of Ubuntu v10.04 LTS, since I got my disk. On a Toshiba Satellite A205 notebook, on a Dell Inspiron 9400 laptop, and as a 2nd OS (w/ XP 1st) on a Dell 4600 tower. I haven't done much w/ the 9400, but pursuing setup on the A205 & the 4600 I ran into the same problem on both. When attempting to use the Update Manager to get software updates, it locks up. On the A205, it locks up when the checking is initiated. I'd already done the initial massive updating, on this one. On the 4600, it locked up when I tried to open the settings adjustment. But, on this one I hadn't done any automated updating at all yet. I'd only installed gufw, Audacious, xmp-audacious, and Firefox add-ons (* No Script, Ad Blocker Plus, Better Privacy, & Down Them All).  In both cases, when I eventually gave up and went to restart the machine using the Restart option from the menu, the process hit a glitch that caused it to throw up a dialog box showing &quot;AT SPI not responding&quot;. On the A205, I cancelled at that point but it was still locked up. Trying it again, same dialog box. I had to choose &quot;Reboot anyway&quot;. On the 4600, I'd alread been through this twice, so I didn't even try cancelling. I just told it to reboot anyway. Given the differences; i.e., locking up of the Update Manager is happening in 2 distinctly different manners, in 2 very different installation settings, and at different points in the setup process. And given the similarity; i.e., the same error of AT SPI not responing, I have to wonder, is this grounds for a bug report?  I also wonder, would this still be happening, if I'd gone w/ Kubuntu instead of Ubuntu?

NOTE: This last paragraph is being added 6 days later, on 07/31/11. When I began this, I wasn't sure. Now, I am. I don't know how to report bugs yet, but there's a big, nasty bug involving the "AT SPI". I've run into this bug on every installation I've done so far, involving 2 different installation/live disks; 1 Dell tower, a Dell laptop, and a Toshiba notebook. My current suspicion is that it's connected w/ me changing the mouse settings to left handed. (Only unusual thing I always do, as far as I can tell...)

---

### Post by fabricator4 on 2011-07-24
> **scruffyeagle said:**
> I've started 3 different installations of Ubuntu v10.04 LTS, since I got my disk. On a Toshiba Satellite A205 notebook, on a Dell Inspiron 9400 laptop, and as a 2nd OS (w/ XP 1st) on a Dell 4600 tower. 

Have you made any changes to any configuration files, or is this a completely unmodified system?

Try updating though command line, it might give you more information:

```
sudo apt-get update && sudo apt-get upgrade
```


> given the similarity; i.e., the same error of AT SPI not responing, I have to wonder, is this grounds for a bug report?  I also wonder, would this still be happening, if I'd gone w/ Kubuntu instead of Ubuntu?

There would be not appreciable difference between any of the LTS releases in this regard, though there maybe something really odd that's causing your problem

Chris

---

### Post by egalvan on 2011-07-24
Have you run a "check media" to VERIFY that the CD is OK?

I use bit-torrent to download (which verifies the blocks),
then I verify the md5 sums,
then I run "media check"
on EVERY CD that I burn.

It may or may not be overkill, but it ensures that the media is NOT the source of any problems.

---

### Post by scruffyeagle on 2011-07-25
_**fabricator4**_: Thank you. Just for S&G's, I'll try that code, and see what happens. But, I've come to the conclusion that my problems could easily be a defective installation CD.

_**egalvan**_: I agree with all you wrote about method & verification. Before coming to the forums tonight, I'd just downloaded a new copy of Ubuntu v10.04 LTS, but I didn't use Bit Torrent. I just did a standard FF download. I'd just installed BT before starting the download, but I didn't discover the link right away for using it. From about halfway through that download, I've been considering re-downloading w/ BT, and I'll probably do that when I'm done here. I haven't found any info yet, on where to get the md5 data, or any instructions on how to apply it once obtained. If you can guide me re. this, thanks in advance!

---

### Post by amjjawad on 2011-07-25
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by scruffyeagle on 2011-07-25
**_fabricator4_**: I was just thinking about this... I don't want to upgrade beyond the Ubuntu v10.04 LTS (v11.04, for example). Wouldn't the second section of this code seek to do that?

---

### Post by sadaruwan12 on 2011-07-25
I'm using LTS 10.04 up to now there have been no issues for me. It has been rock solid what ever I do with the system.

In your case my friend theres something else causing the issue what you're having my best bet is to download a new ISO from different mirror or from torrent. Burn it to a CD or to USB stick re-format every thing on you defective PC install it as a fresh install.

After that don't do anything run a system upgrade and update the system.

---

### Post by scruffyeagle on 2011-07-25
**_amjjawad_**: Thanks for posting those links! I'd discovered them while reading my way through a very long thread elsewhere on the forums, and was coming back here to share what I'd found. But, of course, you've already done it! Cool.

**_sadaruwan12_**: Yes, I've downloaded a fresh copy of Ubuntu v10.04 LTS 32-bit, and verified the md5 checksum. I'm currently downloading a copy of the 64-bit version, because 2 of the machines I want to install Ubuntu v10.04 LTS onto are portables with dual processors. (A "Toshiba Satellite A205" notebook, and a "Dell Inspiron 9400" laptop.)

And yes, it sure would be more convenient if I could use a USB flashdrive as the code source during installations. I have a 1 GB flashdrive at my desk. I could & would gladly wipe all its current contents if I could use it for this purpose instead of going through the hassles of burning & verifying a CD. But, how? Is there a page that would give me detailed instructions on how to do this? TIA!

(In the meantime, while waiting for your reply, I'll start searching.)

**_egalvan_**: Re. using Bit Torrent... I don't think was a good idea. The BT download took at least twice as long (Didn't time it - 3x?) as the regular FF download, and when it was done it started sending data out to the internet. By the time I caught onto what it was doing, its data list showed that it had already sent out 9 MB. I cancelled its operations, then did the md5 verification on what had been downloaded. It matched - so, I have to wonder, exactly what was it sending out to the internet?

---

### Post by mikechant on 2011-07-25
> I have to wonder, exactly what was it sending out to the internet?

It was sending on parts of the file you just downloaded to others, it's called seeding and it's perfectly normal for Bit Torrent - that's how it works! The idea is that with BT you 'give something back' by helping others get the file you just downloaded. It will never upload anything apart from the files you've downloaded with BT so your private files are safe.

Sometimes BT is a lot faster than a simple download, sometimes it's slower, this depends on various factors.

---

### Post by amjjawad on 2011-07-25
> **scruffyeagle said:**
> **_amjjawad_**: Thanks for posting those links! I'd discovered them while reading my way through a very long thread elsewhere on the forums, and was coming back here to share what I'd found. But, of course, you've already done it! Cool.

You welcome :)
It took maybe 10 seconds from me to find these links. Google ROCKS :D

[B]I hope the other posters won't mind if I'll reply that ;)
[/B] 
> And yes, it sure would be more convenient if I could use a USB flashdrive as the code source during installations. But, how? Is there a page that would give me detailed instructions on how to do this? 


[www.ubuntu.com](www.ubuntu.com)
Go to "Get Ubuntu" then on Step #2, please choose USB and then Show me how. That is all :)


> using Bit Torrent... I don't think was a good idea. The BT download took at least twice as long (Didn't time it - 3x?) as the regular FF download, and when it was done it started sending data out to the internet. 


Definitely, when you download a file directly from its source will be faster than downloading the same file from via torrent client.

[http://en.wikipedia.org/wiki/Torrent_file](http://en.wikipedia.org/wiki/Torrent_file)
[http://en.wikipedia.org/wiki/Peer-to-peer](http://en.wikipedia.org/wiki/Peer-to-peer)

However, it's safer to download via torrent clients. Chances your downloaded files are broken will be less.

Usually when you have High Speed Internet, downloading 700MB directly won't be a problem. I had a very slow Internet connection and I had to wait 7-8 hours just to download 700MB. So, I was using Torrent Client much more than now.

Good luck :)

---

### Post by fabricator4 on 2011-07-25
> **scruffyeagle said:**
> **_fabricator4_**: I was just thinking about this... I don't want to upgrade beyond the Ubuntu v10.04 LTS (v11.04, for example). Wouldn't the second section of this code seek to do that?

Hi, 

No it won't upgrade your system from 10.04 LTS.  The 'update' refreshes the file list from the server so that it knows about any new updates to already installed software.  The 'upgrade' simply downloads these updated packages and installs them on your system.  Confusing terminology, I know.

I've found in cases where Update Manager is broken (such as after an interrupted update or when something has gone wrong) the the command line will work.

It doesn't get around the problem of an otherwise broken system however, unless you are lucky enough to get updates of the packages that were broken in the first place. (probably about 50/50 if this is a completely new install).

Chris

---

### Post by scruffyeagle on 2011-07-26
> **mikechant said:**
> It was sending on parts of the file you just downloaded to others, it's called seeding and it's perfectly normal for Bit Torrent - that's how it works! The idea is that with BT you 'give something back' by helping others get the file you just downloaded. It will never upload anything apart from the files you've downloaded with BT so your private files are safe.

Sometimes BT is a lot faster than a simple download, sometimes it's slower, this depends on various factors.

Thanks for explaining this to me. I feel much more secure about BT after reading that.

---

### Post by scruffyeagle on 2011-07-26
> **amjjawad said:**
> You welcome :)
<snipped>
[www.ubuntu.com](www.ubuntu.com)
Go to "Get Ubuntu" then on Step #2, please choose USB and then Show me how. That is all :)
<snipped>
Good luck :)

Yes, I've read that stuff. It requires a 2 GB flashdrive to do, and I've only got a 1 GB on hand. This puzzles me a little. If a Live CD can hold the data in an ISO < 800 MB, then why not a flashdrive? My suspicion is that it's expanding the files onto the flashdrive. As an alternative method, wouldn't it make sense to copy the ISO onto the flashdrive and then write a location translation controller program for accessing the contents of the ISO? I mean, data is data... The trick would be to generate offsets & file lengths on the fly for locations within the ISO file that correspond to locations on the CD. It's a level of programming that's way beyond me - but, given 800 MB used from a 1 GB drive, that would still leave around 200 MB for holding the controller program. And then, once you were able to access the ISO in that manner, the files could be expanded as needed in the same manner a Live CD does it.

---

### Post by scruffyeagle on 2011-07-26
> **fabricator4 said:**
> Hi, 

No it won't upgrade your system from 10.04 LTS.  The 'update' refreshes the file list from the server so that it knows about any new updates to already installed software.  The 'install' simply downloads these updated packages and installs them on your system.  Confusing terminology, I know.

I've found in cases where Update Manager is broken (such as after an interrupted update or when something has gone wrong) the the command line will work.

It doesn't get around the problem of an otherwise broken system however, unless you are lucky enough to get updates of the packages that were broken in the first place. (probably about 50/50 if this is a completely new install).

Chris

I haven't figured out yet, how to get that nifty little box for isolating the code you used in your earlier post...
Explaing my concern: Given
*"sudo apt-get update && sudo apt-get upgrade"*, I thought the "update" portion would seek updates and trigger installment. But, that the "upgrade" portion would affect the version # of my installation by doing the same w/ OS files. My goal at the moment, is to be able to set up 2 stable installations that will remain stable even after updates of existing programs and addition of extra software packages. So, stability is my top priority, followed closely by usefulness. I don't know Linux well enough to entertain any notions re. tweaking the OS, so for my first dive into the Linux ocean I'm attempting to keep tweaking of settings at a minimum, and if possible entirely avoid compiling of files.

---

### Post by amjjawad on 2011-07-26
I think all what you need to know at this point is here: 

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)


> **scruffyeagle said:**
> wouldn't it make sense to copy the ISO onto the flashdrive and then write a location translation controller program for accessing the contents of the ISO?

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Copying the iso to your USB will NOT create a **_bootable_** USB, that's all :)


I haven't tried 1GB USB Drive, I have tired 256MB USB to install and boot [SliTaz]("http://www.slitaz.org/en/") which is an OS with only 30MB :)

---

### Post by fabricator4 on 2011-07-26
> **scruffyeagle said:**
> I haven't figured out yet, how to get that nifty little box for isolating the code you used in your earlier post...

Mark the text that you want in the code box, then click the 'code' button - it's the '#' in the second line of the format buttons at the top of the edit box.

> Explaing my concern: Given
*"sudo apt-get update && sudo apt-get upgrade"*, I thought the "update" portion would seek updates and trigger installment. But, that the "upgrade" portion would affect the version # of my installation by doing the same w/ OS files. 

No, it will only upgrade installed packages within the current release version.  It hasn't upgraded my 10.04 machines to 11.04, or changed anything I didn't want changed. (If it did, I certainly would not be recommending this method).

From a purist Linux point of view, it's actually the "correct" way to update your system, and in fact the only way to do it on server systems with no GUI.  By concatenating the two commands with '&&' you are making the upgrade part dependent on the successful completion of the update - it's called a 'safe update' since it will not try to complete the update if there are unmet dependencies or if there's a problem that will result in only a partial update.

> My goal at the moment, is to be able to set up 2 stable installations that will remain stable even after updates of existing programs and addition of extra software packages. So, stability is my top priority, followed closely by usefulness.

On both these counts I think 10.04 comes out tops.  Personally, I consider it the best Ubuntu release so far, and on principle I recommend the LTS releases to Linux newcomers.  The only exception is on the newest hardware where there may be better support in a later release.  Even then, I've found that these improvements do trickle back to the LTS, it just takes a little more time.

Your problems which appear to be similar across installs on different machines seems to point to a faulty install disk more than anything else. 

Regardless, I think you should try the apt-get update and upgrade fix to run the update before you do anything else to your systems since it may actually update the damaged packages (if you are lucky).  Apart from that, check the MD5sum of the iso you downloaded and check the install CD for any defects.

Chris.

---

### Post by scruffyeagle on 2011-07-27
> **fabricator4 said:**
> Mark the text that you want in the code box, then click the 'code' button - it's the '#' in the second line of the format buttons at the top of the edit box.
<snipped>
Chris.

Thanks, Chris! You provided a LOT of helpful info. For example, now I know how to do this:
```
ls *
```
:lolflag:

---

### Post by scruffyeagle on 2011-07-29
Well, I'm back again. I haven't figured out yet, how to file a "bug report" - but, I'm fairly sure I've pegged the existence of a bug involving "AT SPI". I went through all the work of downloading, md5'ing, burning, & verifying files in Ubuntu v10.04 LTS 32-bit. I reinstalled from scratch (including repartitioning) and did an installation w/ the shiny new OS disk. It worked great, and even updated itself w/o problem. I:
*) tweaked window & font settings,
*) set up FF how I want it,
*) dl'd Gimp, Audacious, Audacity, Gramps, & gufw,
*) Enabled simulated secondary click on the mouse, and
*) Rebooted a few times, in the middle of all this.

The problem happened when I tried to activate the firewall using gufw. The moment I clicked to activate it, the dialog box darkened and none of the controls in it would respond. I chose to reboot the system, and it threw up the dialog box telling me that AT SPI wasn't responding. This isn't me, it isn't this computer (AT SPI has failed on other machines, though not identical manners), and it isn't a faulty OS disk. The failure is the same, although the installation disks were different.

It's a bug!

It's about an hour later now, and I'm editing my post. I have a suspicion about this bug, so I'm here to ask for assistance testing. When I adjusted my mouse settings, I changed from right handed to left handed, increased the double-click time allowance, then activated simulated double click when holding down the mouse button. Activating the simulation function, it told me I was going to need to activate a service that I think also enables other assistive functions. I've forgotten what the name of that service was, but I suspect there's some interaction going on between that service and the "AT SPI" that's freezing up. What I'd like to test, is what would happen if I deactivated that service. Can anybody help me testing this? TIA!

---

### Post by scruffyeagle on 2011-07-31
Back again. Another AT SPI failiure using Ubuntu 10.04 LTS 32-bit. This time, on the Toshiba Satellite A205 notebook. I'd opened the Ubuntu Software Center, and clicked on the menu item "Edit/Software Sources". A box opened in the middle of my screen. It was labelled "Software Sources" across the top. The interior of the box was blank, and stayed that way. I waited a while, but nothing happened. I tried to close it using a couple of different methods. It wouldn't close. I decided to reboot. During shutdown, before completely exiting Gnome, it threw up a message box saying "AT SPI registry not responding". I chose the option of "Reboot Anyway".

After rebooting back into Gnome, I tried to open the Synaptic repository via "System/Administration/Synaptic Package Manager". It opened up, but within 2 seconds the box turned gray and nothing inside it responded. Luckily, this time, the program's box was willing to close. Synaptic was working perfectly yesterday. I used it to download & install the "KDE full" package. Now, it won't work. The only reasonable conclusion, is that the failure of "AT SPI" has disabled Synaptic.

I've been thinking about this, and if this isn't a very common problem, then I'm probably doing something uncommon. There's only 2 things that spring to mind as out of the ordinary in what I'm doing. One, is those times I tried to activate simulation of double click on the mouse. (Note, I quit trying to do that, because it never worked.) In the current installation on the Toshiba Satellite A205 notebook, I haven't done it. The other thing that is probably not common, is that the first thing I do when I set up a desktop in any OS, is I make a dive for the mouse controls to change it to a left-handed mouse. I don't know the nuts & bolts of this OS well enough to say for sure, but isn't it possible that changing the mouse settings is somehow screwing up the AT SPI?

---

### Post by scruffyeagle on 2011-07-31
> **fabricator4 said:**
> <snipped>
Try updating though command line, it might give you more information:

```
sudo apt-get update && sudo apt-get upgrade
```

Chris

Just thought I'd drop word to you, that I did try this code, and yes it did work. No problems at all. Unfortunately, I've discovered that this problem's also affecting other programs after it happens. On the current installation on the Toshiba laptop, it's also disabled the Synaptic repository manager.

---

### Post by scruffyeagle on 2011-08-03
Posting a follow-up here. There really is a big, nasty bug in the "Assistive Technologies" program. Bug reports have been filed in Launchpad. For example: [https://bugs.launchpad.net/ubuntu/+source/at-spi/+bug/477978]("http://s://bugs.launchpad.net/ubuntu/+source/at-spi/+bug/477978"), titled "Bug #477978 in at-spi (Ubuntu): 'AT SPI Registry Wrapper not responding when I try to shut down'”.

After much searching, I found a comment in a post, sharing that the poster had solved this problem by removing AT via the Synaptic Package Manager. Although it was still disabled in Gnome, I was able to use it in KDE. I discovered there were several items related items that hadn't been installed. On the off chance that a lack of one or more of those was stalling it out, I installed them all & rebooted. Open Office became available again, but when I rechecked SPM (after a couple of hours of studying Linux), the SPM window grayed out and stayed that way. Obviously, the bug was still crawling around in my system. I was again able to access SPM by leaving Gnome and entering KDE. I used the complete removal option for all items in the list after using "Assistive Technolog" as a search term. Rebooting, I entered Gnome. I found SPM available again.

There was an error message during Gnome startup, telling me that the "Mouse Tweaks" required the "Assistive Technologies". I clicked to make it proceed without re-installing the AT. I was surprised to discover that the mouse is still set as a left-handed mouse! (Cool. That's the way I want it.) From this, I deduce that the handedness settings of the mouse is NOT dependant on the presence of AT; perhaps, just the ability to change it? I don't know, and I'm not going to worry about testing it. It works now, and I'm content with that.

I won't mark this thread as "Solved", since the problem, the bug infestation, still exists. However, I've discovered a compensatory work-around that could be useful for any others struggling with this problem.

---

