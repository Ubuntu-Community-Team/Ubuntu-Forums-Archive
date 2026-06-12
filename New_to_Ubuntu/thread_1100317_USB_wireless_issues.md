---
title: "USB wireless issues"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by David Battley on 2009-03-19
I hope that someone is able to help me - I was uncertain whether this belonged in "Absolute Beginner Talk" but on the basis of my lack of knowledge about Linux it would be helpful if any solutions are given in beginners language...

I have been using Ubuntu 8.04 (386) as a dual-boot system, maintained and updated to the latest version as at the beginning of this month and it has worked flawlessly, UNTIL...

I have a wireless connection via a USB dongle which worked until I foolishly disconnected it live (I pulled the wrong wire out of the back :() and now it will not recognise the wireless adaptor at all.

On the advice of my more experienced friend I disconnected the stick, deleted the /etc/udev/rules.d/70-persistent-net.rules, and rebooted and sure enough this replaces itself without the reference to the USB dongle.  The theory was that reconnecting the USB stick would then "reinitialise" the connection.  There is a load of gumpf in the system log when I do which ultimately suggests that it has failed to initialise correctly.

Having done this, if I simply reboot with the USB stick in I get a kernal panic, but taking the stick out loads correctly, apart from no internet connection (though it still works in Windows).

I would be happy to post eg the system log or any other outputs here as advised but as you can probably appreciate this is tricky and very time consuming given the need to reboot twice everytime to get back to the internet...

Any help/advice gratefully received!

Kind regards,

David

---

### Post by yeats on 2009-03-19
Hi and welcome to the forum.

A lot of issues like yours caused by hardware tend to get passed over in this forum (Absolute Beginner Talk).  I would consider re-posting (or asking a moderator to move your post) to the Networking and Wireless forum if no one provides a helpful response.  

My only advice would be to investigate the logs in /var/log, especially dmesg* and syslog* to see if there's any thing useful in there.  I have not had a similar problem so I'm not sure what to advise ...

Good luck.

---

### Post by David Battley on 2009-03-19
Thanks Chris, for your welcome and advice.  I have reposted in wireless issues.

If a moderator sees this please feel free to lock, or else let it slide into forum oblivion... :)

Kind regards,

David

---

