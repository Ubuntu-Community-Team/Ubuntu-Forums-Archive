---
title: "Can the Beagle Desktop search utility be installed in Ubuntu 10.10 and 11.04 ?"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by swarup on 2011-06-15
Beagle Desktop search utility is the only search utility I have ever found in Ubuntu which is able to do the search task I need. In order to upgrade to 10.10 or 11.04 I would need to be able to install it. But it doesn't seem to be available in the repos for these versions. Is there some way to install it i.e. for someone not experienced in compiling?

---

### Post by jtarin on 2011-06-15
From what I understand Beagle is no longer updated. [There are alternatives.]("http://ubuntuforums.org/showthread.php?t=1599190")

---

### Post by jtarin on 2011-06-15
[There is also Beagle ++]("http://beagle2.kbs.uni-hannover.de/index.html").

---

### Post by swarup on 2011-06-16
It's true-- Beagle is no longer being updated. But it works great! I am running Ubuntu 9.04 on my laptop, and the Beagle in that machine works better than anything else I've ever seen. 

My main work with the desktop search tool is searching text documents which are in the Hindi linguage. Hindi uses a different alphabet than English, and for whatever reason, all the other search tools I've tried-- such as Tracker, Google Desktop search, and others, fail to search properly in Hindi. Whereas Beagle does it perfectly. I tried Catfish as well, and it wouldn't search my documents at all. Thank you for the reference to Beagle++-- in the documentation it only talks about SUSE. But I've emailed its creator, to ask whether it works in Ubuntu.

---

### Post by jtarin on 2011-06-16
If it works in Suse it will work in Ubuntu after compiling it for your individual situation. it's a little work if you've never done it before.

From the site:
> If you do not have a SUSE 10.2 system you can download this virtual machine. You just need to install a VMware Player, download this ZIP archive and follow the installation instructions.

---

### Post by jtarin on 2011-06-16
> **swarup said:**
> 
My main work with the desktop search tool is searching text documents which are in the Hindi linguage. Hindi uses a different alphabet than English, and for whatever reason, all the other search tools I've tried-- such as Tracker, Google Desktop search, and others, fail to search properly in Hindi. You should investigate "grep' more.....your really overlooking the most powerful search tool available for text within documents.

---

### Post by swarup on 2011-06-16
As I understand grep is a terminal-based application i.e. there is no gui. And one cannot type in Hindi in the terminal window-- so therefore cannot search for Hindi words using grep.

As for compiling, I don't have experience. And running as virtual machine, it sounds a bit unnecessarily complex for such a basic function as a desktop search tool... 

My question is, why was Beagle discontinued. The best search tool available should continue! :) Or at least, something as good should be available. After all, Ubuntu is such a major linux distribution, and prides itself on its international user base. So a basic function like desktop search should be available for people from all over the world. When a desktop search tool is evaluated, it should be evaluated from this standpoint as well-- i.e. does it work in different scripts? ("scripts" meaning different alphabets of different languages around the world.)

---

