---
title: "Me, the idiot who screwed up my own computer"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by qwertyuiop96 on 2009-03-28
I have no idea what the heck I was thinking, and now I think I have screwed up my computer.  Oops.  I'll start from the beginning.  I had to delete some files I needed root permissions for and started exploring the system files.  I ran into the archives folder, looked it it, and found that that is where all my downloaded files had gone.  I deleted the folder.  Obviously I should have done each file, not the whole folder!  Anyway, when I try to add a new program w/ the add/ remove sofware it errors, saying (Cannot find archive folder) and (cannot unlock archive/lock)  So I went in and recreated those folders.  Now the first error doesn't come up, but the second does, and here is he exact error:

E: Could not open lock file /var/cache/apt/archives/lock - open (21 Is a directory)
E: Unable to lock the download directory

Is there any way I could recreate those files in locked form or make them locked?  Or just any way to solve the problem?  If I can't, it appears that a. I must reinstall ubuntu, or b. I can't install any new sofware.

Oh, and Synaptic package manager does the same thing.

---

### Post by Dr Small on 2009-03-28
I've never ran into this problem before, but you can try:
```
sudo dpkg-reconfigure apt
```

---

### Post by qwertyuiop96 on 2009-03-28
Dr. small-  Tried that- asked for pass- then no errors, just the usual prompt.  I went to try to install software- same error.

---

### Post by drs305 on 2009-03-28
*lock* is a file, not a directory. You could try making it with:
```

sudo touch /var/cache/apt/archives/lock

```
Of course, most users want to get rid of locks, not make them. Once you create it you will then have to decide what to do next ...  ;-)

---

### Post by jimmy the saint on 2009-03-28
you aren't trying to run two package managers at the same time are you?  eg, synaptic + add/remove or apt-get + add/remove.  All instances of other package manager apps must be closed (to include synaptic, update manager, apt-get, add/remove etc.) or they will not work. One at a time.  

Just a thought

---

### Post by Delta28 on 2009-03-28
Go into the same place and create new file that is named achieved file then when it goes to find that folder it will recognize the  fake folder and save!I've done something like that on windows its fun to confuse your computer!:lolflag: I remade my "My Computer" file the one under start menu...hehe

---

### Post by Dr Small on 2009-03-28
Ok, so let's see if we can solve the problem by looking at and fixing the permissions. Here are mine (on a Debian machine):
```
drsmall@mycroft:~$ ls -lh /var/cache/apt/ | grep archives
drwxr-xr-x 3 root root  20K 2009-03-24 21:08 archives

```

So, run:
```
sudo chown root:root /var/cache/apt/archives
sudo chmod 755 /var/cache/apt/archives
```

If after doing that it does not solve the problem, try rebooting.

---

### Post by qwertyuiop96 on 2009-03-28
Same stupid persistent error

---

### Post by ByteJuggler on 2009-03-28
Edit: never mind, already suggested.

---

### Post by Delta28 on 2009-03-28
> **Delta28 said:**
> Go into the same place and create new file that is named achieved file then when it goes to find that folder it will recognize the  fake folder and save!I've done something like that on windows its fun to confuse your computer!:lolflag: I remade my "My Computer" file the one under start menu...hehe

Quoted myself lolz!

Dr Small go to my link for my signature and check it out!

---

### Post by qwertyuiop96 on 2009-03-28
Delta 28- you have saved my life!  Thanks.

---

