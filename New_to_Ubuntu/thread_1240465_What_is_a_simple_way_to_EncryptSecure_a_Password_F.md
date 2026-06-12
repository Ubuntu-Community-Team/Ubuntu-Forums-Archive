---
title: "What is a simple way to Encrypt/Secure a Password File?"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by mikodo on 2009-08-14
Hello everyone,

Please point me towards the directions, to encrypt/secure a file, that I use to store my passwords. The easier for a newbie, is best for me.

I use:

/home/******/Desktop/Documents/Passwords file. Where****** is my user name.

Thank you.

---

### Post by Firestem4 on 2009-08-14
I use bcrypt all the time which is easily available in the repositories
```
sudo apt-get install bcrypt
```

Using a strong key (strong password ie: letters, numbers special characters, and no dictionary words) the blowfish algorithm used to encrypt files with has still to this day not been broken.

to encrypt a file using is as simple as 

```
bcrypt <filename>
```
It asks you to enter a password (twice for verification) and its encrypted. It adds the extension .bfe at the end of the file so you know its encrypted.

to unencrypt just do the same thing

```
bcrypt <filename>
```

and it asks you for the password.

---

### Post by HermanAB on 2009-08-14
gpg -c filename

or just right click the file and select encrypt since it is probably already installed on your system!

---

### Post by mikodo on 2009-08-14
> **Firestem4 said:**
> I use bcrypt all the time which is easily available in the repositories
```
sudo apt-get install bcrypt
```

Using a strong key (strong password ie: letters, numbers special characters, and no dictionary words) the blowfish algorithm used to encrypt files with has still to this day not been broken.

to encrypt a file using is as simple as 

```
bcrypt <filename>
```
It asks you to enter a password (twice for verification) and its encrypted. It adds the extension .bfe at the end of the file so you know its encrypted.

to unencrypt just do the same thing

```
bcrypt <filename>
```

and it asks you for the password.


Thank you for the reply,

I installed bcrypt from Synaptic and tried your commands. Seems I am missing something. Please see attached screen shot of terminal.

---

### Post by Ranemills on 2009-08-14
You're in the wrong directory for the file. If the file is in a folder called Documents on your Desktop then you need to run the command
```
cd ~/Desktop/Documents
```Then run the command you want to.

---

### Post by mikodo on 2009-08-14
> **HermanAB said:**
> gpg -c filename

or just right click the file and select encrypt since it is probably already installed on your system!


Hello again, HermanAB

I tried gpg -c PASSWORDS with the following screen shot of terminal results. I am not sure what I am missing.

---

### Post by mikodo on 2009-08-14
> **Ranemills said:**
> You're in the wrong directory for the file. If the file is in a folder called Documents on your Desktop then you need to run the command
```
cd ~/Desktop/Documents
```Then run the command you want to.

Thank you for the code: I ran it and was able to encrypt using bcrypt PASSWORDS in terminal. Now I don't now how to open it or decrypt it.

Please advise, See Screenshot of Terminal.

Thanks

---

### Post by Ranemills on 2009-08-14
I don't have any experience with encryption but from the screenshot it doesn't like it did encrypt to me. Is the file name all uppercase? I believe the terminal is case-sensitive.

As to unencrypting:

> **Firestem4 said:**
> 

to unencrypt just do the same thing

```
bcrypt <filename>
```and it asks you for the password.

And I'd assume opening is just like any normal file once it is unencrypted.

Hope that helps a bit.

---

### Post by mikodo on 2009-08-14
> **Ranemills said:**
> I don't have any experience with encryption but from the screenshot it doesn't like it did encrypt to me. Is the file name all uppercase? I believe the terminal is case-sensitive.

As to unencrypting:



And I'd assume opening is just like any normal file once it is unencrypted.

Hope that helps a bit.


Thank you; I believe the file is now encrypted because I cannot open it on the desktop by clicking it on the desktop either as seen on the desktop Snapshot below:

---

### Post by mikodo on 2009-08-14
Well what started to be an easy exercise, has now got my PASSWORDS file unaccessible to me. 

