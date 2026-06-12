---
title: "Virus HELP"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by mrmgh1 on 2010-06-18
I have been having various problems ,  in the end I resorted to checking for viruses (?) I ran a scan using clamtk which showed up 7 of them !!  - I thought nobody wrote virus form linux !!
However I dont seem to be able to find any way of removing them. Being still inexperienced in UBUNTU, as I often struggle with the technical content of responses posted I an concerned that I may be on the edge of a huge problem. 
Please advise what is the best tool to prevent such attacks .  I have in teh past been advised on these forums that there is no need for firewalls etc ..  this now appears to not be the case ?

---

### Post by wilee-nilee on 2010-06-18
First post the hits, you can't get any help without some sort of confirmation, and the av for Linux gives false positives, which I suspect is the case here.

---

### Post by Perfect Storm on 2010-06-18
> **wilee-nilee said:**
> First post the hits, you can't get any help without some sort of confirmation, and the av for Linux gives false positives, which I suspect is the case here.

+1
A lot of the hits you get by scanning Ubuntu/Linux with an anti-virus application are false positives. Such applications are only good if the persons knows the ins/outs of a Linux systems.
Most of these anti-virus apps you only need to scan for Windows partitions/UBS stick you share with friends or if you are running are mail server (to protect Windows users from malware emails).

---

### Post by gandaran on 2010-06-18
where exactly did clamtk find the virus?
I can only think of one place any linux antivirus  will find virus will be in firefox cache but those will be windows virus they wont do anything to your ubuntu system, just empty firefox cache and they will disappear.

---

### Post by Perfect Storm on 2010-06-18
> **gandaran said:**
> where exactly did clamtk find the virus?
I can only think of one place any linux antivirus  will find virus will be in firefox cache but those will be windows virus they wont do anything to your ubuntu system, just empty firefox cache and they will disappear.

Properly also a testing file which comes with the anti-virus applications will give hits.

---

### Post by wojox on 2010-06-18
Download Bleachbit. It will take care of any problems.

```
sudo apt-get update; sudo apt-get install bleachbit
```

---

### Post by warfacegod on 2010-06-18
> I have in teh past been advised on these forums that there is no need for firewalls et

Working behind a Firewall is always a good idea, no matter what OS you are using.

---

### Post by wojox on 2010-06-18
Do you have a router?

---

### Post by wilee-nilee on 2010-06-18
> **wojox said:**
> Download Bleachbit. It will take care of any problems.

```
sudo apt-get update; sudo apt-get install bleachbit
```

I would concur with this.;)

---

### Post by mrmgh1 on 2010-06-19
thanks for all the pointers / questions , I will put up responses as soon as I Am able, but that may be a few days. So many things seem to be not working as they should that I have a lot to look at and sort out..... and one or two of the questions require me to sort some things out first.

---

### Post by mrmgh1 on 2010-06-19
tried the code as mentioned by two of the above,( ok this may be silly but I need to try something to get things working)  however it came back saying it could not find some file. !!!

---

### Post by Perfect Storm on 2010-06-19
You need to give us in/output from the terminal.

---

