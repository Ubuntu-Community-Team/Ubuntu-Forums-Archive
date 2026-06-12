---
title: "how to downgrade from karmic to hardy"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by jml52187 on 2010-05-07
It is my understanding that lotus notes client 8.5 will not run on Karmic. I was wondering how to downgrade to Hardy (which I already have on another server which runs my Domino server) or Jaunty, if it is any better. Solutions are appreciated.
Thanx,
J

---

### Post by warfacegod on 2010-05-07
Downgrading is only theoretically possible. In practice its almost guaranteed to break your system. If I were you I'd:

01. Find a patch for lotus notes to get it to work in 9.10

02. Find a replacement app for lotus

03. Make a backup of all my data and install Hardy fresh

---

### Post by kwacka on 2010-05-07
Entering 'lotus notes ubuntu' into google led me to this: [How To Install Lotus Notes 8.5.1 in Ubuntu karmic 64 Bit]("http://www-10.lotus.com/ldd/nd85forum.nsf/0/69b50f2db7bb7b0b85257659005ab79e?OpenDocument")

If you're running a 32-bit machine you obviously won't need the ia32 libraries.

---

### Post by jml52187 on 2010-05-07
Tks to both of you.
warfacegod, I figured I would have to download and rip to disk a copy of hardy or jaunty and reformat. This machine will act as a client, and as such has no pertinent data on it. How can I access that? What are your thoughts on jaunty?
 
kwacka, to my knowledge there are not yet any patches and client for some reason will not run on karmic. maybe as a lotus notes (domino) server. Or I could have recieved faulty info. When trying to run the install file in terminal I recieved an "error creating child process..." prompt, and when trying to execute in terminal it can't find the file. I realize that my problem installing is a different than the ability of the program to run on karmic, but a thread that I came across said it just doesn't work.
 
Thanks again,
J

---

