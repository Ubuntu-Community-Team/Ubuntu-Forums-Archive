---
title: "Noob Questionson ubuntu updates, commands"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by hitmen on 2009-11-16
1) I used the command sudo iptables -vL to see my firewall status but the output is command not found
 
2) How do you check the version of ubuntu you are using. I checked it using var/log but I know that this is not the "proper" way. In Windows, we right click and select properties. what is the ubuntu equivalent?
 
3) How do I differentiate which ubuntu updates are necessary and which one are trash? I assume that it is not necessary to install all?:D
 
Thanks in advance!

---

### Post by halitech on 2009-11-16
not sure on 1

2. lsb_release -a will tell  you what version you are using

3. If they weren't necessary they wouldn't release them ;) The ones that get marked as Security you will want to install for sure. The rest, you can read the description and see what they fix.

---

### Post by hitmen on 2009-11-16
Thanks.:D
I got the output :
 
No LBS modules
Ubuntu 8.04 3LTS
 
What is LBS and 3LTS?
 
If my version is 8.04, how come the latest version is not in the updates?

---

### Post by Chris Edgell on 2009-11-16
I'm so relatively new and so uninformed in general that I hope it's okay if I contribute the answer one of my teachers answered when I asked question 3.

"These are not programs or add-ons; these are updates.  And don't worry about space--they don't take up as much space as you're thinking--they fit over the old and just make the necessary changes.  So the healthy way of thinking of them all is that they are the flow of the constant improvement--so you see, none is trash.

---

### Post by hitmen on 2009-11-16
Errr.. another question.
 
I just installed ubuntu guest additions and all the updates.
The CD image with VBOXADDITIONS-3.0.10-54097 appears there.
What am I supposed to do with this? 
delete it?
What purpose does it serve?

---

### Post by travmanx on 2009-11-16
For the iptables question, 

sudo apt-get install iptables

---

### Post by halitech on 2009-11-16
> **hitmen said:**
> Thanks.:D
I got the output :
 
No LBS modules
Ubuntu 8.04 3LTS
 
What is LBS and 3LTS?
 
If my version is 8.04, how come the latest version is not in the updates?

I'm assuming you meant no LSB modules and not LBS modules ;)

LSB is the Linux Standard Base - [http://www.linuxfoundation.org/collaborate/workgroups/lsb](http://www.linuxfoundation.org/collaborate/workgroups/lsb)

the 3 is part of Ubuntu 8.04.3 which is just a way of tracking the updates. the 8 means it was released in 2008, the 04 means April (4th month) and the 3 is how many updates have been condensed into the newest download from the net.

the LTS means Long Term Support and depending on your settings, LTS version normally only show LTS updates.

---

### Post by cariboo on 2009-11-16
If you have Virtualbox installed, the guest additions provide the ability to share files, and drivers for usb, video and sound. If you install different os's you will need them.

---

### Post by Chris Edgell on 2009-11-16
Am I being too simplistic if I clarify a point by saying: 

Updates are more like day to day stuff at school--the upgrade is like going up to the next grade.  They are two different things.  The new versions come twice a year and you can upgrade or not.  Where the updates come all along the way.  In fact, I do all the updates but it is really something to consider if you want to install the upgrade.  Read all about the new one, it just came out about Nov 1--you can read all the comments about the new version.  I decided to wait and get used to the version I have.  

You'll find ways to find out everything you need...well, and as you can see the best way is to ask...but try to ask before you do major things.

---

### Post by Chris Edgell on 2009-11-16
I'm so embarassed.  I have got to learn not to talk so much.  I read Halitech's post and I realize that someone who knows so much DOES call the new versions "Updates"--so there you are, I hardly know what I'm talking about.

Sorry.
I'll try not to enter into what I don't know about.  It's bad enough that I ask questions that show my ignorance without answering questions that show my ignorance.  Thank you all for your patience with me.

---

### Post by stoogiebuncho on 2009-11-16
> **Chris Edgell said:**
> I'm so embarassed.  I have got to learn not to talk so much.  I read Halitech's post and I realize that someone who knows so much DOES call the new versions "Updates"--so there you are, I hardly know what I'm talking about.

Sorry.
I'll try not to enter into what I don't know about.  It's bad enough that I ask questions that show my ignorance without answering questions that show my ignorance.  Thank you all for your patience with me.

Don't worry about it, man.  We're all here to learn.  Thanks for contributing what you know.

---

### Post by Chris Edgell on 2009-11-17
Thanks.

---

### Post by WitchCraft on 2009-11-17
> **hitmen said:**
> 1) I used the command sudo iptables -vL to see my firewall status but the output is command not found
 
2) How do you check the version of ubuntu you are using. I checked it using var/log but I know that this is not the "proper" way. In Windows, we right click and select properties. what is the ubuntu equivalent?
 
3) How do I differentiate which ubuntu updates are necessary and which one are trash? I assume that it is not necessary to install all?:D
 
Thanks in advance!
1. Command not found: you haven't installed the firewall...
   Use the apt-get install suggestion
2. uname -a for the kernel, 
   cat /etc/debian_version
   cat /etc/lsb-release
3. All updates you get with apt-get upgrade are important.
   All updates you get with apt-get dist-upgrade are optional

---

### Post by halitech on 2009-11-17
Hi Chris

Just because I've been around longer and have more posts doesn't mean I automatically know more. To me, anything that makes a change to a program or file is an update, wether its a small update to the existing version or changes it to a completely new version. Both would be considered updating or upgrading and I use both interchangably. Maybe I'm wrong to think that way but that's my choice in how I see linux ;)

---

### Post by hitmen on 2009-11-18
> **cariboo907 said:**
> If you have Virtualbox installed, the guest additions provide the ability to share files, and drivers for usb, video and sound. If you install different os's you will need them.
 Thanks everyone!
So do I get rid of it or do I just leave it there? 
How many I suppose to "use" it?

---

