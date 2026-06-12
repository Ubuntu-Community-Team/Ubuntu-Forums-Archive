---
title: "Installing to Pen Drive"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by Budfudder on 2011-05-07
I'm running 64-bit Windows 7 on an HP Pavilion dv7 Notebook PC with 6.00 GB of ram and processor is Intel(R) Core (TM) i7 CPU Q720 @1.60GHz 1.60GHz.

I'm a complete newbie to Ubuntu and just installed Ubuntu 11.04 to a pen drive to test it out and booted my notebook using it. I rebooted several times, with varied results:

**First boot**
Ubuntu didn't boot. Got to a terminal session showing the following text:

[FONT=Courier New]BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs) Unable to find a medium containing a live file system
[/FONT]
I rebooted by switching the machine off.

**Second boot** appeared to work, but booted to Gnome, not Unity.

I opened Help and system locked up.

I rebooted by switching the machine off.

**Third boot** worked okay (booted to Gnome again), and I created a new user. I rebooted correctly (using the system shutdown menu).

**Fourth boot** while booting got a dialog box showing error:

[FONT=Courier New]Could not updaet ICEauthority file /var/lib/gdm/.ICEauthority[/FONT]

The only option was Close.

Then I got a dialog box showing error:

[FONT=Courier New]There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)[/FONT]

Only option was Close.

Then, in the top right-hand corner a message appeared:

[FONT=Courier New]Could not apply the stored configuration for monitors. Failed to open file '/var/lib/gdm/sconfig/monitors.xml': Input/output error[/FONT]

There was no option to dismiss the message - it just faded by itself.

Eventually booted up and I turned on the setting to show Logon window.

Shutdown using the system shutdown menu. As I shut down the same messages were shown as on boot up.

**Fifth boot** - did not boot.  Got to a terminal session showing the following text:

[FONT=Courier New]BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs) Unable to find a medium containing a live file system[/FONT]

Rebooted by turning the machine off.

After that, it booted with the same messages shown as during the fourth boot.

Obviously there's something wrong - or I've done something wrong. Does anyone have any suggestions as to what I've done wrong/how to fix it?

Thanks in advance for any help.

---

### Post by wigout on 2011-05-07
Sorry for your troubles.

What method did you use to install 11.04 to the pendrive?

-wigout

---

### Post by Budfudder on 2011-05-07
I installed Ubuntu to my pen drive using the Universal USB Installer, which I downloaded from [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/).

I used the 11.04 32-bit ISO which I downloaded from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download).

Note that I have a 64-bit Windows OS, but I installed the 32-bit ISO. From what I read that was the correct one to use on a Windows 64-bit OS.

Thanks for your help.

---

### Post by Budfudder on 2011-05-08
A bit of further information:

Today I took the pendrive to work to try it on my two work laptops.

On the first laptop (a Compaq nc6220 running 32-bit Windows XP):

Ubuntu booted and I got the same 3 error messages I got on my personal laptop during the boot process:

Could not update ICEauthority file /var/lib/gdm/.ICEauthority

There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

Could not apply the stored configuration for monitors. Failed to open file '/var/lib/gdm/sconfig/monitors.xml': Input/output error

The boot process continued and when it finished I had the Ubuntu desktop background - and nothing else. No windows, no bars, nothing. If I clicked on the desktop I got the same menu I normally get when I do that, but there was nothing else at all on the desktop.

On the second laptop (a HP EliteBook 6930p with 3GB RAM and processor: Intel(R) Core(TM)2 Duo CPU P8400 @ 2.26GHz 2.27GHz):

I got exactly the same result I got on my other work laptop. 3 error messages then a blank Ubuntu screen. In addition, on this machine I got problems with Ubuntu apparently not being able to work out the monitor screen size - it came up only using part of the screen (big black spaces on each side). But next time I booted on that same laptop, it had worked out the monitor screen size (still got the same 3 errors).

Any information that can help would be greatly appreciated. Being very new to Linux in general and Ubuntu in particular, I'm really lost.

---

### Post by dwhite on 2011-05-08
i tried many times to install  11.04 on a usb with the **pendrivelinux installer...it never worked** always had the same issues you are having (i was using a computer running windows 7 also). Use the "startup disk creator" in ubuntu to make your usb and it will work very smoothly

