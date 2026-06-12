---
title: "Is this a Virus?"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by seanarickymurphy on 2010-06-26
I installed ClamAV and took a quick scan, mine taking a look at what I'm seeing and explain to me if this is showing that my system has a virus or not?
~~~
ClamAV Scan Results:

sean@sean-laptop:~$ clamscan
/home/sean/.pulse-cookie: OK
/home/sean/.gksu.lock: Empty file
/home/sean/.huludesktop: OK
/home/sean/.xsession-errors.old: OK
/home/sean/.recently-used.xbel: OK
/home/sean/.bashrc: OK
/home/sean/.profile: OK
/home/sean/examples.desktop: OK
/home/sean/.gtk-recordmydesktop: OK
/home/sean/.gtk-bookmarks: OK
/home/sean/.dmrc: OK
/home/sean/.ICEauthority: OK
/home/sean/.xsession-errors: OK
/home/sean/.esd_auth: OK
/home/sean/.sudo_as_admin_successful: Empty file
/home/sean/.bash_history: OK
/home/sean/.bash_logout: OK

----------- SCAN SUMMARY -----------
Known viruses: 802916
Engine version: 0.96.1
Scanned directories: 1
Scanned files: 15
Infected files: 0
Data scanned: 1.92 MB
Data read: 0.97 MB (ratio 1.97:1)
Time: 11.580 sec (0 m 11 s)
sean@sean-laptop:~$ 


So far its saying "Known viruses: 802916", and "Infected files: 0" but what is this saying by Known Viruses, does it mean that my system is infected with over more than 802916 viruses or is it just stating that out that that is how many it knows? On the other hand I only scanned my system with the simple command as "clamscan" and it only scanned the files/folders above for the results, does that show a accurate scan of my entire system or just those folders and files?

---

### Post by d3v1150m471c on 2010-06-26
it means clamav knows of 802916 viruses that are out there and you have "0" of them.  change directory to the root structure and
```

clamscan -r -i

```

that should get in all the corners and shadows

---

### Post by inaneframe on 2010-06-26
> **d3v1150m471c said:**
> it means clamav knows of 802916 viruses that are out there and you have "0" of them.

I'd like to point out that 'you have "0" of them' in that particular folder /home/sean/, you are not doing a recursive scan so it's not looking into your ~/Desktop or ~/Pictures folders or any other folder INSIDE your home directory, only the FILES inside your home folder are being scanned.

```
clamscan -r
```

If you'd like to scan all files on the system:

```
clamscan -r /
```

Do bear in mind that unless you are moving files to a Windows-installed machine or running a mail server, their is little point in running clamav, since that is the intended use of the program.  Another good use of clamav is to clean out a Windows partition if it becomes too rotted up to boot into.

Also, if you email a file to a friend's gmail or yahoo account and he or she is running Windows, they *should* be fine.  I believe that gmail and yahoo have far better antivirus systems than you or I could set up.

---

### Post by inaneframe on 2010-06-26
> **d3v1150m471c said:**
> it means clamav knows of 802916 viruses that are out there and you have "0" of them.  change directory to the root structure and
```

clamscan -r -i

```

that should get in all the corners and shadows

Ah, I see you edited it.  LOL!

---

### Post by 3rdalbum on 2010-06-26
I wouldn't bother checking your Linux system for viruses. We don't get viruses; this is a pretty secure OS.

---

### Post by seanarickymurphy on 2010-06-26
Alright I did a entire scan, one problem with the results, there to long to copy and paste, otherwise I got a "0" infected files and other details that went with it showing "OK" over each folders and files it scanned.
Though if there's a way to paste the results? Can you show me a quick way to do that because the results would probably take a entire page or two. But Nah, I doubt its necessary but its just to show the results, but thanks!

---

### Post by lisati on 2010-06-26
> **3rdalbum said:**
> I wouldn't bother checking your Linux system for viruses. We don't get viruses; this is a pretty secure OS.

Although *[malware]("http://en.wikipedia.org/wiki/Malware")* is _unlikely_ to hurt your Ubuntu installation (particularly if you you are smart about what you let on your machine and what you open) it doesn't hurt to check every now and again if you're likely to be sharing stuff with Windows users.

---

### Post by wilee-nilee on 2010-06-26
Clam usually will throw false positives on occasion so don't freak out if it does.

---

### Post by seanarickymurphy on 2010-06-26
@3rdalbum
> 
I wouldn't bother checking your Linux system for viruses. We don't get viruses; this is a pretty secure OS.

Yeah its true that Ubuntu is a secure OS and not many Viruses are written for it, but on the other hand when ever any OS becomes popular theres bond to be a Virus or two to pop up sooner or later for it.
Instead of worrying over a virus in my opinion hackers seem to be more of a problem, but I havn't seen much activity with them yet, but the same with a virus, every so and often one may rise which can be problem, but thats misleading the topic,

Topic closed.

---

### Post by Perfect Storm on 2010-06-26
> Yeah its true that Ubuntu is a secure OS and not many Viruses are written for it, but on the other hand when ever any OS becomes popular theres bond to be a Virus or two to pop up sooner or later for it.

That is a false assumption I have heard a lot for newcomers. Linux and *nix are the largest when it comes to the servers and a like. Still there's very very few malware for it. (NOTE I use the word malware as a virus is a application than can produce and spread itself which is very very difficult in linux/*nix/*bsd).


Stuff we'll see in Linux will more likely be trojans and backdoors installed by users who have been tricked into installing some stuff (see social engineering).

---

### Post by d3v1150m471c on 2010-06-26
it's difficult for viruses to occur on a linux system because viruses cannot replicate easily in the environment. That doesn't make it impossible. Malware however is easily obtained just as much as it would be on any operating system. Scanning your computer and checking the source code of downloads is **never** a bad idea. Also, clamav checks for viruses that exist for multiple platforms and not just linux or windows.

---

