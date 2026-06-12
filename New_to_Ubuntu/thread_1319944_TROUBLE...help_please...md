---
title: "TROUBLE...help please.."
date: 2009-11-08
forum: New to Ubuntu
---

### Post by nothingman02 on 2009-11-08
I recently got a lenovo g550. It came with vista home premium. I immediately deleted windows and installed Jaunty with no other partitions. 

As usual the other day, while I was obtaining some updates, I saw the update option for 9.10 and went ahead with it. Now its a mess. 

I have no screen!! At first I could restart the computer and had various boot options which I cant remember now. I picked one and I could get a the GUI but my touchpad and mouse would not work. Then I tried my windows restore CD which I had created in the beginning(hoping for some miracle that it would be a complete windows OS and not just a restore) and it did not work. 

Now, I get the grub error 17.

I went to another computer and downloaded 4 varieties 3 of which are ubuntu. Hardy, Jaunty and the karmic koala and then livemint. None of the others even seem to work. If I put in the 9.10, it boots and asks me if I want to try the live CD or make an installation and either of those options turn the screen blank with no further activity. 

Anything I can do at all? I was browsing through and found an option where students could buy the windows 7 upgrade CD for 29.99 bucks. It states its an upgrade CD. Does it mean I need to have some version of windows for the upgrade CD to work? Reading on, there was some info about how one could do a clean install for any OS. So thats confusing. 

Any solution? Little did I know that simply upgrading from 9.04 to 9.10 would create such a mess. Any help would be appreciated. I am unable to figure out any options other than to buy a windows CD. Thanks for the help.

---

### Post by dvlchd3 on 2009-11-08
> I was browsing through and found an option where students could buy the windows 7 upgrade CD for 29.99 bucks. It states its an upgrade CD. Does it mean I need to have some version of windows for the upgrade CD to work?
Yes.

> I went to another computer and downloaded 4 varieties 3 of which are ubuntu. Hardy, Jaunty and the karmic koala and then livemint. None of the others even seem to work. If I put in the 9.10, it boots and asks me if I want to try the live CD or make an installation and either of those options turn the screen blank with no further activity. 
Did you try only 9.10?  There may be some sort of issue with your computer and 9.10.  Try 9.04 disc, boot into the liveCD.  All your data should still be intact on your harddrive.  Backup all the files you want to keep onto an external harddrive/flashdrive.  (It will be listed as "[size_of_your_hd]GB Media" under the Places menu)  Try reinstalling 9.04 over the current installation.

It sounds like something broke in your upgrade.  We could possibly attempt to diagnose it, but I think just doing a fresh install with 9.04 is your best option.

---

### Post by nothingman02 on 2009-11-08
Hi thanks for the quick reply. Im afraid my 9.04 will not work.

I tried installing 9.04 from the CD, I get the grub error 17 right away.
I tried the hardy and had the same problem as above.
I tried livemint and had the same problem as above.
I then tried the 9.10 CD and it would ask me if I wanted to install or try it live and for any option that I pick, the screen goes blank. Nothing happens. 

Basically with every version of Ubuntu, I get the same blank screen. I really thought that going back to 9.04 would solve it but its not happening. Jaunty used to work flawlessly before and was very fast. The only issue I had then was a slight overheating left of the touchpad. Part of the reason why I upgraded thinking that the likely bug would be resolved with the upgrade.

---

### Post by Sealbhach on 2009-11-08
A lot of people on the forums have reported a similar blank screen. I think it must be the new installer not playing nice with your graphics card. I would suggest as well to go back to 9.04 for the time being.

.

---

### Post by Sealbhach on 2009-11-08
> **nothingman02 said:**
> 
I tried installing 9.04 from the CD, I get the grub error 17 right away.


Make sure to change the boot order in the BIOS so that it boots first from CD.

.

---

### Post by yanceypd on 2009-11-08
Make sure your bios on boot has the CD or Dvd drive set as boot device.  Try 8.10 or 9.04 as 9.10 is new release.

---

### Post by QIII on 2009-11-08
Will the LiveCD run in a live session?

---

### Post by k33bz on 2009-11-08
> **nothingman02 said:**
> Hi thanks for the quick reply. Im afraid my 9.04 will not work.

I tried installing 9.04 from the CD, I get the grub error 17 right away.
I tried the hardy and had the same problem as above.
I tried livemint and had the same problem as above.
I then tried the 9.10 CD and it would ask me if I wanted to install or try it live and for any option that I pick, the screen goes blank. Nothing happens. 

