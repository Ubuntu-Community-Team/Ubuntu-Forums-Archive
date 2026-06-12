---
title: "upgrading from the Alternate CD requires 15 hours ???"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by medya on 2010-05-01
I am trying to upgrade from the Alternate CD [but it is downloading] 
I have 9.10
and the alternate cd is for 10.04

but when I try to upgrade it uses my internet and it says it takes 15 hours to download the required files .


am I not upgrading using the CD ? then why the heck it uses internet and requires 15 hours to download?

---

### Post by nhasian on 2010-05-01
one of the questions during install is if you'd like to check for and download any updates during the install process.  you can skip this and do a regular update later.  its just the servers are bogged down now from everyone downloading ubuntu 10.04 at the same time.

---

### Post by clhsharky on 2010-05-01
HI

Make sure that CD is checked in repositories"default is not checked". After you refresh it should see the CD. If it still wants to down load from Internet, disconnect from Internet. Installer will continue with out Internet.

Sharky

---

### Post by medya on 2010-05-01
> **nhasian said:**
> one of the questions during install is if you'd like to check for and download any updates during the install process.  you can skip this and do a regular update later.  its just the servers are bogged down now from everyone downloading ubuntu 10.04 at the same time.


I did that, in the first place it said if I say no, it wont use network at all , then in some steps forward it said this 


You have to download total of 921M ,...

---

### Post by medya on 2010-05-01
> **clhsharky said:**
> HI

Make sure that CD is checked in repositories"default is not checked". After you refresh it should see the CD. If it still wants to down load from Internet, disconnect from Internet. Installer will continue with out Internet.

Sharky

yeah that was the problem, but it is still the problem

because I have not burn the ISO , and I mounted the ISO using mount command.
then when I add it to synaptic package manager , it becomes un-availble [it beocmes un-mounted] so  I can not go to the CD and run 
> sh cdromupgrade

and when I mount it by force , it will get out of the synaptic CD thing

---

### Post by medya on 2010-05-01
> **clhsharky said:**
> HI

Make sure that CD is checked in repositories"default is not checked". After you refresh it should see the CD. If it still wants to down load from Internet, disconnect from Internet. Installer will continue with out Internet.

Sharky

ok guys no matter I do , it still wanna download 900 MB from internet .
I did these things 

1-I already updated my ubuntu 9.10 to latest 9.10
2-I burnt the alternate CD to a blank DVD .
3- I added the CD-ROM to the repository of synaptic pacakge manager.
4- I run "sh cdromupgrade"
5- I Say NO [to using network to get update things]
6- it still wanna download 900 MB from internet 


can somebody please tell me what to do ?

---

### Post by medya on 2010-05-01
bump , I belive this in important quetsion ! someone please reply

---

### Post by ankspo71 on 2010-05-01
Here is instructions to do this.
[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)

> 5- I Say NO [to using network to get update things]
6- it still wanna download 900 MB from internet 

Try unplugging your internet from the computer because the option to say no to using the internet might not be working (always tries to connect).

If for some reason that doesn't work, reconnect your internet, then change the mirrors in System>Administration>Software Sources, to a mirror that is fastest to you. Then it shouldn't take 15 hours (hopefully).

---

### Post by medya on 2010-05-01
> **ankspo71 said:**
> Here is instructions to do this.
[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)



Try unplugging your internet from the computer because the option to say no to using the internet might not be working (always tries to connect).

If for some reason that doesn't work, reconnect your internet, then change the mirrors in System>Administration>Software Sources, to a mirror that is fastest to you. Then it shouldn't take 15 hours (hopefully).

taking 15 hours is because of my internet speed, I have slow internet connection speed .

and thats why I use an alternate CD to upgrade , but it wont stop wanting to download from internet ...it is pissing me off , has anybody for REALL used alternate cd to upgrade?

---

### Post by medya on 2010-05-02
bump,
has anybody for  used alternate cd to upgrade 'without internet'  for reall ?

---

### Post by Russellkhan on 2010-05-02
I upgraded using the alternate CD, from 8.04 to 10.04. I told it not to look for newer packages on the internet and I think it listened. There were some issues (that I will probably start my own thread about if I don't find one that already covers my problems) but upgrading didn't take very long, I think most of the time it took was because it was waiting for me to click on a dialog box telling me about a problem. 

Russ

---

### Post by medya on 2010-05-02
> **Russellkhan said:**
> I upgraded using the alternate CD, from 8.04 to 10.04. I told it not to look for newer packages on the internet and I think it listened. There were some issues (that I will probably start my own thread about if I don't find one that already covers my problems) but upgrading didn't take very long, I think most of the time it took was because it was waiting for me to click on a dialog box telling me about a problem. 

Russ

I am kind of sure, that for you it uses internet too, do u have fast internet ?

---

### Post by medya on 2010-05-02
ok it seems no one can help me here ... sigh

---

### Post by greenfrog on 2010-05-02
Enter this command:


gksu "sh /cdrom/cdromupgrade"   

I could only get it to work with the gksu command.

sh /cdrom/cdromupgrade will not work

---

