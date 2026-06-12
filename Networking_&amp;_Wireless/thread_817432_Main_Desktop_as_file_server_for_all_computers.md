---
title: "Main Desktop as file server for all computers"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by mattgaunt on 2008-06-03
Hey everyone

I am going to have plenty of spare time soon (Exams nearly finished) to set up my main desktop as a file server for uni work and also for sharing videos and music.

In my house I have a wireless router that everyone connects to and from that there is a wire into my room that I then connect to a router to connect my desktop to and occasionally my laptop, otherwise laptop is connected wirelessly.

I was hoping to get the following set-up but not sure how best to go about it.

1.) Make all files on my desktop readable, writable and also deletable from my laptop

2.) Make it so my house mates can read my video files and write video files to my computer but not delete any of them

3.) Be able to connect my laptop to wireless connection and still easily connect to my desktop (Not sure how the ip address sets up because the router that my desktop connects to and then that router connects to the wireless router which the laptop is connected to)

Anyone have any help or guidance for me? ooOoo also this is for mac, xp and vista (Just to make things fun lol)

If im stuffed then please feel free to say and ill drop this

Thanks all

Gaunt

---

### Post by superprash2003 on 2008-06-03
for file sharing you need to install samba [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html) ..you can share accordingly whatever folders you wish and set permissions.. pretty simple.
but i dont think its possible to set permissions in such a way wherein you can write but not delete.. its possible in ftp servers but i dont think you can do it in samba..
   could you explain your network setup a little more? how many routers exactly how they are placed etc?

---

### Post by mattgaunt on 2008-06-04
cheers for the help superprash

There are 2 routers, one wireless router that everyone connects 2 wirelessy, and connected to this wireless router is a secon router that is used just to split the connection to my desktop and laptop to.

Gaunt

---

### Post by superprash2003 on 2008-06-04
is DHCP switch ON on both routers?

---

### Post by mattgaunt on 2008-06-07
yeah just checked and DHCP is switched on for both of the routers

---

