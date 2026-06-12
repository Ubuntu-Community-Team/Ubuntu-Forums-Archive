---
title: "how do i connect using a broadcam 4318"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by austin7 on 2009-05-10
how do i connect wirelessly using broadcam 4318 wirless card i had some troubles doing it on 8.04 and i tried what i did on 8.04 on my 9.04 but when i go to hardware drivers i cant find it what can i do to connect wirelessly in 9.04

---

### Post by anewguy on 2009-05-10
There are many posts here for getting Broadcom chipset adapters working, and it sounds like you have looked at least at some of those.  If you can't get the restricted driver to work (I seem to remember having read something in one of the posts about making sure the source is in the sources list and then doing sudo apt-get update, but I don't know if that would work for you or not).

If you need help, and someone doesn't provide the help to use the built-in restricted driver, post back and I can give you instructions to follow so you can use ndiswrapper instead to get your driver installed and working.

Dave :)

---

### Post by austin7 on 2009-05-10
well im ready for ur instructions wheneva u wana give em to me..plz be simple i havent been using ubuntu for long

---

### Post by austin7 on 2009-05-10
......well im rdy

---

### Post by austin7 on 2009-05-10
well...errr umm anyone??

---

### Post by lkraemer on 2009-05-10
austin7,
First of all you need to have a look at the modules that have been loaded.
Then you need to have a look at what has been blacklisted,  With that
information you should be able to use one of the following three ways to get it working.

If you Open a Terminal Window, cut & paste each line - one at a time:

```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwconfig 
cd /
cd /lib/firmware
ls -alt
cd /b43
ls -alt

```
Then post the output, separated so it is easy to read, as this will give
us a clue as to what is loaded and blacklisted.  Do this before you proceed!

You either need to use:
1. Ndiswrapper and a Windows Driver....bcmwl5.inf & sys
2. bcm43xx module and some Firmware.... B43 & B43legacy *.fw
3. b43 and some Firmware that was downloaded/extracted when you
enabled the Hardware Driver.

So, if I were in your position, and had a fresh install of 9.04 I would
try to enable the Hardware Drivers first by going to the following:
SYSTEN -> ADMINISTRATION -> HARDWARE DRIVERS and enable them if they
aren't enabled.  Then re-boot.  B43 will show in lsmod and there
should be lots of *.fw files that get extracted to /lin/firmware/b43 
& b43legacy.  But this might not work, as it didn't for my Compaq.

The next steps will be determined by what you post from the previous
request, and your choice of using bcm43xx or ndiswrapper and the windows
drivers.

If you search the forum for "HOWTO: & 4318" you should find some good
guides.  I don't have those bookmarked on my laptop I am using now.

