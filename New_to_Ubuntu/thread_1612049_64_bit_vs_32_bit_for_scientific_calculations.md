---
title: "64 bit vs 32 bit for scientific calculations"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by chemantics on 2010-11-02
I have been using Ubuntu to run scientific calculations using MIT Photonic Band software"MPB", see [http://ab-initio.mit.edu/wiki/index.php/MIT_Photonic_Bands](http://ab-initio.mit.edu/wiki/index.php/MIT_Photonic_Bands)

Now that my calculations are become more complex and time intensive, I am looking for ways to speed things up.  Currently, I am using an Intel Core 2 Duo E6600 but am thinking of building a machine (with grant money) just for these calculations with the following:
Intel i7 980X, Asus P6X58D, and 6 GB DDR3

Anyways, I am pretty sure that MPB is a 32 bit program.  If I build this machine, would the 64 bit version of Ubuntu be faster at these calculations than the 32 bit version?  Should I be worried about compatibility issues?  Any guesses on how much faster my new machine might be compared to the one I currently use?

Thanks,

Chemantics

---

### Post by Blutkoete on 2010-11-02
Hello!

As you can see [here]("http://packages.debian.org/en/squeeze/alpha/science/") there is a 64 bit version (pre-compiled for DEBIAN), so there shouldn't be a compatibiltiy issue (search for MPB on that page).

I would go for the 64 bit version, as it speeds things up with MATLAB (it allows better memory use & larger matrices). But of course you can't compare MPB and MATLAB.

The best thing to do is to ask your question on the MPB mailing list.

Best regards,

Blutkoete

---

### Post by tom.swartz07 on 2010-11-02
Im not too sure about simply using a more powerful processor. 
I help my professor with Astrophysics research- our calculations are really intense and would take hours on 1 machine (Pentium 4-ish era). 

Instead we use a cluster. A cluster is a group of computers (in our case, a modest 3) that all run calculations across the 3 processors at the same time. Youre getting it done just as fast.


Rather than spend a ton of money on a new system, look and ask around to see if you could get your hands on some older machines and make a cluster out of them.


That being said, 64bit will allow you to take advantage of larger amounts of RAM, and allow you to keep 'larger' numbers in play during your calculations. 


Best of luck! Hope it helps!

---

### Post by bioterror on 2010-11-02
> **Blutkoete said:**
> Hello!

As you can see [here]("http://packages.debian.org/en/squeeze/alpha/science/") there is a 64 bit version (pre-compiled for DEBIAN), so there shouldn't be a compatibiltiy issue (search for MPB on that page).

I would go for the 64 bit version, as it speeds things up with MATLAB (it allows better memory use & larger matrices). But of course you can't compare MPB and MATLAB.

The best thing to do is to ask your question on the MPB mailing list.

Best regards,

Blutkoete

My Linux Mint 9 (Ubuntu 10.04) has mpb in the repos.
Filename: pool/universe/m/mpb/mpb_1.4.2-14build1_amd64.deb

But yeah, you're doing heavy tasks with your machine and it seems to use 64bit system more wisely than 32bit system.

---

### Post by bioterror on 2010-11-02
:twisted::twisted:> **tom.swartz07 said:**
> Im not too sure about simply using a more powerful processor. 
I help my professor with Astrophysics research- our calculations are really intense and would take hours on 1 machine (Pentium 4-ish era). 

Instead we use a cluster. A cluster is a group of computers (in our case, a modest 3) that all run calculations across the 3 processors at the same time. Youre getting it done just as fast.


Rather than spend a ton of money on a new system, look and ask around to see if you could get your hands on some older machines and make a cluster out of them.


That being said, 64bit will allow you to take advantage of larger amounts of RAM, and allow you to keep 'larger' numbers in play during your calculations. 


Best of luck! Hope it helps!

I also think about this one, but I dont bealive that 3 old P4's or something like can beat a newer i7 with like six cores (12 threads!! :twisted: ).

Ofcourse if those P4's are above 2GHz and supports by that Hyper-Threading, it might come close. But how about power consumption? P4's arent the greeniest CPU's on the market ;))

One thing could be buying a helluva load of old xbox's, install debian or gentoo based linux distribution and make a cluster
[IMG]http://pictures.xbox-scene.com/hsdemonz/XboxCluster/ClusterX-2.JPG[/IMG]

But those are old machines nowdays ;D

---