Basically with every version of Ubuntu, I get the same blank screen. I really thought that going back to 9.04 would solve it but its not happening. Jaunty used to work flawlessly before and was very fast. The only issue I had then was a slight overheating left of the touchpad. Part of the reason why I upgraded thinking that the likely bug would be resolved with the upgrade.

May be a dumb question, but you are wiping your entire system clean when you try to install 9.04 correct? Cause honestly that error is an error on your GRUB.

---

### Post by nothingman02 on 2009-11-08
[B][I]"May be a dumb question, but you are wiping your entire system clean when you try to install 9.04 correct? Cause honestly that error is an error on your GRUB."

[/I][/B]Hi. Actually, could you elaborate on that please? I mean I am not sure. I was thinking that if I try the 9.04, it would clean the system up and then install itself?

The first thing that I had checked was that. That the CD drive was the first in the boot order. In fact I had moved the HDD down to the bottom and the second option is the USB.

---

### Post by nothingman02 on 2009-11-08
[I][B]"Will the LiveCD run in a live session?"

[/B][/I]Nope! I cant even get in!! With all the versions of ubuntu or another flavor of linux, I get the grub error 17. 
And with 9.10, I get an option to try the live version or simply install directly. With both the options, as soon I select the option, the screen goes blank. In one attempt,  I also heard the audio, that brief music which one hears after an OS loads completely, but I could still not see anything but a blank screen!

Im still new and cant figure out what to do other than to buy a windows CD and install windows and then, and this time, dual boot ubuntu. But I really dont want to spend 200 bucks for an OS which I am never going to use. I now understand that the windows 7 available to students for 29.99 is only an upgrade and one would need to have an existing windows OS already running on the computer. 

Any solutions? Thanks for the replies.

---

### Post by nothingman02 on 2009-11-08
When I go to the link here;

[COLOR=Blue]http://windows7.digitalriver.com/servlet/ControllerServlet?Action=DisplayHomePage&Locale=en_US&SiteID=mswpus[/COLOR]

And click on a 'note', it says the following;


[LIST]
[*]                    Upgrading to Windows 7. Choose Upgrade to keep your files, settings, and programs from your current version of Windows, and if your current version of Windows can be upgraded. If your version of Windows  can't be upgraded, you need to choose Custom.
[*]                    [COLOR=SeaGreen]Installing a custom version of Windows.   Choose Custom to completely replace your current operating system, or to install Windows on a specific drive or partition that you select. You can also use Custom if your computer doesn't have an operating system, or if you want to set up a multiboot system on your computer. For more information about setting up a multiboot system, see [Install more than one operating system (multiboot)]("http://windows.microsoft.com/en-us/windows7/Install-more-than-one-operating-system-multiboot").[/COLOR]
[*]                    Reinstalling Windows 7. Choose this option if you want to restore default Windows settings or if you are having trouble with Windows and need to reinstall it by performing a custom installation.
[/LIST]
------------------------------------------------------------------------------------------------

The above is the link I get after I verify my student email address. That is, I can buy the windows 7 upgrade for $29.99.

But if you look at the paragraph in green above, it could be surmised that one could perform a clean windows 7 install on a broken system with  no OS? Is that correct? Right now I have no OS on my system. I mean I certainly dont have windows and the ubuntu 9.10 which I guess is in there is not working right. Can I perform a clean install of windows 7 even though it says its a ** windows 7 upgrade**? I mean the paragraph in green certainly seems to state so.

Anybody? 

It would be great if I can get away with spending just 30 bucks as I only want windows to fix my system and then I am gonna install jaunty. So I dont want to spend too much money there.

---

### Post by Bartender on 2009-11-08
According to GRUB manual, error 17 is:
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

Looks to me like the machine is not booting from the optical drive.  Maybe go back into BIOS and try disabling all other bootable devices except the optical drive and see what error message you get.  You sure you burning those downloads correctly?  You're making an .iso, not just copying the data?

---

### Post by nothingman02 on 2009-11-08
> **Bartender said:**
> According to GRUB manual, error 17 is:
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

Looks to me like the machine is not booting from the optical drive.  Maybe go back into BIOS and try disabling all other bootable devices except the optical drive and see what error message you get.  You sure you burning those downloads correctly?  You're making an .iso, not just copying the data?

Hi,
Thanks for the reply.
Yep. At first, I did not get the GRUB error. I had 4 boot options at restart but cant remember them Im afraid. But only the third option worked and took me into the GUI which was not so good. And the touchpad did not work and neither did the mouse. The CD drive worked though.

