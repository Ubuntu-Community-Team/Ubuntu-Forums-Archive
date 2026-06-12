---
title: "Potential new ubuntu convert - USB trial boot - graphic problems"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by redsaint182 on 2010-10-05
Hi! Like it says in the title, I am a potential new Ubuntu convert, I have been reading about it the past few days and am really intrigued! So, heres my problem:

I followed the short how-to guide on the main Ubuntu site on booting from a USB drive, and once I changed my BIOS settings, I got it to boot Ubuntu. I saw a menu (that has to be navigated with directional arrows) with a few options, and one was to try Ubuntu (that was the first option,) and it automatically picked this option after a couple of seconds. So it started up, and I even heard the starting sound! (kind of African sounding.) -- **But** I couldn't see anything. Well, I could see some bars (going up and down) but they are definitely not part of what is supposed to be the GUI. Theres some purple, and a big white bar going down the middle. I figured it was probably cause of my graphics card? (geforce 8600m gt), but I obviously cannot load any drivers or anything like that if I cannot see, right? Or maybe that isn't my problem. Anyways, hopefully you guys can shed some light on this for me and give me some advice. (I'm running on a Dell Inspiron 1520, if that matters, and am also trying to run 10.04 I think.)

Take care, and thanks to you if you take time to help me out :)

---

### Post by NightwishFan on 2010-10-05
When you get to the menu that says try Ubuntu (by hitting any key as it shows white symbols on the screen) press f6 and select the "nomodeset" option. Then pick "try Ubuntu". Tell me if this works for you.

---

### Post by redsaint182 on 2010-10-05
> **NightwishFan said:**
> When you get to the menu that says try Ubuntu (by hitting any key as it shows white symbols on the screen) press f6 and select the "nomodeset" option. Then pick "try Ubuntu". Tell me if this works for you.

Hi, thanks for the reply. No that didn't work, but I think its my fault. I didn't accurately describe the problem in the original description. In the original, I said that the "try Ubuntu" was an option, but I was wrong, that wasn't the text. The text was "run Ubuntu from this USB device" or something like that. (Also, it was different looking than in most screenshots ive seen with the "try Ubuntu option", because those are in a popup like window.)

There were a few other options on that main screen I was at, but none of them seemed relevant (some were about installation, and one was advanced options, but there were no advanced options in the menu). Then, once I hit "run Ubuntu from this USB device" (or it may have said boot instead of run), then I saw lots of lines of text pop up, then some screwed up colors and lines, and then I heard the ubuntu sound. I tried to hit f6 then, but if it did anything, I couldn't tell (as the screen was all messed up.) -- (Also, when I press f6 at the "run Ubuntu from USB" menu, it just "blinks" but otherwise is the same menu. So i never got to see the "try Ubuntu" popup menu yet (other than screenshots). Sorry for not explaining it in my first post.

---

### Post by NightwishFan on 2010-10-05
The menu that is text only with minimal graphics right after the CD loads. You will need to press a key to access it when you see a white logo at the bottom. (If you do) It should say Try Ubuntu, Install Ubuntu ETC, with a bunch of options for f2 f3 f4 listed on the bottom. You need f6, and a menu should popup that says (for example) acpi=off noapic, you want the one called nomodeset.

---

### Post by redsaint182 on 2010-10-05
> **NightwishFan said:**
> The menu that is text only with minimal graphics right after the CD loads. You will need to press a key to access it when you see a white logo at the bottom. (If you do) It should say Try Ubuntu, Install Ubuntu ETC, with a bunch of options for f2 f3 f4 listed on the bottom. You need f6, and a menu should popup that says (for example) acpi=off noapic, you want the one called nomodeset.

I don't see that menu then. I just see a text menu that says "Boot Ubuntu from this USB" and "Install Ubuntu to the hard disk" or something, and "Advanced Options" and "Help". I didn't see any of those f2 f3 f4 options there, and once I click launch/run/boot Ubuntu from the USb, then it runs tons of text really fast, and the colors immediately mess up (there are no windows and no chances to press anything.) Now, in the help menu (which is text based, on a black screen) there are a bunch of f2 f3 f4 options. But I tried f6 and didn't see the thing you were talking about there.

---

### Post by redsaint182 on 2010-10-05
Actually, I did see something that said vga=277 noapic or something like that. but I didn't see anything that said nomodeset. Is "nomodeset" something I am going to have to type in on that menu?

