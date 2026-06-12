---
title: "One Terminal line that wipes a drive?"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by Curse on 2010-06-30
I've heard that there's a single input I can enter into a terminal to immediately and completely wipe/randomize data on my HDD, is this true?

---

### Post by konqueror7 on 2010-06-30
ummm,,,yeah, why? it pretty much wipes everything depending on what you give to it as parameters...

if you need to wipe a drive, better go use a partition editor, such as, gParted...

---

### Post by Curse on 2010-06-30
> **konqueror7 said:**
> ummm,,,yeah, why? it pretty much wipes everything depending on what you give to it as parameters...

if you need to wipe a drive, better go use a partition editor, such as, gParted...

Just curious what it is, it is just one of those things that would be interesting to know, if that makes sense

---

### Post by djyoung4 on 2010-06-30
pretty sure you'll get kicked off the forums for posting it.  theres something I read on here about it but I can't find it right now.

---

### Post by ankspo71 on 2010-06-30
Hi,
Shred and Wipe are two small command line utilities for secure file deletion. They both have a bunch of options that can be used to configure the erasing process. As far as I know, shred still can't erase individual folders though, but according to a link I saw it can be used to erase an entire drive. Shred and Wipe (especially wipe) can take an incredibly long time to securely erase the average hard drive though. So unless the person is selling their computer, or throwing away a hard drive or something, reformatting a drive is much faster and more convenient (but less secure) way to erase data.
Hope that helps.

---

### Post by CharlesA on 2010-06-30
Using dd incorrectly (or correctly if that's what you want to do) will overwrite a drive. It takes a long time, but I guess it works well if you are getting rid of a computer and want all data to be unrecoverable.

---

### Post by Jakiejake on 2010-06-30
> **CharlesA said:**
> Using dd incorrectly (or correctly if that's what you want to do) will overwrite a drive. It takes a long time, but I guess it works well if you are getting rid of a computer and want all data to be unrecoverable.

So if I type > dd right now will I say Bye Bye to my data? :confused:

---

### Post by Jakiejake on 2010-06-30
Oh and you won't be able to wipe a drive if your currently booting of it!

---

### Post by konqueror7 on 2010-06-30
> **djyoung4 said:**
> pretty sure you'll get kicked off the forums for posting it.  theres something I read on here about it but I can't find it right now.

that's the thing,,,there have been posters that give commands, and users just copy and paste,and the next thing you know, you got more space available...

you could usually see some signatures of some here in the forums, warning you about the command...:p

---

### Post by Curse on 2010-07-01
Anyone care to PM what I would need to input? How about for just a specific folder? Just curious, I don't have any illicit reason for wanting to know, it just seems like it would be useful to be able to permanently remove data.

---

### Post by wojox on 2010-07-01
[How to wipe a hard drive clean in Linux]("http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux")

---

### Post by ankspo71 on 2010-07-01
^ Nice dd example ^

Here are some more examples for secure file deletion:

[U][URL="http://kevin.vanzonneveld.net/techblog/article/delete_files_securely_with_shred/"]Delete files securely with shred
[/URL][/U]_[man page for wipe]("http://manpages.ubuntu.com/manpages/intrepid/man1/wipe.1.html")_

Be careful when it comes to things like this, because sometimes all it takes is one mistyped command to ruin a system.

---

### Post by k3lt01 on 2010-07-01
> **Curse said:**
> Anyone care to PM what I would need to input? How about for just a specific folder? Just curious, I don't have any illicit reason for wanting to know, it just seems like it would be useful to be able to permanently remove data.At the VERY top of the first page of Absolute Beginner Talk there is a thread by jdong titled **ATTENTION ALL USERS: Malicious Commands**. I suggest you read it and you will know why no-one is telling you what you want to know.

---

### Post by yetiman64 on 2010-07-01
@ankspo71

> **ankspo71 said:**
> ...
Shred isn't available in Lucid's repos, but I'm sure it can be still downloaded from elsewhere.

Stock standard Lucid install here,

```
man shred
``` gives,

> SHRED(1)                                                                                      User Commands                                                                                      SHRED(1)

NAME
       shred - overwrite a file to hide its contents, and optionally delete it

SYNOPSIS
       shred [OPTION]... FILE...

DESCRIPTION.....also use it from Lucid live cd as a tool. Edit 2: it's part of the coreutils package.

Edit1: Re k3lt01  +1

---

### Post by ankspo71 on 2010-07-01
Cool, I didn't know it was already installed. I was searching for it using the name only search in synaptic. Changing post now... thanks

---

### Post by Curse on 2010-07-01
> **k3lt01 said:**
> At the VERY top of the first page of Absolute Beginner Talk there is a thread by jdong titled **ATTENTION ALL USERS: Malicious Commands**. I suggest you read it and you will know why no-one is telling you what you want to know.

Understood, as far as I'm concerned this thread is solved, thank you all!

---

