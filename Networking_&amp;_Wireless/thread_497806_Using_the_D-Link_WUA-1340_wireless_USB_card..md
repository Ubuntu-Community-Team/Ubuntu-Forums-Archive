---
title: "Using the D-Link WUA-1340 wireless USB card."
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by jeremysan on 2007-07-10
Hello all.  About a week ago I purchased the D-Link WUA-1340 wireless USB card, and for this last week or so I have been trying to get it to work, but to no avail.  I have searched several places for information, and although there are full tutorials (sort of) posted by users, each that I have tried has not worked for me.  I'm going to take one in particular that I think was more clear than others, and show you every step that I follow and everything that I do, and hopefully somebody out there can point out where I go somewhere or do something that messes it up.  

  I have completely reinstalled my Ubuntu (distro: 7.04 Feisty Fawn) and all I have done so far up to this point installed the updates, so with a fresh copy I will try to install my WUA-1340 (for about the seventh time).

  The tutorial / post that I followed was on this link:
**[COLOR="Blue"]"[/COLOR][[COLOR="Blue"]USB WiFi - D-Link WUA-1340 - SOL maybe?[/COLOR]]("http://ubuntuforums.org/showthread.php?t=146278")[COLOR="Blue"]"[/COLOR]**

and followed these instructions:
> **saveryquinn said:**
> Hello!

Having stumbled blindly for three days with USB wifi 'cards' that didn't work with Dapper (a Belkin, a US Robotics too) I almost ran out of excuses to tell store clerks why I was returning a working USB wifi 'card' (didn't want to hear one more clerk tell me "Well of course it doesn't work.  It isn't made for Linux).  Finally bought the D-Link WUA-1340 Wireless G USB 2.0 Adapter.  

