---
title: "&quot;You do not have the permissions necessary to view ..."
date: 2009-07-10
forum: New to Ubuntu
---

### Post by Wtwine on 2009-07-10
Hi

Why are permissions denied on certain folders, and can they be changed?  

I am trying to get VPNC working, and one thread suggested checking something in /etc/vpnc, but when I try to open the vpnc folder, I get an error message saying "You do not have the permissions necessary to view the contents of "vpnc""

Thanks
Wayne

---

### Post by Kinney on 2009-07-10
Some files aren't meant to be edited or for security reasons read by normal users.

Just use sudo or gksudo.

---

### Post by Troll_the_Great on 2009-07-10
You need to be root (computer administrator) to access some files and folders. Open nautilus as root: hit Alt+F2 and type
```
gksu nautilus
``` and now you can do anything you want.
Just be very careful because you can mess up your computer if you don't know exactly what are you doing.
Cheers!

---

### Post by Wtwine on 2009-07-13
Thanks

Two more questions:

1) What is the difference between sudo and gksudo?
2) How do you get out of root when finished, ie how do you "un-sudo"?

---

### Post by rvgsd on 2009-07-13
Hi.. I am not a techie, but from what I know:

1) What is the difference between sudo and gksudo?
When you use "sudo", it runs inside a terminal, whereas if you use "gksudo", it gives a  graphical interface for you to enter your password, which doesn't need a terminal.
eg. sudo apt-get install xxxxx
      gksudo nautilus folderlocation

2) How do you get out of root when finished, ie how do you "un-sudo"?
I am not sure about this, but I think it stays for some time or until you log out. I am not sure about this one though!

Hope that helps!

---

### Post by aysiu on 2009-07-13
> **Wtwine said:**
> Thanks

Two more questions:

1) What is the difference between sudo and gksudo?
2) How do you get out of root when finished, ie how do you "un-sudo"?
1) Explained here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

2) ```
exit
``` gets you out of *sudo*

---

### Post by vinutux on 2009-07-13
> **Wtwine said:**
> Thanks

Two more questions:

1) What is the difference between sudo and gksudo?
2) How do you get out of root when finished, ie how do you "un-sudo"?



1. sudo = temperory super user


gksu = graphical sudo (not in terminal)

2. simple just close terminal or window your opened.


.

---

### Post by rvgsd on 2009-07-13
actually "exit" doesn't "unsudo". 
For example if, I do
"sudo synaptic" > enter the password > close everything including the terminal. Open the terminal again, and say sudo synaptic, then it does not ask me for a password.
(Of course if I am doing "sudo su", then exit gets me out of the root user terminal).
Can anyone please explain?

---

### Post by aysiu on 2009-07-13
> **rvgsd said:**
> actually "exit" doesn't "unsudo". 
For example if, I do
"sudo synaptic" > enter the password > close everything including the terminal. Open the terminal again, and say sudo synaptic, then it does not ask me for a password.
(Of course if I am doing "sudo su", then exit gets me out of the root user terminal).
Can anyone please explain?
You shouldn't use *sudo* with a graphical application. You should use *gksudo*. Read the link I posted above.

You're right, though, about *exit* not working. I was thinking of *sudo -i* and returning to a normal user prompt afterwards.

---

### Post by rvgsd on 2009-07-13
Yeah, I dont/wont use sudo with a graphical application, i just wanted to say something with an example! Thanks though!
I think it is timed, like if I wait for 10 minutes and do so again, I have to enter the password!

---

### Post by aysiu on 2009-07-13
> **rvgsd said:**
> Yeah, I dont/wont use sudo with a graphical application, i just wanted to say something with an example! Thanks though!
I think it is timed, like if I wait for 10 minutes and do so again, I have to enter the password!
```
sudo -k
``` will end the timeout prematurely.

---

### Post by tjoff on 2009-07-13
> **rvgsd said:**
> 
I think it is timed, like if I wait for 10 minutes and do so again, I have to enter the password!

Exactly, as default it is timed to 15 minutes.

Excerpt from 'man sudo':

(...) Once a user has been authenticated, a timestamp is updated and the user may then use sudo without a password for a short period of time (15 minutes unless overridden in sudoers). (...)

---

### Post by rvgsd on 2009-07-13
wow..thanks for the info!

---

### Post by vinutux on 2009-07-13
plz....Mark thread as SOLVED...........

---

### Post by d8xter on 2010-09-09
Must say thanks, had similar issue. Solved now.

---

