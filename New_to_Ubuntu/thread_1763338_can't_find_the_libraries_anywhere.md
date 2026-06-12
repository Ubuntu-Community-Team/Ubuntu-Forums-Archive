---
title: "can't find the libraries anywhere"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by janbaztaimur on 2011-05-20
Hello Veterns...
                         I am preparing the Ubuntu 11.4 for emulating ASA in GNS3. The tutorial i have ask me to install the libraries. Here is the complete command

root@hardstone:~# sudo apt-get install libncurses5-dev zlib1g.dev libpcap-dev

this is the answer i am getting

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

what am i missing.

Taimur

---

### Post by TeoBigusGeekus on 2011-05-20
Close the Software Centre and/or Synaptic.

---

### Post by janbaztaimur on 2011-05-21
> **TeoBigusGeekus said:**
> Close the Software Centre and/or Synaptic.
 
i've managed the packages in .DEB formats but now when i am installing them using the Software Center it shows a message that "aptdeamon has encountered a problem and can't install the software".

Do i have to uninstall and reinstall it or what.

A Million thanks in advance.

---

### Post by TeoBigusGeekus on 2011-05-21
Give the following commands
```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
```
and then try again.

---

### Post by janbaztaimur on 2011-05-21
> **TeoBigusGeekus said:**
> Give the following commands
```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
```and then try again.


yeeeeeeeeeehaaaa... 

the problem is solved.

last but not the least

how can i use all of the updates that i've downloaded through apt-get on another computer that is not connected to the internet.

---

### Post by TeoBigusGeekus on 2011-05-21
Take them with a flash drive or something and move them to the other computer. You could run them by double clicking them.

...However, I don't think this is a safe method of updating your pc, as you don't know beforehand which updates the system needs; you could end up borking it.

---

### Post by janbaztaimur on 2011-05-21
i know you must be a busy person and don't have time to write a whole tutorial for me. But you can refer me to a link where i can find the solution for this problem and its related problems.


Taimur

---

### Post by Lateralis on 2011-05-21
I only found out about this earlier on through another post on here, so I don't really know how useful this is.  But you might like to check out the [Keryx project]("http://keryxproject.org/").

---

### Post by audiomick on 2011-05-21
> **janbaztaimur said:**
> yeeeeeeeeeehaaaa... 

the problem is solved.

last but not the least

how can i use all of the updates that i've downloaded through apt-get on another computer that is not connected to the internet.

Herman, whose site is worth a look in itself, has a couple of links here

[http://members.iinet.net.au/~herman546/p13.html#Back-up_and_Restore_Added_Software]("http://members.iinet.net.au/%7Eherman546/p13.html#Back-up_and_Restore_Added_Software")

that might help.

---

