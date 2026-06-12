---
title: "Help: Stranger in a strange land trying hard to learn and get file sharing going"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by BrianTheComputerWizard on 2011-05-01
Hello all,

I am very new to Ubuntu.  Currently I am running 11.04 desktop (if I have it right).  I've got it installed in an old Dell Dimension 4550 which is working beautifully.  The upgrade went well.  I followed directions to get samba running and configured. I also turned on sharing for 2 of my files - documents and pubic. My goal is to be able to share documents between windows and ubuntu machines as part of a project/business expansion I am working on.

My "native language" is Windows with a smattering of Dos and BASIC (just to date myself). I am quite comfortable with the whole command line editing routine and am unafraid to learn and follow directions. 

If there is somebody here who can help me to get the file sharing up and running, I will be headed in the right direction and most grateful. 

Thanks in advance for taking the time to help out a very confused new member of the Ubuntu community.

---

### Post by rosencrantz on 2011-05-01
You can manage sharing between Windows and Linux with a Samba server:
[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)
Generally, it's much easier to get Linux to see Windows shares than the other way round.

---

### Post by BrianTheComputerWizard on 2011-05-01
Thanks Rosencranz,

I followed the instructions. I can "see" my Ubuntu machine on the windows (xp) machines, but when I try to access it, I still get, "not accessable. you may need permission to use this network resource."  What am I not doing or doing incorrectly?

Thanks again for your help.

---

### Post by rosencrantz on 2011-05-02
Hm, that's a bit outside my expertise, I'm afraid -  I only used Windows in the past to access shares on Linux computers because the reverse is such a bloody nuisance, and right now I don't have any Windows machines to experiment with.
Do you have a firewall running on Ubuntu? You might have to open some ports, see these links
[http://ubuntu.swerdna.org/ubulanprimer.html](http://ubuntu.swerdna.org/ubulanprimer.html)
[http://www.linuxquestions.org/questions/linux-networking-3/samba-windows-xp-problem-samba-is-not-accessible-223649/](http://www.linuxquestions.org/questions/linux-networking-3/samba-windows-xp-problem-samba-is-not-accessible-223649/)

---

