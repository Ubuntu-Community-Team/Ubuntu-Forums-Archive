---
title: "First Post / NTFS Internal HD Not Mounting / VPN / Voice Recognition"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by stevesdata on 2009-09-23
Hello

This is my first post so please bare with me.

I am currently the Head of IT for a small organisation and starting a small web consulting business. I have been interested in Linux for a long time and have finally installed on a test machine. I am aware of the massive benefits of Unix based operating systems as I own several pcs and 2 macs.

The only initial problem I have had is when I boot a storage partition on my internal HD formatted to NTFS so Win & Ubuntu partitions can access doesnt mount. I am guessing this is because formatted to NTFS? I have looked for options to mount on start up and cant find anywhere. The documentation says internal drive partitions should mount automatically?

So far I am really impressed with Ubuntu and hope to build a webserver and possibly roll out Ubuntu / Xubuntu if we are unable to afford to buy new machines, we would need to breathe life into our old hardware. I would be really interested in learning more about building my own servers I have been recommended to look into using Ubuntu server, Apache, PHP and cPanel. This would be excellent as I would like to offer managed hosting for my clients.

I would really appreciate any information regarding Cisco VPN Client, Remote Desktop into Windows 2003 servers. 

I am also desperately trying to track down a solution for voice recgnition software for Ubuntu. As far as I am aware my options are: Dragon speak and Wine, Julian / Julius or CMU Sphinx. I havent been able to find any recent info on installing Dragon Speak 10 with Ubuntu 9. Only much older versions? I am open to using native open source software ideally rather than emulations, hacks etc. Currently I am dual booting so in theory could use Windows only for Adobe products or Dragon Speak.

I also found this [https://wiki.ubuntu.com/SpeechRecognition](https://wiki.ubuntu.com/SpeechRecognition) and would love to learn more.

Would really appreciate any pointers and hope to become an active member of the Ubuntu community...

:guitar:

---

### Post by Chronon on 2009-09-23
If you want to automount a partition you need to add it to the file system table: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by marcopalla on 2009-09-23
...you are an admin, so, almost quite smart on pc

**problem A)**

1) If you want it to mount when the machine boots and hold the mount open forever you can simply add the mount point to /etc/fstab 

2) If you want it to mount only when you access the drive you will utilize this using autofs
[B]
problem B)[/B]

about dragon and wine ( alcoholic dragon? ;)  ) best/only resource
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2077](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2077)

is rated silver, you'll understand what it means,

**problem C)**

not to be on jedi side... but to become a linux server admin is not a forum/topic question ;) but about years of studing

I hope to have been helpfull, ):P
m.

---

### Post by stevesdata on 2009-09-23
Many thanks guys will check this out when I get home. I also found the Pocketbook. I was considering buying a book, but the community and the fact so much is free is really refreshing (and appreciated).

I would be interested in testing one of the native ubuntu speech recognition softwares as I have had a very mixed experience with running a version of wine on mac.

Does anyone have any recommendations?

Thanks again

:)

---

### Post by marcopalla on 2009-09-23
Red Hat Linux Networking and System Administration(Redhat Press)

Christopher Negus, Linux Bible 2008 Edition 

very good, and if you look around are very.... common

p.s.
mac wine is quite different from linux one

---

### Post by Bölvaður on 2009-09-23
> **stevesdata said:**
> 
Would really appreciate any pointers and hope to become an active member of the Ubuntu community...


This is quite a big website and the advanced users don't check every single thread, they just skim over the topics quickly and see what interest them.

So in order to get their attention, making a dedicated thread to a single topic would attract the correct people in greater quantities.

Also google and these forums combined have answers to almost every problem you could have. There is a problem of too many posts are being made about the same topic / same questions, which berry other peoples threads. Im not telling you not to post at all ;) but rather find solutions already given (make sure it is less than a year old... or 2, as things change rapidly around here and annoyances 2 years ago have been fixed a long time ago)





Your problems:


NTFS:
You can mount this file system very well as long as Windows unmounted this partition correctly.
In Ubuntu (as it comes out of the box) going to *Places* on the top panel will show you all available partitions.
Alternativly you can open nautilus (the file browser) and go to computer:///

Alt+F2```
nautilus computer:///
```

For always mounting it google : "fstab ntfs" and make sure the websites are from 2008 or 2009... older = outdated
[http://ubuntuforums.org/showthread.php?t=949647]("http://ubuntuforums.org/showthread.php?t=949647") &#8592; your answer lies in there.


About your servers and replacing windows, please look at NFS which is a protocol to mount external partitions (on different computers/servers). With it you can store /home partition of a user on a central computer for an example.

for remote desktop:
Applications &#8594; Internet &#8594; Remote Desktop Viwer


click my link
 [sudo apt-get install julius]("apt:julius")
 to install julius you talked about. from the description of the package it looks like it is script based.


Sorry that I became very lazy in the end, but this is quite long reply. Hope some of this will make sense to you and be of any help.:KS

---

### Post by ajgreeny on 2009-09-23
Look at installing **ntfs-3g** and **ntfs-config** using synaptic or apt-get; they will do exactly what you need for the disk mounting and save you the bother of editing fstab manually, though doing that will give you a greater insight into what that file actually does.

---

### Post by stevesdata on 2009-10-22
Many thanks for the advice...

I think the 2 driver options are the most interesting as I am still learning about Linux and tbh there is a ton of other stuff I need to urgently learn. Learning Linux may have to become a hobby.

I am hoping the environment will help me to be more productive as I am learning dev skills atm.

Regarding the speech software I may lurk a little while longer as I have read its a priority to develop a dragonspeak equivilent to increase the the number of companies / offices that move over to Ubuntu.

I have still not read too much about a VPN? I believe Cisco have released one but hear many probs trying to use.

For the remote desktop viewer I am guessing whilst on a network I can simply type a server name and log in like the Windows Remote Desktop?

Thanks again I am really liking Linux.

:)

---

