---
title: "One headache...need help, wine, wow, kbuntu, fsck, firestarter fail"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by Simest on 2010-01-29
First I will open with this:
[http://ubuntuforums.org/showthread.php?t=1392008](http://ubuntuforums.org/showthread.php?t=1392008)

Since then I have installed ubuntu 9.04 , updated to the latest packeges and installed my nvidia drivers.

Things seemed fine and dandy. Even got wine installed proper and did a winecfg. All from console. Downloaded the world of warcraft installer and even got it started with the massive download it has to chug through (I would love to use my DVDS!) for it to install. I havent even started on the expansions or patches.

Its going doing its thing. Plugged in t-mobile side kick lx and was off loading some pictures. FROZEN! No mouse no keyboard nothing.

Press the reset button....*sigh*

Comes to boot up, ubuntu screen load bar...forced to console with fsck failed issue. Run it manually. Fix fix fix. Reboot. *sigh*

Start up the warcraft downloader again. Start browsing through the soft center. Hmmm, firewall sounds like a good idea....maybe later.

Installer finshes! Woot! 'Cant find install data!'
*snort grumble grumble* Ok lets try here. Return to chugging along.

Open home dir. Error cant write log something something something...FREEZE! *sigh* 

Comes to boot up, ubuntu screen load bar...forced to console with fsck failed issue. Run it manually. Fix fix fix. Reboot. *sigh*

Back to up and downloading again. Install firestarter before hand. Open the home directory and start moving those photos around. Nothing system straining, just rename and resort.

Open firefox....*freeze!*

*random obscenity in a long array string*

Reboot. Ubunutu load bar....

Firestarter Loading [FAIL]

With no reaction afterwards. Wait 5 mins nothing. Ok fine, to the laptop. Find out this: [https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/42759](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/42759)

How nice. Leave something that can prevent a system from booting up open to be installed. *sigh*

Recover from cd. Crtl alt f1, sudo blah blah blah sudo apt-get autoremove firestarter. ( [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)  with a note of BrokenDreamz post on the launch pad link)

Removed.

Reboot.

Ubuntu loading screen...forced down to console...Configuring network interfaces [ok]*sigh*

And thats where I sit now at 1:30 in the morning. 

All I want is a ubuntu desktop system (kde isnt snappy imo to want) to run world of warcraft and maybe a few linux games.

Help?

---

### Post by hemimaniac on 2010-01-29
well i would try grabbing the latest wine doors from winehq, in their repos ( yes, settledown, there are repos for wine) fire that in there and after initial set up there is WOW in their repos, along with other neato stuff you may wish for, with all the freezing going on, sounds like something broken ( ya i know, real help there) maybe re-compiling the kernel or upgrading it may help you, but that is only after all the usual stuff, like fdisk then check this and check that, and with any luck you can hit he sack about 02:45 and start fresh in the AM?

good luck

---

### Post by 3rdalbum on 2010-01-29
Any particular reason why you're not using 9.10?

Firestarter will always show "[FAIL]". Bug, I guess. Firestarter is not really maintained anymore, it does several things that scare newbies unnecessarily, and besides which a default installation of Ubuntu doesn't listen to any incoming ports anyway - you don't need a firewall on your computer.

---

### Post by Simest on 2010-01-29
1) The version of wine I am using is 1.1.37 , from the winehq repo.

2) All of the problems I have with my hdd started after I installed wine. Course, I will give it a more through check with UBCD. Thank!

3) 9.04 was what I had burned. I did have plans to upgrade after I had things settled and worked.

4) Firewall was/is a force of habit from windows. Aside that I knew that linux has built in iptables but I wanted to open some ports for warcrafts bit-torrent based patching system.

5) The system isn't bootable for the most part, it is still sitting at the Configuring network interfaces[Ok] from last night. Is there any chance I can recover this or should I just flat reinstalled 9.04 and try again?

Thanks guys.

---

### Post by 3rdalbum on 2010-01-29
Try hitting Control-Alt-F7 or Control-Alt-F2 and typing 'sudo gdm' at the prompt. This may get your graphical login going.

By default on Ubuntu, the firewall lets everything in, if there is anything listening. If you think about it, you don't need a firewall to open ports, because a firewall's purpose is to close ports.

---

### Post by Simest on 2010-01-29
1) Control-Alt-F7 gives me a screen of text with: kinit: No resume image, doing normal boot...

And no input accepted

2) Control-Alt-F2 gives me a blank screen with no text on it.

And no input accepted

3) Noted about the ports then. Thanks.

---

### Post by zipperback on 2010-01-29
My advice is to download and burn the current 9.10 version of Ubuntu.

Then once you have it burned to CD, boot it up and select the option to verify the media.

If the media verifies as being good, I would then do a full clean install of Ubuntu.

Once you have it installed, getting the rest of your applications installed and running should be a pretty simple process.

I hope this helps you,
- zipperback
:popcorn:

---

### Post by Simest on 2010-01-29
Thanks, that is also on my list of possible fixes. I know very well I could get back into my hdd via recoverylivecd then take some of my data back.

I just rue the idea of having to reinstall and doing the several hour wait for warcraft installer again.

---

