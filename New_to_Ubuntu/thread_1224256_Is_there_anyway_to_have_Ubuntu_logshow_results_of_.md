---
title: "Is there anyway to have Ubuntu log/show results of the last File Operation?"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by GHNeko on 2009-07-27
Basically, I have an iPod with a damaged hard drive (the spins skip, ie speed up and die down and repeat) while this means that I need to replace the HDD, I dont have the money to do that at the moment, so I grin and bare the 3x loading times on Rockbox on my ipod.

Recently, I tried using it as a USB Restore disk from a live CD which turned out to be a stupid choice, because even though I had a bootloader on the ipod with an ext3 partition on my ipod for Ipod Linux, I now get the "CONNECT TO ITUNES TO RESTORE" message, meaning I cant access any part of the ipod FROM the ipod itself.

So what I want to do is back up my files and music while under Linux because Windows as a less reliable file copy.

The issue is because the hard drive is damage, files tend to now follow through with the copy, and with 32+ gigs of music being copied at once, I dont have the time to sit by the computer and wait 30 mins for a bad file to fall through nor do I have the time and the paitence to do multiple file copy sessions at a time.

So I have file operations going, copying music from my iPod atm, set to skip all dropped files.

What I want is to have file operations create a log, or display results, something to show/tell  me what files were dropped so that I can go back and manually pull them or re-obtain them myselves later as I know my ipod has a habit of dropping perfectly functional files because it likes to be moody now. And because I have like 5000+ songs that I've obtained throughout the years, I cant really go through my library and figure out what is missing because my memory isnt all that good when it comes to such a large number of files.

So is there any way to get File Operations to display results after its done copying files or am I just going to have to suck it up and never know what files are dropped until I decide to look for a song and find thats its not there?

---

### Post by t0p on 2009-07-27
Try **tail -f**, eg as

```
tail -f /var/log/messages
```

---

### Post by GHNeko on 2009-07-27
Blah. Too late. For whatever reason, right in the midst of the copy, my ipod reset while in disk mode. Seems like whenever I try to copy, it eventually reboots for whatever reason.

---

