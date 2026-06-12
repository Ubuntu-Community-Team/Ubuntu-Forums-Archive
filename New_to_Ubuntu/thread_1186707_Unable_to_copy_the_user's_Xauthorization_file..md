---
title: "Unable to copy the user's Xauthorization file."
date: 2009-06-13
forum: New to Ubuntu
---

### Post by randolf_ambrose on 2009-06-13
i was using Synaptic Package Manager to download and install some 226 applications and plugins... in between my system lost battery power and got shut down...

now when i try to open Synaptic Package Manager, i'm getting the following error... what shall i do... please advice me...
> 
Failed to run /usr/sbin/synaptic as user root.

Unable to copy the user's Xauthorization file.

and when i try to check for updates using Update Manager, i get this error,
> 
Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '113246246' '--update-at-startup' as user root.

Unable to copy the user's Xauthorization file.

would i have to reinstall ubuntu???

or can i resolve these problems permanently...

---

### Post by shifty_powers on 2009-06-13
have you tried opening a terminal and running
```
sudo dpkg --configure -a
```?

---

### Post by mahboop on 2009-11-12
> **shifty_powers said:**
> have you tried opening a terminal and running
```
sudo dpkg --configure -a
```?

I've the same problem too
I've tried your solution but it didn't work

still i'm getting this error when I open Synaptic Manager
```

Failed to run /usr/sbin/synaptic as user root.

Unable to copy the user's Xauthorization file.

```

Please any solution??

---

### Post by falconindy on 2009-11-12
Sounds like your .Xauthority files are having permission problems. Post the output of: ```
ls -la $HOME\.*auth*
```

---

### Post by mahboop on 2009-11-12
here is the result:
username = mahboop
```

-rw------- 1 mahboop mahboop    16 2009-03-19 02:15 .esd_auth
-rw------- 1 mahboop mahboop 39379 2009-11-12 19:29 .ICEauthority
-rw------- 1 mahboop mahboop     0 2009-11-12 19:29 .Xauthority

```
Thanks

---

### Post by falconindy on 2009-11-12
Not a good sign that your .Xauth is empty. I'd say delete it and reboot. A new one will be created on login.

---

### Post by mahboop on 2009-11-12
I deleted the three files and restarted ubuntu but the results are the same.
The files haven't been created by the system.
```

mahboop@mahboop-laptop:~$ ls -la $HOME\.*auth*
ls: cannot access /home/mahboop.*auth*: **No such file or directory**
mahboop@mahboop-laptop:~$ 

```

---

### Post by falconindy on 2009-11-12
> **mahboop said:**
> I deleted the three files and restarted ubuntu but the results are the same.
The files haven't been created by the system.
```

mahboop@mahboop-laptop:~$ ls -la $HOME\.*auth*
ls: cannot access /home/mahboop.*auth*: **No such file or directory**
mahboop@mahboop-laptop:~$ 

```
Strange. Well, they'll be created when they're needed. I just tested this on my VM. By chance, does your /tmp directory have permissions other than 1777 and/or is it not owned by root? Those permissions as "human readable" would look like 'drwxrwxrwt'.

---

### Post by mahboop on 2009-11-13
> **falconindy said:**
> By chance, does your /tmp directory have permissions other than 1777 and/or is it not owned by root? Those permissions as "human readable" would look like 'drwxrwxrwt'.

```

drwxrwxrwt  21 root root   480 2009-11-13 11:20 tmp

```

---

### Post by mahboop on 2009-11-15
^^^^^^

---

### Post by scotjam1981 on 2012-11-11
> **mahboop said:**
> I deleted the three files and restarted ubuntu but the results are the same.
The files haven't been created by the system.
```

mahboop@mahboop-laptop:~$ ls -la $HOME\.*auth*
ls: cannot access /home/mahboop.*auth*: **No such file or directory**
mahboop@mahboop-laptop:~$ 

```

I have the same problem, but I thought it is because of the \ in the command (maybe it's just because I'm new to linux, but shouldn't it be a / rather than a \ ?)

I'm having the same issue (when I run a particular app I get the error "Failed to run /path/to/app as user root. Unable to copy the user's Xauthorization file."). 

My output of ls -la $HOME\.*auth* is:
```
ls: cannot access /home/username.*auth*: No such file or directory
```

Whereas the output of ls -la $HOME/.*auth* is:
```
-rw------- 1 username username 660 Nov 11 21:15 /home/username/.ICEauthority
```

Any thoughts what the issue is and how I might be able to fix it?

---

### Post by scotjam1981 on 2012-11-11
Just to add - the permissions on /tmp/ are:
drwxrwxrwt 13 root root 4096 Nov 11 21:34 tmp

---

### Post by wildmanne39 on 2012-11-11
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

