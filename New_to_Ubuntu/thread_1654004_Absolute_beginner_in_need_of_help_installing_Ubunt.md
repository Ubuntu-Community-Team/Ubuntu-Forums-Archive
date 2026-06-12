---
title: "Absolute beginner in need of help installing Ubuntu"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by pablo0151 on 2010-12-27
Hi all,

Firstly, I'm really sorry for what will probably seem like a pretty daft question, but I'm really struggling to install the latest version of Ubuntu.

I've just bought an Acer Revo 3700 with Linpus pre-installed and thought I'd upgrade to Ubuntu immediately. I've downloaded the ISO, used the USB creator tool to make the drive 'bootable' and configured the computer to boot from removable device. After I choose this though, the screen goes black with a blinking cursor and just hangs.

I'm pretty sure I'm missing something really basic, but I've no idea what. I've tried following a couple of Youtube tutorials to the letter but still get no joy.

Any help with this would be massively apprecaited.

Many thanks

Paul

---

### Post by same.500 on 2010-12-27
Hi!
I thing if you give us more information about your hardware this will help aloot such ( processor type,graphic card,HDD, ....i.e) and what type of iso image you've  downloaded .
I thing this will help you to find agood answer.
Good luck.

---

### Post by kroq-gar78 on 2010-12-27
how long did you wait before concluding that it "hung"?

---

### Post by amjjawad on 2010-12-27
Hello and welcome,

Check the first link in my signature (step1). I'm referring mostly at checking MD5SUM and there are other steps as well.

---

### Post by pablo0151 on 2010-12-27
Ok sorry for the initial lack of info, I'll try and flesh it out a bit more for you:

I downloaded the 10.10 version from the official site to a laptop running MS Vista, I used this to create the bootable USB.

The computer I want to boot Ubuntu on is specced like this:

Intel Atom D525 1.8GHz
2GB RAM
160GB HDD
No Optical Drive
NVIDIA ION 2
Wireless LAN
Linpus Linux