It was then that I gave the windows restore CD which I had first created when I got the laptop a shot. But it obviously did not work since I had deleted windows. I mean it completed the restoration but when I restarted, I got the GRUB error 17.
 
I will now do that. Will disable the other boot options. Will post back here what happens. I have burned them correctly, as in, I did not copy them as data files. I downloaded and burned 8.04, 9.04 and 9.10. The 9.10 actually works for a moment and asks me if I want to install the OS or try it live etc after which it starts acting up. 

Any other options? Can you look at the info in my previous post about the windows 7 upgrade option for 29.99. Its only an UPGRADE option as it states but in the paragraph in green, it seems to suggest that one could perform a clean install even if there is no OS in the computer.

---

### Post by nothingman02 on 2009-11-08
[COLOR=Blue]http://redmondmag.com/articles/2009/11/02/windows-7-upgrade-hacks-not-legal.aspx[/COLOR]

The above is another piece of info I just found about windows 7 upgrade 'hack'.
That is , although its intended for an existing windows OS 'upgrade', it is possible to perform a clean install on a blank drive which is pretty my situation. I do have a broken 9.10 on my system, but its gonna be a blank HDD to windows 7. 

So isnt this a better and quicker option for me? I could get the windows 7 upgrade for 30 bucks and then install it and then boot up my computer after which I could install Jaunty. 

Possible?

I just dont want to spend 299 bucks to buy windows 7 just so I can boot my computer!! The article does state its not "legal" to use windows 7 upgrade WITHOUT an existing flavor of windows OS but the link in my previous post (in green) states I could do a custom install on a blank drive. Essentially, the seller is advocating a windows 7 upgrade hack and hence I will not be doing anything 'illegal'. 

Does this option sound good? Please let me know if there are other ways to get my computer back up. This is the second day that Ive been unable to use my laptop and thats affecting my job and studies as well apart from other work that Iam doing using the computer.Thanks for your replies again.

---

### Post by think13 on 2009-11-08
You should be able to ask Lenovo for a Vista CD since your laptop came with windows vista. From there, you could install Vista.

Are you sure you are booting from the CD? I'm not sure GRUB even runs when you boot from the CD. Watch the screen closely when you boot-before GRUB there should be a key to press to get into the BIOS options. Otherwise, perhaps your CD is corrupted.

The final thing I would try is the alternate install CD. I believe this doesn't use the graphics card at all, so it should work.

---

### Post by QIII on 2009-11-08
If you cannot run a LiveCD session from the CD and it is giving you a GRUB error, then I am pretty sure that one of the three is the case:  Your BIOS is not booting the CD drive first; the drive itself is malfunctioning and the BIOS is failing over to the next drive in the boot order; or the CD is corrupt (unrecognizable as a drive) and the BIOS is failing to the next drive in the boot order.

If, as you say, you were able to get to the screen that allows you to select a live session or installation, the live session works and the installation does not then:

Using the LiveCD, please see if you can post the results of 

```
fdisk -l
```

---

### Post by nothingman02 on 2009-11-08
> **think13 said:**
> You should be able to ask Lenovo for a Vista CD since your laptop came with windows vista. From there, you could install Vista.
[COLOR=Blue]**I am gonna do that. But I believe I have to buy it?**[/COLOR]

Are you sure you are booting from the CD? 
[COLOR=Blue]**Yes!**[/COLOR]

I'm not sure GRUB even runs when you boot from the CD. 
[B][COLOR=Blue]I do have a kinda corrupt(?) 9.10 on my laptop. So GRUB runs _IF _the CD does not boot. 
If I run any OS(tried 8.04, 9.04 and livemint) on the CD other than 9.10, its not being recognized and then the BIOS is moving onto the HDD to boot and thats where I am getting the GRUB error 17 is what it looks like. If I try the 9.10 however, its booting from the CD. only to give me a blank screen.[/COLOR][/B]

Watch the screen closely when you boot-before GRUB there should be a key to press to get into the BIOS options. Otherwise, perhaps your CD is corrupted.
**[COLOR=Blue]Im certain the CD is not corrupted. I already had a CD. I made a new CD (DVD) as I had a similar doubt that the CD might be bad. Besides, as mentioned, 9.10 works even if only for a moment but there are atleast 3 others that donot work.[/COLOR]**

