---
title: "How do I access program functinos remotely?"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by Maheriano on 2008-09-26
I've seen all the threads on SSH and remote desktop but I have a specifically different request. I want to be able to create a simple webpage in whichever language and have the choices mapped to functions on my Desktop.

For example, I have a >> button on the webpage and when I click it, it changes the song in Audacious on my desktop. The overall function I'm looking for is to be able to use my Blackberry as a remote control to be able to change the song, volume, anything else related to media. There's no infrared and bluetooth might not reach all around the house. Any ideas?

---

### Post by Maheriano on 2008-09-30
bump

---

### Post by rsambuca on 2008-09-30
What you are kind of asking for is to design a website that will hack into your desktop.  Don't you think this is a little bit of a security risk?

---

### Post by Maheriano on 2008-09-30
Could it be? If so then I could just take care of it with good security. But I was hoping to just have the media functions mapped and that's it. Kind of like remote desktop very, very stripped down.....and people do remote desktop all the time without security risk so how is it different?

---

### Post by rsambuca on 2008-09-30
Most remote desktop apps will use some sort of encrypted secure shell (SSH) tunnel to go from one computer to another.  If I understand you correctly, you want to access a website with one computer, and somehow have that website then execute a command on another PC?

I think you should use something like freenx and nxclient to control your desktop securely.

---

### Post by Maheriano on 2008-09-30
Okay, sounds like this is going to be too computational-intense for my Blackberry to do so how about doing it through Bluetooth? Most of the time when I want to change the song or volume I'll be close enough for Bluetooth so would that be more secure and easier to make?

---

### Post by Maheriano on 2008-12-15
Since I first asked this question I have set up Apache2 on my desktop and am now able to access websites on it via my Blackberry. So would it be possible to access a website that is on my physical machine and have it access the media functions on that same machine? I could password protect the site or something. Will this work at all?

---

### Post by smetj on 2009-02-15
Hello Maheriano,

Maybe not an immediate complete solution for what you want to achieve, but check out [http://www.smetj.net/wiki/Teleporter](http://www.smetj.net/wiki/Teleporter).  It allows you to remotely execute commands on a box over http(s) and process the output of the command on the client.

Cheers,

Jelle

---

