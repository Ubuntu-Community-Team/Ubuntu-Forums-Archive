---
title: "Lost Password"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by bizmeds on 2009-03-25
Have need to change the password the webmaster has quit and we do not have the password. I tried to change the password: Asks for password how do I do this.

~$ passwd
Changing password for webmaster.
(current) UNIX password:

---

### Post by Hospadar on 2009-03-25
Here's a helpful page:
[http://www.linuxclues.com/articles/11.htm](http://www.linuxclues.com/articles/11.htm)

---

### Post by llamabr on 2009-03-25
Is this an ubuntu system?  Do any of your users have sudo access?  You want to change the root password?

---

### Post by bizmeds on 2009-03-28
Solved

Thanks for the link Hospadar. The article paid off in kudos! The site has some information of interest I spent a couple of days reading and implementing the tuts.

For your info llamabar it is in fact an Ubuntu 8.0.4 server system and luckily we didn't have any other users accessing the terminal. Here is what I did in case others have the same problem.

I booted the server in recovery mode (from the GRUB menu with the arrow keys) > press enter. Then run "passwd webmaster" I was then able to set new passwd then on reboot I was able to access.

---

