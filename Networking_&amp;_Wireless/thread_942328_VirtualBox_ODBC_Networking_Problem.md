---
title: "VirtualBox ODBC Networking Problem"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by Falcon397 on 2008-10-09
I have been searching long and far for a solution but have hit a wall.  What I want to do seems simple, perhaps I should post to the newb forum.  But in any case I am trying to get my host machine (Windows XP Pro) to setup an ODBC connection to my VirtualBox Ubuntu PostgreSQL database.  I have done what it suggests to do in the manual, using vboxmanage to set the NAT to forward off TCP packets that access port 5432 to the virtual machine with limited success.  I want to use Access as a front end and PostgreSQL as my back end, but I would much rather use Ubuntu to serve the database than Windows.  I am thinking that it is either I am using the wrong address for the guest machine or the guest machine cannot accept an ODBC connection.  My address in ifconfig is 10.0.2.15, but from what I understand about NAT's is that is just another network, so typing in that address from my host is not going to accomplish anything since it is on a different network altogether.  Any help would be appreciated.

---

### Post by FrostyFlames on 2008-10-09
[http://forums.virtualbox.org/viewtopic.php?p=6924#6924]("http://forums.virtualbox.org/viewtopic.php?p=6924#6924")

I'm not sure if that will work exactly for you. The only other thing that I can think of at this late hour would to just bind the linux VM network adapter to a host interface. The following picture shows that setup. That will create another NIC that you can access it from that is locally.

---