---

### Post by NightwishFan on 2010-10-05
Hmm.. I am unsure how to get you there from what you describe. Did you by change make this usb boot with Unetbootin? If so that would explain it. I have no real idea how to edit boot options using that program.

The screen I speak of looks like this (colors may be different now)
[IMG]https://help.ubuntu.com/community/BootOptions?action=AttachFile&do=get&target=mainboot.png[/IMG]

---

### Post by NightwishFan on 2010-10-05
If that option is not in the sub menu, press esc once to get out of it and there should be a cursor in a box of text. Type nomodeset and then push enter to boot.

---

### Post by redsaint182 on 2010-10-05
Yeah, thats not quite the menu I see (though a couple of the options are similar.) On mine, the "help" is something you select with the dpad. Anyways, I'll try a couple other things, including the nomodeset boot thing if I can find out how to get to where you type it in at.

---

### Post by redsaint182 on 2010-10-05
I tried the nomodeset thing, and it didn't work. It wouldn't even boot. And I still can't get it to boot right, even after looking at a lot of the options. Still, its just some colors and lines, and no words or anything.

EDIT: Also, I made the USB install with Universal USB Installer: [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by beew on 2010-10-05
> **NightwishFan said:**
> Hmm.. I am unsure how to get you there from what you describe. Did you by change make this usb boot with Unetbootin? If so that would explain it. I have no real idea how to edit boot options using that program.

The screen I speak of looks like this (colors may be different now)
[IMG]https://help.ubuntu.com/community/BootOptions?action=AttachFile&do=get&target=mainboot.png[/IMG]

The boot screen for Lucid is just the word "Ubuntu" in a purple background with 5 orange dots, nothing that fancy so OP is not missing much. :)

---

### Post by beew on 2010-10-05
Well I had installed Ubuntu 10.04 on an Inspiron 8500 with a Nvidia card. When the usb booted, the graphic was totally off, the cursor wasn't quite working and yeah, there were some very big white stripes like the OP discribed. Basically unusable. 

