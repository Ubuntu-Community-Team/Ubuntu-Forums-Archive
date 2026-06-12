---
title: "Amule and Internet problems"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by FranciscoBagulho on 2007-03-15
Hi!

since I've installed ubuntu edgy, I can't have a decent upload average on aMule and as a result of that my download list takes a eternity to complete, problems that in windows xp, 45 days ago, didn't happened, or anything close to this problem.

well, this wouldn't be a huge problem except, when I have aMule online, I can't surf on the web properly, and have aMsn online more than 3 minutes.

my computer and internet specs:
-amd64 3500+ venice, dfi lanparty nf4 ut, 1gb ddr, x300SE.
-netcabo(Portuguese ISP) 8Mbit/512kbit, thomson tcm425 cable modem, wireless-g router(I think this is a Matrixx brand).

on aMule the maximum upload rate is 16Kbytes/s, maximum connections 300 and maximum sources per file 500, all the other options are default.

the only tweaks I've made are: tcp-ip as in this  [link](http://www.ubuntuforums.org/showthread.php?t=251509) and ipv6 off as shown in this [link](http://www.ubuntuforums.org/showthread.php?t=87798).

still after that I can't notice any improvements. any thoughts on this issue would be great. 

in this image [http://img110.imageshack.us/img110/227/uploadvl8.png](http://img110.imageshack.us/img110/227/uploadvl8.png) are my aMule stats.

Ps: all port redirection on my router are 100% correct so, lowid is out of the question.

Ps2: even before the tweaks I had the same problem.

---

### Post by FranciscoBagulho on 2007-03-16
come on guys, it's really annoying. 

doesn't this problem seem familiar to one you had in the past?

thanks anyway...

---

### Post by esaym on 2007-03-16
Hmm sounds interesting.  I don't have any problems at all with amule.  I have it on my desktop and I have the gui-less version on my webserver that I use though amule web feature.  Only thing I can think of would be to delete the user directory and re-install again.  ```
sudo aptitude remove amule
```

Then delete the emule user directory if it is not already deleted: /home/*yourusername*/.aMule

Then reinstall again: ```
sudo aptitude install amule
```

There is also a very good amule forum: [http://forum.amule.org/](http://forum.amule.org/)


I really don't understand why it would slow your connection if it is not uploading that much.  Perhaps there is another computer on your network that has another p2p app running and using all the bandwidth up???

Keep us updated :)

---

### Post by FranciscoBagulho on 2007-03-18
thanks for replying.

i've done the re-install 2 times including the cvs from the amule site.

there's no other computer draining the connection on my network.

the only reason that i didn't go to amule forums it's because I belive the problem is with ubuntu, since azureus haves the same problem(just tried this today), and when I download from rs.com sometimes the download gets "stuck" (i guess using firefox download manager doesn't help).

---

### Post by esaym on 2007-03-18
Oh, very interesting.  What network card do you have?

You can see with lspci

---

### Post by FranciscoBagulho on 2007-03-18
right now i'm using the nf4 ultra ethernet link, but with the marvell gigabit ethernet i have the same problem.

> ...since azureus **has** the same...

sorry it has been quite a while since i had a proper english conversation. :biggrin:

---

### Post by esaym on 2007-03-18
Well I am not sure what to say, I will think about this one.  In the mean time you might as well make a post on the aMule forum :D

---

