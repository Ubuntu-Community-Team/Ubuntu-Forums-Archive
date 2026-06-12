---
title: "Unable to burn DVDs in Karmic"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by sarayuvijay on 2009-12-19
Like I said in my other posts I am new to Ubuntu and the initiation has not been a smooth ride. Problems not withstanding I am enjoying using Ubuntu. One of the few remaining unsolved problems is that I am unable to burn DVDs in Brassero. I couldn't while I was using Jaunty and hoped that after upgrade to Karmic this issue might get resolved but it did'nt. My Brassero version is 2.28.2. Whatever type of disc I use whether DVD +R or DVD RW the results are the same. When I try with Brassero the first few steps go ok. then I get an error message stating "please replace the disc with a supported cd or DVD. It is not possible to write with the current set of plugins".  
When I try with cd/dvd creator and click on write to disc I see a window titled "Burning Data DVD" and below that a bar moving endlessly across the window  titled "creating checksum  for image files". Nothing happens after that.
Can somebody please help in fixing this problem.
Thanks
Sarayuvijay

---

### Post by rburkartjo on 2009-12-19
sara try using the k3b program

---

### Post by joes7 on 2009-12-19
Download an Open Source CD Burner such as Alcohol 120%.

---

### Post by Extract_Here on 2009-12-19
+1 for alcohol 120%

---

### Post by ankspo71 on 2009-12-19
Hi,
Have you tried disabling all available plugins in Brasero? Have you tried any other cd burner programs? Ubuntu has several to choose from in the repositories. K3b, gnomebaker, xfburn just to name a few of the bigger ones. Switching burning programs has helped alot of people who had trouble burning. Also, you could try burning another cd by launching ' brasero ' from the terminal to see if it reports any errors. It's never hurts to check, and if it does report errors, at least you'll have some error info that can help solve the problem. 

Currently I am using Ubuntu 10.04 (alpha testing release) and I am having cd/dvd burning troubles again like I did when Ubuntu 9.10 first came out. I can't burn anything, with any program (again), on either of my different dvd burner drives, which is extremely rare as far as I can tell. My cd's are said to be successful burns, but they don't work at all and I have to throw them away, even the rewritable cds. I'm just that lucky I guess. :P  

Anyways, I'll be watching your posts to see if you have any success because it could also help me too.

---

### Post by space-cake on 2009-12-20
Hi, 

Does anyone here have an idea where the default cd/dvd burner in Ubuntu 9.10 stores its temporary files? I looked in the temp folder, but didn't find anything there. 

Yesterday I wanted to burn a dvd, but then I stopped the program halfway through the making of the iso file. Since then every time I start Ubuntu I get a message that I have too little disk space. My guess is that the cd/dvd burner has stored the iso file somewhere and not deleted it after I stopped the program. 

But where could this be?

---

### Post by space-cake on 2009-12-26
I found it. For anyone who might wonder, Brasero stores the temporary iso files in the home folder. 

[Duh. Now that I've found the file I was looking for it looks kind of obvious, I know.]

---

