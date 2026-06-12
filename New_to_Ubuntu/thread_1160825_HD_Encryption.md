---
title: "HD Encryption"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by myolbug on 2009-05-16
Am I able to encrypt my hard drive after I have installed Ubuntu?  I was given the choice when I installed 8.10, but I recently did the online upgrade and I am just wondering.

---

### Post by ViperChief on 2009-05-16
I don't personally use Ubuntu, but if you don't get any other replies, try out [http://www.truecrypt.org](http://www.truecrypt.org) One thing I like about them is that you can actually hide your entire OS and create a dummy one. Your password determines which OS it boots into so that no one will ever know the other exists.

---

### Post by HermanAB on 2009-05-16
Yes, but...

You can encrypt the /home partition, but you first have to copy your data to another partition, then encrypt /home and finally copy the data back again.  

There is a wizard called gnome-luks-format that can do it, but even with the use of a wizard, this is all rather complicated and hard to guide someone through.  Your best bet is to re-install - it only takes about 30 minutes anyway.

---

### Post by Lampi on 2009-05-16
> **myolbug said:**
> I was given the choice when I installed 8.10
That was about encrypting home only, wasn't it? In Jaunty this is done by eCryptfs. There is also a similar tool called encfs. Last but not least for full disc encryption there is LUKS. Keep in mind they dramatically slow down file access performance, so you might only want to encrypt your data, maybe only *some* of your personal data. It's up to you.

---

