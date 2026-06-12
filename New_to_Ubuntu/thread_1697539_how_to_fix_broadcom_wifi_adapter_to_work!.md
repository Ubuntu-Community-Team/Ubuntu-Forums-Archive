---
title: "how to fix broadcom wifi adapter to work!"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by jettaknight on 2011-02-28
OK, I am a complete novice when it comes to anything linux. I am somewhat familiar with Windows, I can get around and am not afraid of trying things beneath the surface.  But I am also not a programmer by any means.  I would really, really like to try kubuntu or ubuntu on my new asus 1015pem netbook.  I did successfully install kubuntu onto a usb stick and was able to boot the netbook into kubuntu.  I am writing this in firefox within kubuntu on wired connection.  However, I have spent hours trying to find out/figure out how to fix the dang drivers so that the broadcom 4313 wireless will work.  I've stumbled through websites, files, programs within kubuntu, tried everything I can imagine and get nowhere.  When I do stumble on "packages" and they somehow start to install, there are inevitable errors.  I just want to get the wireless to work so I can learn to use kubuntu!  CAN ANYONE give me straight forward steps to install the correct drivers in a non-technical language.  It seems that the instructions I do find always contain words or instructions that the writer assumes everyone understands or is familiar with. I am about ready to throw in the towel.   I sincerely appreciate any help you can offer.:confused::confused::confused:

---

### Post by zenwalker on 2011-02-28
Just search this forum for broadcom wireless. Youll get alot of threads. Just follows those to solve. Its simple!

---

### Post by jettaknight on 2011-03-01
Zenwalker, I appreciate your reply and suggestions.  But unfortunately that only points out my problem.  I have looked through many threads...the stuff that seems simple "just type in the following code in the terminal and do this and such" even when I've tried to copy them, it is not so easy.  I guess I'm from the old-man generation for which this doesn't come as second nature.  I'm looking for a simple solution like go to such and such website, download this file, click on the icon and install the new driver".  I believe that Linux is powerful, simple, open, etc. but it is NOT (in my opinion) straight-forward and intuitive for a rookie.Or, why doesn't it just work out of the box?  I don't mean to complain or knock anyone or anything...just my frustration coming out.  Thanks anyway for your response!

---

### Post by Bucky Ball on 2011-03-01
System>Administration>Additional Drivers. If you have plugged in with a cable and gotten your updates there should be the Broadcom driver there. Most Broadcom cards work virtually 'out of the box' now so suprised you're having so much trouble. :(

You shouldn't need to use the terminal to get this going.

UPDATE: You can also look here:

[http://ubuntuforums.org/archive/index.php/t-1505697.html](http://ubuntuforums.org/archive/index.php/t-1505697.html)

... at the fix from pytheas22 in post #6 dated June 12th, 2010, 06:28 AM.

---

### Post by grahammechanical on 2011-03-01
I do not agree with your opinion about Ubuntu.

 > I believe that Linux is powerful, simple, open, etc. but it is NOT (in my opinion) straight-forward and intuitive for a rookie

You purchase a machine that has an operating system pre-installed, where the maker has made sure that everything works as advertised. Both the manufacturer and the OS producer collaborate to make sure that everything works to the buyer 's satisfaction.

You then compare this experience against an operating system that you install yourself, where the developers have had no cooperation from the makers of hardware. They do not want to give away trade secrets. They see little profit in producing drivers for this OS, so they either do not or they are not willing to invest employee labor on getting things to work out of the box.

You pay a lot of money for the first operating system but you get the second OS free of change. And you complain.

You are frustrated. I know the feeling.

I am fed up with reading these type of complaints. It makes me feel that I should not bother trying to help people solve their problems.

Have you not noticed that some people ask for help on a Ubuntu forum for problems that they are having with Windows. And the good folk on these forums give what help they can.

This is just my little rant. Put it down to my appreciation for the gift of Linux and Ubuntu.

Regards.

---

### Post by jettaknight on 2011-03-01
First, to Grahammechanical.  I accept and agree with some of your statements about the purchased system is designed to work, I pay for it and the software, etc. etc.  I get that!  I also GET that Linux is sort of an every-man's software. I AM TRYING TO EMBRACE IT.  But what I'm trying to say is that the linux community unfortunately doesn't embrace very well those people who know little to nothing about programming, or at the very least the new terminology and language of Linux.  Should I take the time to find out myself?  Believe me I have already spent hours doing that.  IF I could get straight forward and workable instructions (for me) then I'd gladly move on to experiencing this new world.  I know there are an amazing array of linux forums and people willing to help...maybe what I'm saying (selfishly) is can someone dumb-it-down enough for me?  I hope so, if not well it was worth a try.

Case in point, I tried the two suggestions offered a couple entries above to install updated drivers. I found the admin and new drivers section, tried installing (applying?) the driver...Failed.  Then I tried the second option of keying a couple lines into terminal....again failed.  So I'll try it again.  Here's the text of the error from terminal.  I would sincerely and greatly appreciate suggestions!


DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
/usr/sbin/update-initramfs: 15: lzma: not found
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 initramfs-tools
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

It would seem that "initramfs-tools" is the common denominator in both failures I experienced.  Again, thanks in advance for any assistance.  (And I will not bring up the "other" issue again):D

---

### Post by Old *ix Geek on 2011-03-01
> **jettaknight said:**
> I did successfully install kubuntu onto a usb stick and was able to boot the netbook into kubuntu.
...
However, I have spent hours trying to find out/figure out how to fix the dang drivers so that the broadcom 4313 wireless will work.From your main menu, select **System | Hardware Drivers**. You should be prompted for your password. There will be a search for available drivers. When the list comes up, select the **Broadcom STA wireless driver** and then select **Activate**. (Assuming the STA driver shows up, of course! If it doesn't, but a different Broadcom driver does appear, choose it. Definitely go with STA if there's more than one Broadcom choice.) Follow the instructions, which I believe will include rebooting.

Several years ago the Broadcom 43xx series was notorious for taking a bit of tweaking--command line tweaking, which a lot of new Linux users are intimidated by--but has been a simple click or two away in the recent past. Post again if you're still having problems.

---

### Post by jettaknight on 2011-03-01
Thanks "Old *ix Geek".  I have actually tried that multiple times on both ubuntu and kubuntu installs and basically get a failure to load and error messages very similar in wording to what I posted just above.  Still seems to be something not exactly correct.  Also, I have a broadcom 4313 wifi adapter and the package you refer to includes 4312,etc. but doesn't list 4313.  Don't know if that matters or not.

---

### Post by dodle on 2011-03-01
I use a Broadcom 4306 wireless card. To get it working I had to install b43-fwcutter.You need to be connected to the internet to download. Open a terminal and type in the following command:

```
sudo apt-get install b43-fwcutter
```

Hit "Enter" then type in your password and it should install. After it installs it should search for your hardware then an icon will appear in your system tray telling you that there are proprietary drivers available. If the icon doesn't show up you will have to do like Bucky Ball says and go to your menu, then go to System -> Administration -> Additional Drivers (or something like that, I am not used to Kubuntu). Then all you should have to do is tell it to activate the driver.

I hope this works for you.

---

### Post by 3177 on 2011-03-01
I have a broadcom card in my laptop and I feel your pain. so if you haven't fixed your problem yet please follow these instructions:
1: go to synamptic package manager. SYSTEM/ADMINISTRATION/SYNAMPTIC PACKAGE MANAGER.
2: search BROADCOM
3(here is what worked for me) install all but BROADCOM-STA-SOURCE.

I hope this works for you, ive had to do this after every release (9.04, 9.10, etc)
Please tell me how it went.:P

---

### Post by jettaknight on 2011-03-01
Tried suggestions from Dodle. ran the fwcutter command successfully. No icon appeared on screen anywhere.  Kubuntu doesn't have synaptic, but I think KPackageKit is the same thing?? Went there and found 3 things. Both "b43-fwcutter" and "bcmwl-modaliases" only had the option to "remove".  "bcwml-kernel-source" the broadcom 802.11 Linux STA wireless driver source had the option to "install".  I have tried this install multiple times, but tried it again.  At the end I get an error code:  System error: installArchives()failed.

3177 in your comments you mention leaving something out of the install.  I don't see how you get to the option of not installing a portion of the STA package.  The only option I see is to install (or rather apply) the entire package.  The journey continues!:P

---

### Post by 3177 on 2011-03-01
I don't care what you think of my instructions, I can tell by what you said you didn't try, 
the boxes to the left of the names are what you need to click., then click apply. i even removed all the packages and followed my own instructions to make sure it would work, so if it doesnt work, tough luck.

---

### Post by jettaknight on 2011-03-01
3177. Truly wasn't questioning your instructions. Can't find synaptics in kubuntu. Assumed KpackageKit is the comparable utility. I see what you mean in your screenshot.  I just don't see those options on my screen.  Using KpackageKit I searched for broadcom and came up with the three options I mentioned above.  I appreciate your help. Sorry to take up so much space on the forum, s'pose I better give it a rest. A sincere thanks to all for your time.

---

### Post by Old *ix Geek on 2011-03-01
> **jettaknight said:**
> Can't find synaptics in kubuntu. Assumed KpackageKit is the comparable utility.You can use KPackageKit to install Synaptic or do it from a command line with apt-get. (I NEVER use KPackageKit...and actually forgot that Synaptic doesn't just come along with Kubuntu. :o )