This was fixed by a real installation when I installed the Nvidia driver (can't do it with a live usb with persistence, installing graphic card will break it)

If you have a Nvidia card IMO it is pointless to try the live usb because the quality of the graphics would be horrific (plus the touch pad/mouse may behave strangely, don't know why though). 

You can only fix the problem by installing the Nvidia driver but you can't do that with the live usb, installing graphic cards will break it. You need a real installation to install the graphic card.

Another option would be to do a full installation of  Ubuntu in an external hard drive (not a live usb, but a real installation) and then plug it into your computer to try it out. This way it is safe like running a live usb but at the same time allow you to install the Nvidia driver. If you do it try to get an external hard drive instead of a USB. While a 8 G (or even 4 g) usb would have enough room, it would be very slow if you have a real installation in it (as oppose to live with persistence)

---

### Post by redsaint182 on 2010-10-05
> **beew said:**
> Well I had installed Ubuntu 10.04 on an Inspiron 8500 with a Nvidia card. When the usb booted, the graphic was totally off, the cursor wasn't quite working and yeah, there were some very big white stripes like the OP discribed. Basically unusable. 

This was fixed by a real installation when I installed the Nvidia driver (can't do it with a live usb with persistence, installing graphic card will break it)

If you have a Nvidia card IMO it is pointless to try the live usb because the quality of the graphics would be horrific. You can fix it by installing the Nvidia driver in a real install but you can't do that with the live usb. Installing graphic cards will break it.

Another option would be to do a full installation of  Ubuntu in an external hard drive (not a live usb, but a real installation) and then plug it into your computer to try it out. This way it is safe like running a live usb but at the same time allow you to install the Nvidia driver. If you do it try to get an external hard drive instead of a USB. While a 8 G (or even 4 g) usb would have enough room, it would be very slow if you have a real installation in it (as oppose to live with persistence)

I do have an external hard drive, but it connects by USB. Would that be a problem? And, if I install it there, then would I still see the messed up interface I see now? Because, with the way it is now, I can't even see a cursor or anything, so I have no chance of even being able to install an Nvidia driver on a full install, if this same problem happens. I won't be able to see anything.

Edit: also, do you think it would work better if i tried that "Wubi" thing?

---

### Post by beew on 2010-10-05
> **redsaint182 said:**
> I do have an external hard drive, but it connects by USB. Would that be a problem? And, if I install it there, then would I still see the messed up interface I see now? Because, with the way it is now, I can't even see a cursor or anything, so I have no chance of even being able to install an Nvidia driver on a full install, if this same problem happens. I won't be able to see anything.

Connecting by usb is not a problem. Yes, you will see very mess up interface but then once you are in Ubuntu you can install the graphic driver and after that, reboot, then the world is beautiful. (My Inspiron actually looks really nice now once the Nvidia card was installed).

But you may need a second computer for the installation because you have to boot into a live usb first and then install Ubuntu in the external drive. Obviously you can't quite use the Inspiron with the Nvidia card.

**EDITED **Come to think of it the graphics in my Inspiron was very terrible when Windows XP booted initially as well (before the Nvidia card was installed) Though it was 10X worse with Ubuntu without the Nvidia driver. With XP the resolution was way off but with Ubuntu the resoulution of off and the interface was a mess.

---

### Post by redsaint182 on 2010-10-05
> **beew said:**
> Connecting by usb is not a problem. Yes, you will see very mess up interface but then once you are in Ubuntu you can install the graphic driver and after that, reboot, then the world is beautiful. (My Inspiron actually looks really nice now once the Nvidia card was installed).

But you may need a second computer for the installation because you have to boot into a live usb first and then install Ubuntu in the external drive. Obviously you can't quite use the Inspiron with the Nvidia card.

Am I just out of luck if I don't have a second computer to use? Cause I don't have one, and I don't really know how I am going to install the graphic driver.

---

### Post by beew on 2010-10-05
> **redsaint182 said:**
> Am I just out of luck if I don't have a second computer to use? Cause I don't have one, and I don't really know how I am going to install the graphic driver.

Well then you may want to try dual booting if you don't mind backing up your stuffs first. Just wrote a very long post to explain it but it was lost in the internet. I don't feel like retyping it now.

But basically;

You should have the windows install disk in case you want to remove Ubuntu later. Need that to fix the MBR (If you don't have one, there are ways to back up and restore your MBR but I don't know how, maybe others can help.

You should be connected to the internet during installation, use a wired connection instead of wireless as your wireless card may require proprietary drivers.

Once Ubuntu is up and running go to System > Administration > Hardware Drivers. It will do some scanning and then offer to activate the Nvidia card. Click yes and wait for it to do its things, when finished reboot and you should see nice graphics.

* I think you should download the iso image and make the usb again just to make sure the usb is not corrupted or anything. The easiest way 
[http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/]("http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/")

* If you have Windows Vista or Windows 7 instead of XP there may be a few extra things you need to do  to create the dual booting.,

---

### Post by redsaint182 on 2010-10-05
> **beew said:**
> Well then you may want to try dual booting if you don't mind backing up your stuffs first. Just wrote a very long post to explain it but it was lost in the internet. I don't feel like retyping it now.

But basically;

You should have the windows install disk in case you want to remove Ubuntu later. Need that to fix the MBR (If you don't have one, there are ways to back up and restore your MBR but I don't know how, maybe others can help.

You should be connected to the internet during installation, use a wired connection instead of wireless as your wireless card may require proprietary drivers.

Once Ubuntu is up and running go to System > Administration > Hardware Drivers. It will do some scanning and then offer to activate the Nvidia card. Click yes and wait for it to do its things, when finished reboot and you should see nice graphics.

* I think you should download the iso image and make the usb again just to make sure the usb is not corrupted or anything. The easiest way 
[http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/]("http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/")

* If you have Windows Vista or Windows 7 instead of XP there may be a few extra things you need to do  to create the dual booting.,

I just used Wubi, and made a dual boot (at least I think I did. I can choose between Vista and Ubuntu at startup now.) ANyways, there is a 0% chance of me being able to click system > administration >hardware drivers. I cannot even make out a desktop. All I see is a solid blue/purplish color, and a thick vertical white stripe down the screen, a little to the right of the center :( 

I guess maybe no Ubuntu for me? I might just save up and get a mac (I don't like windows.) 

Anyways, thanks to both of you for your posts, even though my problem isn't fixed, I appreciate the effort in helping :)

I'll look around a bit and see if anyone else has a fix for this problem, but I haven't been able to find anything yet...

---

### Post by TCHebb on 2010-10-05
Are you sure you're using a 10.04 desktop edition USB drive? From the menus you describe, it sounds like you've got an older version. 10.04 works fine out of the box on nVidia cards (no 3D acceleration of course, but that doesn't matter for just installing).

---

### Post by redsaint182 on 2010-10-05
> **TCHebb said:**
> Are you sure you're using a 10.04 desktop edition USB drive? From the menus you describe, it sounds like you've got an older version. 10.04 works fine out of the box on nVidia cards (no 3D acceleration of course, but that doesn't matter for just installing).

Well, the ISO I used (downloaded from the Ubuntu site) says "ubuntu-10.04.1-desktop-i386"

---

### Post by S.R on 2010-10-05
Doing an amateur dual boot install is pretty is easy to deal with. My recommendation is the following:

1. Burn the install to disc.
2. Disconnect your internal hard drive (Kind of hard to muck something up that isn't attached.)
3. Attach external.
4. Set your BIOS to boot from CD
5. Once install is complete and Ubuntu is set then reconnect internal hard drive and set BIOS to boot options to USB then HDD then CD (or CD first if you prefer)

From there when you boot if the external is not attached it will boot from the HDD if it is attached it will boot GRUB and you will have the option of booting to windows.

---

### Post by TCHebb on 2010-10-05
Could you take a picture of the selection menu and one of what you see after you hear the startup sound and post them here?

---

### Post by redsaint182 on 2010-10-05
> **TCHebb said:**
> Could you take a picture of the selection menu and one of what you see after you hear the startup sound and post them here?

Hi, I'll try and post some as soon as I can. I just tried, but now I have a new set of problems. It isn't even trying to boot from the USB anymore, and instead is going to windows. And, since trying the Wubi thing, I think my windows may be a tad messed up (cause I can't uninstall the Ubuntu that I installed via Wubi now, I get an error.) Anyways, will be back in a little bit when I can get some pics...

EDIT: I think I can solve the "cannot uninstall Ubuntu" problem though. But yeah, I'll get back with some pics when I can of the USB boot problem.

EDIT 2: I'm also going to make the reformat the USB drive and put the installer back on their over again, and see if that helps at all.

---

### Post by redsaint182 on 2010-10-05
Okay, here are the pics. Pic 1 is of the start screen the next one is what it looks like soon after running Ubuntu from the USB (after the text scrolls,) and then a few seconds after that pic, the last pic comes in along with the Ubuntu music, and it just sits there like that forever.

Someone else on youtube mentioned the f6 "nomodeset" thing and linked to this page: [http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html) . But again, that menu with that option isn't the one I have. Someone here mentioned I may not have 10.04, and it kind of looks that way, but the file I got came from ubuntu's official site, and it says on the file name of the iso "10.04.1" so idk... anyways, hopefully the pics will help.

Hope to hear from you soon, take care! :)

EDIT: I tried pressing tab on the first entry, and typing "nomodeset" there, but still no dice. Same end result.

---

### Post by TCHebb on 2010-10-05
Can you describe the screens that you see before you get to the menu? Sorry for asking so many questions, I'm just trying to understand what exactly is happening.

---

### Post by redsaint182 on 2010-10-05
> **TCHebb said:**
> Can you describe the screens that you see before you get to the menu? Sorry for asking so many questions, I'm just trying to understand what exactly is happening.

Well, starting from when I turn my computer on, its the Dell logo, and it loads up (and I can press f2 for settings and all that, which I usually do, to select the USB drive for starting before the HDD), and then once I select the USb drive and save it, then it is black for a few seconds, and then it goes to the screen in Pic 1.

---

### Post by redsaint182 on 2010-10-05
SOLVED!

okay, here is what I did. At the screen in Pic 1, I pressed tab on the first option, and then entered " nouveau.modset=0" (make sure the space is there), and then I can see the desktop like I am supposed to. Thanks for everyone that responded in the thread! The response time in the linux community is really great haha.

The guy who helped me do this can be found here: [http://www.youtube.com/user/thisweekinlinux](http://www.youtube.com/user/thisweekinlinux) I figured I should plug his youtube channel since he helped out... he knows his stuff!

Thanks again guys.

---

### Post by waynefoutz on 2010-10-05
glad it worked

---