(Sorry, I'm not sure if this is sufficent).

Also, I'd say I left the black screen on for about 5 mins before switching off (too hasty on my part??).

Thanks again for any help.

---

### Post by amjjawad on 2010-12-27
> **pablo0151 said:**
> Ok sorry for the initial lack of info, I'll try and flesh it out a bit more for you:

I downloaded the 10.10 version from the official site to a laptop running MS Vista, I used this to create the bootable USB.

The computer I want to boot Ubuntu on is specced like this:

Intel Atom D525 1.8GHz
2GB RAM
160GB HDD
No Optical Drive
NVIDIA ION 2
Wireless LAN
Linpus Linux

(Sorry, I'm not sure if this is sufficent).

Also, I'd say I left the black screen on for about 5 mins before switching off (too hasty on my part??).

Thanks again for any help.

I'm sorry if I wasn't so specific :)

Have you checked this?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by ubaidillah on 2010-12-27
> **pablo0151 said:**
> Hi all,

Firstly, I'm really sorry for what will probably seem like a pretty daft question, but I'm really struggling to install the latest version of Ubuntu.

I've just bought an Acer Revo 3700 with Linpus pre-installed and thought I'd upgrade to Ubuntu immediately. I've downloaded the ISO, used the USB creator tool to make the drive 'bootable' and configured the computer to boot from removable device. After I choose this though, the screen goes black with a blinking cursor and just hangs.

I'm pretty sure I'm missing something really basic, but I've no idea what. I've tried following a couple of Youtube tutorials to the letter but still get no joy.

Any help with this would be massively apprecaited.

Many thanks

Paul

Hai, what ubuntu version you use? if you use Ubuntu 10.10 i hope this will help you [http://installingubuntulinux.blogspot.com/2010/12/installing-lenovo-ideapad-s10-3-with.html](http://installingubuntulinux.blogspot.com/2010/12/installing-lenovo-ideapad-s10-3-with.html)

---

### Post by nm_geo on 2010-12-27
> **pablo0151 said:**
> Ok sorry for the initial lack of info, I'll try and flesh it out a bit more for you:

I downloaded the 10.10 version from the official site to a laptop running MS Vista, I used this to create the bootable USB.

The computer I want to boot Ubuntu on is specced like this:

Intel Atom D525 1.8GHz
2GB RAM
160GB HDD
No Optical Drive
NVIDIA ION 2
Wireless LAN
Linpus Linux

(Sorry, I'm not sure if this is sufficent).

Also, I'd say I left the black screen on for about 5 mins before switching off (too hasty on my part??).

Thanks again for any help.

Paul a question.  Have you tried to run the computer off the Linpus Linux with the live/USB removed?  I have no experience with Linpus but I would think you could make a live/USB of Ubuntu within that distro.  Then doing the md5sum will let you know if the download of the Ubuntu netbook/desktop 10.10 was clean.  By the way be sure you don't download the alternate iso unless you don't want GUI.

---

### Post by pablo0151 on 2010-12-28
> **nm_geo said:**
> Paul a question.  Have you tried to run the computer off the Linpus Linux with the live/USB removed?  I have no experience with Linpus but I would think you could make a live/USB of Ubuntu within that distro.  Then doing the md5sum will let you know if the download of the Ubuntu netbook/desktop 10.10 was clean.  By the way be sure you don't download the alternate iso unless you don't want GUI.


Hi

I tried downloading the ISO using the linpus computer but when I tried to make the bootable USB on it, the file was trying to open as a Windows exe file. I've no experience with Linux of any sort so I'm not sure whether I can use linpus to do this??

I will try doing the md5sum and see how I get on (never used it though).

---

### Post by pablo0151 on 2010-12-28
I've run the Md5Sum program on the ISO that I downloaded and it reported that the Check Sums are the same.

I'm going to try and create the bootable USB using linpus and see if that makes a difference. 

Would anyone happen to know if using Windows to create the USB causes problems??

Also, I left the black screen for 10 minutes this time and nothing happened, so I think there must be something I'm doing that's wrong.

Thanks again for the help.

---

### Post by amjjawad on 2010-12-28
> **pablo0151 said:**
> I've run the Md5Sum program on the ISO that I downloaded and it reported that the Check Sums are the same.

That's your first successful step. Good :)

> I'm going to try and create the bootable USB using linpus and see if that makes a difference. 

Try this: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

>  Would anyone happen to know if using Windows to create the USB causes problems??

I don't think so.

> Also, I left the black screen for 10 minutes this time and nothing happened, so I think there must be something I'm doing that's wrong.
What is your Graphics Card again?

---

### Post by superchef on 2010-12-28
I've also had problems with the live usb drive creator that ubuntu recommends from their site, so I've been using [UNetbootin]("http://unetbootin.sourceforge.net/") for the past couple of ubuntu releases (you can also use UNetbootin to create live usb's of other linux distros). Unetbootin can be run in windows and linux, and all you have to do is select the "disk image" option in the program, select the .iso that you just downloaded, select your usb drive, and click ok. The program will write the iso to your usb drive and make it bootable. 

Another note, when you boot off of the usb drive, UNetbootin gives you a couple of boot options. I usually pick "default" because that should load the live environment where you can test things out and choose to install.

Good luck!

---

### Post by same.500 on 2010-12-28
Hi!
so your iso image is not damaged but is't 32bit or 64bit, i thing if you can run the iso image and install it as wubi in you'r computer this will be agood start to learn more about ubuntu before install it as operating system.

---

### Post by amjjawad on 2010-12-28
> **superchef said:**
> I've also had problems with the live usb drive creator that ubuntu recommends from their site, so I've been using [UNetbootin]("http://unetbootin.sourceforge.net/") for the past couple of ubuntu releases (you can also use UNetbootin to create live usb's of other linux distros). Unetbootin can be run in windows and linux, and all you have to do is select the "disk image" option in the program, select the .iso that you just downloaded, select your usb drive, and click ok. The program will write the iso to your usb drive and make it bootable. 

Another note, when you boot off of the usb drive, UNetbootin gives you a couple of boot options. I usually pick "default" because that should load the live environment where you can test things out and choose to install.

Good luck!

+1

Very informative :)

---

### Post by pablo0151 on 2010-12-28
> **superchef said:**
> I've also had problems with the live usb drive creator that ubuntu recommends from their site, so I've been using [UNetbootin]("http://unetbootin.sourceforge.net/") for the past couple of ubuntu releases (you can also use UNetbootin to create live usb's of other linux distros). Unetbootin can be run in windows and linux, and all you have to do is select the "disk image" option in the program, select the .iso that you just downloaded, select your usb drive, and click ok. The program will write the iso to your usb drive and make it bootable. 

Another note, when you boot off of the usb drive, UNetbootin gives you a couple of boot options. I usually pick "default" because that should load the live environment where you can test things out and choose to install.

Good luck!

Thanks for the info, I've just tried using UNetbootin to create the USB, and I actually ran this one from the linpus system but I still only get the black screen with the flashing cursor. Any ideas what I'm doing wrong?? From all the info I've read it seems I've done it correctly but you never know eh...

Also: my grapics card is shown as 'nVidia Corporation GT218 [ION] (rev a2)' - if that helps at all?

Thanks again

---

### Post by amjjawad on 2010-12-28
> **pablo0151 said:**
> Also: my grapics card is shown as 'nVidia Corporation GT218 [ION] (rev a2)' - if that helps at all?

Thanks again

Do you get this screen or not?

[IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7132[/IMG]

If yes, Press F6 and try the other options you'll find listed there.

---

### Post by pablo0151 on 2010-12-28
> **amjjawad said:**
> Do you get this screen or not?

[IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7132[/IMG]

If yes, Press F6 and try the other options you'll find listed there.


No, I've never got that screen...just the blinking cursor.

---

### Post by amjjawad on 2010-12-28
> **pablo0151 said:**
> No, I've never got that screen...just the blinking cursor.

If you are using UNetbootin, you'll get a white background menu
Choose the default as the other poster suggested.

If you're using another USB Live Creator, not sure what you'll get.

However, once you start your machine, I assume you get some tables with the system info and stuff like that. Once it skips this, and the screen goes black, press any key in order to get the screen I posted in the previous post.

What is the name of the iso file you downloaded?

---

### Post by msandoy on 2010-12-28
Your specs are very similar to my Asus Eeebox, that I use for a home server, It should have no problem what so ever to run Ubuntu 10.10. Have you tried to boot another computer from the USB drive you made?

---

### Post by pablo0151 on 2010-12-28
> **amjjawad said:**
> If you are using UNetbootin, you'll get a white background menu
Choose the default as the other poster suggested.

If you're using another USB Live Creator, not sure what you'll get.

However, once you start your machine, I assume you get some tables with the system info and stuff like that. Once it skips this, and the screen goes black, press any key in order to get the screen I posted in the previous post.

What is the name of the iso file you downloaded?

When I start the machine and choose 'boot from USB' the next screen just shows a black background with a blinking white cursor (sorry if I'm repeating myself). If I try pressing keys then, it just makes a clicking sound and nothing else happens.

The name of the ISO is 'ubuntu-10.10-desktop-i386'.

---

### Post by amjjawad on 2010-12-28
> **pablo0151 said:**
> When I start the machine and choose 'boot from USB' the next screen just shows a black background with a blinking white cursor (sorry if I'm repeating myself). If I try pressing keys then, it just makes a clicking sound and nothing else happens.

The name of the ISO is 'ubuntu-10.10-desktop-i386'.

I'm sorry to keep asking but I'm trying to figure out what's wrong.

Do you have another machine so that you can try your LiveUSB as msandoy suggested?

Does this machine support booting from USB anyway? just double check your BIOS.

If you have a fast Internet Connection, try to download Ubuntu 10.04.

I'm trying to find out what's wrong. Let's exclude the possibility there's something wrong with your machine. There are many steps to do before we start thinking about that.

---

### Post by msandoy on 2010-12-28
Ok, I think you might want to go into BIOS, go to boot options, hard drive, and when you expand that one, with the USB stick in place, move the usb drive up, so that it will be the first hard drive to boot from. Then choose boot from hard drive. This is a usual fix with some more stuborn BIOS versions.

---

### Post by pablo0151 on 2010-12-28
> **amjjawad said:**
> I'm sorry to keep asking but I'm trying to figure out what's wrong.

Do you have another machine so that you can try your LiveUSB as msandoy suggested?

Does this machine support booting from USB anyway? just double check your BIOS.

If you have a fast Internet Connection, try to download Ubuntu 10.04.

I'm trying to find out what's wrong. Let's exclude the possibility there's something wrong with your machine. There are many steps to do before we start thinking about that.

It's ok, I'm sorry this is such a pain.

I'm running Vista on a laptop as well so I'll try and run the live USB on this and see if it works.

I've been in the BIOS of the other computer and there are options for it to boot from the USB, it also has no CD drive.

Is version Ubuntu 10.04 avaialable from the main site?? If so, I'll have a go at downloading that too.

One thing I noticed is that when I create the USB using the UNetbootin on Windows it uses up just under 1 gig of space. When I created it on the linpus system though it was only around 50kb...neiter worked, but does it sound like the linpus one isn't working correctly??

---

### Post by msandoy on 2010-12-28
Well, the liveUSB should be just under 1GB.
Even if you have various options for booting from USB in BIOS, those might not work if you have a stuborn BIOS. Then the option is to reboot the computer with the usbdrive in place, and select it as the first "Harddrive" to boot from in the boot order in BIOS. This is as I said a usual way of doing it if normal USB booting does not work.

---

### Post by amjjawad on 2010-12-28
> **pablo0151 said:**
> It's ok, I'm sorry this is such a pain.

I'm running Vista on a laptop as well so I'll try and run the live USB on this and see if it works.

I've been in the BIOS of the other computer and there are options for it to boot from the USB, it also has no CD drive.

Is version Ubuntu 10.04 avaialable from the main site?? If so, I'll have a go at downloading that too.

One thing I noticed is that when I create the USB using the UNetbootin on Windows it uses up just under 1 gig of space. When I created it on the linpus system though it was only around 50kb...neiter worked, but does it sound like the linpus one isn't working correctly??


Yes, try to use the LiveUSB on your other machine.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
10.04 is available but you need to choose that from the drop down list.

The blinking cursor is the 2nd step after that screen I posted before. Somehow, your machine or the LiveUSB is skipping that step.

---

### Post by amjjawad on 2010-12-28
Does your BIOS looks like that somehow?

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191[/IMG]

USB-HDD0 = Means the machine will boot from USB Drive
The 2nd one is the HDD.

That's the BIOS settings in my PC and I know yours is different but I'm using this image to help you so that we could be in the same page :)

Edit: Note that, your USB Drive MUST be plugged in before you enter BIOS. If you'll plug it in after you enter BIOS, your BIOS will not detect it.

---

### Post by IndyGunFreak on 2010-12-28
If he's got 10.10.. There's no reason to download ubuntu 10.04... It's not going to change hardware recognition.

OP... did you download the 10.10img file, or the 10.10 ISO?

---

### Post by amjjawad on 2010-12-28
> **IndyGunFreak said:**
> If he's got 10.10.. There's no reason to download ubuntu 10.04... It's not going to change hardware recognition.


That's not the reason why I asked him to download 10.04.

---

### Post by jitender.140 on 2010-12-28
try using USB DVDROM/CD-ROM may that can help you.

---

### Post by kevxh on 2010-12-28
Hi,
I've had this problem with some Dell machines which turned out to be a simple problem with the key. I was using an older 1gb key and whilst my laptop (also a Dell) would boot from it the other machine (a Dell Vostro desktop) would just sit there. So I used a different key and all was fine.

I didn't investigate it further and I know in that situation I could simply have created a cd.

Anyway, that was my experience of the same issue, usb keys are cheap so you have little to loose buying a new one.

Kev

---

### Post by pablo0151 on 2010-12-28
> **msandoy said:**
> Well, the liveUSB should be just under 1GB.
Even if you have various options for booting from USB in BIOS, those might not work if you have a stuborn BIOS. Then the option is to reboot the computer with the usbdrive in place, and select it as the first "Harddrive" to boot from in the boot order in BIOS. This is as I said a usual way of doing it if normal USB booting does not work.

Right, I've just set the BIOS to boot from the USB and selected an option that gives removable devices first priority and I'm still getting the same black screen.

I did try the live USB on my other computer and it worked fine, so I'm guessing it's a problem with my new computer and possbily the BIOS...no idea what it is though.

Just wondering, if it would be more helpful if I were to post images of what I'm doing and the results??

Really appreciate this help everyone.

---

### Post by pablo0151 on 2010-12-28
> **kevxh said:**
> Hi,
I've had this problem with some Dell machines which turned out to be a simple problem with the key. I was using an older 1gb key and whilst my laptop (also a Dell) would boot from it the other machine (a Dell Vostro desktop) would just sit there. So I used a different key and all was fine.

I didn't investigate it further and I know in that situation I could simply have created a cd.

Anyway, that was my experience of the same issue, usb keys are cheap so you have little to loose buying a new one.

Kev

Thanks for the suggestion, at this point I'm willing to try anything so I'll try and get my hands on different one.

Cheers

---

### Post by amjjawad on 2010-12-28
I have a better suggestion.
Read The User Manual of your new machine.

That's the best you could do at the moment. Perhaps, you're missing something ;)

As long as the USB is working on the other machine, there's no point to get new one in my humble opinion but yes, I understand you're trying to do everything possible :)


Edit:
I'm logging off.
Good luck and hope you'll fix that ;)

---

### Post by msandoy on 2010-12-28
We are at least a few steps closer to a solution. We know the liveUSB drive works. Now it is a matter of figuring out how to make it work on your computer.
Pictures of your BIOS setting would be nice, and they may clear things up a bit.

---

### Post by pablo0151 on 2010-12-28
> **msandoy said:**
> We are at least a few steps closer to a solution. We know the liveUSB drive works. Now it is a matter of figuring out how to make it work on your computer.
Pictures of your BIOS setting would be nice, and they may clear things up a bit.

Ok I've took a few snaps of the BIOS and how I've got it set up now...

The first shot is, the front page of the BIOS.

The second is where I've tried to set the USB as the first bootable device.

Hope these help somewhat.

---

### Post by msandoy on 2010-12-28
I have been trying to find the user manual for your computer, but no luck. Acer only gives out a extremly basic user guide, only covering how to unpack and connect a mouse.

---

### Post by pablo0151 on 2010-12-28
amjjawad - Thanks for all your help, hopefully it'll all be sorted soon.

IndyGunFreak - I downloaded the ISO file from the main download page of the Ubuntu site.

---

### Post by msandoy on 2010-12-28
On the second picture, below the 4th boot device, you have hard drive priority. If you reboot your computer with the USB drive in place, you should be able to enter there, and it should show up as a hard drive, set up the USB as first priority. Then you need to set HDD as 1st boot device.

---

### Post by pablo0151 on 2010-12-28
> **msandoy said:**
> On the second picture, below the 4th boot device, you have hard drive priority. If you reboot your computer with the USB drive in place, you should be able to enter there, and it should show up as a hard drive, set up the USB as first priority. Then you need to set HDD as 1st boot device.

I've tried what you suggested, but I'm still getting the black screen, sorry but I've never really played around with a BIOS before.

I've set the 'Removable Device Priority' as first, and disabled the Hard Disk Drive priority...not sure if this is correct.

I've attached a few more pics to show what I've done.

---

### Post by amjjawad on 2010-12-28
> **pablo0151 said:**
> Ok I've took a few snaps of the BIOS and how I've got it set up now...

The first shot is, the front page of the BIOS.

The second is where I've tried to set the USB as the first bootable device.

Hope these help somewhat.

Almost the same BIOS of my other PC.

In the second screenshot, you already have the correct options. USB is set to boot before your HDD which is exactly what you need to do.
Now, we know there is nothing wrong with BIOS.

---

### Post by amjjawad on 2010-12-28
> **pablo0151 said:**
> I've tried what you suggested, but I'm still getting the black screen, sorry but I've never really played around with a BIOS before.

I've set the 'Removable Device Priority' as first, and disabled the Hard Disk Drive priority...not sure if this is correct.

I've attached a few more pics to show what I've done.

I appreciate the other attempts to help you but just read this carefully please.

There is a difference between "Boot Device" and "Hard Disk Priority".
I know that kind of BIOS as it's the same as mine but a newer version.

When you enter "Hard Disk Priority" and your USB Drive is plugged in. Does your BIOS detect it as a HDD-0 or something? or it does not detect anything under "Hard Disk Priority"?

In my BIOS which looks like that, when my USB-Drive is plugged in, I find it listed under "Hard Disk Priority".
If that is the same in your case, set the 1st Boot Device to Hard Disk and ignore the other options then enter "Hard Disk Priority" and set the priority to your USB.

Let me know the outcome.

---

### Post by msandoy on 2010-12-28
Well, so much for the BIOS option. I guess you have to try another USBdrive, as kevxh suggested. Just to recap:
1. USB drive tested on different computer, found working.
2. USB set as as default in BIOS, and still you only get a black screen, not even the grub boot menu.

---

### Post by msandoy on 2010-12-28
> **amjjawad said:**
> I appreciate the other attempts to help you but just read this carefully please.

There is a difference between "Boot Device" and "Hard Disk Priority".
I know that kind of BIOS as it's the same as mine but a newer version.

When you enter "Hard Disk Priority" and your USB Drive is plugged in. Does your BIOS detect it as a HDD-0 or something? or it does not detect anything under "Hard Disk Priority"?

In my BIOS which looks like that, when my USB-Drive is plugged in, I find it listed under "Hard Disk Priority".
If that is the same in your case, set the 1st Boot Device to Hard Disk and ignore the other options then enter "Hard Disk Priority" and set the priority to your USB.

Let me know the outcome.

THIS is what I have been trying to say. I might have been unclear in earlier posts. I don't have a similar BIOS in front of me, and I have to take all the options from memory.

---

### Post by amjjawad on 2010-12-28
> **msandoy said:**
> THIS is what I have been trying to say. I might have been unclear in earlier posts.

I know, I know :) don't take that in the bad/offended meaning :)
I was just trying to be more clear, that's all.

---

### Post by pablo0151 on 2010-12-28
> **amjjawad said:**
> I appreciate the other attempts to help you but just read this carefully please.

There is a difference between "Boot Device" and "Hard Disk Priority".
I know that kind of BIOS as it's the same as mine but a newer version.

When you enter "Hard Disk Priority" and your USB Drive is plugged in. Does your BIOS detect it as a HDD-0 or something? or it does not detect anything under "Hard Disk Priority"?

In my BIOS which looks like that, when my USB-Drive is plugged in, I find it listed under "Hard Disk Priority".
If that is the same in your case, set the 1st Boot Device to Hard Disk and ignore the other options then enter "Hard Disk Priority" and set the priority to your USB.

Let me know the outcome.

Ok, when I enter 'Hard Disk Drive Priority' (option under '4th Boot Device'), all I see is 'SATA: PM-Hitachi HTS545016B9A300' which I guess is the HDD??

Does this mean somehow the BIOS isn't recognising the USB?

---

### Post by cottfcfan on 2010-12-28
I had a similar problem to you.
When you get the flashing cursor try typing: HELP then hit the return button.
Don't ask why but that worked for me.
I got the tip from somewhere else.

---

### Post by msandoy on 2010-12-28
Yes, that is what it means. I guess that is your problem. Can I ask what brand and type of USB drive you have?

---

### Post by amjjawad on 2010-12-28
> **pablo0151 said:**
> Ok, when I enter 'Hard Disk Drive Priority' (option under '4th Boot Device'), all I see is 'SATA: PM-Hitachi HTS545016B9A300' which I guess is the HDD??

Does this mean somehow the BIOS isn't recognising the USB?


Yes, that's the HDD of your machine.

Usually, BIOS detect USB-Drives as HDDs.
I think your BIOS doesn't detect your USB to begin with. Unless you have totally different BIOS which I doubt.
To make sure of that, go to your other machine and check that.

This is another BIOS but still USB-Drive can be detected under "HDD".

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7174[/IMG]

This is when the USB-Drive not plugged in.
Yes, there are two HDDs. Just an example.


[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191[/IMG]

This is when USB-Drive is plugged in before you enter BIOS.



As I mentioned, try to check the same USB on your other machine. Enter BIOS and check it out there.

Can you somehow find your user manual? it will help you a lot.

If you want to easy route: Get new USB-Drive (as already been suggested by another poster) and try it out if you're tired of testing here and there :)

---

### Post by pablo0151 on 2010-12-28
> **msandoy said:**
> Yes, that is what it means. I guess that is your problem. Can I ask what brand and type of USB drive you have?

I tried typing HELP and and pressing enter on the black screen but nothing actually shows when I hit the keys and nothing subsequently happened.

The USB stick I'm using is a 'Transcend Jet Flash 2GB'...and very much considering nipping to Asda to pick up something new.

---

### Post by amjjawad on 2010-12-28
> **pablo0151 said:**
> The USB stick I'm using is a 'Transcend Jet Flash 2GB'.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=179528&d=1293561047[/IMG]


Isn't that the same name appearing here or it's just me who can't see clearly?

---

### Post by pablo0151 on 2010-12-28
> **amjjawad said:**
> Yes, that's the HDD of your machine.

Usually, BIOS detect USB-Drives as HDDs.
I think your BIOS doesn't detect your USB to begin with. Unless you have totally different BIOS which I doubt.
To make sure of that, go to your other machine and check that.

This is another BIOS but still USB-Drive can be detected under "HDD".

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7174[/IMG]

This is when the USB-Drive not plugged in.
Yes, there are two HDDs. Just an example.


[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191[/IMG]

This is when USB-Drive is plugged in before you enter BIOS.



As I mentioned, try to check the same USB on your other machine. Enter BIOS and check it out there.

Can you somehow find your user manual? it will help you a lot.

If you want to easy route: Get new USB-Drive (as already been suggested by another poster) and try it out if you're tired of testing here and there :)

I've just loaded the BIOS of my other computer and had a look round, I can't seem to find the USB in there as a hard drive...but then there is no option to select another hard drive other than the main one anyways. I did test Ubuntu on this computer ealier and it did boot fine from the USB.

Just having a look online for a user manual now as the stingy gits didn't include one!! Think I'll also nip out and try another USB while I'm at it.

If I get another USB, should I repeat your previous instructions with it??

---

### Post by amjjawad on 2010-12-28
> **pablo0151 said:**
> If I get another USB, should I repeat your previous instructions with it??

Yes, follow the normal procedure and if you need anything, post back here :)

Sorry you have lots of problems but it happens.

---

### Post by pablo0151 on 2010-12-28
> **amjjawad said:**
> Yes, follow the normal procedure and if you need anything, post back here :)

Sorry you have lots of problems but it happens.

Yeah no probs, I'll get there in the end...hopefully!!

Just nipping to Tesco to pick up a new USB so I'll report back soon.

---

### Post by amjjawad on 2010-12-28
> **pablo0151 said:**
> Yeah no probs, I'll get there in the end...hopefully!!

Just nipping to Tesco to pick up a new USB so I'll report back soon.

Good luck :)

---

### Post by msandoy on 2010-12-28
Sure hope everything works out for you. :-)

---

### Post by pablo0151 on 2010-12-28
Ok I've arrived back with a new USB, used UNetbootin to create the bootable and tried again...it gets a bit weird here though.

When I go into the BIOS, I still can't see the USB under 'Hard Drive Priority' and when I try and boot from the USB as normal it just loads linpus and ignores the USB!!

Maybe it's been a long day, am I missing something basic now??

Cheers

---

### Post by amjjawad on 2010-12-29
> **pablo0151 said:**
> Ok I've arrived back with a new USB, used UNetbootin to create the bootable and tried again...it gets a bit weird here though.

When I go into the BIOS, I still can't see the USB under 'Hard Drive Priority' and when I try and boot from the USB as normal it just loads linpus and ignores the USB!!

Maybe it's been a long day, am I missing something basic now??

Cheers

Paul,

All what I could think about is this:

A)

1) Plug your USB
2) Reboot your machine
3) Enter BIOS
4) From the page of Devices where it says 1st Device, 2nd Device, etc.
Enter that list and try to find your USB. See if it's listed.

