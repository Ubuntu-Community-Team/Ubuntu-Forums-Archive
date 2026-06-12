---
title: "Office 2007 in ubuntu 10.04"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by AR1974 on 2010-12-16
Hi, 
i used Crossover to install Access 2007 on my ubuntu 10.04. Although the utility appears as it has been installed, it doesn't run. could anyone help me? thank you.

---

### Post by redbook4574 on 2010-12-16
> **AR1974 said:**
> Hi, 
i used Crossover to install Access 2007 on my ubuntu 10.04. Although the utility appears as it has been installed, it doesn't run. could anyone help me? thank you.

I think you will have problems, I have never successfully enabled access in either crossover or wine.

---

### Post by migs73 on 2010-12-16
Try this;

Find the .exe file. Right click on it select Properties and then select the permissions tab.
Click on the check box to 'Allow executing file as a program'.


Then try to run it again.

Mike

---

### Post by AR1974 on 2010-12-16
> **migs73 said:**
> Try this;

Find the .exe file. Right click on it select Properties and then select the permissions tab.
Click on the check box to 'Allow executing file as a program'.


Then try to run it again.

Mike


thank you!

---

### Post by migs73 on 2010-12-16
> **AR1974 said:**
> thank you!

Assuming you thanked me because it worked :) could you please mark the thread as solved.

Top of the first post, click on Thread Tools then Mark as Solved


Glad to be of help

Mike :)

---

### Post by amjjawad on 2010-12-16
I know some will disagree with me but I always think it's much better to use each program with its native platform especially if that program is designed to work with a particular platform.

---

### Post by migs73 on 2010-12-16
> **amjjawad said:**
> I know some will disagree with me but I always think it's much better to use each program with its native platform especially if that program is designed to work with a particular platform.

I agree completely, but as Access is more business orientated software I assume the OP will have no option (the software specified by others) than to use it.

OP if this is not the case, then amjjawad is correct, that a native program would (of course) be better.

Try here;

[http://www.osalt.com/](http://www.osalt.com/)

to see if there is an alternative for you.

---

### Post by AR1974 on 2010-12-16
> **migs73 said:**
> Assuming you thanked me because it worked :) could you please mark the thread as solved.

Top of the first post, click on Thread Tools then Mark as Solved


Glad to be of help

Mike :)

Mike, I just wanted to thank you about answering me; sorry I was not clear. I've just tried your solution but it didn't work. Any other idea?

---

### Post by migs73 on 2010-12-17
Have you looked at the native alternatives available?

If you do not need to run Access, then they will be the best option.

I am not an expert in Wine (I can't get mine working in 10.10) but I only used it for a couple of silly games.

For any MS apps I require I use a Virtual Machine (Oracles Virtualbox), it is incredibly (surprisingly) easy to set up, but you do need a (legitimate of course) copy of a windows OS. I used the OEM one for my laptop (on which the VM runs).

If you go by this route, please download the PUEL version from Oracles website as the version in the Ubuntu Software Centre does not support USB which can be a bit of a pain.

EDIT on reading the OP again I see you used Crossover, maybe getting in touch with them may help any issues you have. They list Access as a successfully ported(?) program only on the Office 2000 flavour.

---

### Post by amjjawad on 2010-12-17
If you have Windows installed, go ahead and install Office there, period.
If you don't have it, then you may want to check what migs's suggested.

I have no experience with Wine and I don't want to have one :)
If I want to run office, I won't think twice and will install Windows if it's not already installed.

---

### Post by migs73 on 2010-12-17
> **amjjawad said:**
> 
I have no experience with Wine and I don't want to have one :)


I wish I hadn't!! ;)

---

### Post by A_M_S on 2010-12-17
You can run Office 2007 in vitual machine using Virtual Box. I works fine to me.

---

### Post by amjjawad on 2010-12-17
> **migs73 said:**
> I wish I hadn't!! ;)

I saved my time and didn't go through that path :D


OP, this might help you: [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

Perhaps you'll find a solution for your problem "IF" you still want to use Wine :)

---

### Post by AR1974 on 2010-12-17
thanks Mike. I'd like to learn more on native alternatives, such as GLOM.

---

### Post by migs73 on 2010-12-17
I am afraid I can't help you there, I don't use one. Why not search the forums to see if any other have used alternatives or start a new thread asking which alternative people have found to be best for them.

Good Luck

Mike

---

### Post by Mark Phelps on 2010-12-17
> **AR1974 said:**
> Hi, 
i used Crossover to install Access 2007 on my ubuntu 10.04. Although the utility appears as it has been installed, it doesn't run. could anyone help me? thank you.

Had you bothered to check the WineHQ site for info about Access, you would have seen the following:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=12]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=12")

Bronze means that it barely works -- as opposed to Garbage, which means it does not work.

IF you click on the Test Results area, you will find out what others did to get it working (or not).

---

