---
title: "ClamAV False positives?"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Chaplipman on 2008-12-24
I recently scanned my computer and got three "possible" viruses. Are they false positives? Can someone please help?

/sys/kernel/slab/                    -                     0000056/slab_size
/var/lib/ucf/cache/                           -                          etc
/var/log/gdm/                       -                                  0.log

---

### Post by oilchangeguy on 2008-12-24
> **Chaplipman said:**
> I recently scanned my computer and got three "possible" viruses. Are they false positives? Can someone please help?

/sys/kernel/slab/                    -                     0000056/slab_size
/var/lib/ucf/cache/                           -                          etc
/var/log/gdm/                       -                                  0.log

read this, it may put you at ease:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

i doubt they are a virus. but even if they were they won't run in linux.

---

### Post by Sef on 2008-12-24
Here's the [clam av support page]("http://www.clamav.net/support/").

---

### Post by handydan918 on 2008-12-24
> **Chaplipman said:**
> I recently scanned my computer and got three "possible" viruses. Are they false positives? Can someone please help?

/sys/kernel/slab/                    -                     0000056/slab_size
/var/lib/ucf/cache/                           -                          etc
/var/log/gdm/                       -                                  0.log

Yeah, seriously, forget about viruses. I've been using linux since last millenium, and never had any sort of virus issue. Not even the one where I opened the attachment from the Nigerian businessman. It was a virus, alright. I zipped it and sent it to Avast....they didn't have it in their database yet. 

The unix permissions model makes it nearly impossible to run/replicate a virus on a Linux system. 

Relax.

---

### Post by Chaplipman on 2008-12-24
Thanks for the feedback guys, but the reason I worry is because I transfer a lot of files over from my linux desktop to my PC. So, if anyone could shed any light on these files, please do.

---

### Post by albinootje on 2008-12-24
> **Chaplipman said:**
> I recently scanned my computer and got three "possible" viruses. Are they false positives? Can someone please help?

/sys/kernel/slab/                    -                     0000056/slab_size
/var/lib/ucf/cache/                           -                          etc
/var/log/gdm/                       -                                  0.log

Afaik /sys is some "virtual" directory just like /proc is some "magic" mirror of the Linux kernel.

(By the way, searching for a definition of "/sys Linux" in a search-engine seems hard, .. anyone ?)

Here's the listing of the /sys file you mentioned on my Ubuntu install :

# ls -la /sys/kernel/slab/:a-0000056/slab_size
-r--r--r-- 1 root root 4096 2008-12-25 03:25 /sys/kernel/slab/:a-0000056/slab_size


Just out of curiosity I just installed clamav on my 8.10 installation.

# freshclam 
ClamAV update process started at Thu Dec 25 03:25:55 2008
main.cvd is up to date (version: 49, sigs: 437972, f-level: 35, builder: sven)
daily.cvd is up to date (version: 8798, sigs: 41342, f-level: 38, builder: sven)

# clamscan -r /sys/

----------- SCAN SUMMARY -----------
Known viruses: 478934
Engine version: 0.94.2
Scanned directories: 2819
Scanned files: 8749
Infected files: 0
Data scanned: 0.00 MB
Time: 9.119 sec (0 m 9 s)

What clamav parameters did you use ?
Or did you use a GUI like clamavtk or klamav ?

---

### Post by Chaplipman on 2008-12-24
I used a gui clamavtk. I did a recursive scan of the filesystem with no maximum size while scanning hidden files.

---

### Post by albinootje on 2008-12-24
> **Chaplipman said:**
> I used a gui clamavtk. I did a recursive scan of the filesystem with no maximum size while scanning hidden files.

I did a scan again in /sys and again nothing.

I would not worry much about it. You are not gonna give those files to anyone else anyway.

If you're really worried that you're machine is somehow compromised, install and run also :
```

sudo apt-get install chkrootkit rkhunter

```

You can also boot from a Linux Live cd, and then scan your disk for viruses (and the like), and see whether that gives the same result.

---

### Post by newbee70 on 2008-12-25
> **Chaplipman said:**
> I recently scanned my computer and got three "possible" viruses. Are they false positives? Can someone please help?

/sys/kernel/slab/                    -                     0000056/slab_size
/var/lib/ucf/cache/                           -                          etc
/var/log/gdm/                       -                                  0.log

If your unsure of them being viral. 

upload the file here to have it tested.

** [http://www.virustotal.com/](http://www.virustotal.com/)  **

btw I do get a lot of false positives with clam "phishing warnings".

---

### Post by balaknair on 2008-12-25
Yep I agree with newbee70

If you're unsure about the files, copy them and upload to virus total. It'll take maybe 2 minutes, and you'll know for sure.
They scan the files with multiple virus scan engines(39 of them), so if only ClamAV scanner tags it as a virus, it's most likely a false positive(from the file names they do look like false positives, but it's better to be safe).