If it is listed > Set that as your first **Device** to boot from. Then set the HDD as the 2nd **Device** to boot from.

If it's NOT listed > Set HDD as the first **Device** to boot from. Then go to "HDD Priority" and check if your USB is listed or not.


B)
[http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/](http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/)


These are the only things in my mind as of now :)

---

### Post by same.500 on 2010-12-29
Hi!
I don't know if i understand it very clear.
But from what i see you don't have aproblem whit you'r iso image,usb you've created working,live CD working and you chose the right iso image for you'r devise but you still can't install ubuntu; And i don't thing you have aproblem whit BIOS because you try to boot from both usb and live CD but nothing worked will and you can't hit F6 to try another boot options ( i don't know why) .
So i suggested you'r problem is whit graphic card so why not try download the alternative iso image and give it atry.

---

### Post by pablo0151 on 2010-12-29
> **amjjawad said:**
> Paul,

All what I could think about is this:

A)

1) Plug your USB
2) Reboot your machine
3) Enter BIOS
4) From the page of Devices where it says 1st Device, 2nd Device, etc.
Enter that list and try to find your USB. See if it's listed.

If it is listed > Set that as your first **Device** to boot from. Then set the HDD as the 2nd **Device** to boot from.

If it's NOT listed > Set HDD as the first **Device** to boot from. Then go to "HDD Priority" and check if your USB is listed or not.


