---
title: "Alcatel Speedtouch USB ADSL using PPPoA - firmware loads and then authentication fail"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by samadams on 2006-11-14
I'm using a green (revision 0) 'stingray' Alcatel Speedtouch USB ADSL modem.  My service provider is Bellsouth, thus I need to use PPPoA and a 8,35 VPI/VCI.  I'm using Dapper 6.06 LTS. (note - on my XP bootup, I never could get the Speedtouch to work either [it worked fine under win98, but not under XP] I have to use an Intel Pro/DSL 3200 USB modem which from what I can find is not compatible with Linux.  The Speedtouch is my only other option for an internet connection - I really don't want to have to buy another piece of hardware if I can avoid it)

I have followed the [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html) instructions to the letter.  I used the instructions on [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html) to extract the firmware.  I tried *_**both**_* sets of firmware with the exact same results.  Nada.

Here's what happens:

Initially, left light is flashing red, right light is off.
Upon boot, after the file system is mounted, both lights go solid green.  They stay solid until the network hardware is loaded then they both blink once together and then remain solid green.

That's it.

Upon examining the [FONT=Fixedsys]syslog[/FONT] and [FONT=Fixedsys]messages[/FONT] files this is what I find:

Both firmware files were found ([FONT=Fixedsys]speedtch-1.bin[/FONT] and [FONT=Fixedsys]speedtch-2.bin[/FONT])
sometimes there is an entry for [FONT=Fixedsys]pppd[/FONT], sometimes not.  If there is, it says [COLOR=Red]"authentication failed"[/COLOR].  (even though I used the [FONT=Courier New][COLOR=Blue]noauth[/COLOR][/FONT] command in my [FONT=Fixedsys]speedtch[/FONT] script)  [FONT=Fixedsys][FONT=Verdana]Additionally[/FONT] ntp[/FONT] reports that *ntp.ubuntu.org* cannot be found.  Also [FONT=Fixedsys]DHCP[/FONT] persistently is trying to do something with [FONT=Fixedsys]eth0[/FONT] - why, I don't know.  (yes I did use [FONT=Courier New][COLOR=Blue]defaultroute[/COLOR][/FONT] and [FONT=Courier New][COLOR=Blue]pppoatm.so[/COLOR][/FONT] in my script just as the instructions said to)

I followed those instructions EXACTLY; four times.  All to no avail.

My *username@isp* is correct in both my [FONT=Fixedsys]speedtch[/FONT] file and in the [FONT=Fixedsys]pap[/FONT] & [FONT=Fixedsys]chap secrets[/FONT] files.

My login password is correct.

The files are stored where the instructions say for them to be stored.

The links are all made correctly. (as far as I can tell, I issued the commands but how does one check if the link is there?)

Interestingly there is a file in /etc/ppp/ called [FONT=Fixedsys]pppoe on boot.  [FONT=Verdana]I didn't put it there and I don't know if it is being run or not.  It has a [FONT=Courier New][COLOR=Blue]modprobe pppoe[/COLOR][/FONT] command in it.  Just thought I'd let you know.  Could it be that this file is executing after my [FONT=Fixedsys]speedtch[/FONT] script, thus negating my [FONT=Courier New][COLOR=Blue]modprobe pppoatm[/COLOR][/FONT] command?

Also, I read elsewhere that I can dial manually using the PPPoA dialer in Applications>System Tools.  However, 'System Tools' does not exist as an entry in my Applications menu.  (ubuntu was installed direct from the CD with no errors in case you were wondering)  How do I get it there?

I tried to go to Administration>Networking to tell ubuntu to 'dial' using my USB modem as I have to do in Windows XP - but Networking will not list anything but my regular fax/modem as available hardware - even using the auto detect option.  **In networking I have a [FONT=Fixedsys]eth0[/FONT] connection and [FONT=Fixedsys]pppoa[/FONT] connection visible.  Everytime I startup - no matter what settings I make in networking, they default to [FONT=Fixedsys]eth0[/FONT] being active and [FONT=Fixedsys]pppoa[/FONT] being inactive.  [FONT=Fixedsys]pppoa[/FONT] is where I attempted to instruct the USB modem to dial, but it was not on the hardware list.

I tried to manually call [FONT=Fixedsys]speedtch[/FONT] via the terminal.  However, I need to be [FONT=Arial Black][COLOR=Red]root[/COLOR][/FONT] to do so.  When using [FONT=Courier New][COLOR=Blue]sudo[/COLOR][/FONT] to set up the modem, all went well, I was asked for my password the first time, and that was it.  But when attempting to issue a [FONT=Courier New][COLOR=Blue]sudo call speedtch[/COLOR][/FONT] command, I am asked for my password, and everytime it responds "Authentication Failed.  Sorry."  What gives?  Any ideas? ](*,)
[/FONT][/FONT]