Antivirus apps etc are only the second line of defence. The most important factor is always following proper security practices- Don't install stuff from untrusted sources(no cracks and warez), don't share your user ID and password, don't click on links in unsolicited emails(better yet don't open them at all), always update installed software on your computer...
This is regardless of the OS, since no OS is 100% proof against a clueless user.

---

### Post by FreewheelinFrank on 2008-12-25
Stick to scans of /home because scanning the root directory will produce false positives with any scanner.

---

### Post by WitchCraft on 2008-12-25
> **albinootje said:**
> 

sudo apt-get install chrootkit rkhunter


should be chkrootkit, not chrootkit

I once had a rootkit on my machine. was very interesting, i disassembled it, found an email address - and sent the author a hatemail. Since then, my email gets spammed on a regular basis... :lolflag:

---

### Post by albinootje on 2008-12-25
> **WitchCraft said:**
> should be chkrootkit, not chrootkit

Thanks for that typo correction! (Have edited it now)
> 
I once had a rootkit on my machine. was very interesting, i disassembled it, found an email address - and sent the author a hatemail. Since then, my email gets spammed on a regular basis... :lolflag:

hehe :)

---

### Post by JBA2337 on 2008-12-26
I just installed a new copy of ubuntu 8.10, and I scanned everything with clamtk. The results claimed that I have three "possible viruses". I eliminated two of them very quickly with virus total. 

virus total gave me the following results:

/var/log/gdm/0.log.2                   CLEAN, NO VIRUS

/var/lib/ucf/cache/etc                 CLEAN, NO VIRUS

the third "possible virus" could not be submitted.

