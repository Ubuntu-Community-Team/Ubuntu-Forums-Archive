---
title: "Permission Problems"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by SoulMazer on 2009-06-16
Just today I created a new partition on my hard drive and did a fresh install of Ubuntu on it. I simply mounted my old Ubuntu file system and copied the entire home directory to my new home directory (this required sudo). Yet, I tried to open a text file and save it, and it said I did not have permission to do so. I am guessing this is because the owner is "root". How can I recursively set the owner of all these files/directories to my current user?

Thanks in advance for any help.

---

### Post by theozzlives on 2009-06-16
```
sudo chown user:group /home/user -R
```NOTE: that is a capital R

---

### Post by SoulMazer on 2009-06-16
Exactly what I needed. The -R at the end was messing me up.

Thanks.

---

### Post by lavinog on 2009-06-16
The terminal is usually the easiest way:
```
sudo chown -R username path
```

the graphical way would be to start nautilus as root:
alt-f2:
gksudo nautilus
then right-click the folder you need to change the owner of.
select properties
then permissions (tab)
change the owner
click on Apply permissions to enclosed files
close the properties window and close nautilus (so you don't continue to use it and accidently do something you don't want to)

---

### Post by chrisgaffrey on 2009-06-19
> **lavinog said:**
> The terminal is usually the easiest way:
```
sudo chown -R username path
```


Lavinog, thank you kindly for this. I was having a similar issue with permissions and needed to find out how to change them.

So as to not have any problems in the future, I gave my self ownership of the entire filesystem, by running:

```
sudo chown -R username /
```

And the problem was solved.

However, I wanted to ask, is there any reason why having a user as the owner of the entire filesystem might cause problems? Thanks in advance.

Edit: Do not do run ```
sudo chown -R username /
``` it screws up your system.

---

### Post by lavinog on 2009-06-19
> **chrisgaffrey said:**
> Lavinog, thank you kindly for this. I was having a similar issue with permissions and needed to find out how to change them.

So as to not have any problems in the future, I gave my self ownership of the entire filesystem, by running:

```
sudo chown -R username /
```

And the problem was solved.

However, I wanted to ask, is there any reason why having a user as the owner of the entire filesystem might cause problems? Thanks in advance.

There is a huge security issue for one.
That command you show, changes the ownership of the entire system. I have never used it, but I would think that it should at least give you some error messages.
By changing the ownership of **everything** you effectively removed the requirement for sudo for any system changes, and removed a major security barrier that protects your system from malicious activities.

Restoring this might not be very trivial.
I think you should chown the following to root:
/etc
/bin
/usr
/lib

Personally I think you may want to consider a reinstall.

---

### Post by BandD on 2009-06-19
> **lavinog said:**
> there is a huge security issue for one.
That command you show, changes the ownership of the entire system. I have never used it, but i would think that it should at least give you some error messages.
By changing the ownership of **everything** you effectively removed the requirement for sudo for any system changes, and removed a major security barrier that protects your system from malicious activities.

Restoring this might not be very trivial.
I think you should chown the following to root:
/etc
/bin
/usr
/lib

personally i think you may want to consider a reinstall.

+1

---

### Post by chrisgaffrey on 2009-06-19
> **lavinog said:**
> There is a huge security issue for one.
That command you show, changes the ownership of the entire system. I have never used it, but I would think that it should at least give you some error messages.
By changing the ownership of **everything** you effectively removed the requirement for sudo for any system changes, and removed a major security barrier that protects your system from malicious activities.

Restoring this might not be very trivial.
I think you should chown the following to root:
/etc
/bin
/usr
/lib

Personally I think you may want to consider a reinstall.

Yeah, I screwed the pooch on that one. I just got down reinstalling and now have to reconfigure everything. Well there's a noob mistake I hope others will not make.

Gonna go edit my other post so as to warn other not to do that.

---