---

### Post by fishpie on 2006-11-15
> 
I tried to manually call speedtch via the terminal. However, I need to be root to do so. When using sudo to set up the modem, all went well, I was asked for my password the first time, and that was it. But when attempting to issue a sudo call speedtch command, I am asked for my password, and everytime it responds "Authentication Failed. Sorry." What gives? Any ideas?
Reply With Quote
I'm assuming you mean ' sudo pppd call speedtch' rather than 'sudo call speedtch'. Due to the fact that sudo is asking for a password each time the "Authentication Failed. Sorry." message appears to be coming from the sudo command rather than the pppd command. Try the following
```
sudo su
```
enter your password at the password prompt.  You should now be presented with the root command prompt which should look something like "root@computername:/home/user#" Every command that you type now will run with superuser privileges i.e.  as though preceded by 'sudo' although no password will be required. BE VERY CAREFUL. Now type 'pppd call speedtch' and post the exact result here and I'll try to help. now type 'logout' 'exit' or hold ctrl and press 'd' to return to the normal prompt.

---

### Post by samadams on 2006-11-18
Thanks fishpie for the reply.   I've been out of town, so I'm just getting back to this tonight.   I tried going root by the method you suggested and it worked, though for some reason, I still get the [FONT=Courier New][COLOR=Blue]Authentication Failed[/COLOR][/FONT] message when trying to do it all in one step.   Puzzling...  Also, yes I was typing the '[FONT=Courier New][COLOR=Blue]pppd[/COLOR][/FONT]' first, I just missed it when I posted this query.   So I did as you suggested and here's what I got:

[FONT=Courier New][COLOR=Blue]plugin pppoatm.so loaded.
connect (8.35): No such device
[/COLOR][/FONT]
Also, this time in [FONT=Fixedsys]syslog[/FONT] and [FONT=Fixedsys]messages[/FONT] there are entries for [FONT=Courier New][COLOR=Blue]pppd[/COLOR][/FONT] that never appeared before.  They are the same as the one above except just before them is the message [FONT=Courier New][COLOR=Blue]pppd: connect script failed[/COLOR][/FONT]

The FAQ on the HowTo page I used notes this error and that it has something to do with the kernel not being compiled correctly, but it gives no solution.   Unfortunately, I don't know enough yet about Linux to know where to begin on this.   Any advice?

---

### Post by fishpie on 2006-11-19
> 
plugin pppoatm.so loaded.
 connect (8.35): No such device


If pppd cannot find your modem then the problem is probably to do with the firmware

> The FAQ on the HowTo page I used notes this error and that it has something to do with the kernel not being compiled correctly

The faq says:
> this means that your speedtouch kernel module is not correctly configured or that the firmware didn't load. Did the lights flash?
Unless you are using some sort of non-standard kernel then this is a firmware problem. Did you try my previous advice with both firmwares? I should have told you to in my previous post. Looking back you say:
> they both blink once together and then remain solid greeitially, left light is flashing red, right light is off.
 Upon boot, after the file system is mounted, both lights go solid green. They stay solid until the network hardware is loaded then  they both blink once together and then remain solid green.
When a piece of firmware loads onto the modem you should see the left led solid green while the right led flashes green
are you trying with both the KQD6_3.012 firmware and the mgmt.o firmware? are the LED sequences and the error messages identical for both pieces of firmware?

---

### Post by samadams on 2006-11-20
I've tried to bring up the modem both manually and through startup for both pieces of firmware several times, I even tried the revision 4 firmware as well - all with the same results.  I even tried them all again several times each after your post just for kicks.  Still the same result.

I also tried booting up without the modem attached and then attaching it afterwards.  The only difference is that I got notes in sysylog that 'main' had an error loading the firmware.  Then it states that the firmware is found.  But that's it.  I still get 'No Such device' when manually attempting to connect and still get 'connect script failed' in syslog when doing so through the boot process.  When the modem is plugged in through the boot I never get an error that the firmware failed to load.  I don't always even get the 'connect script failed' message from pppd.  Sometimes it tells me that, sometimes it doesn't.

