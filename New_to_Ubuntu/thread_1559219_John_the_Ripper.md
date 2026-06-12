---
title: "John the Ripper"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by newport_j on 2010-08-23
I am using john-the-ripper software to crack my own password. I started it last night and as of this morning it was still running. I am using the defualt brute force method and its warns you before you begin that this may take some time.
 
My question is should I be worried? My password is not that complicated, and I am assuming it will find it - eventually.
 
I am runing Ubuntu 10.04 and I used the the Synaptic package manager to install john-the-ripper, but I do not believe I got any word lists. Is there a better way to install it? Also, can I get word lists for free or do I have to pay?
 
 
James Yunker

---

### Post by J V on 2010-08-23
Get word lists and (If it's MD5/LM/NTLM) use rainbow tables...

---

### Post by newport_j on 2010-08-24
Okay, that is fine. But I have been runnig john-the-ripper now since Sunday night and it is now Tuesday morning. I am concerned that this running time might be excessive since I thought that most password cracking programs were fast. I am using the brute force method and it does give a warning about excessive time possible when using this program option.
 
Also, I am trying to crack the pasword on my own laptop. This is just an exercise. I am not sure how to use john-the-ripper to crack a password on a computer that I cannot log on to since I do not know the password! Let us say I have forgetten it. I assume one must use an Ubuntu live CD, but that does not have john-the-ripper installed on it. So how does one access john-the-ripper in this case?
 
 
Newport_j

---

### Post by newport_j on 2010-08-25
What are rainbow tables?
 
 
Newport_j

---

### Post by newport_j on 2010-08-25
Oaky, okay, I think that I know what rainbow tables are.
 
Newport_j

---

### Post by LiquidMeson on 2010-08-25
Ophcrack live cd, much easier. If that doesn't grab the pass export from ophcrack to plaintext.

---

### Post by newport_j on 2010-08-26
My JTR has been running since Sunday night. I get no indication of progress. It has not listed anything after my initial command. Is there a way to check on it without completely stopping it and having to start over?
 
Also, I believe that my password is an MD5 hash. I did not explicitly state that as an option on the command line. I am assuming that if I explicitly state that as an option then JTR will run much faster. So how do I get this option known to JTR?
 
 
James Yunker

---

### Post by Surkow on 2010-08-26
[This]("http://www.disenchant.ch/blog/teaching-john-the-ripper-how-to-crack-md5-hashes/106") page helped me to use the program for MD5 hashes.

---

### Post by Rubi1200 on 2010-08-26
This comes from a post by bodhi.zazen, who wrote the security stickies on the forum:
[http://ubuntuforums.org/showpost.php?p=9370460&postcount=4](http://ubuntuforums.org/showpost.php?p=9370460&postcount=4)

---

### Post by newport_j on 2010-08-26
I am running Ubuntu 10.04 so I am unsure if the instructions shown apply. I know there is a new patch and some other things are out of date.
 
Is there a later version of jtr than john-1.7.2.tar.bz2?
 
Is the latest patch still
 
john-1.7.2-all-9.diff.gz.
 
If there arer later versions please tell me!
 
Newport_j

---

### Post by dynamo2 on 2010-08-26
did you use the -w option with john? e.g ./john --wordlist=wordlistfile passwordfile

the official JTR site has a small collection of wordlists and cracking with wordlists should be much quicker than brute force. you could also do a search for wordlists, there are many free ones on the net.

as for the other point, you can try using Ubuntu Complete Remix 10.04 LiveDVD, it includes JTR, and you can copy a wordlist onto a USB flash drive and use that with JTR on the LiveDVD.

---

