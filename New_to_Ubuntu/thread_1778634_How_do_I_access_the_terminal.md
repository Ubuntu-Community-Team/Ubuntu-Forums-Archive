---
title: "How do I access the terminal?"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by Greenwick on 2011-06-09
I received this message:

```
Software Index is Broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

I tried opening Synaptic, but I had no idea what to do from there.  I also read in some other topics on this problem that entering info in the terminal works much better.

Thank you!

---

### Post by hakermania on 2011-06-09
Press Ctrl+Alt+T

---

### Post by PowerBarry43 on 2011-06-09
Hi
 
you should find the terminal in Applications/accessories/terminal in the menu bar along the top if you're running Gnome :)
 
hope that helps.
Barry

---

### Post by Frogs Hair on 2011-06-09
The terminal is located on the accessories menu.

---

### Post by astrobob.tk on 2011-06-09
> **Greenwick said:**
> I received this message:

```
Software Index is Broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

I tried opening Synaptic, but I had no idea what to do from there.  I also read in some other topics on this problem that entering info in the terminal works much better.

Thank you!

Welcome Greenwick to both the forums & the Ubuntu community.

As i start i recommend checking this official documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)

As for your issue, you can open a terminal as follows (assuming your in the gnome gui):

1) Main Menu > Accessories > Terminal (or Gnome Terminal), OR

2) Alt+F2 > gnome-terminal > enter

Either of these opens a black box called the terminal.

Try issuing the following commands in the terminal (run one command at a time & wait for each to finish):

> sudo apt-get update
sudo apt-get upgrade
udo apt-get install -f

P.S.: sudo gives you "root" access. You will be asked for the user password when you use it.


As for Synaptic, its called 'Synaptic Package Manager'. Its the piece of software that contains an index of all software available for download/installation.
To open it:

Main Menu > System > Administration > Synaptic Package Manager (you will be asked for the root password): [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
In regard of broken packages as yours: [https://help.ubuntu.com/community/SynapticHowto#How](https://help.ubuntu.com/community/SynapticHowto#How) to fix broken packages

Good luck

P.S.: when your problem is solved, please mark the thread as solved for others to use.

---

### Post by hakermania on 2011-06-09
> **astrobob.tk said:**
> Welcome Greenwick to both the forums & the Ubuntu community.

As i start i recommend checking this official documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)

As for your issue, you can open a terminal as follows (assuming your in the gnome gui):

1) Main Menu > Accessories > Terminal (or Gnome Terminal), OR

2) Alt+F2 > gnome-terminal > enter

Either of these opens a black box called the terminal.

Try issuing the following commands in the terminal (run one command at a time & wait for each to finish):



P.S.: sudo gives you "root" access. You will be asked for the root password when you use it.

Good luck

A small correction:
sudo will ask you for user's login password, su will ask you for root password :)

---

### Post by astrobob.tk on 2011-06-09
> **hakermania said:**
> A small correction:
sudo will ask you for user's login password, su will ask you for root password :)

Corrected. Thanks :D

---

### Post by Swagman on 2011-06-09
Which you **WONT** see as you type it

You might need to run

```
sudo dpkg --configure -a
```

---

### Post by Greenwick on 2011-06-19
Wooh, thanks everyone!  I am so glad that there are people here who can answer newbie questions like mine.  :D

Unfortunately, I am not sure of the passwords, so I'll have to wait till my boyfriend gets back for me to get those.  But now I know what I'm doing!

Thanks again!

---

### Post by Swagman on 2011-06-19
Good to hear a follow up from the initial OP

Your question was probably answered within the first 5 minutes though !!

Your sudo password is the same password you used to login.. Assuming you don't have "auto login" enabled.

---

### Post by Greenwick on 2011-06-27
No, I don't have auto login installed.  And it was still helpful to get lots of different answers.

I managed to log in this time, but got this:

greenwick@Gwyrddwic:~$ sudo apt-get install f-
[sudo] password for greenwick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package f

Not sure what's going on there.  The computer wasn't trying to install any update for me when I tried this, so maybe I just have to wait?

Anyway, I'm just glad that now I know how to log in.  Progress!


Edit:  Success!  I looked around a bit and found this page - [http://www.cyberciti.biz/faq/how-do-i-update-ubuntu-linux-softwares/](http://www.cyberciti.biz/faq/how-do-i-update-ubuntu-linux-softwares/)  So I followed that, then followed instructions from this thread.  Now my Ubuntu is updated.  Awesome!  Thanks so much for all your help!

---

### Post by oldos2er on 2011-06-27
You had the hyphen in the wrong place, should be ```
sudo apt-get install -f
```

---

