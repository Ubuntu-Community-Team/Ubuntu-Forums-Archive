---
title: "Sharing problems"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by Nazgoth on 2007-10-19
Hello, i have a network problem i hope ppl can help me with. this is my first time using Ubuntu and i'm a linux noob, please keep that in mind. I have just installed the new Gutsy Gibbon on my old computer (athlon 1,33ghz 512mb ram) which i use as a download and storage computer.

Once gutsy was installed the other (ntfs) hard disks were automatically recognized and mounted so i could read files (music/vids) that were on it. i then tried to share a folder on 1 of the partitions (where all the downloads arrive) so i can access them via my network from my other computer.

I go in nautilus to the correct folder, right-click -> share folder and get an 'acces denied' error. apparently 'root' is the owner of the disk/partition and there's nothing that i can do about it. i have ntfs-3g installed, it doesn't help. i started nautilus with root priviliges (terminal -> sudo nautilus) to try and change the owner in the drop down in properties. everytime i change from 'root' to 'username' it automatically goes back to 'root' once my mouse leaves the dropdown box.

i would really like to get this working but i can't understand how it can be so incredibly difficult just to share a folder via the network.

---

### Post by scrooge_74 on 2007-10-19
Security issues.

What kind of sharing are you planning to do?

Linux to XP  = samba server
Linux to Linux = nfs

---

### Post by Nazgoth on 2007-10-20
been looking around the forum a lot since i created the thread and came across this thread:

[HOWTO: Setup Samba peer-to-peer with Windows]("http://ubuntuforums.org/showthread.php?t=202605")

and i got it working :)

---

### Post by smuggly on 2007-10-20
I Had The Problem Try The Host Tab sys/admin/network highlight your devise/properties then assign your network#   192.168.0.XXX, & Name case sensitive This Worked For Me,I Could See The Other Puters But Coulnt Connect Til I Did This
                                                           Tom:guitar:

---

