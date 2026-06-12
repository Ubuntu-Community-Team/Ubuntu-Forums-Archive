---
title: "can a 165 gig HD be cloned to a 35 gig HD _ if only 25 gigs of data are on the 165 HD"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by s1baker on 2011-05-31
Hello,
Recently, I cloned a 35 gig HD ( with about 25 gigs of data on it ) to a 165 gig HD using clonezilla. Everything went beautifully and the 165 gig HD works perfectly. Now I would like to clone regularly the 165 HD to the 35 ( of course, as long as the data on the 165 does not surpass 35 gigs )
Can I do that?

Thanks

---

### Post by jerrrys on 2011-06-01
yes it can be done, but you will get a warning that this is not supported and there is a possibility of failure.  so if you do this on a regular basis, i would think that would be a bad gamble.

a 35G partition may be a better idea.

---

### Post by s1baker on 2011-06-01
so, I would need to create a 35 gig partition on my 165 HD and just clone that to the 35 HD?

---

### Post by CaptainMark on 2011-06-01
if you are just thinking about data backup then I would advise using rsync or its gui counterpart grsync, it syncs data to any other location, it wont re copy files if they havent changed so its very fast after the first run and only copies used space so wont throw you any error messages unless you go over your 35gb limit ```
rsync -a /path/to/source /path/to/destination
```is the command you need just replace /path/to/... with the paths of where you want to copy data from/to

---

### Post by s1baker on 2011-06-01
Captain, what I want to do is back up my 165 HD to my 35 HD about every 2 weeks because I am now using Ubuntu on my 165 HD to make my living. I have noticed that when the regular updates come in, there is the possibility of some programs to stop working in some manner, and I am worried about a program that I am depending upon to make my living not working after an update. Therefore I thought that if I could backup up my main working 165 HD before an update, I would have assurance that if something went wrong with the update, that I could at least fall back upon the backup 35 HD.

---

### Post by CaptainMark on 2011-06-03
okay well then i believe you want clonezilla if youd like a complete backup of your drive, im sure it only copies used space so it wont matter if the second hdd is smaller as long as you havent used that much or more on your main drive

---