The only other difference was when I tried the revision 4 firmware, I got a pop up error message from Linux saying HAL failed to load.  During that session, my DVD-ROM, and Floppy were not visible nor accessible, nor were a windows restore partition or my main linux partition visible.  (I still had access to my hd via the 'file system' icon in 'computer' though. I guess that firmware is definitely a no-go.)

I also noticed that syslog messages (for the entire boot process) are not always the exact same each bootup even if I didn't change anything.  I know this is another topic, but might this have something to do with the firmware not being loaded?  Are things possibly, for some strange reason, not occuring in the proper order?  Shouldn't the boot process be exactly the same every single time if no changes have been made to the system?

I don't think that the modem doesn't like the firmware.  It's as if Linux can't find the firmware or the device at all it when it tries to load it. (then it finds it but doesn't re-attempt to load it)

I tried to re-extract the firmware via the instructions in [http://www.linux-usb.org/SpeedTouch/firmware/index.html](http://www.linux-usb.org/SpeedTouch/firmware/index.html).  But it never worked - I kept getting the error that './configure was not a directory'.  So I just used the method described in the original HowTo for splitting the files in to speedtch-1.bin and speedtch-2.bin.  I also read something on the bottom of that firmware-extractor page about worrying about "udev" if I manually compiled it (which to my knowledge I have not) so I didn't bother more with it, but could something there (udev) be the cause of this?

---

### Post by samadams on 2006-11-20
I just thought of something.  Are these firmware files, the KDQ6_3.012 and the mgmt.o, for the ***ALCATEL*** Speedtouch modem?  or are they for some *other *brand? (I've seen references to a different brand of speedtouch in the forums)  Mine is a sort of Aqua color and looks like a stingray. (not at all what the one on the HowTo page looks like)  Just curious.

---

### Post by fishpie on 2006-11-21
Yes those firmwares are for the alcatel speedtouch

---

### Post by samadams on 2006-11-21
Okay, so where to now?  I've tried all of the firmware under various circumstances as I indicated above.  All with the same results.  (Did you notice I had two posts back to back?) So does this look like a problem with the firmware or the kernel?  (since it fails to load the firmware, then finds it but doesn't attempt to re-load it - and since the syslog is different at every boot even if nothing is changed in the system) Is udev an issue here?

Oh, and when I started up my system this morning, it didn't give me the GRUB allowing me to dual boot into XP - it just went straight to Ubuntu.  After I did a restart however, I got GRUB back.  I sense some instability issues here.

---

### Post by fishpie on 2006-11-22
> Did you notice I had two posts back to back?
Oops, no I didn't

>  I also tried booting up without the modem attached and then attaching it afterwards. The only difference is that I got notes in sysylog that 'main' had an error loading the firmware. Then it states that the firmware is found.
I used to get this with Dapper as well.  The error messages are because the firmware helper doesn't find the firmware files where it first looks. This doesn't matter since it still manages to find the firmware files. Changing the names of the firmware files should get rid of the error messages, but is probably best left until after you get the modem working.

> I also noticed that syslog messages (for the entire boot process) are not always the exact same each bootup even if I didn't change anything. I know this is another topic, but might this have something to do with the firmware not being loaded? Are things possibly, for some strange reason, not occuring in the proper order? Shouldn't the boot process be exactly the same every single time if no changes have been made to the system?
I think the bootup should be broadly the same every time. I don't think that small variations are necessarily anything to worry about.

> I tried to re-extract the firmware via the instructions in [http://www.linux-usb.org/SpeedTouch/firmware/index.html](http://www.linux-usb.org/SpeedTouch/firmware/index.html)
These instructions involve compiling the firmware-extractor from source. This should nor be necessary since you should have already downloaded the firmware-extractor binary and used it for the original extraction 



> Okay, so where to now? I've tried all of the firmware under various circumstances as I indicated above. All with the same results. (Did you notice I had two posts back to back?) So does this look like a problem with the firmware or the kernel?
Definitely the firmware.  I notice the instructions for using the mgmt.o firmware are not clear. You should have done something like this download the [http://download.ethomson.com/download/speedmgmt.tar.gz]("http://download.ethomson.com/download/speedmgmt.tar.gz")speedmgmt.tar.gz [http://download.ethomson.com/download/speedmgmt.tar.gz](http://download.ethomson.com/download/speedmgmt.tar.gz) file and place it in the same directory as the firmware_extractor file. then try the following
```
tar xvzf speedmgmt.tar.gz
cd mgmt
../firmware-extractor mgmt.o
sudo cp speedtch-* /lib/firmware/

```
And reboot

If having done this you are still having the same problem I have found another firmware file that might work with your modem download the following file and place it in the same directory as the firmware extractor [http://steve-parker.org/speedtouchconf/firmware/alcaudsl.sys]("http://steve-parker.org/speedtouchconf/firmware/alcaudsl.sys")
then try this
```
./firmware-extractor alcaudsl.sys
sudo cp speedtouch* /lib/firmware/

```
And reboot

> Oh, and when I started up my system this morning, it didn't give me the GRUB allowing me to dual boot into XP - it just went straight to Ubuntu. After I did a restart however, I got GRUB back. I sense some instability issues here.
The grub menu will will only appear for a few seconds if a key isn't pressed it will boot Ubuntu. I am confident that this is a firmware problem and not a kernel, udev, or boot script problem that you are experiencing. Many people who use these forums including me have managed to get there speedtouch moodems working with Dapper using the normal Dapper kernel. I feel confident that if you follow the advice in this post then one of the firmware files will work for you. Once you get the modem to work creating the following soft links should remove the error message from your syslog
```
cd /lib/firmware
sudo ln -s speedtch-1.bin speedtch-1.bin.2.00
sudo ln -s speedtch-2.bin speedtch-2.bin.2.00

```

---

### Post by samadams on 2006-11-25
Sorry I didn't get back to you sooner.  I've been out of town for Thanksgiving.

So I tried your last advice.  I re-unzipped the mgmt.o version and copied the appropriate files to [FONT=Fixedsys]/lib/firmware.[/FONT]  I got the same results as before.  I tried the new firmware you suggested - [FONT=Fixedsys]alcaudsl[/FONT] - with the same results. I even tried the renaming bit at the end with all three firmware versions,  I still get [FONT=Courier New][COLOR=Blue]"No Such Device."[/COLOR][/FONT]

Is there a way I can manually load the firmware after boot rather than letting Linux do it automatically?  I could understand if I got an error telling me the firmware didnt load.  But a "No Such Device" seems like another problem.  (or maybe Linux just isn't very clear or intuitive on its error messages)  I interpret the "No Such Device" to mean it doesn't even see the modem on the USB port.  Yet in syslog it identified the modem just fine and then told me it found the firmware.  The modem also shows up in my hardware profiles.  (though it never confirms that the firmware was loaded correctly, or otherwise)  It also doesn't give me an error that the connect script failed until after I manually call [FONT=Fixedsys]speedtch[/FONT].  Shouldn't I get this error when the system calls it but it fails due to the above firmware problem?  Or does this mean that [FONT=Fixedsys]speedtch[/FONT] isn't being called by Linux?  In that case, how do I know [FONT=Fixedsys]Dial[/FONT] even got executed.  I never see any messages for that one either.

Oh and a side note, though the situation hasn't repeated itself yet, I really didn't get GRUB that one time.  I was specifically sitting there waiting for it so I could log in under XP.  The bios precedures ran, then the screen went blank for a few seconds, then Ubuntu came up - No Grub.  Unless for some weird reason it decided not to echo anything to the screen that one time.  Strange.

If none of this applies and this is still a firmware issue, is it possible to somehow convert or use the windows drivers located on the modem's installation disk?

---

### Post by samadams on 2007-01-20
UPDATE - nothing to update.  I've been busy, so I abandoned ubuntu for the most part for now.  That's really ashame.  I like how it works, and I'd rather use it than XP, but with no internet connection or built-in support for mp3 playback - I won't bother for now.  I'm not sure where 'fishpie' went or if anyone else is reading this thread that could help me.

I was browsing at the bookstore the other day and came across some instructions for getting the alcatel up and running.  Unfortunately, I didn't have the $40 to take the book home or even a pen handy to write anything down.  What I do remember though is that the instructions referred to a file called 'modem run.'  There is no mention of this file or associated steps in the tutorials I used. (referenced above)

Is this file used in older distros of Ubuntu or is it vital to getting the modem working?

Any ideas?

---

### Post by samadams on 2007-02-15
UPDATE - With the excellent help of Duncan Sands at Alcatel I now have my Stingray up and dialed in on pppoatm. Apparently some modems need 512 bytes from something else first before they will dial in.  Weird.  I'm trying to figure out how to work those commands into my dialup script but they do work - almost.   I still cannot surf the web or send email or use any other web application.  I'm told this is a DNS problem, but I have no idea how to resolve this or where to start.  I've stumbled across this issue on this forum before but can't find it now for anything in the world.

Anyone know how to begin tackling this one?

---

