---
title: "some questions on a separate home parttion"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Rayob on 2008-12-22
I have recently installed ubuntu 8.10 on approximately 30 gb of free space that I made by shrinking Vista. I am quite happy and everything is working well. However I like the idea of having a separate home partition so that anytime in the future I can install the latest version of ubuntu and not lose my stuff. I have read up on how to do this, but as a complete novice it looks too complicated for me. My question is, if I did a fresh install, and at the partitioning stage, make 3 partitions, one for the ubuntu os of about 7 or 8 gb, a home partition of about 20 gb and a small swap partition, and then carried on with the installation. Would my docs and pictures be automatically stored in the separate home partition, or would there still be a home folder as present and if so would this cause conflict. Hope I'm making some sort of sense. Any answers in simple terms would be mast appreciated.

---

### Post by Duck2006 on 2008-12-22
It's a good idea to have a home partition so if you have to do a reinstall or you upgrade to a new ubuntu install you still have your stuff saved. this will help in making one.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by drs305 on 2008-12-22
During the install when you set up the partitions you would designate one as /home. Your configuration files and default home folders would all be set up in /home/yourusername. There would be only one $HOME - i.e. there wouldn't be a /home used in your / partition.

Presumably that is where you would keep your data unless you decide to make a separate paritition for data/music/etc, which is what I do.

---

### Post by MeeMaw on 2008-12-22
> **Rayob said:**
> Would my docs and pictures be automatically stored in the separate home partition, or would there still be a home folder as present

If you re-partition and make a separate /home  your install from there will put your stuff in your new separate /home and install the rest of Ubuntu in the root folder. 

Make sure you save any files you need, because you will probably be formatting those two partitions, but after you do that, you will have your dual boot with a separate /home.

Welcome to Linux!!!!!

(drs305 beat me to the post!)    :P

---

### Post by Rayob on 2008-12-22
Thanks to everyone that seems to answer my question, and will get round to doing a fresh install soon. Sorry I didnt make that partition when I was originally installing, but always good to learn, Thanks again

---

### Post by Duck2006 on 2008-12-22
> **Rayob said:**
> Thanks to everyone that seems to answer my question, and will get round to doing a fresh install soon. Sorry I didnt make that partition when I was originally installing, but always good to learn, Thanks again

If you have the space to make a home partition, you can do it now with the link i posted for you.

---

### Post by namdung on 2008-12-22
Is it possible to have the Home folder saved in a network server so that it is accessible from any PC connected to the server? The users can logon using AD credentials.

---

### Post by M4rotku on 2008-12-22
I think you might want to look into thin clients.  Assuming that you want more than one user to be able to do this.

[https://help.ubuntu.com/community/ThinClientHowto]("https://help.ubuntu.com/community/ThinClientHowto")


That link is a bit outdated, so it might not work for the install.  I just wanted to give you an idea of what they are.

---

### Post by namdung on 2008-12-22
> **M4rotku said:**
> I think you might want to look into thin clients.  Assuming that you want more than one user to be able to do this.

[https://help.ubuntu.com/community/ThinClientHowto]("https://help.ubuntu.com/community/ThinClientHowto")


That link is a bit outdated, so it might not work for the install.  I just wanted to give you an idea of what they are.

No I'm not looking for Thin Client solution but rather roaming profile/redirected folder like in Windows. 
Thanks for prompt reply.

---

### Post by kansasnoob on 2008-12-22
> **Rayob said:**
> I have recently installed ubuntu 8.10 on approximately 30 gb of free space that I made by shrinking Vista. I am quite happy and everything is working well. However I like the idea of having a separate home partition so that anytime in the future I can install the latest version of ubuntu and not lose my stuff. I have read up on how to do this, but as a complete novice it looks too complicated for me. My question is, if I did a fresh install, and at the partitioning stage, make 3 partitions, one for the ubuntu os of about 7 or 8 gb, a home partition of about 20 gb and a small swap partition, and then carried on with the installation. Would my docs and pictures be automatically stored in the separate home partition, or would there still be a home folder as present and if so would this cause conflict. Hope I'm making some sort of sense. Any answers in simple terms would be mast appreciated.

IMHO don't bother! If you should somehow hose 8.10 and need to reinstall it would be a great benefit because you could largely leave /home alone and all should be fixed *maybe!*

I find it much better to create a separate data partition (I use external drives) and store all important data completely separate from any OS. Using "pmount" which is available in synaptic I find external drives easily mountable and I can not only store my data safely, but I can access it easily on any computer!

Just one opinion!

---

