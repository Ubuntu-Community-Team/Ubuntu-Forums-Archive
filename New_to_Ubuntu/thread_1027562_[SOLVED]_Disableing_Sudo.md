---
title: "[SOLVED] Disableing Sudo?"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by dellwood on 2009-01-01
Hi, 

I recently installed ubuntu 8.10 to my hard drive.  My father and I had a mutual agreement that we would install dansguardian *and* make sure that the program could not be reconfigured before we installed ubuntu.  We tried adding a new user without administrative access, but that does not allow me to download files (using the synaptic package manager).  We added a password to sudo, but found that with administrative access we (I) could rename the password without knowing the previous one.  So, my question is, is there a way to password protect the password for the superuser (if that makes sense) *or* is it possible to deny administrative privileges but somehow allow the privilege of downloading files (using the SPM).  

Any and all help is greatly appreciated :D.

-dellwood :)

---

### Post by DGortze380 on 2009-01-01
> **dellwood said:**
> Hi, 

I recently installed ubuntu 8.10 to my hard drive.  My father and I had a mutual agreement that we would install dansguardian *and* make sure that the program could not be reconfigured before we installed ubuntu.  We tried adding a new user without administrative access, but that does not allow me to download files (using the synaptic package manager).  We added a password to sudo, but found that with administrative access we (I) could rename the password without knowing the previous one.  So, my question is, is there a way to password protect the password for the superuser (if that makes sense) *or* is it possible to deny administrative privileges but somehow allow the privilege of downloading files (using the SPM).  

Any and all help is greatly appreciated :D.

-dellwood :)

1) Make sure you have an administrative user. One with full sudo access. Typically the first user you created on the system. (Ubuntu Supported Suggestion... not the way I'd do it)

2) Create a new unprivileged user. With the User/Group GUI or the newuser command on the command line

3) Remove the NEW user from /etc/sudoers
   Use visudo to edit sudoers
   Be very careful, errors with editing this file will result in a  toasted system.

---

### Post by drs305 on 2009-01-01
> **dellwood said:**
> is it possible to deny administrative privileges but somehow allow the privilege of downloading files (using the SPM). 


You can make changes to the sudoers file to allow specific commands to be run without the password (you still precede the command with 'sudo'). I'll use 'synaptic' as the command you want to be able to run without knowing the sudo password.

Edit sudoers:
```

sudo visudo

```

In the " # Cmnd Alias specification section " , add something like this (including any commands and the full path to those commands):
```

# Cmnd alias specification
Cmnd_Alias TEST = /usr/sbin/synaptic

```

At the bottom of the sudoers file, add the user(s) who can run the command:
```

*your.user.name* ALL=(ALL) NOPASSWD: TEST

```

---

### Post by sdennie on 2009-01-01
I just tried the following in a VM and it does what you want.  As stated above, use:

```

sudo visudo

```

Add the following line to the bottom of the file:

```

your_username ALL=NOPASSWD: /usr/sbin/synaptic

```

Then use:

```

sudo deluser your_username admin

```

Logout and then log back in.  You will have access to synaptic but to no other sudo functionality.  Note that unless you have another user on your system that does have admin abilities, the only way to do any administration on your system outside of using synaptic is to start the machine in recovery mode or use a live CD.  That being the case, you will probably want to take the advice above in creating a new user with admin abilities before doing this.

---

### Post by dellwood on 2009-01-02
Thanks for the responses!  They really helped.

-dellwood :)

---

### Post by handydan918 on 2009-01-02
Of course, the original conundrum remains. Access to synaptic will allow removal and reinstallation of dansguardian.


unless it is installed from a tarball...

---

