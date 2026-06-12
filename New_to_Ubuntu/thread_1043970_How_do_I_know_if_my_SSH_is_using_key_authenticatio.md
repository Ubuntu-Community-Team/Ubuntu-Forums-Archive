---
title: "How do I know if my SSH is using key authentication"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by paikchris on 2009-01-19
I figured out my keys arn't being used for whatever reason. I'm trying to connect from my ubuntu laptop --> Windows XP. Normal ssh works. This is what i've done.

1. I have a set of keys generated from terminal in ubuntu
2. I've copied and pasted the public key into the "authorized_keys" file in C:documents and settings/Me/.ssh

Now i'm lost.

I've tried "ssh Me@Myip" but it asks me for my password. How do i disable this. So i can just log in using my key. 

I've also tried using Putty for ubuntu. I went to the "Auth" and loaded my key. But it's unable to use my key. the private key is located in /home/chris/.ssh on my ubuntu laptop

---

### Post by blackened on 2009-01-19
Turn off password logins, if it accepts your login, then it's using the keys.

---

### Post by paikchris on 2009-01-19
how do i do that?

Do i do that on my laptop (ubuntu)?
or on my Windows XP at home?

---

### Post by blackened on 2009-01-19
On the laptop, which is the one that's running openssh-server I'm assuming.

Edit the file /etc/ssh/sshd_config. Change "PasswordAuthentication" to no.

---

### Post by hyper_ch on 2009-01-19
if it just auto-logins into the other machine without being asked for a password then they kex exchange was successful.

---

### Post by paikchris on 2009-01-19
status update

---

### Post by hyper_ch on 2009-01-19
>  9 Minutes Ago   	  
paikchris

a little help?

You replied to my thread concerning ssh. If you could answer a couple questions i'd really appreciate it.


--> no private support (and you're now on my blocklist)

---

### Post by paikchris on 2009-01-19
> **hyper_ch said:**
> --> no private support (and you're now on my blocklist)

a simple pm would have sufficed

---

### Post by blackened on 2009-01-19
A secondary role of this forum is that it acts as an archive that people can access for already-solved problems. This also helps in reducing thread/post count across the forum, hence private support is discouraged by many.

---

### Post by tangibleorange on 2009-01-19
```
gksu gedit /etc/ssh/sshd-config
```

Find the line that says "PasswordAuthentication", uncomment it, and change 'yes' to 'no'. then run:

```
sudo /etc/init.d/ssh restart
```

---

