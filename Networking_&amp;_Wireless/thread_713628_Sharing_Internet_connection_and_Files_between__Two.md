---
title: "Sharing Internet connection and Files between  Two PC's"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by arindom on 2008-03-02
I have two PC's. One with Ubunt 7.10 (which is connected to the Internet via Cable Broadband) and another PC where I have Win loaded. I have added an Ethernet NetWork Card in the Ubuntu PC via which I am trying to connect the Win PC.

I have connected both the PC's via Cable. And I have also assigned local IP to both of them.

So when I ping from Win PC to Ubuntu PC I can ping and when I ping from Ubuntu PC (works only if I am pinging from Win PC) I can also ping.

My questions are  :
a) How do I set up my Win PC so that I can access the Internet?
b) How can I share files among the two PC's?
c) Is this arrangement safe?

I have firestarter installed in Ubuntu PC where I have allowed sharing the Internet option.

Any help in this matter will be great for me.

---

### Post by superprash2003 on 2008-03-03
first your need to enable Internet

---

### Post by superprash2003 on 2008-03-03
first your need to enable Internet connection sharing in ubuntu... there is a good tutorial here [http://www.ubuntuguide.org](http://www.ubuntuguide.org) ..search for internet connection sharing... to share files you need to install samba in ubuntu... a very useful tutorial on this is available in the link above.. just search for samba..
  Yes it is indeed safe...Since you have enabled sharing option in firestarer it should work..enable DHCP in firestarter and go to the xp macine and go to network properties.. go to local area connection properties.. and select tcp/ip properties.. there set it to automatically assign ip.. if you have not set up dhcp in firestarter.. then manually type  the ip in the tcp/ip properties

---

### Post by arindom on 2008-03-03
Thanks  for the help. Now I have been able to connect the PC's.

---

