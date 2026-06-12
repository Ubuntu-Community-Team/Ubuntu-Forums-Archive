---
title: "where/how to install applications"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by cmpscabral on 2009-03-22
Hi,

Where should I install applications (not in repositories) and which user should I use to do it?

I just installed [Protege]("http://protege.stanford.edu/download/download.html") using a shell script with user "root" in "/usr/local/Protege" but now only the root user has access to it.

what's the common procedure?


thanks

---

### Post by 123456789123456789123456 on 2009-03-22
Threre is three ways to install programs, you can use the add programs section, that may add several files/programs you don't want.  The program you want may not be listed.
the second way is using command line
with the apt command

for instance to get the program Protege using apt

sudo apt-get install Protege

the third way is to install from the code you found on the companies web site.

You will have to install it under the user you want to use the program
to install the program you wanted Protege, you would need to install under your user name.
use sudo command ahead of any other command to give you root privilages.
I don't remember the command off hand, but I believe there is an extra command, or switch to tell linux to install the program for all users on the machine.

you can probably fix the Protege program to run for you.  You will need to locate the files used by the program
get a list by ls -l command in terminal
identify the group owner of the files
add that group to your user account
you should then gain access to the program.
easiest way though is to simply remove the program, probably by using synaptic packet program.

---

### Post by Skol312000 on 2009-03-22
under SYSTEM for Synaptic manager

ADD/REMOVE under "Applications"

and terminal "sudo apt-get whatever"

---

### Post by blandman3 on 2009-03-22
how do you use the synaptic program?  I downloaded it today, but it doesn't show up.

---

### Post by James_Lochhead on 2009-03-22
Synaptic is installed by default. System > Administration > Synaptic Package Manager

---

### Post by James_Lochhead on 2009-03-22
> **cmpscabral said:**
> 
what's the common procedure?


You have done it right. Just make sure that you have permission to execute the program as a normal user.

---

### Post by blandman3 on 2009-03-22
> **James_Lochhead said:**
> Synaptic is installed by default. System > Administration > Synaptic Package Manager

It doesn't show under system>administration>synaptic package manager, maybe I didn't do it right or something.  Oh well, don't need it I guess.

---

### Post by oldos2er on 2009-03-22
Open a terminal and enter
```
gksu synaptic
```

 If you're running KDE, look for a program called Adept.

---

