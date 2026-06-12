---
title: "How to copy files 101"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by mistypotato on 2010-12-16
Hi

I thought after about 600 posts and several years with Ubuntu, I could AT LEAST copy files back and forth...WRONG !!!

I have a folder MyData on my Desktop and I want to copy all the files contained in that folder to  /var/lib/mysql/MyData

The folder is on the Desktop and permissions are 770 recursively

I am logged in as admin on the system. I have full rights to the folder in question....besides I'm sudoing.

In Terminal, I navigate to my Desktop for my account so I am at the Desktop

I type the following

sudo cp -R /MyData /var/lib/mysql


the response is that there is no such file or directory

OBVIOUSLY, I am lacking a fundamental piece of knowledge needed to survive in Ubuntu because I have this problem CONSTANTLY...over and over and over....sometimes it works perfectly...other times....fights me till I'm ready to throw in the towel.

Can someone point me towards an idiots guide to copying files?

Maybe a sub-idiots guide would be better.

):P

---

### Post by amauk on 2010-12-16
sudo cp -R ~/Desktop/MyData /var/lib/mysql

---

### Post by Joe of loath on 2010-12-16
OR if you're in the directory with the folder you want to copy, 

sudo cp -R ./MyData /var/lib/mysql

---

