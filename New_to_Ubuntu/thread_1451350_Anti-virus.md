---
title: "Anti-virus"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by Malacath on 2010-04-10
I'm a new user to Linux. Just installed it using wubi.exe after seeing a video about it on youtube.
Anyway what I need to know is can linux catch viruses?

Do I need anti-virus?

I've search google but can't get a straight answer.

---

### Post by jrothwell97 on 2010-04-10
> **Malacath said:**
> I'm a new user to Linux. Just installed it using wubi.exe after seeing a video about it on youtube.
Anyway what I need to know is can linux catch viruses?

Do I need anti-virus?

I've search google but can't get a straight answer.

Welcome to Ubuntu!

The short answer is that you don't need to bother with anti-virus software: Ubuntu (along with all other Linux distributions, and other UNIX-like systems such as Mac OS X) has a "permissions" system that makes it very hard for programs to damage your system without your explicit permission.

The long answer is that you don't need anti-virus, but you must still exercise caution. Take care when installing applications from places other than the Ubuntu repositories, and update your system regularly.

**Really geeky information if you're curious:** The reason it's so difficult for malware to damage your system is because of what we call the 'super-user', or 'root'. Your "administrator" account in Ubuntu does not have permission to change any file on the system, but it *is* allowed to act as if it were the super-user (root) for a short time, if necessary. (You will see this when you install software using the Ubuntu Software Centre, or when using Update Manager.) You can't log in as the super-user, but you can become root briefly when necessary (look up *sudo* and *gksudo*.)

This means that when you run a program normally, it can't change any system files. It's only allowed to change system files if you explicitly give it permission to become root and change whatever it needs to. (In short, if a virus eats your system, or turns it into a botnet zombie, which is *highly* unlikely, it's your own fault. :P)

It's a bit like running Windows as a limited user, with the firewall enabled: since nothing has permission to change or damage anything important, nothing can and you can get away without anti-virus software as long as you exercise common sense.

Anyway, hope that cleared things up. Welcome to the Forums!

---

### Post by Hamchan on 2010-04-10
Linux cannot run Windows programs natively. Most viruses are written to run on Windows, so they would not run on Linux. There are very few Linux viruses and installing them requires deliberate effort from the user and even then it wouldn't be able to do a whole lot.

While there are a few anti-virus programs available for Linux, their primary purpose is to scan for Windows viruses. This is useful if you share information with Windows computers as it would keep the Windows computers safe. 

I've been running Linux for 2 years and have never installed anti-virus.

---

### Post by adam22 on 2010-04-10
You only need an anti virus if you plan on sharing files with Windows machines. For most users, you don't need one.

---

### Post by @rizz on 2010-04-10
But if you share files with your friends (who are still using windows) they might fall victim to the virus. So you might want to clean up the files or flashdrives before you share them with your friends.

you might want to take a look at KlamAV.....

of course you could do a better job and ask then to use linux:P

---

### Post by uRock on 2010-04-10
Welcome to Ubuntu Forums,

No anti-virus is needed.

Cheers,
Ronnie

---

### Post by _h_ on 2010-04-10
This should help you out some more:

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by HotShotDJ on 2010-04-10
> **adam22 said:**
> You only need an anti virus if you plan on sharing files with Windows machines.

> **@rizz said:**
> But if you share files with your friends (who are still using windows) they might fall victim to the virus. So you might want to clean up the files or flashdrives before you share them with your friends.
I hear comments like these all the time.  Where anybody got the idea that it was the responsibility of Linux users to protect the users of Windows is beyond me.  Of course, if you are running servers with the intention that Windows clients will be using them, then you do have a responsibility to those users.  Otherwise, running anti-virus software is simply a waste of YOUR resources.  People who run Windows are responsible for the security of their own machines.

---

### Post by Malacath on 2010-04-10
Thanks everyone.

It's good to know that I don't have to slow the computer down by running anti-virus.

---

### Post by albert s on 2010-04-10
> **HotShotDJ said:**
> I hear comments like these all the time.  Where anybody got the idea that it was the responsibility of Linux users to protect the users of Windows is beyond me.  Of course, if you are running servers with the intention that Windows clients will be using them, then you do have a responsibility to those users.  Otherwise, running anti-virus software is simply a waste of YOUR resources.  People who run Windows are responsible for the security of their own machines.


unless its your wife/partner on windows then you dont want their wrath. !  :lolflag:

---

### Post by adam22 on 2010-04-10
> **HotShotDJ said:**
> I hear comments like these all the time.  Where anybody got the idea that it was the responsibility of Linux users to protect the users of Windows is beyond me.  Of course, if you are running servers with the intention that Windows clients will be using them, then you do have a responsibility to those users.  Otherwise, running anti-virus software is simply a waste of YOUR resources.  People who run Windows are responsible for the security of their own machines.

Common courtesy....also, if the other machines in my house run Windows, I don't want to infect those...

---

### Post by uRock on 2010-04-10
I honestly expect the Windows programs to have much better, up to date definitions. The files I share with Windows machine are created within my machine, such as .docx documents, so I am not worried about infections.

---

### Post by HotShotDJ on 2010-04-10
> **albert s said:**
> unless its your wife/partner on windows then you dont want their wrath. !  :lolflag:Well, that is a completely different issue altogether. :)  But, I can't imagine allowing anybody that I cared about to run Windows. :popcorn:

---

### Post by lisati on 2010-04-10
> **albert s said:**
> unless its your wife/partner on windows then you dont want their wrath. !  :lolflag:

Or you're trying to appease your ISP when you're setting up an email server and want them to unblock port 25.

---

