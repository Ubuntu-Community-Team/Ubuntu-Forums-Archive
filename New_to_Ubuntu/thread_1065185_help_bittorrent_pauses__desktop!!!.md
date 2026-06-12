---
title: "help bittorrent pauses  desktop!!!"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by si9000 on 2009-02-09
please help if you can. 

when i try and use one of the torrent clients the desktop pauses after 30 seconds. it doesn't lock up just pauses, if i use the keyboard or are watching a streaming website it works away quite happily. to get around it i have the bbc news site open in a tab in the corner of the destop.

strange eh 

any advise apreaciated.

thanks in advance 

simon

---

### Post by khelben1979 on 2009-02-09
Have you tried [KTorrent]("http://en.wikipedia.org/wiki/Ktorrent")?

---

### Post by houstonbofh on 2009-02-09
What is your hard drive light doing when this happens?  It could be a disk based IO issue.

---

### Post by si9000 on 2009-02-09
no lights at all i'm afraid it all just seems to freeze.even the clocks stops until i use the keyboard and then it continues as if nothing has happened but without catching up the lost time.

---

### Post by si9000 on 2009-02-09
no only bittorrent and transmition

---

### Post by mkvnmtr on 2009-02-09
Those should be low resource using clients. Open Htop and watch your cpu and memory usage when this happens. Many times I use all my bandwidth on my torrenting and it slows my other internet usage but I find it strang that your clock is affected. You might post the specs of your system to see if someone can give you an idea.

---

### Post by si9000 on 2009-02-10
hi I have tried watching top to see if anything is running which may effect it but to no avail. 


I'm not sure its a resource issue because if use the keyboard or watch a streaming video it all works fine without pauseing.:confused:

its a advent laptop 1.3 celeron m /500mb ram/30gb hd

thanks 

si

---

### Post by RomeReactor on 2009-02-10
Hi. Is your desktop set as the download folder? Are Transmission and BitTorrent verifying the downloaded chunks every time they launch? Are you downloading many files simultaneously? Are these files large?

---

### Post by si9000 on 2009-02-10
well the the answers in order of asking are: yes,yes,its only been part of one file as it pauses all downloads drop their connection, and ive only been testing to see if i can sort it out so it was files of vairying sizes.

i have used monitors to see the workload with a torrent client and it was no more than about 50% when pauseing, but if i use the bbc iplayer descktop it goes much higher without the same problem.

thanks for your help

simon

---

### Post by RomeReactor on 2009-02-10
I suggest creating a "Downloads" folder within your home directory and redirecting Transmission and/or BitTorent there, along with the files, to see if that makes a difference. Do you have enough free space in your hard drive? Also, maybe the 512 MB of RAM have something to do with it.

---