rereading your first post it occurs to me you don't have ubuntu up and running so you won't have access to the startup disk creator, if you are looking to try ubuntu out without installing my suggestion would be to burn the iso to a dvd rather than the pendrive, or if you know someone running ubuntu have them download the 11.04 .iso and put it on the usb using the "startup disk creator" program.

---

### Post by Redblade20XX on 2011-05-08
Dude try unetbootin to install 11.04 on a usb driver! Google it! Good luck!

---

### Post by Budfudder on 2011-05-09
> **Redblade20XX said:**
> Dude try unetbootin to install 11.04 on a usb driver! Google it! Good luck!
I tried it - sadly, it made no difference. The new installation was as buggy as the previous ones made with the Universal USB Installer.

---

### Post by Budfudder on 2011-05-09
> **dwhite said:**
> i tried many times to install  11.04 on a usb with the **pendrivelinux installer...it never worked** always had the same issues you are having (i was using a computer running windows 7 also). Use the "startup disk creator" in ubuntu to make your usb and it will work very smoothly

rereading your first post it occurs to me you don't have ubuntu up and running so you won't have access to the startup disk creator, if you are looking to try ubuntu out without installing my suggestion would be to burn the iso to a dvd rather than the pendrive, or if you know someone running ubuntu have them download the 11.04 .iso and put it on the usb using the "startup disk creator" program.
Thanks for your suggestion. I was able to get my USB Ubuntu working long enough to use the "startup disk creator" to make another USB. However, when I boot from that one, I get a large screen which gives the option to either Install Ubuntu or Try it. When I select the Try it option, it takes a good 10 minutes more to boot. I've no idea what it's doing for that 10 minutes.

I'm starting to think that perhaps the problem is the 11.04 iso? Perhaps that's why the USB I created from my USB Ubuntu had the "Install/Try" option? Is there a version of 11.04 that I can put on my USB that doesn't have any of the "Install" option anywhere? All I want to do is install and run it from a USB. That's it. I don't want to install it from that USB later.

I must confess that I'm pretty disappointed in Ubuntu at this stage. When I first found that I could install it to USB to try it out I was overjoyed - but that idea is fast turning sour. It's looking more and more like I can't try out Ubuntu without a full install - and (particularly given how badly the USB install works) I'm not going to do that, that's for sure.

---

### Post by Budfudder on 2011-05-09
After a fair bit of experimentation, I've come to believe that many of the problems I've been having were due to using the USB on a 64-bit OS. At work I've repeatedly re-installed Ubuntu on my USB drives and booted using them (on 2 32-bit machines), and haven't got a repeat of the problems I noted earlier.

However, I now consistently get the problem that the machine just locks up at random times. Sometimes during startup (showing the login panel), sometimes after startup, when Ubuntu is fully booted. No special circumstances, it just seems to happen randomly. The keyboard will still work, but the system ignores all mouse input.

---

### Post by Dreigo42 on 2011-05-09
From my knowledge, the startup disk creator in Ubuntu burns the iso to the USB for startup and installation. If you want a working install on the usb, you would have to install it on the usb and ensure (and this is critical) that GRUB is installed on the usb. You would then boot the computer from the USB drive. I have played with this on and off and I have yet to find a perfect setup. 

Note: If you don't specify Grub to install on the USB it will install it on your current boot drive and overwrite any boot loader that is currently there. Made this mistake and then could boot the native windows install that I had on the computer previously.

---

### Post by Budfudder on 2011-05-09
> **Dreigo42 said:**
> From my knowledge, the startup disk creator in Ubuntu burns the iso to the USB for startup and installation. If you want a working install on the usb, you would have to install it on the usb and ensure (and this is critical) that GRUB is installed on the usb. You would then boot the computer from the USB drive. I have played with this on and off and I have yet to find a perfect setup. 

Note: If you don't specify Grub to install on the USB it will install it on your current boot drive and overwrite any boot loader that is currently there. Made this mistake and then could boot the native windows install that I had on the computer previously.
So is there any way I can just get a Ubuntu installation on my USB drive that actually works? I don't want to be able to install from it, I just want the damn thing to work!

---

