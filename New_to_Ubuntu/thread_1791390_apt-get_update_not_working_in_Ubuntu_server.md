---
title: "apt-get update not working in Ubuntu server"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by janaahan13 on 2011-06-26
Hi,
I'm a newbie to ubuntu.

I installed ubuntu server 11.04 64-bit in my machine and I wanted to install the ubuntu-desktop on top of that.

I tried sudo apt-get update and received an error message similar to 

sudo apt-get update
ERR [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
   temporary failure resolving security.ubuntu.com
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
   temporary failure resolving archive.ubuntu.com
... this repeats a few times, then I get
IGN [http://security.ubuntu.com](http://security.ubuntu.com) hoary-updates Release.gpg
.....  with some all the lists

same case for sudo apt-get install ubuntu-desktop

How do I solve this problem?

Thanks in advance

---

### Post by wolfen69 on 2011-06-26
Are you sure you installed 11.04? Hoary was released years ago.

---

### Post by Bachstelze on 2011-06-26
Wow, that brings back memories...

---

### Post by janaahan13 on 2011-06-26
I have clearly mentioned the word "similar". Mine was "nasty" or something else. The question was the type of errors msg. Sorry if i had confused you

---

### Post by dFlyer on 2011-06-26
I'm very confused about what your current os is. Hoary is no longer supported, and nasty is not an ubuntu distro. If you want help please be specific and post the exact error message.

---

### Post by jtarin on 2011-06-26
In a terminal ```
cat /etc/apt/sources.list
```and check the addresses it refers to and see that they are valid "Ubuntu" and "your version" repositories. If you can't determine, post your  /etc/apt/sources.list here.

---

### Post by haqking on 2011-06-26
> **janaahan13 said:**
> I have clearly mentioned the word "similar". Mine was "nasty" or something else. The question was the type of errors msg. Sorry if i had confused you


did you mean natty ? as in natty narwhal 11.04

however that doesnt explain why your sources.list is pointing to old outdated repos ?

---

### Post by jtarin on 2011-06-26
[Need a new sources list?]("http://askubuntu.com/questions/49572/how-do-i-restore-the-sources-list-file"). I woul;d like to mention that your message says temporary.....sometimes a server could be down. Changing server from the default has its advantages.

---

### Post by jtarin on 2011-06-26
[Working with repositories from the commandline.]("https://help.ubuntu.com/community/Repositories/CommandLine")

---

