---
title: "firefox problem with 11.04 ubuntu os on usb stick"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by user987 on 2011-05-02
i have the latest ubuntu 11.04 os on a flash drive and use it to boot up my dell netbook.

it work fine the other day and i was surfing the web and book marking sites to the firefox browser.

today i boot up and evrything looks fine including seeing the wireless connection , but when i click on the firefox tab to launch , nothing happens.

i never get the browser, what happen between being perfect yesterday and today.

is something coruppted during shut down of the computer?:confused:

---

### Post by lovinglinux on 2011-05-02
First delete the *compatibility.ini* file from your Firefox profile and check if it starts.

Then try starting Firefox in safe-mode.

```
firefox -safe-mode.
```

If it starts, then is an add-on causing the problem. Otherwise, create a new profile.

See [http://www.webgapps.org/firefox/general-troubleshooting](http://www.webgapps.org/firefox/general-troubleshooting)

---

### Post by user987 on 2011-05-02
i had reformat the usb stick and reinstall the os and 
 firefox work, but when i logon again i can't launch firefox again.

so i think you are right the profile is some how screw up when i logoff and i need to delete the current profile and creat a new one.

how do i 1) get into the firefox profile and delete the current one.
             2) create a new profile.

is it easy to do?  i am a newbie in linux and am use to the window point and click method rather then typing command codes.

that is why i think this unity version of linux seem great except for bugs right now.

thanks in advance.

---

### Post by lovinglinux on 2011-05-02
> **user987 said:**
> i had reformat the usb stick and reinstall the os and 
 firefox work, but when i logon again i can't launch firefox again.

so i think you are right the profile is some how screw up when i logoff and i need to delete the current profile and creat a new one.

how do i 1) get into the firefox profile and delete the current one.
             2) create a new profile.

is it easy to do?  i am a newbie in linux and am use to the window point and click method rather then typing command codes.

that is why i think this unity version of linux seem great except for bugs right now.

thanks in advance.

See [http://www.webgapps.org/firefox/profiles-and-backups](http://www.webgapps.org/firefox/profiles-and-backups)

If you want to try to fix your profile and preserve some settings, then see [http://www.webgapps.org/firefox/fixing-corrupted-profiles](http://www.webgapps.org/firefox/fixing-corrupted-profiles)

Please ignore item 2.1. It is outdated and is unnecessarily  complicated. I am rewriting that tutorial, but won't be available soon.

---

### Post by user987 on 2011-05-02
hey, thanks for the hints.

i can now get into firefox via the terminal , by typing firefox -p and then select the default profile. 

but i wonder what is causing me to not get in via the firefox icon , because i see my flash  drive blinking after i click on the icon but nothing happens.

also i don't have any book mark or add on's in firefox other then what came with the OS.

i also did a reinstall of firefox via the terminal and click on the icon and it still won't lanuch

so it seems the work around is to always launch from the termial via the firefox -p and select the default profile or create a new profile.

also can you tell me what this means

(firefox-bin:4617): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut:assertion 'gtk_accelerator_valid(key, modifer)" failed

it shows up in my terminal command line after i type firefox -p

but i can get into firefox browser , so what gives?

again thanks for your help!:)

---

### Post by lovinglinux on 2011-05-02
> **user987 said:**
> hey, thanks for the hints.

i can now get into firefox via the terminal , by typing firefox -p and then select the default profile. 

but i wonder what is causing me to not get in via the firefox icon , because i see my flash  drive blinking after i click on the icon but nothing happens.

also i don't have any book mark or add on's in firefox other then what came with the OS.

i also did a reinstall of firefox via the terminal and click on the icon and it still won't lanuch

so it seems the work around is to always launch from the termial via the firefox -p and select the default profile or create a new profile.

also can you tell me what this means

(firefox-bin:4617): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut:assertion 'gtk_accelerator_valid(key, modifer)" failed

it shows up in my terminal command line after i type firefox -p

but i can get into firefox browser , so what gives?

again thanks for your help!:)

I suspect the error is related to global menu, which doesn't work with Firefox 3.6.

---

### Post by davec80 on 2011-05-02
Hey, I have the exact same problem as User987.  I've freshly formatted a USB PNY flash drive three times, using YUMI to install Ubuntu 11.04 and some other random distro (like DSL).  The version of YUMI I use does not officially support 11.04, but all i had to do was change the ISO name to 10.10...
Works great!

EDIT:  Forgot to mention, my ubuntu 11.04 installs I have tested are all persistent with a ~1.7GB casper-rw file.  Changes save fine, but firefox is broken as soon as I shut the system down.

Now on firefox...
First time I noticed firefox not launching, I had no plugins installed.  Googled for a while until I found someone mentioning a profile problem.  Created a new profile.  That kind of worked.  It allowed me to start firefox from terminal without the -p switch.  But the shortcut on the bar on the left would still do nothing.  OH, and I got the same error message someone else mentioned...
"dbusmenu_menuitem_property_set_shortcut:assertion 'gtk_accelerator_valid(key, modifer)" failed"

