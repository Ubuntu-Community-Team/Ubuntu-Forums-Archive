---
title: "Strange login message ........... what's up?"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-02-26
I finally went from 8.04 to 8.10 and I have certain regrets.

One of the problems is that every time I boot my computer this message pops up after entering login name and password.

"Users $HOME.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

What's up?

Thanks.

---

### Post by lykwydchykyn on 2009-02-26
Can you post the output of:
```

ls -l ~/.dmrc

```

---

### Post by tahitiwibble on 2009-02-26
```
dad@dad-desktop:~$ ls -l ~/.dmrc
-rw------- 1 dad dad 27 2009-02-22 08:27 /home/dad/.dmrc
dad@dad-desktop:~$ 
```

---

### Post by lykwydchykyn on 2009-02-26
Hmm... try this and see if it fixes it:
```

chmod 644 ~/.dmrc

```

That will make the permissions what the error suggested.  Not sure why they need to be 644, but I suppose the program knows what it needs.

---

### Post by tahitiwibble on 2009-02-26
```
dad@dad-desktop:~$ ls -l ~/.dmrc
-rw------- 1 dad dad 27 2009-02-22 08:27 /home/dad/.dmrc
dad@dad-desktop:~$ chmod 644 ~/.dmrc
dad@dad-desktop:~$ ls -l ~/.dmrc
-rw-r--r-- 1 dad dad 27 2009-02-22 08:27 /home/dad/.dmrc
dad@dad-desktop:~$
``` 

Done! I'm logging out to try it.

---

### Post by tahitiwibble on 2009-02-26
Hmmm ........... I just rebooted and checked the requested permissions are good and **still** get the same message?

---

### Post by apmcd47 on 2009-02-26
Stupid question, but what are the ownerhip/permissions of /home/dad? ie what is the output of ```
ls -ld $HOME
```

---

### Post by The Cog on 2009-02-26
Then try deleting it (it will get re-created):
**rm ~/.dmrc**

---

### Post by tahitiwibble on 2009-02-26
```
dad@dad-desktop:~$ ls -ld $HOME
drwxrwxrwx 101 dad dad 4096 2009-02-26 12:22 /home/dad
dad@dad-desktop:~$ 
```

---

### Post by tahitiwibble on 2009-02-26
> **The Cog said:**
> Then try deleting it (it will get re-created):
**rm ~/.dmrc**

I just did, then rebooted and **still** get the same message! Gremlins??

edit* and the file wasn't recreated yet.

---

### Post by empty_spaces on 2009-02-26
I had this same issue a couple of weeks ago, the following link helped resolve this.
[http://ubuntuforums.org/showthread.php?t=371052](http://ubuntuforums.org/showthread.php?t=371052)
The solution comes up at post #8, although I don't quite remember if I changed the permissions to 700, or 755, or 766, or 777.

---

### Post by apmcd47 on 2009-02-26
> **tahitiwibble said:**
> ```
dad@dad-desktop:~$ ls -ld $HOME
drwxrwxrwx 101 dad dad 4096 2009-02-26 12:22 /home/dad
dad@dad-desktop:~$ 
```

```
chmod go-w $HOME
```

should do the trick. $HOME is insecure. See also open_spaces' post in this thread.

Andrew

---

### Post by tahitiwibble on 2009-02-26
Have to take 5 for a while ...... will try the two last two posts suggestions as soon as I get back. 

Thanks guys ........... a lot!

---

### Post by tahitiwibble on 2009-02-26
> **apmcd47 said:**
> [CODE] $HOME is insecure. 

Andrew, please, what does **that** mean?

---

### Post by apmcd47 on 2009-02-26
> **tahitiwibble said:**
> Andrew, please, what does **that** mean?

The permissions for your home directory are (were?) rwxrwxrwx. These are three sets of permissions: the first are the owner, or User, permissions, the second are the Group permissions and the third Other permissions (everyone else). The three characters are R for readable, W for Writeable and X for eXecutable. Normally a home directory would have rwxr-xr-x for publicly-readable directory, rwxr-x--- for group-readable or rwx------ for private. Anyone can write into your directory. That is what I meant by insecure.

Andrew

---

### Post by presence1960 on 2009-02-26
> **tahitiwibble said:**
> I finally went from 8.04 to 8.10 and I have certain regrets.

One of the problems is that every time I boot my computer this message pops up after entering login name and password.

"Users $HOME.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

What's up?

Thanks.

I found a graphical solution when this happened to me. I opened nautilus from a terminal (use sudo nautilus)then went to the .dmrc file in my home directory. right clicked on it and chose properties. went to permissions and changed ownership to me. closed it out and rebooted. everything worked then.

Edit: if I remember correctly I used a live cd.

---

### Post by tahitiwibble on 2009-04-26
> **The Cog said:**
> Then try deleting it (it will get re-created):
**rm ~/.dmrc**

Ever since I did this on the 26th February, the file was not re-created and I have no more .dmrc file! I still get the same error message but the computer is not affected in any apparent way. Is this risky?

---

### Post by Briga on 2009-04-27
I had the same issue here with a fresh install of 9.04. 

The first time is related to .dmrc and a chmod 644 will do the job but my home dir reverts back to 777 despite taking out write permissions to group and others. Maybe it's some daemon that updates it?

---

### Post by WhiteHorse on 2009-04-27
This worked for me on 9.04, I didn't test on 8.04...replace ricardimo with your username.

> sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo

---

### Post by Didius Falco on 2009-04-27
> **tahitiwibble said:**
> Ever since I did this on the 26th February, the file was not re-created and I have no more .dmrc file! I still get the same error message but the computer is not affected in any apparent way. Is this risky?

The .dmrc file simply tells the system any startup information it didn't find elsewhere. Here is what's in mine:

```



[Desktop]
Session=default
```Mine does have the two lines of white space - I don't know if that's the default or if it evenmatters, but I'd think not - since it's simply reading information, the system should just ignore the white space. It could also contain language startup options, but since I'm using only one language, it doesn't need to be in there.

Here is some community documentation that should walk you through exactly how to fix this:

[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

First, get your Home permissions set up properly, then you can work on the .dmrc situation. I'm currently looking around to see if the system will recreate it automatically or if you can roll-your-own.

One other thing: [COLOR=Red]**NEVER**[/COLOR] delete any kind of configuration or system file without making a backup of it first.

---

### Post by tahitiwibble on 2009-04-27
WhiteHorse, the problem is that I don't even have a dmrc file any more.

Didius Falco, thanks for the info and the link. I agree that the content of the dmrc file in my case doesn't seem very important because I don't even have one. I'll do as you suggested. Cheers

---

### Post by tahitiwibble on 2009-06-30
Could someone tell me how to re-create my .dmrc file.

Thanks

EDIT - PROBLEM SOLVED

---