### Post by Dreigo42 on 2011-05-09
The process of installing it to a USB is a bit tricky and doesn't always work. Like I said, I have never had a perfectly working install on a USB drive. But what you would have to do is burn the installation .iso file to a CD or DVD and boot from that and then, in the install process, select the USB drive as the install location and make sure that GRUB is being installed on the USB otherwise it will overwrite the Boot loader on the computer you are using. This is a tricky operation and I wouldn't recommend it without extreme caution.

What would be nice is a "Ubuntu Portable" or "Ubuntu USB" that was designed for something like this because I have found that it is usually the changes in hardware that keep this type of install from working well.

---

### Post by Budfudder on 2011-05-09
> **Dreigo42 said:**
> The process of installing it to a USB is a bit tricky and doesn't always work. Like I said, I have never had a perfectly working install on a USB drive. But what you would have to do is burn the installation .iso file to a CD or DVD and boot from that and then, in the install process, select the USB drive as the install location and make sure that GRUB is being installed on the USB otherwise it will overwrite the Boot loader on the computer you are using. This is a tricky operation and I wouldn't recommend it without extreme caution.

What would be nice is a "Ubuntu Portable" or "Ubuntu USB" that was designed for something like this because I have found that it is usually the changes in hardware that keep this type of install from working well.
I'm starting to think that that was my problem - I thought that this was "Ubuntu Portable". So I guess I'm expecting things of it that aren't the case.

Thanks a lot for your help.

---

### Post by Dreigo42 on 2011-05-09
Yea, sadly there hasn't been one created that I am aware of.

---

### Post by dwhite on 2011-05-09
> **Budfudder said:**
> 
I'm starting to think that perhaps the problem is the 11.04 iso? Perhaps that's why the USB I created from my USB Ubuntu had the "Install/Try" option? Is there a version of 11.04 that I can put on my USB that doesn't have any of the "Install" option anywhere? All I want to do is install and run it from a USB. That's it. I don't want to install it from that USB later.

I must confess that I'm pretty disappointed in Ubuntu at this stage. When I first found that I could install it to USB to try it out I was overjoyed - but that idea is fast turning sour. It's looking more and more like I can't try out Ubuntu without a full install - and (particularly given how badly the USB install works) I'm not going to do that, that's for sure.

yes 10 minutes is too long, and it is possible the iso is corrupt (i don't understand why there isn't a checksum of somesort to check the integrity of the download from ubuntu like there is when downloading linux mint for example), and yes i wouldn't do a full install until you have tried it out and are happy.

i've had a nice experience running ubuntu this past year and wish you the same, all i can say is that something is amiss, i'm not sure what and you don't want to get burned out banging your head against the wall ](*,) so maybe try a new approach (i've not used it but the unetbootin website that was suggested by Redblade20XX earlier looks good) alternatively you could buy a preloaded usb or a cd from canonical at [http://shop.canonical.com/](http://shop.canonical.com/)  or from [http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu?ad=google&gclid=CMyC-q-q3KgCFUOo4Aod-iTAxw](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu?ad=google&gclid=CMyC-q-q3KgCFUOo4Aod-iTAxw) or somewhere else  that you could be pretty darn sure would work, just sit back don't worry and in a few days be able to try it out without the pain... anyway good luck, it shouldn't be this hard, relax and don't get overly frustrated if you can help it.

oh ... as far as i've seen you always have the install option, although someone else may know better
and i've had my ubuntu running from my usb on about 4 different machines now, it's a bit slow but kind of like ubuntu portable, if you give it some persistent memory also saves your preferences and bookmarks

---

### Post by Budfudder on 2011-05-10
Thanks for all who've made suggestions. I think I may have found the problem. I created a user. A bit of testing reveals that as soon as I create a user (other than the default 'ubuntu' user) and set it up to force the user to login, Ubuntu starts locking up.

Does that sound at all familiar to anyone? It seems very strange to me, but I've been working on Ubuntu now for a couple of hours quite happily - with no user created.

---

### Post by wigout on 2011-05-10
Sort of familiar-

I've ran "live" usb versions of fedora and ubuntu- and I was always a "default" user. I am glad you've got it working. When my pc has crashed, booting to live usb (or live usb's with persistent memory) has kept me going.

-wigout

---