To recap what I have done:

Installed bcrypt from Synaptic Package Manager

ran ```
cd ~Desktop/Documents
``` in Terminal

ran ```
bcrypt PASSWORDS
``` in Terminal

Entered in the required new encryption password twice

And found I cannot open the PASSWORDS file either in Terminal or by clicking on the icon in panel in Gnome desktop.

Please see earlier screenshots of my attempts at opening the file PASSWORDS in previous posts.
 
I am at a loss, as to what to do now.

Thank you

---

### Post by Shig on 2009-08-14
**Usage**   bcrypt [-orc][-sN] file ...
  Encrypted files will be saved with an extension of .bfe. Any files ending in .bfe will be assumed to be encrypted with bcrypt and will attempt to decrypt them. Any other input files will be encrypted. If more than one type of file is given, bcrypt will process all files which are the same as the first filetype given.
  By default, bcrypt will compress input files before encryption, remove input files after they are processed (assuming they are processed successfully) and overwrite input files with random data to prevent data recovery.


You should have passwords.bfe instead of passwords after encrypting with bcrypt. If the file does not end in .bfe, bcrypt will encrypt the file, if the file ends in .bfe, bcrypt will **decrypt** the file.


You may have to rename the file to passwords.bfe, but bcrypt should have done that for you, so check to see if there is a passwords.bfe file.

---

### Post by mikodo on 2009-08-14
Yes Shig, the file is now called Passwords.bfe

As my earlier posts show in the screenshots, I am not able to decrypt it with running bcrypt in terminal nor open it on desktop in any way. 

Any ideas?

What does this mean?  **Usage bcrypt [-orc][-sN] file ... **

All is not lost though: A testament to all you geeks out there who have been telling us less informed to backup; backup; backup.... "has paid off in Spades". The PASSWORDS file remains available to me on an external hard drive that I use for backups.

but, let's see if we can figure out my screw up and get me opening the encrypted file. 

Thank you.

---

### Post by mikodo on 2009-08-14
Oh well, I restored the PASSWORDS file from backup and renamed it as passwords. Now I have an decrypted file I can open; And a PASSWORD.bfe file I cannot.

If anyone else wants to take a stab at this, I would be appreciative. For all who have given advice, please accept my thanks.

Mikodo

---

### Post by Ranemills on 2009-08-15
Since it became encrypted, have you tried running the original code?
```
bcrypt file
```I can't see it in any screenshots or maybe you just haven't shown it. From what I see in earlier replies, that is what you need to decrypt it.

This is a quick summary of what's happened and what needs to be done:
From what I can see, the file has a .bfe file extension. This means it is encrypted. Run the command that you used to encrypt it again and the .bfe extension should be removed and you should be able to access it.

---

### Post by jakupl on 2009-08-15
wow this thread is confusing.

To make it clear:

When you decrypt the file again, you must write ```
bcrypt <file>.bfe

```
so remember that the file has gotten an extention.

And beware, if you have one file called "passwords" and one encrypted file called "passewords.bfe", and you decrypt the file, it will overwrite the original "passwords" file.

---

### Post by mikodo on 2009-08-15
Hello everyone,

All is now fine. Following the advice of other posters in this thread, success was found by the following:

Initially I needed to be in the correct directory,so ran

```
cd ~/Desktop/Documents
```

then ran,

```
bcrypt PASSWORDS
```

then entered a Encryption Key twice as prompted,

Now the PASSWORDS file became encrypted as seen in documents as PASSWORDS.bfe



When I wanted to decrypt PASSWORDS.bfe to allow me to open it, I opened terminal and ran again to enter into the correct directory,

```
cd ~/Desktop/Documents
```

then ran,

```
bcrypt PASSWORDS.bfe
```

then, per the prompt, entered the Encryption Key again, and PASSWORDS.bfe was decrypted to PASSWORDS in documents and could be opened.


Following the advice and code from the top, allowed me to encrypt PASSWORDS again, and so on...


Thank you everyone, for your patience and help.

---

### Post by bhagwad on 2009-10-26
Thanks for the clear instructions!

---

