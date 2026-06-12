---
title: "Dell Inspiron 1501 Ethernet Detected-Internet Not Working"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by A Silver Mt Zion on 2007-01-21
[solved]

For some reason the internet worked when connected to my router but not to my modem. I have no clue why, but that is just how it is.
Thanks for all those who replied!

---------------------------------------------------------------------------------


I was just able to get ubuntu 6.10 on my dell inspiron 1501 using some hints from these forums (thanks for all the help), and now I am trying to get wi-fi to work. I found the thread that shows how, but I must get my physical ethernet working first to do this. My physical ethernet is detected and is recieving/sending, but the internet itself will not work. I can't figure out why not! It appears as if others using the same laptop have had no trouble, but for some reason the internet just won't connect. 

Anything at all is appreciated!

---

### Post by redDEADresolve on 2007-01-22
bump, I wonder whats going on here. It should work. Have you checked to make sure the connection is enabled?

Make sure you don't need a login name and password?

I'm throwing stuff at a wall

---

### Post by mindwarp on 2007-01-22
Please do the following:
[LIST=1]
[*]Post the output of "sudo route -n"
[*]Post the output of "ping www.yahoo.com"
[*]Post the output of "sudo traceroute www.yahoo.com"
[*]Post the output of "cat /etc/resolv.conf"
[*]Post the output of "ifconfig -a"[/LIST]

---

