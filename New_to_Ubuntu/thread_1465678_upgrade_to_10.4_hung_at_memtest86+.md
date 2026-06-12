---
title: "upgrade to 10.4 hung at memtest86+"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by chirpis on 2010-04-29
Hey guys.
I'm using wubi on an Acer Aspire 6530. I just tried to upgrade from 9.10 to 10.4. After a couple of hours of downloading and half an hour of installation, the whole thing hung at "Preparing memtest86+". The terminal readout showed several lines of "found linux image: /boot/vmlinuz-2.6.32-21-generic". After waiting a while to see if it would progress any further, I restarted. Now I can't boot into ubuntu at all. I'm pretty upset. :(

---

### Post by chirpis on 2010-04-29
Hey guys.
I'm using wubi on an Acer Aspire 6530. I just tried to upgrade from 9.10 to 10.4. After a couple of hours of downloading and half an hour of installation, the whole thing hung at "Preparing memtest86+". The terminal readout showed several lines of "found linux image: /boot/vmlinuz-2.6.32-21-generic". After waiting a while to see if it would progress any further, I restarted. Now I can't boot into ubuntu at all. I'm pretty upset. :sad:

---

### Post by P4man on 2010-04-29
I take it its a wubi install? If so you are not alone:
[http://ubuntuforums.org/showthread.php?t=1465491](http://ubuntuforums.org/showthread.php?t=1465491)

---

### Post by madjr on 2010-04-29
hmm, upgrades are never too reliable, and less with wubi

before any upgrade you're advised to backup your stuff, i hope you did

you should had deleted your 9.10 wubi install and then install the wubi 10.04

---

### Post by chirpis on 2010-04-29
Hmm, doesn't sound good. :(  Thanks for replying, though.

---

### Post by arrrghhh on 2010-04-29
> **chirpis said:**
> Hey guys.
I'm using wubi on an Acer Aspire 6530. I just tried to upgrade from 9.10 to 10.4. After a couple of hours of downloading and half an hour of installation, the whole thing hung at "Preparing memtest86+". The terminal readout showed several lines of "found linux image: /boot/vmlinuz-2.6.32-21-generic". After waiting a while to see if it would progress any further, I restarted. Now I can't boot into ubuntu at all. I'm pretty upset. :(

Wubi is really just a way to "discover" Ubuntu.  I didn't think it was meant to be run as a permanent solution, especially not one that's updated to a new distro... is it?

---

### Post by cariboo on 2010-04-29
Do you get a grub menu at all, If you have a single boot system, you won't see grub, unless you hold down the shift key during the boot process. If you don't see a grub menu, you can boot from a live cd, Karmic or newer and repair grub following the [instructions]("https://wiki.ubuntu.com/Grub2") here. Scroll down to Recover Grub 2 via LiveCD.

---

### Post by zeroseven0183 on 2010-04-29
This is a duplicate post to [http://ubuntuforums.org/showthread.php?t=1465678](http://ubuntuforums.org/showthread.php?t=1465678)

My comment sounds like triaging bugs :(

---

### Post by P4man on 2010-04-29
> **zeroseven0183 said:**
> This is a duplicate post to [http://ubuntuforums.org/showthread.php?t=1465678](http://ubuntuforums.org/showthread.php?t=1465678)
(

Its certainly looks similar. VERY similar. In fact, unbelievably similar :p

---

### Post by stmrider on 2010-04-29
> **chirpis said:**
> Hey guys.
I'm using wubi on an Acer Aspire 6530. I just tried to upgrade from 9.10 to 10.4. After a couple of hours of downloading and half an hour of installation, the whole thing hung at "Preparing memtest86+". The terminal readout showed several lines of "found linux image: /boot/vmlinuz-2.6.32-21-generic". After waiting a while to see if it would progress any further, I restarted. Now I can't boot into ubuntu at all. I'm pretty upset. :(
I had exactly the same problem. After several lines of "found linux image: /boot/vmlinuz-2.6.32-21-generic" I pressed ctrl+c and I received a message telling me that the previous script has been terminated by the user and it will try the newer one, which have succeeded. After that, everything went well with the remaining upgrade procedure. This is not very helpful though for your case, but it's a possible solution when somebody faces the problem at first place.

---

### Post by yjh3207 on 2010-04-30
> **stmrider said:**
> I had exactly the same problem. After several lines of "found linux image: /boot/vmlinuz-2.6.32-21-generic" I pressed ctrl+c and I received a message telling me that the previous script has been terminated by the user and it will try the newer one, which have succeeded. After that, everything went well with the remaining upgrade procedure. This is not very helpful though for your case, but it's a possible solution when somebody faces the problem at first place.

Hey, buddy. Your way does work well. Thank you!:lolflag:

---

### Post by alco75 on 2010-04-30
I had exactly the same problem upgrading Wubi 9.10 to Wubi 10.04 and the ctrl-c solution worked, apparently without affecting the upgrade. I've rebooted 10.04 twice and nothing bad has happened thus far.

10.04 is looking fantastic! :P

---

### Post by Dr_Snapid on 2010-04-30
thanks stmrider!

---

### Post by Bill80 on 2010-05-01
Hi

I've just run the Wubi upgrade to 10.4 and got the same error on my Toshiba Satellite.

First I did an update on 9.10 to get all the latest updates. Had to signon as root to do this.

Then I clicked on the button to upgrade to 10.4.
It downloaded and started the install.
Then I got a terminal window hang with the found linux image message.
Luckily I had read this thread first, so I refused to panic and pressed control C to cancel the script. 
Then I got the warning about how the end of the world might happen if I continued to cancel the script. I ignored this and continued.
Got another pause, querying whether I wanted to reinstall GRUB.
I tossed a coin and decided, yes, OK.
Install then carried on and seemed to finish OK and asked to reboot.
I rebooted into Ubuntu, But just got the Background displayed with nothing else. No menus, no icons, no response.
Now I had to clutch my lucky rabbit's foot, and powered off.
Powered on again and all seems to be OK this time.
Upgrade seems to have worked. Phew!

But I think I would recommend to delete the old Wubi first then do a clean install. It would probably be safer.

---

### Post by AntoniusUno on 2010-05-01
ok so here I am also, in the middle of 10.0.4 upgrade and script also hangs at the memtest86. I had installed ubuntu with wubi never knowing it is not a permanent solution but ok that's in the past. Control-C tells me indeed that my system will be left possibly in a corrupted state.
System still functions, I can still back-up. What is wisdom?

How do I get rid of this wubi stuff? I still have dual boot with windows 7 and don't want to mess up that partition.

---

### Post by Paddy Landau on 2010-05-01
> **AntoniusUno said:**
> How do I get rid of this wubi stuff? I still have dual boot with windows 7 and don't want to mess up that partition.
Wubi is installed *as if* it were just another Windows program.

So, uninstall it as you would any Windows program. **Remember to back up your Wubi data first.**

Once that's all working (Windows without any Wubi), then download the Live CD and do a native installation. **Remember to back up your Windows data first.** I also recommend that you back up your entire disk using [CloneZilla]("http://clonezilla.org/") (or Norton Ghost or whatever), so if the installation is a total screw-up then you can restore everything.

A native installation has a few advantages over Wubi: More reliable, more resilient, faster, and can hibernate and suspend.

---

### Post by AntoniusUno on 2010-05-01
So will that mean I have to reinstall completely ubuntu again? I spent weeks getting it configured the way it is now. It does hibernate and suspend and it does work fast. Don't really want to go through all that again.

Is there another way like to backup config files and all I have to do is make sure I have the complete list of SW again installed and voila, all i again configured as it was?

---

### Post by Paddy Landau on 2010-05-01
> **AntoniusUno said:**
> It does hibernate and suspend and it does work fast.
What, WUBI can suspend and hibernate? That doesn't sound right.
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php) and scroll to "Any gotcha?"

Are you sure that you're using WUBI?

> **AntoniusUno said:**
> Is there another way like to backup config files and all I have to do is make sure I have the complete list of SW again installed and voila, all i again configured as it was?
Yes. Back up your **entire** home directory ([FONT=Courier New]/home/yourusername[/FONT]), including all hidden files. When you've reinstalled, restore the entire home directory. You'll need to exclude certain directories.

Here is a suggested command to copy the entire home directory to a safe place (e.g. to your Windows drive). Replace *path* with the path to where you want to back it up, e.g. a directory on your Windows drive.
```
cd ~
tar -cjf path/homebackup.tbz --one-file-system *
```(Warning: It will take quite a while to run.)

To restore this file when you've created a new installation:
```
cd ~
tar -xjf path/homebackup.tbz --recursive-unlink *
```BUT:

As I said, it sounds as though you're not using WUBI.

---

### Post by antonius uno on 2010-05-03
I pressed CTRL+C as well in the terminal and ignored the message. Install continued and I am now successfully upgraded to 10.04. Yippie!
Vuze was messed up but nothing a reinstall wouldn't fix. Volume key issue on my DELL Studio is SOLVED which is another hurray for Ubuntu. 
Looks are nice, only the boot takes slightly longer this time. But still nothing compared to Windows7.

About the WUBI, still don't know what to say. I installed ubuntu using Wubi and I still get the boot message that boot is looking for wubildr. 

Anyway, my problem is solved for the moment.

---

