---
title: "Wireless Settings Not Saving"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by esc1 on 2007-06-27
I have my /etc/network/interfaces set up for my wireless but when I boot I have someone elses connection.  It is a network I connected to with manual connection before.  Even though manual connection is saved for my network it always gets the other connection on start.

---

### Post by esc1 on 2007-06-28
Bump

---

### Post by Anonymvs on 2007-06-28
Have you disabled roaming mode?

---

### Post by esc1 on 2007-06-28
Yes.  It is unchecked.

---

### Post by Anonymvs on 2007-06-29
How about changing the file then making it immutable with the chattr command?

---

### Post by esc1 on 2007-06-29
The file never changes when connected to another wireless network.  :-k

---

### Post by esc1 on 2007-06-30
Any guesses?

---

### Post by Perfex on 2007-06-30
My suggestion is to rid your self of network-manager and use wicd you will be much happier
[http://ubuntuforums.org/attachment.php?attachmentid=36648&d=1182982852](http://ubuntuforums.org/attachment.php?attachmentid=36648&d=1182982852)

---

### Post by esc1 on 2007-07-01
I went to add/remove and took off network manager but it is still on my system.  When I try and install wcid it tells me network manager conflicts with it.  I also see network manager still comes up under system, admin, network.  Do I have to log in as root to remove it?

---

### Post by imdano on 2007-07-02
You should just be able to use sudo.  Make sure you remove both network-manager and network-manager-gnome.

edit: Also I'd recommend getting the newest version of wicd (1.3.0) from [http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