B)
[http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/](http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/)


These are the only things in my mind as of now :)

I've just tried my new USB on laptop (the one running Vista) and booting from the USB works fine, I get the Ubuntu menu and can boot into it no probs.

Just tried the suggestion for the BIOS and when I try and boot from the USB it just goes straight through to the usual Linpus system.

I'm guessing that from the looks of it, that my BIOS is having problems booting from USB devices.

Really stuck now to be honest...

---

### Post by amjjawad on 2010-12-29
> **pablo0151 said:**
> I've just tried my new USB on laptop (the one running Vista) and booting from the USB works fine, I get the Ubuntu menu and can boot into it no probs.

Just tried the suggestion for the BIOS and when I try and boot from the USB it just goes straight through to the usual Linpus system.

I'm guessing that from the looks of it, that my BIOS is having problems booting from USB devices.

Really stuck now to be honest...

Try Plop from the link I posted, Paul.
Or, try to get an external CD Drive but that would be USB and not sure whether it will work or not.
Sorry but I can not think about anything else. I am in bed with strong flu. It is good I am still typing.

Do not lose hope.

---

### Post by pablo0151 on 2010-12-29
> **amjjawad said:**
> Try Plop from the link I posted, Paul.
Or, try to get an external CD Drive but that would be USB and not sure whether it will work or not.
Sorry but I can not think about anything else. I am in bed with strong flu. It is good I am still typing.

