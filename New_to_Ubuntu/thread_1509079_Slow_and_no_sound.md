---
title: "Slow and no sound"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by breathoffog on 2010-06-13
I updated to ubuntu 10.4 about a month ago, and recentally my sound isnt working and the OS is running VERY slow and unresponsive. im somewhat new to this OS since the first version i ran was 9.04. everthing was working perfactally fine until about 3 hours ago. and this just suddenly happened out of nowhere. I have no idea what to do, can i please get some help?:confused:
By the way - Windows 7 runs just fine with no problems so im guessing its an OS issue
My specs are:
ASUS striker 2 formula
Core 2 duo E7300 @ 2.66GHz
4GB DDR2 800
1TB seagate barricuda dual boot win 7 - ubuntu 10.4 taking 250GB
corsair TX750W @ 750 watts
Nvidia 9800GTX+

---

### Post by NightwishFan on 2010-06-13
Well to check the sound issue, open a terminal and run:
```
alsamixer -c0
```
Check your mixers and see if your volume is ok or muted. If not, look for user lidex to help you out.

You can check CPU usage with top, see what (if anything) is causing slowdowns. I had a similar problem upgrading a machine to lucid as well. It was very choppy almost as if it could not read from the disk efficiently. Is that what is occurring for you?
```
top
```

---

### Post by breathoffog on 2010-06-13
I looked at my CPU usage and its at 2.5% or less, and my audio is detected - but the speaker icon shows "---" next to it, and when i click on it (and wait about 2 minutes) it just gives me a "mute audio" option. just getting into the terminal to exicute the code that was given to me was like a wait at the DMV. thanks for your help so far. i really hope that eventually i can get this resolved.

---

### Post by NightwishFan on 2010-06-14
It seems like your card isnt working. Run this command to find out what kind it is.
```
sudo lshw -C sound
```

---

### Post by lidex on 2010-06-14
What is the terminal output of:
```
uname -a
```
Terminal="Applications->Accessories->Terminal"
Did you try a reboot?

---

### Post by NightwishFan on 2010-06-14
Perhaps a re-installation would be in order if the system appears too slow to work. That is not usual. By any chance are you using 64-bit?

---

### Post by breathoffog on 2010-06-14
I have rebooted many times. Iv'e been using windows to jump onto the forum because firefox keeps crashing - im considering a system wipe unless i can reinstall ubuntu back on to that partition and not have a load of OS choices when grub loads. ill run the other  lines of code when i get home from school tonite. thanks

---

### Post by NightwishFan on 2010-06-14
I am sorry you had to experience this as well. I will answer any questions I can, but I advise you do the following for a re-installation.

[LIST]
[*]Back up important data to a DVD or another partition. If you back up any files in Ubuntu to Windows, perhaps put them into a folder titled 'Ubuntu Data'.
[*]Download and burn an Ubuntu 10.04 Live CD. Test to make sure basic hardware such as sound works. If not, ask lidex, he knows the sound system better than anyone I see around here. Use Gparted on the live CD to delete your existing Ubuntu partitions. They will be the ones marked ext3, ext4, or swap. (fat16/32 and NTFS are for windows)
[*]Then run the installer and choose to install Ubuntu in the free space. If you understand how partitioning works then choose manual, perhaps make a logical partition setup with one for swap, one for /, and one for /home. That way if you reinstall, you will have all your data/settings in /home, and you only have to reformat the / partition.
[*]The Grub boot loader will indeed be reinstalled only with the detected systems, so the old Ubuntu entries will be gone.
[*]Then finally restore your backed up files.
[/LIST]

As I said feel free to ask any questions. If all of this was already obvious to you, forgive me for seeming patronizing, I just hope to help. :)

---

### Post by breathoffog on 2010-06-14
> **NightwishFan said:**
> I am sorry you had to experience this as well. I will answer any questions I can, but I advise you do the following for a re-installation.

[LIST]
[*]Back up important data to a DVD or another partition. If you back up any files in Ubuntu to Windows, perhaps put them into a folder titled 'Ubuntu Data'.
[*]Download and burn an Ubuntu 10.04 Live CD. Test to make sure basic hardware such as sound works. If not, ask lidex, he knows the sound system better than anyone I see around here. Use Gparted on the live CD to delete your existing Ubuntu partitions. They will be the ones marked ext3, ext4, or swap. (fat16/32 and NTFS are for windows)
[*]Then run the installer and choose to install Ubuntu in the free space. If you understand how partitioning works then choose manual, perhaps make a logical partition setup with one for swap, one for /, and one for /home. That way if you reinstall, you will have all your data/settings in /home, and you only have to reformat the / partition.
[*]The Grub boot loader will indeed be reinstalled only with the detected systems, so the old Ubuntu entries will be gone.
[*]Then finally restore your backed up files.
[/LIST]
As I said feel free to ask any questions. If all of this was already obvious to you, forgive me for seeming patronizing, I just hope to help. :)
 
 
When you mention Gparted - are you talking about the partitioning system that you have an option to use during the installation?

---

### Post by NightwishFan on 2010-06-15
System -> Administration -> Gparted. However the one in the installer works as well.

---

### Post by lidex on 2010-06-15
Check your logs for any clues.
```
cat /var/log/syslog
cat /var/log/messages
dmesg
```

---

### Post by breathoffog on 2010-06-15
I deleted the old EXT4 partition and installed 9.04. thank you for all of your help, and hopefully this issue doesn't happen to any of you. it wasnt really an inconvenience to wipe the partition since i didn't have much on it other than compiz, Lm sensors and a few other things. still blows my mind how something like that happened out of nowhere though.

---

