---
title: "KpackageKit and updates not working"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by Sirius B on 2011-01-04
KpackageKii not working, when i click on check for new updates i get error saying something like "cannot get the exculsive lock on the packaging backend please close any other package legacy tools that maybe open" well there isn't any other tools open so i dont uderstand

So i have opened terminal and typed

Sudo apt-get update

reply back is: 

E: could not get lock /var/lib/apt/lists/lock - open (11 resorse temp unavailable)
E: Unable to lock directory /var/lib/apt/lists/

anyone ever had this and know how to solve it?

P.s my internet is working and conected

---

### Post by nick_goodfate on 2011-01-05
A reboot should fix it...

If not, this command will show you if an other package legacy tool is running
> ps | grep apt

find it and kill it 
> killall {name of app}

---

### Post by Sirius B on 2011-01-05
> **nick_goodfate said:**
> A reboot should fix it...

If not, this command will show you if an other package legacy tool is running


find it and kill it
your commands didnt seem to work.

Anyway i may have solved to problem

i rebooted like you said then ran sudo apt-get install  kpackagekit and it came back as already installed. So i ran  sudo apt-get update and it still got to 99% and asked for kubuntu disc. 

So i opened the kpackagekit in the GUI and looked at the repository  settings and found that one of the places it looked for updates was the  disc so i unticked that and clicked apply and then ran sudo apt-get  update and it now works


This thread is now solved to hopefully it will help someone in the future

---

### Post by nick_goodfate on 2011-01-05
my command work, just doesn't give any output. What it does is to show you all the curently running programms that contain "apt" in their name(The programm that caused you the problem). So it was normal to not give you any output since you didn't have the same problem.

Good to know you solved it!

EDIT: You're right, my command doesn't work. :-\"
The correct command is > ps -e | grep apt

But again it would probably give you no output...

---

### Post by Sirius B on 2011-01-05
> **nick_goodfate said:**
> my command work, just doesn't give any output. What it does is to show you all the curently running programms that contain "apt" in their name(The programm that caused you the problem). So it was normal to not give you any output since you didn't have the same problem.

Good to know you solved it!

EDIT: You're right, my command doesn't work. :-\"
The correct command is 

But again it would probably give you no output...
thanks anyway nick :D

---

