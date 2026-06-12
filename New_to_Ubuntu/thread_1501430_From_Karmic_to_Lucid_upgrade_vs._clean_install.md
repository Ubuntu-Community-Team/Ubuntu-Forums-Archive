---
title: "From Karmic to Lucid: upgrade vs. clean install?"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by damnated on 2010-06-04
I've upgraded from Jaunty to Karmic and had no problems, in fact if I remember correctly, most of my installed programs worked fine after the upgrade. 
How healthy is upgrading to Jaunty, though? Through update manager I mean. Being a bigger difference between the two versions and all. 
Am asking because I'm too lazy to burn a CD and reinstall everything again. Or I'll lose my installed stuff anyway?

---

### Post by sydbat on 2010-06-04
This is my suggestion - 

1) back EVERYTHING up
2) download and burn a Lucid CD/USB just in case (unless you have access to another computer)
3) do the upgrade
4) if all goes well, no problem
4a) if your system borks, you have the option of a clean install due to #2

---

### Post by Guy Sibley on 2010-06-04
I am always in the clean install camp.  I just back up and clean install always.  It works well for me.

---

### Post by howefield on 2010-06-04
> **damnated said:**
> Am asking because I'm too lazy to burn a CD and reinstall everything again.

With more and more of stuff going digital, I fear for the long term well being of your computing environment. It is only a matter of time before a disaster hits.

Being lazy isn't an option ;-)

---

### Post by Tombgeek on 2010-06-04
I still say it is better to do a clean install. I still do that. I never upgrade, because there is always the potential of something going wrong.

---

### Post by Paqman on 2010-06-04
I've done both updates and clean installs of Lucid, both worked equally well.

I'd say go for the upgrade, you can always do a clean install if it really doesn't work.

---

### Post by oldfred on 2010-06-04
After doing updates from 6.04 thru 9.04, I decided to do a clean install of Karmic and am now a fan of clean installs. I also wanted to convert to ext4 and use grub2 which the upgrade in place would not let you.

It does required a little planning to do a clean install. You need to have  a separate /home or good backup. You can export a list of all installed programs and reinstall. And if you did any special system wide configuration you may want to back up those files from /etc. The config files from version to version may not always be required since some systems get obsoleted. And sometimes old settings interfere with the new version.

Since root is small with a separate /home I now just install in a new 20-25GB partition and keep the old root for a while.

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

---

### Post by damnated on 2010-06-04
How can I generate a list of installed programs?

EDIT: just saw the links at the end of your post oldfred, never mind :)

---

### Post by Guy Sibley on 2010-06-04
I was going to reply but old fred got it i guess, so that command (sudo cp /etc/apt/sources.list ~/sources.list.backup) will show all the programs you have installed and back them up? awesome!

---

### Post by WinterRain on 2010-06-04
> **guy sibley said:**
> i am always in the clean install camp.  I just back up and clean install always.  It works well for me.

+1

---

### Post by oldfred on 2010-06-04
Not quite, the sources list is the list of repositories. Usually just the Ubuntu, but if you have added one's like medibuntu you would want to be sure to include them.

the list of programs installed is this. See links above for details.
 dpkg --get-selections | grep -v deinstall > ubuntu-files
or
 dpkg --get-selections > ubuntu-files

The above list is just a text file and the reinstall will update to the current (new) version.

If you want a list with more descriptions (but not for reinstall)
List with explanations of programs
dpkg -l > ~/Desktop/installed_programs.txt

---

### Post by KirbySmith on 2010-06-06
I can't help jumping in with a question that has nagged at me for some time and follows the topic here ...

Given 9.10, a backed up /home directory, all video, photo, document, etc. data are stored somewhere (preferably unreachable by the installer so no mistakes are made), and 

Given a successful install of 10.04 followed by successful installs of all programs one wants to reinstall, then what?

I would think that overwriting the new /home directory with the old one would not be a good strategy.  I could probably figure out restoration of Firefox and Thunderbird files, as I somehow got most of them from a broken Win2k environment, but what about all the other stuff, such as any of the myriad preferences one might have previously set for the reinstalled programs? 

In other words, the instruction to back up /home obviously has a purpose, but the details are unclear.

And as icing on the question, is the answer different if upgrading from 32-bit karmic to 64-bit lucid than if upgrading 32-bit to 32-bit?

Thanks for any clarification.

kirby

---

### Post by oldfred on 2010-06-06
All your user settings are in /home including all the settings your various programs use. You can copy all or just some parts of your old home back if it is not a separate partition and you mount it as part of the new install.

Programs are designed to update from the previous version's data so updating to new versions of the programs should cause no problems. You may be be able to go back as the new verison may have settings that are not compatible with the older version.

---

### Post by KirbySmith on 2010-06-07
Thanks oldfred.  Let me be sure I understand.  If I do a clean install, and then replace the newly created /home with the old /home before installing various supplementary programs, they should install and behave properly, and the clean install itself won't have become messed up in some way, such as deciding that my password is invalid?

kirby

---

### Post by oldfred on 2010-06-07
It is easier to have a separate /home. But you should be able to copy everything over. Passwords are in system settings, but I have used same name & pw for my new installs. 
If you have more than one user you need to make sure you set them up in the same order. Do not know if you have things encrypted what may happen.

---

### Post by KirbySmith on 2010-06-07
Thanks for your help.

k

---

