---
title: "Now... how do I install something?"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by TheStabe on 2009-06-25
Hi, I'm REALLY new to Linux. Like, really really new. Here's my latest problem; how do I install stuff? I see I can't just double click on the AssaultCube installer icon like windows, lol. I read a bunch of stuff on how to work the terminal, but I still can't figure this stuff out. A step-by-step would be appreciated.

---

### Post by Cheesemill on 2009-06-25
A bit of background reading for you:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by 73ckn797 on 2009-06-25
Look here: [https://help.ubuntu.com/community/TitleIndex](https://help.ubuntu.com/community/TitleIndex)

---

### Post by fooman on 2009-06-25
best and easiest way is to first check add/remove (applications > add/remove) or synaptic package manager (system > administration > synaptic package manager).

there is an incredible amount of software/games to choose from there!  :P

---

### Post by Cheesemill on 2009-06-25
I've just had a look at AssualtCube for you.

They don't supply a .deb file so download the AssaultCube_v1.0.2.tar.bz2 file, then right-click on it and select 'Extract Here'. Open the extracted folder, double click on assaultcube.sh and choose 'Run in terminal'.

---

### Post by TheStabe on 2009-06-25
That didn't work. I click run in terminal and nothing happens.

---

### Post by oldos2er on 2009-06-25
Running ./assaultcube.sh in a terminal worked for me; you need to be in the directory where you extracted the archive (on my system that's ~/Downloads/AssaultCube_v1.0.2).

---

### Post by Wiebelhaus on 2009-06-25
> **Cheesemill said:**
> A bit of background reading for you:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Good suggestion!

---

### Post by fugaki on 2009-06-25
you should also learn to use apt

you can use apt-cache search <string>
to search for software, then use

apt-get install <package>

to install it automatically.

This will also usually grab all of the dependencies and make it fairly headache free to install software.

If you are installing things from websites and the software is not in the repos, then check out alien, it will convert other package types to .deb files and make them easier to install.

---