The final thing I would try is the alternate install CD. I believe this doesn't use the graphics card at all, so it should work.
[COLOR=Blue]**Hmmm...does that mean a text based installation with no graphics? Im afraid, im still new and am not familiar with the commands. Do you mean that since 9.10 is tha only flavor being recognized, I should install it without graphics and then install Jaunty using the command line? **[/COLOR]

---

### Post by nothingman02 on 2009-11-08
Hi QIII,
Both the live and the install options do not work. I get a blank screen with both the options. I am sitting here with the laptop and just tried it again.

---

### Post by lavinog on 2009-11-08
Do you get a blank screen with the jaunty live cd?

If you can boot the jaunty live cd, do a fresh install, but make sure you format all partitions.

Also, what video card do you have? (ATI, nVidia, Intel...)

---

### Post by nothingman02 on 2009-11-08
> **lavinog said:**
> Do you get a blank screen with the jaunty live cd?

If you can boot the jaunty live cd, do a fresh install, but make sure you format all partitions.

Also, what video card do you have? (ATI, nVidia, Intel...)


Hi,
I have an intel 4500.

---

### Post by ronaldbrijo on 2009-11-08
If you want to get your pc to boot back to windows you need a win98 install cd. Insert in  your drive to boot from cd (boot with cd rom support). When it gets to the command prompt all you need to do is type the following command: "fdisk /mbr".

This command will clear the master boot record that has been corrupted.

---

### Post by lavinog on 2009-11-08
> **ronaldbrijo said:**
> If you want to get your pc to boot back to windows you need a win98 install cd. Insert in  your drive to boot from cd (boot with cd rom support). When it gets to the command prompt all you need to do is type the following command: "fdisk /mbr".

This command will clear the master boot record that has been corrupted.
He wiped windows.
Plus vista has a utility to fix the boot record.
Is the win98 cd compatible with vista installs?

---

### Post by nothingman02 on 2009-11-10
Anybody ? Any help please? Still struggling to get my laptop up!!

Just to recap,

I deleted windows vista and installed jaunty. It was great for a month until I tried to upgrade jaunty to koala and now I get a blank screen. I tried the windows restore disks and they did not work probably cause I deleted windows?
Now I get the grub error 17!!

1) I get a blank screen if I try to boot 9.10.
2) If I try Jaunty, I get the screen asking me if I want to install or try a live version of Jaunty (I made a new disk and its now booting from the CD drive..). But then it hangs up. I get a series of errors...
3) I tried PClinuxos. The same happens as with Jaunty in #2 above. 

Any other options for me? 

I just called lenovo and they told me they dont have an OS disk but will send me those 3 windows vista restore disks. Apparently those disks are "images of the system in factory condition". Or something along those lines. Will that really work? I mean I have wiped out windows so are those specific 'image' restore disks gonna work? She said I also would not have drivers and would have to download them seperately from the website. 

Is there any version of linux that is sure to work right now? I had jaunty running great till last week! .I tried pclinuxos cause its supposedly the simplest and works on most systems but thats a no go.

Any help would be appreciated!

---

### Post by lavinog on 2009-11-10
> **nothingman02 said:**
> (I made a new disk and its now booting from the CD drive..). But then it hangs up. I get a series of errors...
3) I tried PClinuxos. The same happens as with Jaunty in #2 above. 

Try checking the cd first. (one of the boot options on the live cd)
It could be your cd drive is dirty or faulty.

---

### Post by nothingman02 on 2009-11-10
i ran the 'media check' options in all the cases. I am actually trying out, again, pclinuxos and ran the media test and it was 'pass'.

The drive itself seems fine and clean. The laptop (lenovo g550) is pretty new. Its barely 2 months old.

pclinuxos seemed to be installing fine just now. Everything was showing [ok] and then the screen went blank!! again!

I am at my wits end! I was thinking that buying a new windows OS and installing would likely solve the problem but now I am not even sure about that. I mean I may get that blank screen with windows too?? I just dont want to spend 300 bucks for an OS I will never use. Any options please?

---

### Post by nothingman02 on 2009-11-10
buffer i/o error on dev sr0, logical block 173047 
Buffer i/o error on dev sr0, logical block 173064
and so on.....on various blocks....

Followed by,
SQUASHFS error, unable to read page block xxxxxxxx
SQUASHFS erroe, failed to read block xxxxx

start-stop daemon: unable to start usr/bin/xxxx input output error

then the repeat of the above

start-stop daemon: unable to start usr/bin/xxxx : networking...input output error

so on....


Im am trying to get the screen but it keeps moving quickly and over and over until it stops which is for around  3-5 minutes. 

Can anybody make anything of this?

