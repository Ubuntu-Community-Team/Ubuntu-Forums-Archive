---
title: "LOSING IT! dell wireless connection problems broadcom corp. 4353"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by Quantum Paradox on 2011-02-25
PLEASE HELP ME PRETTY PLEASE!!!!!!!!!!!!!:lolflag:


Ok so I have been trying for months and giving up on this. right now i have wubi with windows 7. windows 7 auto connects out of the box to the internet and ubuntu from wubi will not. 

when i type in lspci

the bottom two lines are

ethernet controller:atheros communication artheros/lic Gigabit Ethernet Adapter (rev 0)

broadcom corperation device 4353 (rev 01)

I managed to get ndiswrapper installed i believe so now I would need the windows driver right? so shouldnt the windows driver be downloaded on the windows 7 side of my laptop? and if so could i save the driver from windows on a storage divice and use it in ubuntu? or are there any distros of linux that support my wireless card "out of the box". 
I really want to have a real particion instead of wubi but I dont know how to do that really and i am worried about losing all of my fires from windows 7 

PLEASE HELP ME!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by vivek.pandey on 2011-02-25
i know this is an idiotic question but can you tell what are you using to connect? like modem or something . i saw the output but i am not that good with commands

---

### Post by arochester on 2011-02-25
First, try the easy way. Look in your Menu for an item called "Hardware Drivers." Open that. Does the driver for your wireless card appear in there? If it does, temporarily, connect your computer by wire and click the Enable button. It takes a little while. It should download, install and enable the driver. REBOOT. Job done.

Second, if that doesn't work, try:
1) Connect by wire
2) sudo apt-get update
3) sudo apt-get install b43-fwcutter
4) modprobe -r b43
5) modprobe b43

---

### Post by Quantum Paradox on 2011-02-25
well I am trying to connect wirelessly to my broadcom 4353 wirless card device to my router and can connect in windows 7 but cannot connect in ubuntu (to the 1st poster) second poster I will see if i can get it to connect with a wire.

---

### Post by migs73 on 2011-02-25
Assuming you are using Ubuntu 10.04 or 10.10, it is now called 'Additional Drivers' not 'Hardware Drivers' and it is in the System--> Administration menu.

FYI the **last** post on this thread seems to say the above will work for your card;

[http://ubuntuforums.org/showthread.php?t=1398426](http://ubuntuforums.org/showthread.php?t=1398426)


Good Luck

Mike :)

**arochester**; what a helpful bunch we scots are!!


On your second question about wubi to partition, try looking here;
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
and do a bit googling about partitioning in general. **ABOVE ALL, ALWAYS BACK UP YOUR DATA BEFORE ANY TYPE OF PARTITIONING**

---

### Post by Quantum Paradox on 2011-02-25
ok i tried both methods, i was able to connect wired for the 1st idea i got all the way to the end and it said system error failed to lock var/cashe/apt/archives/lock (btw i found an activate button but not an enable button)
and in the terminal i got really close but at the end i typed in the second last line and nothing happened then i typed in the last line and it said fatal error

morpheus@ubuntu:~$ modprobe -r b43
morpheus@ubuntu:~$ modprobe b43
WARNING: Error inserting cfg80211 (/lib/modules/2.6.32-21-generic/kernel/net/wireless/cfg80211.ko): Operation not permitted
WARNING: Error inserting mac80211 (/lib/modules/2.6.32-21-generic/kernel/net/mac80211/mac80211.ko): Operation not permitted
WARNING: Error inserting ssb (/lib/modules/2.6.32-21-generic/kernel/drivers/ssb/ssb.ko): Operation not permitted
FATAL: Error inserting b43 (/lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/b43/b43.ko): Operation not permitted
morpheus@ubuntu:~$ se

---

### Post by migs73 on 2011-02-25
> **Quantum Paradox said:**
> ok i tried both methods, i was able to connect wired for the 1st idea i got all the way to the end and it said system error failed to lock var/cashe/apt/archives/lock (btw i found an activate button but not an enable button)

The failed to lock error sometimes comes up if you have another apt program open ie Ubuntu Software Centre or synaptic. Try again with all other programs closed down.

Mike

---

### Post by vivek.pandey on 2011-02-25
system error failed to lock var/cashe/apt/archives/lock

this error is displayed when you have one more process which needs sudo or root privileges (need your password) so close the other one and try from additional drivers once more. i guess you were trying on terminal as well as additional drivers simultaneously

---

### Post by Quantum Paradox on 2011-02-25
haha yah i was trying both methods cuz i didnt reolize that the were both the same? but one in the terminal and one out of the terminal? I will update once i can use the wirered internet again. gotta wait =/ thanks for the help everyone I have a feeling I will be on line in ubuntu soon! I hope!:KS

---

### Post by Quantum Paradox on 2011-02-25
YAY! i AM SO HAPPY! I HAVE BEEN WORKING ON THIS FOR MONTHS WITHOUT IT BEING WIRED BECUASE I DID NOT HAS ACCESS TO THE WIRED INTERNET! But yay it works now! you have no idea how HAPPY! i am thanks so much guys! (and gals) not sure if it was guy, gals or both helping me but yay thanks! it worked with the 1st method posted but I had the terminal open so it wasnt working :KS:KS:KS:KS:KS:KS:KS I could just :popcorn: with joy =]

---

### Post by migs73 on 2011-02-25
I am sure I speak for us all when I say, you're more than welcome. If you could mark the thread as solved (above the first post, click in thread tools and then mark as solved) it may help others find answers to similar problems.

Welcome to Ubuntu

Mike :D

---

