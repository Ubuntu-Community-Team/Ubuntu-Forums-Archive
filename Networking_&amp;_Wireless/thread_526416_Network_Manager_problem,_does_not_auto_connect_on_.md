---
title: "Network Manager problem, does not auto connect on login"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by opendevlite on 2007-08-15
Hello,

I am having problems with Network Manager; when I log in it doesn't auto-connect -- my solution is to left-click and select 'Wired Network'.  Is there a way to automatically connect this after logging in?

Thanks.

---

### Post by Steve1961 on 2007-08-15
I presume from your post that your using a wired connection rather than a wireless.  Go into system>admin>network and then into the properties dialogue for your wired connection.  Uncheck roaming mode and make sure the rest of your settings are OK.

---

### Post by opendevlite on 2007-08-15
it is already uncheck.

---

### Post by Steve1961 on 2007-08-15
Mmmm... OK, you could always try forcing it to connect by putting an entry in rc.local

sudo gedit /etc/rc.local

and put the following just before the exit 0 entry

dhclient eth0 (assuming eth0 is your ethernet)

Save and close and then do:

sudo chmod +x /etc/rc.local

---

### Post by opendevlite on 2007-08-15
by default, in Ubuntu 7.04, on connecting to the internet do you have to do it manually? through network manager?

---

### Post by Steve1961 on 2007-08-16
No, should setup everything automatically, but doesn't always work that way.

---

### Post by walkerk on 2007-08-16
I always recommend wicd for users. Most are usually happy with it.

[Click here for instructions]("http://ubuntuforums.org/showpost.php?p=3115947&postcount=20")...

---