/sys/kernel/slab/0000672/slab_size     sent to [http://www.virustotal.com/](http://www.virustotal.com/)
                                       submission to virus total failed.


/sys/kernel/slab/0000672/slab_size  sent to: [http://cgi.clamav.net/sendvirus.cgi](http://cgi.clamav.net/sendvirus.cgi)  
                                    submission to clamav.net failed


Does anybody else have an idea about slab_size?


JBA2337

---

### Post by albinootje on 2008-12-26
> **JBA2337 said:**
> I just installed a new copy of ubuntu 8.10, and I scanned everything with clamtk. The results claimed that I have three "possible viruses". I eliminated two of them very quickly with virus total. 

virus total gave me the following results:

/var/log/gdm/0.log.2                   CLEAN, NO VIRUS

/var/lib/ucf/cache/etc                 CLEAN, NO VIRUS

the third "possible virus" could not be submitted.

/sys/kernel/slab/0000672/slab_size     sent to [http://www.virustotal.com/](http://www.virustotal.com/)
                                       submission to virus total failed.


/sys/kernel/slab/0000672/slab_size  sent to: [http://cgi.clamav.net/sendvirus.cgi](http://cgi.clamav.net/sendvirus.cgi)  
                                    submission to clamav.net failed


Does anybody else have an idea about slab_size?


What happened with your original files ? 
Are those the same as before ? 
Did you install over your previous Linux installation ?
If you really formatted your partitions, and did a fresh install, then why don't I have any infection results from clamtk scanning /sys yesterday or the day before. (I'm using 8.10 32-bit, and installed clamtk from the Ubuntu repositories.)

And I as wrote before, the /sys directory is as far as I can tell, kind of similar concerning the structure as /proc
/proc is a sort of "magic" mirror of the Linux-kernel
Yesterday when I looked at some files in /sys (with ls -la in the terminal), they looked like sockets or device files or something like that. Not like normal files.
That could also be the reason that your uploads of those files failed.

Check your output of 
```

mount

```
You will probably see this amongst others :
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)

If you still believe that those files were virus infected, why not install a few other anti-virus check programs for Linux and use those too to compare.

---

### Post by Norm24 on 2008-12-26
> **albinootje said:**
> I did a scan again in /sys and again nothing.

I would not worry much about it. You are not gonna give those files to anyone else anyway.

If you're really worried that you're machine is somehow compromised, install and run also :
```

sudo apt-get install chkrootkit rkhunter

```

You can also boot from a Linux Live cd, and then scan your disk for viruses (and the like), and see whether that gives the same result.

Have chkrootkit and rkhunter installed.Just can't find it!

---

### Post by JBA2337 on 2008-12-26
I don't think I have any virus infections. I installed a new copy of Ubuntu 8.10, and my computer was not even connected to the Internet, and yet Clamtk identified three files as "possible viruses". I eliminated two of them as viruses, by submitting them to [www.virustotal.com](www.virustotal.com).

The third possible virus is the only one that I had a question about:
/sys/kernel/slab/0000672/slab_size

slab_size,  when sent to [http://www.virustotal.com](http://www.virustotal.com),
or to [http://cgi.clamav.net/sendvirus.cgi](http://cgi.clamav.net/sendvirus.cgi)  fails the submission process.

According to what I have read elsewhere most virus scanners make errors when scanning /sys, so I am not going to worry about it. 

slab_size is not a virus.

JBA2337

---

### Post by 2hot6ft2 on 2008-12-26
> **Norm24 said:**
> Have chkrootkit and rkhunter installed.Just can't find it!
They are run in a terminal
Applications>Accessories>Terminal
 with these commands
```
sudo rkhunter -c

```

```
sudo chkrootkit
```

---

### Post by 2hot6ft2 on 2008-12-26
You 2 need to quit sharing. Or is it the same one? Sure sounds alike. Nearly identical postings going on here. [http://forumubuntusoftware.info/viewtopic.php?f=46&t=2444](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2444)

---

### Post by Norm24 on 2008-12-27
> **2hot6ft2 said:**
> They are run in a terminal
Applications>Accessories>Terminal
 with these commands
```
sudo rkhunter -c

```

```
sudo chkrootkit
```

Thanks.

Sometimes the answer is so obvious I just miss it.Even after using Ubuntu for such a length of time those old Windows tendencies creep in on occasion!

---

### Post by Norm24 on 2008-12-27
While running rkhunter I received a warning of a suspicious file in /dev.

I'm supposed to check the logfile but when trying to do so I'm told I don't have the proper permissions.

Would it be proper to assume that I need to do this through terminal(using sudo) rather than trying to open up the actual folder?

---

### Post by albinootje on 2008-12-27
> **Norm24 said:**
> While running rkhunter I received a warning of a suspicious file in /dev.

I'm supposed to check the logfile but when trying to do so I'm told I don't have the proper permissions.

Would it be proper to assume that I need to do this through terminal(using sudo) rather than trying to open up the actual folder?

```

sudo tail -f -n50 /var/log/rkhunter.log

```
Or :
```

sudo less /var/log/rkhunter.log

```

---

### Post by Norm24 on 2008-12-27
This is the warning after running rkhunter.

```
[08:49:00] Warning: Suspicious file types found in /dev:
[08:49:00]          /dev/shm/pulse-shm-86832484: data

```

Any ideas as to what this is/means?

These are the end results:

```
[08:49:17]
[08:49:17] File properties checks...
[08:49:17] Files checked: 127
[08:49:17] Suspect files: 0
[08:49:17]
[08:49:17] Rootkit checks...
[08:49:17] Rootkits checked : 109
[08:49:17] Possible rootkits: 0
[08:49:17]
[08:49:17] Applications checks...
[08:49:17] Applications checked: 3
[08:49:17] Suspect applications: 0
[08:49:17]
[08:49:17] The system checks took: 5 minutes and 54 seconds
[08:49:17]
[08:49:17] Info: End date is Sat Dec 27 08:49:17 EST 2008
(END) 

```

No rootkits were found,so should I worry about that suspicious file?

---

### Post by Zip247 on 2008-12-27
> [08:49:00] Warning: Suspicious file types found in /dev:
[08:49:00]          /dev/shm/pulse-shm-86832484: data

This is from pulse audio.

see this post [http://ubuntuforums.org/showthread.php?t=1016995](http://ubuntuforums.org/showthread.php?t=1016995)

wdecker

---

### Post by Norm24 on 2008-12-27
Thanks for the link wdecker.

PS Is it safe to simply just delete this file?

---

### Post by albinootje on 2008-12-27
> **Norm24 said:**
> Thanks for the link wdecker.

PS Is it safe to simply just delete this file?

Why do you want to remove it ?

I also have it :
$ ls -la /dev/shm/pulse-shm-*
-r-------- 1 a a 2097176 2008-12-27 14:28 /dev/shm/pulse-shm-1207867287

If you're paranoid about using the internet with Linux, start playing with the Firefox add-on no-script to start with. :)

[https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)

---

### Post by Zip247 on 2008-12-27
> PS Is it safe to simply just delete this file?

Dont delete it, just follow the procedures in the link and white list it.

wdecker

---

### Post by 2hot6ft2 on 2008-12-27
I have it to. Just leave it. If you delete it you may screw your sound up.
It didn't say it was one it just said to look at it and decide if it's ok or not.

---

### Post by Norm24 on 2008-12-27
> **2hot6ft2 said:**
> I have it to. Just leave it. If you delete it you may screw your sound up.
It didn't say it was one it just said to look at it and decide if it's ok or not.

That's kinda what I thought.I'm real happy with my sound,the last thing I wanna do is screw it up.

I just ended up whitelisting the file as per the instructions in the link wdecker provided.

---

