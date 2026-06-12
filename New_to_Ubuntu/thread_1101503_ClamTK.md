---
title: "ClamTK"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by Wovaki on 2009-03-20
I am having a problem with my VirusScanner (ClamTK).

I downloaded ClamTK from the package manager, I have tried updating it, reinstalling, but nothing seems to work.

It says that there is 0 virus signatures.

In the "anti virus information" window it says:
[B]Build: ClamAV 0.94.2	

Signatures: 0	
()

GUI Version: 3.11[/B]

Could someone help me out please?

And please don't say "Anti virus is not needed" I know it is not necessary, but I want one for my own peace of mind.

Thanks

---

### Post by rburkartjo on 2009-03-20
wov, download the deb package on this link

[http://sourceforge.net/project/showfiles.php?group_id=131278&package_id=144061&release_id=661956](http://sourceforge.net/project/showfiles.php?group_id=131278&package_id=144061&release_id=661956)

---

### Post by rburkartjo on 2009-03-20
and wov bookmark this page to get the lastest updates 



[http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)

---

### Post by 123456789123456789123456 on 2009-03-20
Have you tried downloding the deffinitions file.
go to terminal
type sudo freshclam
it should update the deffinitions file.
get new deffs
I don't know why it is saying there are no deffinitions, unless, packet manager did not download all the files it wanted.  I used the add remove programs feature when I installed clam.

---

### Post by Wovaki on 2009-03-20
Thanks I got it, how come the version in the repos is not updated?

I also got another question, since I could not get this before I tried installing AVG for linux, but not I can't remove it.

Any ideas?

Thanks

---

### Post by rburkartjo on 2009-03-20
wov dont know why not updated in repos but keep that link i gave you when clamtk is updated you will have to go to website to update. also try this is terminal to remove avast open terminal type in sudo -i (notice the space between sudo and -i) then it will ask for you password just type it in you wont see your password but it will switch you to root user then enter the following command  apt-get autoremove avast. let me know how you do

---

### Post by SunnyRabbiera on 2009-03-20
ClamTK really isnt needed, nor any anvirus in Linux as Linux doesnt get windows viruses...

---

### Post by 73ckn797 on 2009-03-20
> **SunnyRabbiera said:**
> ClamTK really isnt needed, nor any anvirus in Linux as Linux doesnt get windows viruses...


YEP, someone had to say it!!:D

---

### Post by 123456789123456789123456 on 2009-03-20
sorry to disagree, but there are viruses out there for linux, mac and windows.  Plus there are a few windows viruses, that were created in java, and that can and have infected windows, mac, and linux computers.  So even if it is rare to get a virus, it does not mean that no protection is needed.

---

### Post by Sir Jasper on 2009-03-21
Hi 

I have Ubuntu 8.10 and W98SE dual boot and I use Wine.

I read the command is    gksu clamtk    and then go to help and update signatures. However, I think clamtk has an automatic update which is lightning quick and not apparent (if not updated for days it may show).

Only yesterday I installed Avast and it does on demand scans on my Home directory 5 to 6 times quicker than clamtk and it checks more than twice as many files (on a different computer or with various tweaks the results may well be different). I have Avast set for automatic updates. 

My regards

---

### Post by SunnyRabbiera on 2009-03-21
> **123456789123456789123456 said:**
> sorry to disagree, but there are viruses out there for linux, mac and windows.  Plus there are a few windows viruses, that were created in java, and that can and have infected windows, mac, and linux computers.  So even if it is rare to get a virus, it does not mean that no protection is needed.

But Clam covers windows viruses, windows viruses are rendered useless under Ubuntu.
Really dont use root and you are safe, also take note the difference between an exploit and a virus.

---

### Post by rburkartjo on 2009-03-21
yes you dont need an anti virus on linux but as a former windows user i like the security i do use wine a lot. it cant hurt

---