I've been able to re-create this problem multiple times on multiple fresh format installs.  If it matters, the hardware is lenovo S10-3 netpad.

As far as I'm concerned, this is a bug with ubuntu 11.04, not firefox.  Yeah, I can mess around with firefox until firefox works.  But, firefox works fine (no messing around) on ubuntu 10.10.  In fact, I'm using ubuntu 10.10 and firefox to report this problem with ubuntu 11.04.

I have noticed that Chromium and Seamonkey (related to firefox) both work perfect in ubuntu 11.04.  So that would seem to SUGGEST that the problem is with firefox.  But I'm still leaning toward the problem being with ubuntu 11.04.  If firefox can run perfectly on 10.10, there's no reason that it should be defective suddenly, just because the operating system was upgraded.  That does not pass the smell test.

I wish someone would find a fix for this bug in ubuntu 11.04.  It is annoying to have the default browser work wonderfully until the first time you shut down your computer.

---

### Post by lovinglinux on 2011-05-02
Try my [Profile Cleaner]("https://addons.mozilla.org/en-US/firefox/addon/213326/") extension.

---

### Post by user987 on 2011-05-05
well, i guess it was too good to last, the work around of typing firefox in terminal got me on the internet.

now after a few days, it give me a  screen saying cannot access the the site i want and to try again.

any ideas on why i can't launch firefox from terminal now?

i still see my wifi connection, so i know i have a connection, but firefox don't work.

---

### Post by user987 on 2011-05-05
one more thing is there a portable firefox that runs on 11.04 os, if so how do i make it work?

i use portable ff in window and it is great, don't have to use the one installed on the the host computer.

---

### Post by user987 on 2011-05-05
i have installed ubuntu 11.04 os on a usb stick and boot from it.

the first time i boot up i have to install wifi driver and reboot, once done i get into firefox and the internet.

the next day when i boot up via usb , i cannot lanuch firefox,

but thanks to forum help i went to terminal and type firefox and launch that way.

but now after a few days of doing this that don't work either and to add insult to injury,

when i boot back up via usb i can;t get in, but just hang there with the ubuntu logo and the 4 dots flashing.

any ideas on what happen?

i am downloading a new 11.04 iso and reinstall it on my flash drive but don't give any memory to the persistence file, so hopefully everytime i boot up it is a clean boot with nothing remember to screw up thye os,  does this make sense??

---

### Post by dwhite on 2011-05-05
> **user987 said:**
> 

i am downloading a new 11.04 iso and reinstall it on my flash drive but don't give any memory to the persistence file, so hopefully everytime i boot up it is a clean boot with nothing remember to screw up thye os,  does this make sense??

i would give some memory to the persistence file

 when i made my bootable usb with 11.04 i did, it allowed me to save preferences/bookmarks/drivers etc. so don't need to set up everytime...but maybe that's not what you are looking to do?

---

### Post by Grayman on 2011-05-05
If you haven't set up a persistent memory allocation, or if you can't set up one because you only have a 1GB flashdrive, then any changes you make to the image, including setting up drivers, changing backgrounds, etc will have to be redone each time you boot. 
I'm not exactly sure how to set it up after you created the bootable drive though, perhaps someone else has the answer to that?

Gray

---

### Post by CVGH on 2011-05-05
Boot the CD.
Run the USB installer.
Tell it to do a 128mb persistence file.
After finished, open in Nautilus and delete the 128mb
persistence file casper-rw.
Open Gparted and look at sdb [usually]. Unmount it.
Shrink the partition down to just hold the "cdrom" files.
Make another partition in the unallocated space, format as ext2 and label it casper-rw. 
I did this on a 16GB stick and had a 14GB+ install.
But gave up on it as it was slow and hung a bunch....

The thing about running from a USB is noatime needs to bet set in fstab, but never could figure that one out :)

AFAIK, you cannot change the size of casper-rw?

---

### Post by beew on 2011-05-05
OP said he installed Ubuntu into a usb, this can be a real install instead of a live usb.

Then he wrote 

> the first time i boot up i have to install wifi driver and reboot, once done i get into firefox and the internet.


I take it to mean the wifi driver survived the first reboot so it means the usb is either a full install or, if it is a live usb it already has persistence.

Op pleases clarify how did you install Ubuntu into the usb.

---

### Post by beew on 2011-05-05
> **user987 said:**
> 
i am downloading a new 11.04 iso and reinstall it on my flash drive but don't give any memory to the persistence file, so hopefully everytime i boot up it is a clean boot with nothing remember to screw up thye os,  does this make sense??


That wouldn't make any sense if you need to install wifi driver as it wouldn't survive a reboot without persistence.

---

### Post by user987 on 2011-05-05
i created the usb  os via the universal usb installer and pick ubuntu 11.04 iso which i had downloaded earlier, i also pick 1g of memory for the persistence file size.