[http://ubuntuforums.org/showthread.php?t=870086&highlight=HOWTO%3A+4318](http://ubuntuforums.org/showthread.php?t=870086&highlight=HOWTO%3A+4318)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

[http://ubuntuforums.org/showthread.php?t=197102&highlight=HOWTO%3A+4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=HOWTO%3A+4318)

[http://ubuntuforums.org/showthread.php?t=779754&highlight=HOWTO%3A+4318](http://ubuntuforums.org/showthread.php?t=779754&highlight=HOWTO%3A+4318)



lkraemer

---

### Post by anewguy on 2009-05-10
Sorry, but I made the reply and went on for supper and some left over Mother's Day responsibilities.  If you have the Windows drivers (as mentioned above, they should be something like bcmwl5.sys and inf - it may be bcmwl5a) then follow these:

Be sure ndiswrapper and it's utilities are installed - check this in synaptic package manager (system/adminstration/synaptic package manager).  If they are not marked as installed, you will need to install them.  Since you have been posting to the net I will assume you have a hard wired connection currently.  Also be sure the network-manager package has been installed in the same way.

open a terminal window via applications/accessories/terminal - log on using your normal userid and password.


I assume now that you have copied the .sys and .inf files for your Windows driver to the desktop.  Please note that unless things have changed, these need to be the 32-bit drivers for Windows XP.

cd Desktop <press enter>

sudo ndiswrapper -i xxxxxxx <press enter> where: xxxxxxx is the name of your .inf file.  It's a lower case "I" there for "install"

sudo ndiswrapper -l <press enter> That's a lower case "L" for "list".  This should show your device and driver as installed.  If not, stop here and post back.

sudo depmod -a <press enter> Builds up the dependencies list for the module.

sudo modprobe ndiswrapper <press enter>  This will load the ndiswrapper module.

sudo ndiswrapper -m <press enter> This makes sure the ndiswrapper module is loaded at boot.  In a previous release this didn't always work, so also do the following:

cd /etc <press enter>

sudo gedit modules <press enter>  This will call up an editor and open the modules file in it.  Scroll to the end of the file, go to the end of the last line and press enter a couple of times so we know we are adding a new line to the end of the file.  Type the following:

ndiswrapper <press enter>

Now save the file and exit the editor.


We now need to blacklist the built-in driver information.  I know this changed some so I hope I am including all the modules - if not I'm sure someone will correct me.

cd /etc/modprobe.d <press enter>

sudo gedit blacklist.conf <press enter>  This will call up the editor again this time with the blacklist.conf file.  Scroll to the end of this file, go to the end of the last line, press enter a couple of times, then add these lines:

blacklist b43 <press enter>
blacklist ssb <press enter>

save the file and exit the editor.  This step stops the b43 and ssb modules from being loaded - they are part of the built-in driver for the bcm 43xx.  In addition, that file has already blacklisted the old bcm43xx file so we no longer need to do it.

It's possible this file should be called just "blacklist", as that is what it used to be.  However, looking the modprobe.d folder in my 9.04 installation that file doesn't exist and the blacklist.conf appears to have replaced it.


Now just reboot.  If things went right, you'll have the network manager icon on the top line and by clicking it you should see available wireless networks.

Dave :)

---

### Post by austin7 on 2009-05-11
yea man its ok thanks alot im on my school computer right now ill do it when i get home thanks

---

### Post by austin7 on 2009-05-11
thanks alot i got my internet to work i rely appreciate everything

---

### Post by lkraemer on 2009-05-11
austin7,
Since Dave and I were kind enough to post detailed instructions for you
to follow, will you at least describe what you did to get your Wifi working
so others that read this post will have some clue as to one option that
worked?

Thanks.

lkraemer

---

### Post by austin7 on 2009-05-11
If you Open a Terminal Window, cut & paste each line - one at a time:

 	Code:
 	lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwconfig 
cd /
cd /lib/firmware
ls -alt
cd /b43
ls -alt

---

### Post by lkraemer on 2009-05-14
ATTENTION ALL MODERATORS,
I wish to lodge a FORMAL COMPLAINT against austin7 for his post!  

The first two words of the previous post say it all.  These two words
not only DO NOT COMPLY with the Forum Posting rules, but the total
reply was inconsiderate, and non informative to any other person
trying to gain knowledge, or answers by reading posts on the Ubuntu Forum.

If I were a Moderator, this young man, wouldn't have access in the future,
and his IP address would also be banned from access to the Forum forever.

What is your Opinion?  Are you willing to let this continue?

lkraemer

---

### Post by anewguy on 2009-05-14
I hope you also reported the post with the report link on the left, the little icon right after the icon the says if the user is online or not.

This, in variations (like WTF) have been popping up more and more on the forum.  They have only one meaning, and as such the users should at a minimum get a warning or a suspension (I used the "h" word in a reply to a very abstinent user and got a warning quite a while ago).

Dave :)

---

### Post by sugarsim on 2009-05-15
I think austin copy and pasted the reply but missed the "i" from the word "if".  I'm sure he didn't mean any offence.

---

### Post by Rocket2DMn on 2009-05-15
I'm quite sure that was just a copy/paste accident.  I've edited the post.  Thank you.

---

### Post by lkraemer on 2009-05-15
Dave,
THANKS, I did make a Report.......

sugarism,
You're too kind!  If one assumes he actually was making a proper response, and was in fact cutting and pasting, and accidentally missed the leading character, why would he be cutting and pasting Terminal commands that would only show specific items installed or present on his machine.  This in no way answered the easy question that was asked of him so others pouring over the post could learn of what solved his problem?  In fact Dave and I, assisted him without being snotty and rude, and obviously one of us gave him the tidbit that solved his problem.  But, he being rude, arrogant, and inconsiderate, didn't want to share the answer that was provided, or the different way that he found to solve the problem, leaving all other forum readers wondering what the answer is..........  And...... you better have another look at his hands on his Avatar!

lkraemer

---

### Post by sugarsim on 2009-05-15
OK, I agree that he could have described the steps he took to solve the problem.  I've had more than enough entertainment getting this card to work on my system and I know it's a real pain.

However, this is what I used to configure the card on both Intrepid and Jaunty and it works nicely:

[http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/](http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/)

---

### Post by ccmcphe on 2009-05-19
My Broadcom 4318 is a Compact Flash card, and if yours is the same, then you will need rebuild the b43 driver with CONFIG_B43_PCMCIA set. The UBUNTU distributions never have this set for the b43 drivers. Once I rebuilt my drivers with CONFIG_B43_PCMCIA set, my 4318 started working.

---

### Post by austin7 on 2009-08-20
I'm rly sry It was a copy and paste problem I ment no offense at all and I did repost what fixed the problem in the post that everyone wanted to report me for

---

