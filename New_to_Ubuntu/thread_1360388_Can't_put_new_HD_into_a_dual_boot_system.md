---
title: "Can't put new HD into a dual boot system"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by paulbyr on 2009-12-20
Hi,
When I added a new HD, I put it at boot pri 3 in the BIOS boot Priority list, below the HD with Win XP and the separate HD with Ubuntu.  I get Grub error 22.  

If I unplug the new HD I can go back to regular dual boot.  All 3 are SATA WD drives.  Suggestions?

Also, what do the "quick reply icons" look like?

---

### Post by 73ckn797 on 2009-12-20
What version of Ubuntu are you using?

Can you boot the system with the LiveCD with the 3rd drive connected?

---

### Post by paulbyr on 2009-12-21
I'm using  Ubuntu 9.10 on one HD and WINXP on a different HD.  I am trying to install a third HD (NTFS formatted) for WINXP use.

I will try a live CD boot with the HD re-connected and reply with results.  Please tell me what a quick reply icon looks like.  I just clicked the reply to thread button to write this.

---

### Post by adam814 on 2009-12-21
> **paulbyr said:**
> Hi,
When I added a new HD, I put it at boot pri 3 in the BIOS boot Priority list, below the HD with Win XP and the separate HD with Ubuntu.  I get Grub error 22.  

If I unplug the new HD I can go back to regular dual boot.  All 3 are SATA WD drives.  Suggestions?

Also, what do the "quick reply icons" look like?
The quick reply icon is the arrow in the bottom right of each post.

---

### Post by oldfred on 2009-12-21
If you want to give even more information this combines many commands and other boot info into one:

Boot Info Script 0.41 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions:  louieb's 
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
or as example if on desktop or  downloads directory from liveCD download: 
sudo bash ~/Desktop/boot_info_script*.sh
sudo bash ~/Downloads/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory.(Ver41 put mine in my home dir). Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

and if you ever had raid installed on the drives:
ls /dev/disk/* -l

---

### Post by brettbed on 2009-12-21
This link might help. Don't know if you already tried this. It's pretty basic. She's hot too!

[http://www.youtube.com/watch?v=WtBBl6HvdpM](http://www.youtube.com/watch?v=WtBBl6HvdpM)

Worked for me :)

---

### Post by paulbyr on 2009-12-21
[73ckn797]("http://ubuntuforums.org/member.php?u=641480"), I currently have 9.10 installed and my liveCD is 9.04.  Do I need to get a new liveCD for 91.0? 
With the new HD connected, I can boot using the 9.04 liveCD and see the hard drive.  Is the problem that I formatted the new HD as NTFS instead of FAT32?

The later responses after yours in this thread seem to want me to re-install GRUB.  That seems strange just because I connect a hard drive.  Is there consensus that I should reinstall GRUB (with the new hard drive connected)?

I am a real newbie and this just seems foreign to me.  Thank you all for your help and interest.
Paul

---

### Post by paulbyr on 2009-12-21
Adam814,
thank you, I never saw the info about the quick reply icon.

---

### Post by paulbyr on 2009-12-21
Brettbed,
thanks, I did enjoy watching her but it says it does not apply to Karmic Koala and I didn't understand much of it any how ( was I watching instead of listening ?)

---

### Post by paulbyr on 2009-12-21
What I am really not understanding is that I am "apparently" the only new user who ever decided to add a hard drive to a computer.  Since Newegg must sell thousands of hard drives a week, can it be that no other Newegg customer tries to use Ubuntu?

I really appreciate the help and now that I have failed miserably to understand it, I guess I need to remove Ubuntu from my computer (that also seems to be a chore) and install my new HD.  I do have an older computer which can be my Ubuntu box so I'll pursue that path.

Thank you all for your assistance.  Have a happy holiday!

Paul

---

### Post by presence1960 on 2009-12-21
> **paulbyr said:**
> What I am really not understanding is that I am "apparently" the only new user who ever decided to add a hard drive to a computer.  Since Newegg must sell thousands of hard drives a week, can it be that no other Newegg customer tries to use Ubuntu?

I really appreciate the help and now that I have failed miserably to understand it, I guess I need to remove Ubuntu from my computer (that also seems to be a chore) and install my new HD.  I do have an older computer which can be my Ubuntu box so I'll pursue that path.

Thank you all for your assistance.  Have a happy holiday!

Paul

Quitting already? Come on give us a break...why did you ask for help? oldfred asked you to boot from the Live CD and download & run a script which will give us info we need to hopefully diagnose and solve your problem, but you have not done so yet.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by paulbyr on 2009-12-24
Thank you Presence1960, I will try that tomorrow (Christmas Eve) If I have time.  I really appreciate the instructional quality of your suggestion.  I do want to learn more and have a couple of books to support learning, once I get a kick start.  It has been many years since I did control language on VAX 11-780 and I do intend to learn to use the terminal and SUDO.
Paul

---

### Post by presence1960 on 2009-12-24
> **paulbyr said:**
> Thank you Presence1960, I will try that tomorrow (Christmas Eve) If I have time.  I really appreciate the instructional quality of your suggestion.  I do want to learn more and have a couple of books to support learning, once I get a kick start.  It has been many years since I did control language on VAX 11-780 and I do intend to learn to use the terminal and SUDO.
Paul

A lot of us went through that with Linux. Those of us who stuck it out and learned some are glad we did so. Terminal is not really that hard, just very different from GUI. GUI's vary from version to version but the terminal commands remain the same. it is much easier to give instructions and do a fix in terminal than say click this, scroll down to here, click this tab, etc- especially since GUI's may vary from version to version, even software application to software application.

If you are willing to learn and are determined to do so it will materialize. It happened for me & countless others.

---

