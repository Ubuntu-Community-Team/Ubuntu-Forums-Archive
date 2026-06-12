---
title: "What is firestarter blocking?"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by edm1 on 2007-11-27
Before i start...I dont want to hear how firestarter isn't a firewall, that general theme seems to dominate any post stating a problem with firestarter. My problem isn't with the gui but the firestarter daemon loading the rules into iptables.

Anyway, i am no networking wizz so i was hoping someone could shed some light. The problem is that since installing firestarter i am no longer able to see any windows shares on my network and Rhythmbox cant see any daap shares. This happens even though i allow samba, nfs and daap ports in my policy. If i completely disable the firewall i have no problems, i am able to see and use all shares, also, i can re-enable the firewall once i'm connected to a share i also have no problems. It seems firestarter is blocking my ability to "see" others on my network.

My only guesses so far are that it has something to do with portmap but i cant figure it out. I hope someone can help point me in the right direction. Thanks.

---

### Post by pneaveill on 2007-11-27
> **edm1 said:**
> Before i start...I dont want to hear how firestarter isn't a firewall, that general theme seems to dominate any post stating a problem with firestarter. My problem isn't with the gui but the firestarter daemon loading the rules into iptables.

Anyway, i am no networking wizz so i was hoping someone could shed some light. The problem is that since installing firestarter i am no longer able to see any windows shares on my network and Rhythmbox cant see any daap shares. This happens even though i allow samba, nfs and daap ports in my policy. If i completely disable the firewall i have no problems, i am able to see and use all shares, also, i can re-enable the firewall once i'm connected to a share i also have no problems. It seems firestarter is blocking my ability to "see" others on my network.

My only guesses so far are that it has something to do with portmap but i cant figure it out. I hope someone can help point me in the right direction. Thanks.

Not sure if this will help, as much to comfort you to know that you are far from alone with this issue as I have discovered around cyberspace. I, too, am facing these similar problems. Once I loaded firestarter on this machine, it was invisible to the rest of my network. Yet, oddly enough, I could print to the print server down in the basement.

---

### Post by timcredible on 2007-11-27
might be more effective to start a thread titled 'what port does samba browse use?' or something like that since you're not really have a problem with firestarter, but need to know what port to open.  fwiw, there's a 99% chance you don't need a firewall

---

### Post by edm1 on 2007-11-27
i know what port samba uses 137-139 and 445, i think. Thats the entire problem. It appears there is something else firestarter is blocking but im having extreme trouble figuring what it is.

---

### Post by Ocxic on 2007-11-27
could be netbios,, I know windows uses that i think

---

### Post by edm1 on 2007-11-27
they are ports 137-139 which is covered by enabling samba ports.

---

