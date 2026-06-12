---
title: "Upgrade needs a total of 704M free space on disk '/'."
date: 2010-09-23
forum: New to Ubuntu
---

### Post by peter6961 on 2010-09-23
Hey everyone,
   I'm very new to all this, ive only eva used windows and now after upgrading to W7 Ultimate when it came out i have had nothing but problems with viruses.
  
  So Ive now had 10.04 since it came out but have only installed compiz and nothing else, now the problem is it keeps saying when i go to update -

(The upgrade needs a total of 704M free space on disk '/'.
plese free at lease an additional 187Mof disk space on '/'.)etc,etc.......:confused:

    (There is also a screen shot of the error message attached).

Since installing Ubuntu i have expanded my partition to an extra 112gb seeing i want to make this my default OS.
 
Thank you in advance....

And if you need more info or screen shots let me know and ill try my best...

Ive also tried that sudo thing but it didn't seem to do anything and i still get the same message..

---

### Post by mcduck on 2010-09-23
could you run "df -h" in a terminal (Applications/Accessories/Terminal) and post the output here?

That would give us a better look at your hard drive partitions and the amount of space used&available on them.

---

### Post by peter6961 on 2010-09-23
Hey thanks for your reply mcduck.

Im still getting used to all this but is  that saying Ive got Ubuntu installed with only 509m available?
because halved my windows partition thats somthing like 600gb so 300gb each ad ive got the 1tb external..
  sorry just confused out of my mind lol:P.

---

### Post by CharlesA on 2010-09-23
Is this a Wubi install?

---

### Post by peter6961 on 2010-09-23
yeah it is a Wubi  but should that really matter?

---

### Post by mcduck on 2010-09-23
Yes, it does, since when installed through Wubi your Ubuntu isn't installed into a separate partition, but inside the Windows partition instead. And the amount of space available for Ubuntu is what you define during the install.

So, the df output is telling that your windows partition (/dev/sda6) is 106 GB, and that you have reserved 4,6GB of that space for your Ubuntu system.

The size of the external HD is irrelevant, as it's not added into space available on / (which is where you are running low on space now).

I haven't played with Wubi myself, so I have no idea how to resize the space given for Ubuntu after the install, or if that's even possible.

---

### Post by CharlesA on 2010-09-23
Yeah. Wubi installs on a virtual hard drive that's stored on a file on the machine.

It looks like it's around 5GB in size.

If you don't have a lot of stuff on that install, you could just uninstall Wubi and reinstall it and select a larger amount of space to use during install.

---

### Post by searchfgold6789 on 2010-09-23
If you plan on using ubuntu as your default OS I recommend not using wubi. I found that going through the trouble to make a Live USB or Live CD is really worth it.
Instead of using synaptic, try this:
Open up a terminal, and run ```
sudo aptitude
```Type in your password and press enter. Wait for the screen to load.
Press Shift+U
Press G to start the upgrades.
Hope this helps.

---

### Post by Lateralis on 2010-09-23
[This]("https://wiki.ubuntu.com/WubiGuide") Wubi Guide should help you either migrate your Ubuntu installation across to a dedicated partition, or increase the size of the Wubi install.  The Misc. section (section 8 ) is of particular importance.  

I personally have no experience with Wubi so have no clue how easy either of these things are to achieve, or how easy one method is relative to the other.  Both methods though seem to make use of [LVPM]("http://lubi.sourceforge.net/lvpm.html") which apparently doesn't work properly with Wubi 10.04.  

In any case, have a read of both links.  If you need further help either migrating or expanding your Wubi install, I suggest starting a new thread with specific questions.  

Hope this helps.

---

### Post by peter6961 on 2010-09-23
:)ok great thank you heaps guys.
 so if i do those cmd's will i loose my windows install ?
    what exactly dose it do?

---

