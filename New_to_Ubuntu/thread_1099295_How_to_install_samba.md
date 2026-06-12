---
title: "How to install samba"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by steve70 on 2009-03-18
I need some research help, 

I've been googling all evening long to find how I can get my XP home PC to access files from my 8.10 PC using samba. Any good links (or advice?) to get this started?

---

### Post by Warren Watts on 2009-03-18
After reading several complicated guides to setting up Samba, I came across this guide:

[Howto: Quickly & Easily Setup Samba filesharing with windows for Ubuntu]("http://ubuntu-unleashed.blogspot.com/2007/08/howto-quickly-easily-setup-samba.html")

Using this HowTo, I had Samba up and running on the server in less than an hour and-a-half! Perhaps it doesn't get into all the nitty-gritty details of exactly how it all works, but for a quick-and-dirty guide I found it to be quite excellent. I would definitely recommend it for anyone trying to set up basic filesharing with a windows box.

---

### Post by bodhi.zazen on 2009-03-18
Should work out of the box.

In Ubuntu. right click a directory to share (you must have permission to read / write the directory). Do NOT share your home directory.

Select "Sharing options" -> Install Samba from the next menu.

After installing samba, log off and back on to ubuntu and again share a directory.

Then go to your windows box and map / mount a network share.

If you get stuck, we need to know where you got stuck and what you have done.

---

