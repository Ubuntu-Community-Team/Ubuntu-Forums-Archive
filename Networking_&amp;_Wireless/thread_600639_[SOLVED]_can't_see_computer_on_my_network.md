---
title: "[SOLVED] can't see computer on my network"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by tyggna1 on 2007-11-02
I have three computers that all hook into a router (also running linux).

Dell inspiron running 7.04
IBM thinkpad running 7.10
Dell optiplex running 7.10


The Inspiron can see the thinkpad and can transfer files.   The thinkpad can't see anyone else, and the optiplex appears to be both blind and invisible to my network shares.   

I've tried using samba software--but have not had any luck getting any kind of connection.

I don't know the first thing about networking in Linux--so it would seem.   I went to administration and shared folders using the SMB (windows) protocol.  All I really care about is the optiplex--as I use it as a home server.

Could someone please give me a few helpful commands/hints to fixing this?

---

### Post by tyggna1 on 2007-11-02
anyone know of any useful man pages for this problem?

---

### Post by tyggna1 on 2007-11-02
I've tried 
> sudo aptitude reinstall smb* samba*
on my optiplex, but I still can't see anything when browsing the network.   Someone please help, I'm lost here and I feel like I'm groping around in the dark.

---

### Post by tyggna1 on 2007-11-02
helpful links would be appreciated

---

### Post by tyggna1 on 2007-11-02
thanks for mentioning the nfs community documentation, or even the samba community documentation.   Even if I'd have been called a noob, info is info. 

 :( sadness :(

solved by mounting after installing nfs-kernel-common and editing the /etc/exports file.

read  [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo") if you find this post and you're trying to link between to linux machines.

Read [here]("https://help.ubuntu.com/community/SettingUpSamba") if you have problems with networking with windows.   Chances are, if that doesn't work, then you should go and complain to microsoft to release their TCP/IP code so the linux developers can start compensating for their mistakes.

Solved!

---

### Post by de_valentin on 2007-11-10
I have a very similar problem, I can see my wife's xp-desktop and the NAS (that runs on linux) and even my virtualbox xp in the network folder but ubuntu refuses to show itself. Same goes for my Gutsy laptop. 

I have tried many howto's untill now but I just gave up, more or less. So when I found your thread I had my hopes up again. 

Well I can share files through the virtual xp which of course is not the normal way but hey it works.

Bummer on the community though:(

---

### Post by de_valentin on 2007-12-02
I created a new thread on this maybe there will be some answers here.

[Ubuntu invisible on network]("http://ubuntuforums.org/showthread.php?p=3876788#post3876788")

---