Do not lose hope.

Bad news re the flu...hope you beat it soon.

Just had a quick look at that Plop program, the only thing I was thinking is that does it only run on Windows machines?? The machine I'm trying to get Ubuntu on has this awful Linpus OS running on so not sure if Plop will work on it.

---

### Post by amjjawad on 2010-12-29
> **pablo0151 said:**
> Bad news re the flu...hope you beat it soon.

Unfortunately, it's beating me so I'm going to the hospital tomorrow morning.
Thank you so much :)

> 
Just had a quick look at that Plop program, the only thing I was thinking is that does it only run on Windows machines?? The machine I'm trying to get Ubuntu on has this awful Linpus OS running on so not sure if Plop will work on it.

[http://en.wikipedia.org/wiki/Linpus_Linux](http://en.wikipedia.org/wiki/Linpus_Linux)

Which means it's a Linux OS after all. So yes, it should work.
[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

I think there's another way to install Ubuntu via the network but I have no idea how to do so. Above all, I've heard it's an advanced approach.

Of course the traditional way is to take the HDD out, connecting it to another machine and install from there but I'm afraid you'll lose your warranty as it's a new machine. Just double check that before doing anything.

I hope someone else could have better ideas as I'm running out from that :)

---

### Post by pablo0151 on 2010-12-29
> **amjjawad said:**
> Unfortunately, it's beating me so I'm going to the hospital tomorrow morning.
Thank you so much :)



[http://en.wikipedia.org/wiki/Linpus_Linux](http://en.wikipedia.org/wiki/Linpus_Linux)

Which means it's a Linux OS after all. So yes, it should work.
[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

I think there's another way to install Ubuntu via the network but I have no idea how to do so. Above all, I've heard it's an advanced approach.

Of course the traditional way is to take the HDD out, connecting it to another machine and install from there but I'm afraid you'll lose your warranty as it's a new machine. Just double check that before doing anything.

I hope someone else could have better ideas as I'm running out from that :)

Good luck at the hospial then, and thanks for helping me out so much when you feel lousy.

I'm going to try that Plop program tonight and see how I get on...if that doesn't work I might contact the company I bought the PC off and see if they know of any faults. Failing that, I guess it's a copy of XP and a USB CD drive.

---

### Post by msandoy on 2010-12-29
Well, if you can get a hold of a USB cd drive, then you might as well try booting frm the ubuntu CD. :-)

---

### Post by amjjawad on 2010-12-29
> **pablo0151 said:**
> Good luck at the hospial then, and thanks for helping me out so much when you feel lousy.

I'm going to try that Plop program tonight and see how I get on...if that doesn't work I might contact the company I bought the PC off and see if they know of any faults. Failing that, I guess it's a copy of XP and a USB CD drive.

Thank you so much, I appreciate that and I'm sorry I couldn't be so much help to you.
I'm on and off here because if I'll stay in bed, I'll feel worse :)

You know what? not trying to make things worse but I'm so mad at Acer now. I hate it before and I have yet another reason to hate it even more. How come they sell things without manual? anyway, I enjoy calling companies and give them hard time when they fail to deliver what they promise to do.
Good luck with that.

I'm not sure if you could do it but is there any way to replace that machine with something better? sorry, it might be a good machine but I'm just saying if there's something better?
Edit: better = does not give you hard time :)

---

### Post by verymadpip on 2010-12-29
I've been having similar USB issues & have found this thread very informative.
Now I've things to try when I get home later.

This forum & its members ROCK!!! :p

---

### Post by pablo0151 on 2010-12-29
GREAT NEWS!!

I think I've mangaed to solve this awful problem using a topic from this forum I found Googling the computer

<a href="showthread.php?t=1202852" target="_blank">[HTML]http://ubuntuforums.org/showthread.php?t=1202852[/HTML]Basically it seems my computer's BIOS would treat any USB that is 2gb or less as a floppy drive and therefore not boot from it...how stupid is that setting?!

I went in and changed the setting, saved and re-booted and I'm now just waiting for the install to finish.

Hard work but got there in the end and now looking forward once again to using Ubuntu.

Massive thanks to everyone who helped me out, it gives me confidence that any future problems can be solved...and it's also great to see so many people willing to help out.

Cheers once again

Paul

---

### Post by amjjawad on 2010-12-30
> **pablo0151 said:**
> GREAT NEWS!!

I think I've mangaed to solve this awful problem using a topic from this forum I found Googling the computer

<a href="showthread.php?t=1202852" target="_blank">[HTML]http://ubuntuforums.org/showthread.php?t=1202852[/HTML]

Paul, I'm so much happy to know that. WELL DONE :)

HOWEVER :)