### Post by peter6961 on 2010-09-23
hey thanks [Lateralis]("http://ubuntuforums.org/member.php?u=481237") im starting to wonder if i should just wipe my 10.04 install and start from scratch, doing it properly.
 i didnt want to do it like this because realy i have no idea what im doing with ubuntu lol but i guess its the only way im going to learn.

---

### Post by Lateralis on 2010-09-23
Hehe.  Learning any new OS takes time.  You are probably very familiar with Windows purely because you've been using it for years and is probably the only OS you've ever used.  Ubuntu - and Linux generally - is very logical once you have learned the basics.  And of course if you ever get stuck there are the Ubuntu forums to help you out!  

As for your current problem, I always advocate installing Ubuntu to a new hard drive partition.  Wubi definitely has its uses but equally has its limitations.  For starters, it allows people to try out Linux to see if they will get on with it, see if there is software available to meet their needs and if they're hardware can cope with it.  On the flip side, Wubi doesn't run as smoothly or efficiently as a full install, I hear that upgrading the distribution to the next version can be problematic (if not impossible) and when you run out of disk space it can take a great many number of steps to fix!  

So for my money, installing to a separate partition would be the best thing to do.  Certainly that's what I would do (but you are free to take whichever decision you are most comfortable with).  

If you did want to install from scratch then you will need to burn a copy of the [LiveCD]("http://www.ubuntu.com/desktop/get-ubuntu/download") (if you don't have that already) and boot into that.  You can choose to make use of the LiveCD before you install it and when you do install it, the installation guide is simple and straightforward.  Links to the [Ubuntu Installation Guide]("https://help.ubuntu.com/community/Installation") and the [Dual Boot Guide]("https://help.ubuntu.com/community/WindowsDualBoot") may provide useful information for you.  

And of course, feel free to ask questions in the forums if there is anything you don't understand.  :)

---

### Post by CharlesA on 2010-09-23
Best way to see if yer hardware will cope is to boot off a livecd and make sure that all the stuff is working.

I'm a fan of running a copy of Ubuntu in VirtualBox so I don't have to reboot to access it. It's probably got more overhead then running a pure dualboot system, but I'll deal with it for not having to reboot to switch between OSes.

---

### Post by psusi on 2010-09-23
Yes, you should uninstall wubi from windows, then reinstall Ubuntu the right way; on its own partition.

---

### Post by JKyleOKC on 2010-09-23
> **peter6961 said:**
> Im still getting used to all this but is  that saying Ive got Ubuntu installed with only 509m available?
because halved my windows partition thats somthing like 600gb so 300gb each ad ive got the 1tb external.As the others have said, your Wubi install didn't touch the 300 GB that you set aside for it, so you can back up to the 1-TB external any important data that you now have in Ubuntu, then use Windows Add-Remove programs in the Control Panel to remove the Wubi installation. This should also remove the changes to boot.ini that show up when you boot the system, and give the 5 GB that Wubi was using back to Windows. It's essential that you do this from Windows in order to clear out all the hidden stuff involved, such as the boot menu and registry changes.

Then use the live CD to install Ubuntu again, and at the partitioning step select "manual" from the list of options. This should show you a thermometer-like view of your hard drive, with the first half of it used by Windows and the second half showing as unallocated. Select the second half and specify all but about 5 GB of it as type ext4 and named "/", with the "format" checkbox checked. Save that specification, then set the remaining 5 GB as "swap". Tell it then to write the new partition table. It will take a few minutes to format the "/" partition but will then go on with the installation and will create a new boot menu that lets you choose between Ubuntu and Windows.

This should get you up and running easily. You may see some discussion on the forums about setting up a separate partition for "/home" and it's a very good idea eventually, but for your initial experience I think it's better to have a single main partition so that you don't risk running out of space for new software that you may want to experiment with. Once you're more familiar with the system, it's not that difficult to change the setup.

---

### Post by sandyd on 2010-09-23
If you don't have anything you need on /dev/sda2, just delete the partition through windows 7 and when installing ubuntu, choose "use largest block of free space" (or something like this, wording may vary)

---

