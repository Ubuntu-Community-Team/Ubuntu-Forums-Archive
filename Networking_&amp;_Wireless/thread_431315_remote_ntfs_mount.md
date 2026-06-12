---
title: "remote ntfs mount"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by blahfod on 2007-05-02
HI guys,

I am an extraordinarily happy newbie to the Ubuntu community. Thanks for a fantastic product. I do have a request however, 

i would like to be able to access an NTFS hardrive that i have shared on my windows network from my ubuntu box. here's the details:
 I am running one computer (thinkroom) as a dual boot machine. I have a second computer (mediaroom) that is running only windows xp (for now). the mediaroom computer has a ntfs drive that acts as a shared drive on my windows network, it contains music and movies. I would like to be able to access that drive from my Ubuntu box (thinkroom). I understand that i have to mount it and then edit fstab to establish a permanent mount, but all of my attempts have ultimately ended in failure. Can someone take the time to explain what i need to do and dumby proof it. 

many thanks,

blahfod

---

### Post by pompeyjohn on 2007-05-05
polite bump

---

### Post by haloedrain on 2007-05-07
I'd like the answer to this too...
*bump*

---

### Post by dmizer on 2007-05-08
the only time you need to worry about ntfs is if the ntfs drive is in the same machine as your ubuntu box, AND windows is not booted.

if you want to mount a shared drive, it doesn't matter what file system is on the drive because the os sharing the drive controlls the read/writes to the drive.

have a look at the second link in my sig to mount your remote drive.

---

### Post by haloedrain on 2007-05-11
Thanks for responding!  I got a bit lost at the netbios name step.  The computer I'm connecting to has to be configured as a server?  I can't just use ordinary network share things like I can for files that are not on the second hard drive?

---

### Post by dmizer on 2007-06-04
sorry for the long delay in reply on this.  i've been too busy at work and haven't been able to catch up on all my posts.

follows is a bit of a jargon lesson:

any computer which shares information to other computers IS a server.  so, if your windows computer has a network shared directory available for other computers to connect to, your windows computer is a acting as a server.  it doesn't matter if it's "ordinary network shares" or otherwise, upon configuring your share you have configured a server.  servers are also often referred to as "hosts".

to further this a bit, any computer which connects to a server is a client.

in a common network, any computer can (and often does) act as both a server and a client, so it's important to keep in mind where the actual data exists, and which direction the data is traveling.

if you have more problems, please post in the howto thread, and i'll see your reply much more quickly.

---

### Post by blahfod on 2007-06-10
thank you so very kindly for help, my conversion to ubuntu is almost complete. All that remains is being able to synchronise my nokia phone.

once again, thank you 

blahfod

---