> Basically it seems my computer's BIOS would treat any USB that is 2gb or less as a floppy drive and therefore not boot from it...how stupid is that setting?!
Seriously, how could they do that? I think it happens only when it's Acer :D

> Hard work but got there in the end and now looking forward once again to using Ubuntu.
The best part is you did not give up. That's really great :)

Keep it up and wish you all the best.

Don't buy Acer machines again ;) :D


P.S.
Don't forget to mark this thread as "SOLVED" 

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

### Post by msandoy on 2010-12-30
Great!! I hope you find Ubuntu to be a nice and userfriendly OS. Maybe you could make a "Howto install ubuntu on a Acer 'something'" thread in Tutorials and Tips?
The people you meet in this forum is great, and always willing to help.
Good luck with your new OS!

---

### Post by pablo0151 on 2010-12-30
> **msandoy said:**
> Great!! I hope you find Ubuntu to be a nice and userfriendly OS. Maybe you could make a "Howto install ubuntu on a Acer 'something'" thread in Tutorials and Tips?
The people you meet in this forum is great, and always willing to help.
Good luck with your new OS!

That's a good idea and something I'll try and get round to doing. The fix was simple in the end, but it was really obscure and hard to find so documenting it will be worth it.

Enjoying the OS so far, hope to keep it that way!!

