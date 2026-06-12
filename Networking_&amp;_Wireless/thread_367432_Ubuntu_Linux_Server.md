---
title: "Ubuntu Linux Server"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by JackOuzzi on 2007-02-22
Hi,

New to forum but been 'fiddling' with Linux for some time (a number of distro's)
I have a spare PC (dont ask) P4 2.8Ghz 1Gb memory 160Gb Disk with a small 8Gb secondary disk which I would like to setup as a 'server only' to my home network of 2 (other) desktops and a laptop with a combination of wired and wireless access and all running Windows XP which I need to keep on the other machines. Any advice as to the 'best way to go' would be appreciated, many thanks. Ubunto not yet loaded onto 'spare' ...

JO

---

### Post by chili555 on 2007-02-22
I think it really depends on what you see this server doing for you and your family.

I have an old-timer (Pentium 3, 733Mhz, 256Mb RAM) running on a shelf in the garage. We use it as a backup server. About weekly (I know, I ought to set up a cron job to run automagically), I synchronize both my wife's and my /home to the server. Rsync is set up to add files that have been added and delete files that have been deleted.

If this is about what you want to do, I would install Ubuntu server using the 8Gb disc for / and swap and the 160Gb for /var. In a server, /var/www/html is where the goods are stored.

I would look at any of several excellent LAMP howto's, such as this one: [http://www.debianadmin.com/ubuntu610-edgy-lamp-server-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu610-edgy-lamp-server-installation-with-screenshots.html)

I would then fire up a WYSIWYG html editor and create an easy-to-navigate web page that simply navigates to your files. It needs be no more elaborate than:

[CENTER]Welcome to Chili's Server[/CENTER]

[LEFT]Click for /chili[/LEFT][RIGHT]Click for /mrschili[/RIGHT]

Set up the server with a static IP and then those within the LAN can see their stuff at [http://192.168.1.xxx](http://192.168.1.xxx). Bookmark that page.

Good luck and have fun!

---

### Post by MetalMusicAddict on 2007-02-22
JackOuzzi. chili555 is right. It comes down to what you want to do.

I have a machine as just a file/print server running headless. Well I dont know if "server" is the best word. :) I run Xubuntu on it and control it via VNC. More just a desktop with a TB of storage and bunch of shares. :)

---

