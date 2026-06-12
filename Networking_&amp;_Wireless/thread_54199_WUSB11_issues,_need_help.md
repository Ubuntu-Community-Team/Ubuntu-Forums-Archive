---
title: "WUSB11 issues, need help"
date: 2005-08-03
forum: Networking &amp; Wireless
---

### Post by theinvictus on 2005-08-03
Alrite, I've done my best to search the forum and google for potential answers involving my wireless network card, however while there seems to be a plethora of information out there, there is very little that I understand.

I am a true newb, I just installed Ubuntu about an hour ago. I have a dual boot setup, and I connect to the internet on windows via the Linksys WUSB11 Wireless internet card that I am trying to get to work with linux.

Much of what I read includes downloading certain files, and I don't understand how i am to download those files into linux without an existing internet connection withing linux. 

This particular thread: [http://ubuntuforums.org/showthread.php?t=29554](http://ubuntuforums.org/showthread.php?t=29554)
involves the same card as mine.

I tried the steps advocated in the first few steps, and no matter what I did I got the 
E: Couldn't find package atmel-firmware

Also, when I searched for them in synaptic they couldn't be found. On a sidenote there were only some 8,000+ packages in there so I'm thinking I might be missing some update or something.

Could someone please be kind enough to create some step by step instructions, based on the assumption that I have yet to do anything to my OS, to help me get my USB wireless card working,

Thnx,
-TheInvictus

---

### Post by amohanty on 2005-08-03
I think you might have to enable the universe repos., to get amtel-firm....
Instructions at:
[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28Repositories%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28Repositories%29)

---

### Post by theinvictus on 2005-08-05
the packages still don't show up, even after I follow the directions on that site. Do I need an active internet connection in order to get them?

---

### Post by amohanty on 2005-08-05
Yup. Synaptic needs to download the packages.(tar.?).gz file to get a list of packages available in the repo.

AM

---