---

### Post by Bartender on 2009-11-11
nothing -
You still out there?
I want to go back to something you said.  You said that you made recovery discs.  Right?  Those recovery discs should work whether you deleted Windows or messed it up or whatever.
I'm going to cross my fingers that your recovery discs are good.  Borrow some time on someone else's PC and create a GParted LiveCD.  Link under my sig.  Download the latest stable .iso, burn it like you would an Ubuntu download.  

When you've made the disc, take it to your sick PC and boot from the Gparted LiveCD.  Wipe out all partitions until you have one big unallocated space.  Format that space as a primary NTFS partition.

Get out of GParted, boot up the first recovery disc.  My Vista recovery discs (this was an Acer) were unable to do anything with a HDD that was formatted in a Linux file system.  I got nowhere until I did as described above, then the Vista recovery discs worked.

let's at least try to get you back to a working PC, then you can decide what to do from there!

---

### Post by lavinog on 2009-11-11
can you post the output of:
```

dmesg|grep ATAPI
```
There could be a bug with your cdrom drive.
Also see if there is a firmware update for your drive( don't think this will be the case, but it will be good to check anyway.)

---

### Post by fatcrab on 2009-11-11
If you want to install 7 with a upgrade disk you will need a xp or vista disk.I think it has to be a full verison to work.You can buy OME for $109 at newegg.

---

### Post by nothingman02 on 2009-11-11
> **Bartender said:**
> nothing -
You still out there?
I want to go back to something you said.  You said that you made recovery discs.  Right?  Those recovery discs should work whether you deleted Windows or messed it up or whatever.
I'm going to cross my fingers that your recovery discs are good.  Borrow some time on someone else's PC and create a GParted LiveCD.  Link under my sig.  Download the latest stable .iso, burn it like you would an Ubuntu download.  

When you've made the disc, take it to your sick PC and boot from the Gparted LiveCD.  Wipe out all partitions until you have one big unallocated space.  Format that space as a primary NTFS partition.

Get out of GParted, boot up the first recovery disc.  My Vista recovery discs (this was an Acer) were unable to do anything with a HDD that was formatted in a Linux file system.  I got nowhere until I did as described above, then the Vista recovery discs worked.

let's at least try to get you back to a working PC, then you can decide what to do from there!

Hi Bartender and thanks for the reply. I just tried this out.
I downloaded the iso image of gparted live and then deleted one partition and was left with only one unallocated space of 232 GB.
I formnatted it as an NTFS (It only took less than a second!)

I then restarted and booted form the CD with the VISTA restore disks 1 and 2.
Everything went fine and the restoration was complete.
Now I get the following;
[B]
[FONT=Arial,Helvetica][SIZE=2]Broadcome UNDI PXE-2.1 v11.4.1
copyright (c) 2000-2008 broadcom Corporation
copyright (c) 1997-2000 Intel Coroporation 
all rights reserved

[/SIZE][/FONT][/B][FONT=Arial,Helvetica][SIZE=2][B]Broadcom Base Code PXE-2.1 v1.1.0
copyright (c) 2000-2008 broadcom Corporation
copyright (c) 1997-2000 Intel Coroporation 
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Broadcom PXE ROM. [/B]
[/SIZE][/FONT]


I keep getting the above again and again and nothing happens. Any idea what the above is?


Thanks again to everybody for all the help.

[FONT=Arial,Helvetica][SIZE=2]
[/SIZE][/FONT]

---

### Post by marshmallow1304 on 2009-11-11
> PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Broadcom PXE ROM.

According to [this]("http://forums.techguy.org/hardware/104472-solved-pxe-e61-media-test.html"), you need to check your boot order.  You may have left the network boot option before the hard drive option.

---

### Post by drakkoss on 2009-11-11
[quote=nothingman02;8275458][I][B]"Will the LiveCD run in a live session?"

[/B][/I]Nope! I cant even get in!! With all the versions of ubuntu or another flavor of linux, I get the grub error 17. 
And with 9.10, I get an option to try the live version or simply install directly. With both the options, as soon I select the option, the screen goes blank. In one attempt,  I also heard the audio, that brief music which one hears after an OS loads completely, but I could still not see anything but a blank screen!

  I'm still new and cant figure out what to do other than to buy a windows CD and install windows and then, and this time, dual boot ubuntu. But I really dont want to spend 200 bucks for an OS which I am never going to use. I now understand that the windows 7 available to students for 29.99 is only an upgrade and one would need to have an existing windows OS already running on the computer.

---