Works through ndiswrapper like an ugly black charm (well, when your laptop is an Inspirion 6400 black just doesn't go with it).  

How'd it work?  WARNING: Relative Linux newbie offering advice here.  Use caution.  There may be and probably are a half-dozen simpler ways of doing this.

Pre: Running Ubuntu Dapper (Gnome) on a Dell Inspirion 6400 with the latest version of ndiswrapper and wine from the Ubuntu repositories.

1. Put the D-Link resource CD in the drive.  Plug in the adapter.  

2. Go to the file "Drivers"

3. There sits a file "setup.exe"

4. In the shell type: wine setup.exe or in Nautilus 'right-click' the icon and either "Open with Wine" or "Open With Other Application."  In the case of the latter, when the new 'select your app' window opens, click "Use a Custom Command" and enter "wine" in that command line.

5. The D-Link setup wizard should appear.  Follow all the steps just like you were in good ol Windows.

6. Once the installation is complete DON'T EXPECT your usb device to be working just yet (even though the setup wizard suggests it might be).

7. In Nautilus open your "Home" folder.  Crtl-H to show your hidden files.  Scroll down and open folder ".wine." 

8. Now open the folder "drive_c"

9. Now open the folder "program files"

10. In that file there should be (if Wine and the D-Link wizard were successful) a folder named "Drivers"  You can make sure this is the correct folder by opening it.  Inside should be a number of files including that oh-so-prized Dr71WU.inf file!

11. Copy this whole "Drivers" folder to your home directory or wherever you'd like to have it for ndiswrapper's needs.

12. Once copied, go back to the command line.

13. Run: ndiswrapper -l

14. Run: sudo ndiswrapper -i /home/yourname/yourdirectory/dr71wu.inf
 (note here: on my laptop the inf file, when copied to my home folder, transformed from Dr71WU.inf to dr71wu.inf)

15. Run: ndiswrapper -l   to see if the driver loaded.  If everything worked you should see that both the driver and the hardware are present.

16. Run: sudo modprobe ndiswrapper

That's about it. 

My adapter wasn't running until I rebooted my computer.  That's an old Windows habit.

If you run into trouble during the installation, check resource pages for wine and ndiswrapper running under Ubuntu.

Good luck!

So here I go, starting at **step one**.
I have inserted the disk and put the USB stick into the USB slot.
Let me point out that I have tested this USB stick on my Windows XP and it works 100 percent.
Now, I plugged it in and the orange LED on it turns on and occasionally flashes.
I am also able to see available wireless networks (there are two in this house) under my Network Notification Area, but when I try to connect, it simply attempts for about one minute and then falls back to my wired connection:

[[COLOR="Blue"]**Screenshot**[/COLOR]]("http://ubuntuforums.org/g/index.php?n=828")  (I didn't know how else to integrate screenshots so I uploaded them into the gallery.)

For convenient's sake, I removed the WEP encreption of the router that I will be trying to connect to the most.

For **steps two and three**, I went simply where he said (on my CD) and found the setup.exe file.

For **step four**, he doesn't specify the prerequisite of having Wine, but that is not a problem.  Here i went to **[COLOR="Blue"][WineHQ]("http://www.winehq.org/site/download-deb")[/COLOR]**, where I followed the instructions there exactly as told:

In my terminal I put the following lines:
[I][LIST]
[*]wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
[*]sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list
[*]sudo apt-get update
[*]sudo apt-get install wine
[/LIST][/I]
At this point I could continue with **step four**, and I then went to the setup.exe file, right-clicked, and opened with Wine.

Now, on **step five**, I have at this point my USB stick already plugged in.  Following the installer, I am then told to insert my device.  Confused (because it is already inserted) I simply clicked **next**.

[**[COLOR="Blue"]Screenshot[/COLOR]**]("http://ubuntuforums.org/g/index.php?n=829")

A window then popped up and said that the device was not found, and to insert it now:

[[COLOR="Blue"]**Screenshot**[/COLOR]]("http://ubuntuforums.org/g/index.php?n=830")

So I simply continued, and pressed **Ok**.  At this point the installation wizard closed, so I believe it is completed.  But, a confusing thing at this point was that at the bottom of my screen it still showed there being a window existing:

**[COLOR="Blue"][Screenshot]("http://ubuntuforums.org/g/index.php?n=831")[/COLOR]**

I right-clicked on it and clicked **Close**, but close it would not.  For the remainder of my time here I simply ignored it.

Moving on, I went through **step six**, **step seven**,** step eight**, and **step nine** without any problems.

On **step 10**, however, I again ran into a weird problem.  The Dr71WU.inf file was not in the Drivers folder like it was supposed to be, but it was in the Windows/inf folder.

[[COLOR="Blue"]**Screenshot**[/COLOR]]("http://ubuntuforums.org/g/index.php?n=832")

That being said, atleast I had the file *somewhere*, and I was able to copy it with the other files, in **step eleven**, and put it in a folder named "Drivers" on my Desktop, along with the other files.

Now on through **step 12** and onto **step 13**,  I again didn't at this point have the prerequisite of having NDISwrapper installed and functioning, so I went to get that done.
For this I simply used Synaptic Package Manager.  Here is what I installed:

[[COLOR="Blue"]**Screenshot**[/COLOR]]("http://ubuntuforums.org/g/index.php?n=833")

AFter that, I closed the Package Manager and did what **step 13** tells me to, and put
[I]
ndiswrapper -l[/I]

into my terminal, and basically nothing happened.

[COLOR="Blue"]**[Screenshot]("http://ubuntuforums.org/g/index.php?n=834")**[/COLOR]

But maybe that was supposed to go like that.  I don't know.  That is why I am posting this whole thing in the first place, because I have no idea how to get my WUA-1340 to work.  :(

Onto **step 14**, I did as instructed, and because my Drivers folder was on my desktop, this is what I put into the terminal:

*sudo ndiswrapper -i /home/jeremy/Desktop/Drivers/dr71wu.inf*

asking me for my password, I put it in and this is what the result was:

[I]installing dr71wu ...
couldn't open /home/jeremy/Desktop/Drivers/dr71wu.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.[/I]

This is clearly something I could not ignore and simply move onto the next step; at this point I'm in trouble.  So I think that is as far as I am going to go before I get a response.  I would really appreciate the help and effort, as I have been suffering from this for a long time.
Any help at all is very appreciated; please tell me where I went wrong.

-Jeremy

---

### Post by mkoyle on 2007-07-11
> **jeremysan said:**
> 
Onto **step 14**, I did as instructed, and because my Drivers folder was on my desktop, this is what I put into the terminal:

*sudo ndiswrapper -i /home/jeremy/Desktop/Drivers/dr71wu.inf*

asking me for my password, I put it in and this is what the result was:

[I]installing dr71wu ...
couldn't open /home/jeremy/Desktop/Drivers/dr71wu.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.[/I]

-Jeremy


Jeremy,

If 
 ls /home/jeremy/Desktop/Drivers
shows dr71wu.inf, then you aren't doing anything wrong-- there is something wrong with your script.  If it gives an error, then you have the directory name wrong (remember it's case sensitive).  If it doesn't list dr71wu.inf, then you haven't copied the file.

I would probably suggest installing the newest version of ndiswrapper as described at [http://ubuntuforums.org/showpost.php?p=159661&postcount=1](http://ubuntuforums.org/showpost.php?p=159661&postcount=1) ... You have already gotten the driver -- it is that dr71wu.inf file.  You could just as easily have copied it from your Windows partition, but it doesn't really matter where you got it.

Anyway, for some reason, the Ubuntu ndiswrapper package calls itself 1.9 (but it is really 1.38), and the current version is 1.47.

Just follow the instructions at the ndiswrapper post and I think you're in business.  I might put the driver file in a different directory (something like /home/jeremy/ndiswrapper or /var/ndiswrapper would probably be better-- your desktop is always in front of your nose waiting for you to delete things and cleaning house one day you might get rid of your driver.

--Matthew

--Matthew

If you get stuck, post again and we'll stop by and help.

---

### Post by Count Doofus on 2007-10-21
You'll get that error @ line 174 if the case of the filename  is wrong !


had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
I got - No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE - Mrv8000c.INF - 

GRRRRRRRRR!%@$#$###!$!@@!$@!@#!

---

### Post by nutz on 2008-03-04
So how well does this network adapter work? Has anyone tried it with a 64 bit version of Ubuntu?

I am considering purchasing this adapter but I want some feedback on how well it works before I buy it.

---

### Post by nutz on 2008-03-06
Anyone?

---

