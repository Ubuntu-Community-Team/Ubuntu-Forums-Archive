---
title: "File System"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by jotnarta on 2011-05-02
Hi Everybody
I am an absolutely newbie, I am from a windows background, and finished installing ubuntu alongside windows 7.

I can see the file system in Places > File System .. But, most of the commands in ubuntu must run from commands.

I want to install Oracle 11g R1, and I found a document that list in steps how to install Oracle.

The problem is, I downloaded Oracle zip package, and I want to access it from terminal, but I can't access the folder that contains the zip file, I got the error: can't access SOA Suit ???, the "SOA Suite" is the drive name in "media":(

Is there any specific place that I have to download the zip files in, to be accessible??
Please help

Thank you

---

### Post by dniMretsaM on 2011-05-02
Is that the exact error? It's probably a file permission problem. Post the error exactly as it's shown in terminal.

---

### Post by jotnarta on 2011-05-02
Thank you, after running this command:
cd /media/SOA Suit

this is the error: ***bash: cd: SOA: No such file or directory***. 

My question is, I downloaded the zip file to "SOA Suit" drive, inside "Linux Software/database" directory, and I want to access the file "runInstaller.sh" from the terminal, any help pleeeeeeeeeas??

---

### Post by dniMretsaM on 2011-05-02
Try SOA_Suit instead of SOA Suit. Also try going to each subsequent director individually.
```
cd /media
``````
cd /SOA Suit
```Make sure your typing the names out correctly too. Sometimes I have cd problems that appear random and when I finally figure it out, I have no idea what I did differently. Just try some different things.

---

### Post by jotnarta on 2011-05-02
Thank you buddy.

Here is what I did.

I moved to the root directory '/'. and ran the command 'cd /SOA Suit' directly. but I got the same error.

I tried to change the name of the drive to "SOA_Suit", I got this error:

**The item could not be renamed, Operation not supported by backend**

---

### Post by cek on 2011-05-02
The command line is a little tricky when it comes to spaces in file names, try this:

```
cd /media/SOA\ Suit
```

OR if the directory is actually called "SOA Suite" as you mentioned:

```
cd /media/SOA\ Suite
```

---

### Post by jotnarta on 2011-05-02
Yessssssssssssssssssssssss, it worked fine :), 

I tried the following:

'cd /media/SOA\ Suit', and worked fine....:popcorn:

Thank you very much Buddy :guitar:

---

### Post by Sam White on 2011-05-02
Just a quick note, if a location has a space in it you can also enclose it in quotes.

Sam

---

