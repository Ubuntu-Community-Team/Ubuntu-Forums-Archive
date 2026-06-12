---
title: "GDM fails, possible corupted users folder, no way 2 login"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by cael_shadowhunter on 2009-08-29
Hi guys

 my brother's dell inspiron 1300 running ubuntu, intrepid, crashed. It wasnt the first time, the laptop didnt pack quite enough punch to run the os and I had been meaning to install xubuntu packages but never got around to it. So the crash was probably not symptom of following fault.


 He rebooted his laptop and ubuntu loaded fine until he got to the login interface instead of the usual gui he got this message in terminal  said:

> chown invalid user: 'syslog :adm'
[COLOR="Magenta"][this line was repeated about 10 times][/COLOR]
User syslog does not exist, aborting         [COLOR="Red"][fail][/COLOR]
                                                          [ ok ]

boing wcom setup...
starting kernel log daemon...
chown: invalid user: 'klog:klog'
chown: invalid user: 'klog:klog'
start-stop-daemon:uset 'klog not found'
(Success)

chown invalid user: 'messagebus'
starting Avahl mDNS-SD Daemonavahil-daemon 
Timout reached while waiting for return value 
Could not return value from daemon process

[[COLOR="Magenta"]then someting about starting myqld but this failed and disappeared to quickly for me to copy down the exact quote  [/COLOR]}

I then get a bios style block graphic informing me that 'The user GDM user  'gdm' does not exist. Please correct GDM configuration and restart GDM.'

i select ok which is the only option available to me 

i am prompted 2 login on command line however correct details come back as 'incorrect login'

my brother had not added a guest account or updated programs prier 2 fault.

any ideas about how 2 correct this or failing that salvage some data from the hdd 

i suppose i could try 2 fix partitions using gparted

i would imagine laptop hdd is 2 old 2 be sata but 2 be honest i havnt checked
 
my brother keeps no backups

---

### Post by DSn0wMan on 2009-08-29
I am not sure how to fix your problem, but if you want to rescue some data you can just load up the live CD and copy your data to any type of external drive.

---

### Post by cael_shadowhunter on 2009-08-29
> **DSn0wMan said:**
> I am not sure how to fix your problem, but if you want to rescue some data you can just load up the live CD and copy your data to any type of external drive.
I tried with an xubuntu jaunty (live) cd which (bizarrely) didnt show any files from the laptops hardrive. 

Also when i tried to search for files i had a very short wait then a message about a nondescript 'fatal error'

any ideas?

---

### Post by cael_shadowhunter on 2009-09-10
helooo anybody out there?

---

### Post by ukripper on 2009-09-10
you can reinstall gdm and reconfigure with below commands:
```
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
```

---