---

### Post by 3177 on 2011-03-01
> **jettaknight said:**
> 3177. Truly wasn't questioning your instructions. Can't find synaptics in kubuntu. Assumed KpackageKit is the comparable utility. I see what you mean in your screenshot.  I just don't see those options on my screen.  Using KpackageKit I searched for broadcom and came up with the three options I mentioned above.  I appreciate your help. Sorry to take up so much space on the forum, s'pose I better give it a rest. A sincere thanks to all for your time.

sorry, I i didnt see the prefix.

---

### Post by bill516 on 2011-03-01
I found a "HowTo" over on the Linux Mint forum that might speak to this situation.  It does address the Broadcom card at issue here, I believe.

Mint is a pretty close spin from Ubuntu.  I think that with just a bit of translation it might give jettaknight a good guide.

Go to [http://forums.linuxmint.com/viewtopic.php?f=141&t=57056]("http://forums.linuxmint.com/viewtopic.php?f=141&t=57056")

Worth a shot I think.

---

### Post by jettaknight on 2011-03-02
Thanks all.  Bill516, I checked the link you included and that looks very promising.  I'm not going to have a chance to give it a try for a few days, but will let you know how it all shakes out!  Thanks again.  Jettaknight

---

### Post by jettaknight on 2011-03-05
A final update on the saga of Broadcom wifi on Asus 1015pem netbook.  SUCCESS!

After looking at the suggestion from the Mint forum I did research and ended up installing Mint 10.  For me at least, it is a much simpler and more familiar interface for a linux beginner coming from Windows.  I also found  extremely helpful directions on the "howtogeek.com" website on "install linux mint on your windows computer or netbook".  I followed those instructions to the letter, installed Mint, it identified the need to install the broadcom driver, and it worked! To me it looked like exactly the same update package for the broadcom sta driver that I had tried in both ubuntu and kubuntu, but this time no error messages and the wifi started working beautifully (after picking my router and keying in the wep key).  The Mint installation also setup the dual boot screen automatically so at startup it is easy to choose Mint or Windows 7.

I'm writing this response from Mint on the wifi.  This is really fun to explore the new system and it is so much faster!  For this beginner, Mint is the way to get started in Linux. Thanks again to all who offered help!

---

### Post by Bucky Ball on 2011-03-05
Good news. Please mark thread as solved from 'Thread Tools', top right, to help others. Have fun! ;)

---