---

### Post by tpkaznowski on 2011-01-17
Hi GUys, 

I have just bought a Revo 3700 with linpus already installed... I want to install ubuntu. I have created a USB boot disk with ubuntu on it. I have been searching the web for ages and have found several posts relating to the difficulties with the BIOS in these machines. I have tried several different things - I have turned Quick and quiet boot off - I have turned Usb to primary boot option and I have Made sure that the USB is recognised as a HDD rather than AUTO. When I boot up it goes to the screen "press escape to boot" and when i press it, the machine boots into linpus again.....

I am getting very frustrated.... Can anyone help?

Taz:(

---

### Post by amjjawad on 2011-01-18
> **tpkaznowski said:**
> Hi GUys, 

I have just bought a Revo 3700 with linpus already installed... I want to install ubuntu. I have created a USB boot disk with ubuntu on it. I have been searching the web for ages and have found several posts relating to the difficulties with the BIOS in these machines. I have tried several different things - I have turned Quick and quiet boot off - I have turned Usb to primary boot option and I have Made sure that the USB is recognised as a HDD rather than AUTO. When I boot up it goes to the screen "press escape to boot" and when i press it, the machine boots into linpus again.....

I am getting very frustrated.... Can anyone help?

Taz:(

Hello Taz,

Did you read this thread? the whole thing? if not, please start now.

If you read it and did NOT find anything useful, please start your own thread because most likey ONLY those who posted here will check this thread. NO ONE will bother with "SOLVED" thread so your own thread is the better idea ;)

Thank you!

---

