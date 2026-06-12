---
title: "How to change the default address Phreebooks logs in with?"
date: 2014-05-01
forum: Networking &amp; Wireless
---

### Post by John_McAdoo on 2014-05-01
I recently set up a LAMP server at home to get Phreebooks installed for my business. Going through all the steps I got it set up and working. I realized today, however, that when I got to the office to run the software, it would not log in. It was trying to use the default private IP (192.xx.xx.xx) while my business runs on the (10.xx.xx.xx) private IP scheme.

My question is, can I change the ip address so that I do not have to reinstall the software or do I need to redo it? If I need to change the IP address, is Apache the program I need to log into to change it?

---

### Post by John_McAdoo on 2014-05-01
I just wanted to repost here and say that I figured it out with some trial and error. Just to help pass the knowledge on to others who may run into the same issue, if you instal at home from a different ip address, you can NANO or VI the configure.php file in your includes folder to match the ip address needed. Restart apache and log back in and good to go!

---