so now when reformat my drive and use usb installer to create a new os on my usb 1 was going to leave the persistence at 0g.

so when i boot up each time nothing will be save but at least i have a clean start, because it seems after a couple of boots the os on the usb get screw up.

any ideas on what could being doing it?

---

### Post by beew on 2011-05-05
> **user987 said:**
> i created the usb  os via the universal usb installer and pick ubuntu 11.04 iso which i had downloaded earlier, i also pick 1g of memory for the persistence file size.

so now when reformat my drive and use usb installer to create a new os on my usb 1 was going to leave the persistence at 0g.

so when i boot up each time nothing will be save but at least i have a clean start, because it seems after a couple of boots the os on the usb get screw up.

any ideas on what could being doing it?

Try a different ISO, maybe your last one was corrupt.

---

### Post by user987 on 2011-05-06
i have a new iso just downloaded and reinstall on usb and it seems to be running fine.

somewhere it must have been corrupted, wonder what did it?

but anyway, thanks to all who help.

---

### Post by C.S.Cameron on 2011-05-06
> **CVGH said:**
> 
AFAIK, you cannot change the size of casper-rw?

You can mount a casper-rw file and copy the data to a larger casper-rw file.

---

### Post by I2k4 on 2011-05-06
I'm a trial user of Ubuntu, testing out different versions on Live USB.

I was perfectly successful in running 11.04 from a 2GB "Live USB" drive assigning 1GB for the OS and 1GB for Persistence.  I didn't like it because it is slower than Lubuntu 10.10, but it did work perfectly.  I use the excellent instructions here whenever I install a new version to try it out:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

but I always add the Persistence step to the installation at Step 2 of "Show Me How".  I've learned that Ubuntu versions usually need 1GB or at most 2GB to run well, and the rest of the USB drive should be allocated to Persistence.

After trying it out, I think the new 11.04 should be installed on a USB drive that is at least 4GB:  the operating system needs 2GB because it is bigger than 10.10, and the size of Persistence really depends on how much additional software you want to install.  I don't personally like the new Unity interface so much and don't want the LibreOffice and other preinstalled software for my purposes, so went back to Lubuntu 10.10, but these are personal judgments.

Hope this helps.

---

### Post by user987 on 2011-05-13
Hi,
     i am running 11.04 os on a 4 g stick and i had no problem after the initial setup to run wireless wifi etc.  

i installed sea monkee browser 

the next time i log back on  i lanuch sea monkee  and suft the web and i get the following message:
               program gvfsd-metedata close unexpectedly

you have some obsolute package version installed, please update:

libplymouth 2 , perl-base,plymouth,tzdata

i proceed to update and then surf again, the gvfsd-metedata pop up again.

i then went to terminal and type rm -rf ~/.local/share/gvfs-metadata

logoff and log back on.


now i can't lanuch firefox or sea monkee browser or the ubuntu software center

what happen?


i have been having similiar problems with firefox if you check my other threads

so is the problem in unity or the persistence file, or plymouth?

thanks in advance for any help.:confused:

---

### Post by TAspr on 2011-05-13
Is there a repair function on the cd?  Maybe a live cd will help so you can make changes to the OS.  Why not stick with the default browser?  I know, variety..

---

### Post by C.S.Cameron on 2011-05-13
Persistence is taken care of by the casper-rw file and limited by the file size, (Max 4GB). If you fill casper-rw the drive will not boot.
The original files are in a squash file and can not be deleted.

I would check the downloaded iso MD5SUM to insure there was no corruption.

---

### Post by user987 on 2011-05-15
i am running the 11.04 os via a usb and over the past 2 weeks

i find that after 2 or 3 log on, i would get system problem of some kind as talk about in my previous posts.

i always end up reformat the drive and then reinstall via universal usb installer.

i am good again with a fresh uncorrupted os for 2 or 3 log on log off.

this last corruption gave me a new os back ground color and icons.

it look like a earlier version of the os.

like i asked in previous posts, what could be doing this?

is it that this method of running the os from usb is for trial purpose of linux and that one must install it on the computer hard drive itself to avoid the corrupt files?

where is the corruption happening?

i suspect the persitence file or casper-rw file

can a expert give some help?

my usb is 4g and i gave the persitence 2.8g

thanks in advance for any help:confused:

---

### Post by mikewhatever on 2011-05-17
A live USB is not an installation, it's just an ISO written to a USB device and made bootable. While nothing can stop you from running Ubuntu from live USB forever, it's really intended for installation and evaluation purposes. Looking over the three (or was it four) earlier posts on the same subject, it seems as if you expect a live USB to function as if it was a proper installation, which obviously isn't the case. In any case, you might want to reconsider the use of 'rm -rf' as a means of fixing problems, as well as starting multiple threads on the same subject.

---

### Post by jtarin on 2011-05-17
There are other Linux USB installs if you want to go that way.

---

### Post by Elfy on 2011-05-17
3 threads merged, 1 closed

Please do not post duplicates, it dilutes community effort.

---

