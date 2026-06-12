---
title: "How to keep a journal?"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by a_satari on 2011-04-19
Hi everyone,

I use penzu.com to keep a journal, however I think its more secure if I kept it on my own computer.
Does anyone write a journal on their own computer and if so what methods do they use?

What I was thinking; write it in something like abiword, encrypt each entry then back-up. This does seem cumbersome,
but I can't think of a better solution. There must be software for Linux that covers this.

Thanks

---

### Post by mynameisnotbob on 2011-04-19
I know nothing about the topic, but it is discussed [here.]("http://ubuntuforums.org/showthread.php?t=212369")
Out of interest, what is abiword? Is it specifically for Xubuntu?

---

### Post by XubuRoxMySox on 2011-04-19
I journal! Using Abiword, as you do. But instead of encypting each new document, why not store them all in a single encrypted or password-protected folder instead.

I journal online too somewhat ([blog]("http://dixiedancer.posterous.com")), but I don't have all the personal stuff online of course.  My private journals are a record of prayers and answers, lessons gleaned from my bible reading, and my attempts to apply the lessons.  I dunno if I really need to encrypt that kinda stuff, but if it had lots of juicy stuff in it I sure would! :)

-Robin

---

### Post by uRock on 2011-04-19
To create the enrypted folder mentioned above you need only to run a few commends, then you have a private folder in you Home, that can only be accessed while you are logged into your account.> **Setup Your Encrypted Private Directory**

 
[LIST=1]
[*]Install ecryptfs-utils ```
sudo apt-get install ecryptfs-utils
```
[*]Setup your private directory```
 ecryptfs-setup-private
```
[*]Enter your login password, and either choose a mount pass phrase or generate one.
[LIST]
[*]**Record both pass phrases in a safe location!!! They will be required if you ever have to recover your data manually.**
[/LIST]
 
[*]Logout, and Log back in to establish the mount
[/LIST]
 
**Use Your Encrypted Private Directory**

 After logging back in, all content of any files or folders you write in **~/Private** will be encrypted when written to the disk, in the hidden directory **~/.Private**. For more information go to [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

### Post by ttshivers on 2011-04-19
You might want to use Tomboy Notes to keep a journal.  You can make a notebook containing journals and then create a new note for every day you write an entry.

---

### Post by Blasphemist on 2011-04-19
This started me thinking, a dangerous thing, and I found RedNotebook in the software center.

---

### Post by mynameisnotbob on 2011-04-19
i saw that when I ran a synaptic search!
But does it encrypt?

---

### Post by Blasphemist on 2011-04-19
> **uRock said:**
> To create the enrypted folder mentioned above you need only to run a few commends, then you have a private folder in you Home, that can only be accessed while you are logged into your account.For more information go to [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

The software I mentioned doesn't provide encryption that I can tell but what I quoted from above here tells you how to encrypt the folder that you use to store the documents.

---

### Post by mynameisnotbob on 2011-04-19
True that.

---

