---
title: "Passwords and bereavement or how do I reinstall an OP"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by Keir23 on 2010-02-25
Hi every one, I'm new to Ubuntu 

Recently I have been given a PC tower the only problem is Ubuntu is already on the machine with a pass word. Unfortunately the only person who knew the pass word has passed away. 

I am new to computers but am trying to teach my self as I go along.  

I think my options are: 

1) Reinstall an operating system 
2) change the hard drive over 

3) Fined a way to bypass the password so I can fined out what is on the hard drive. 

If any one has any advice for my problem it would be greatly appreciated. 

Thanks Regards Keir23.

---

### Post by plucky on 2010-02-25
> **Keir23 said:**
> Hi every one, I'm new to Ubuntu 

Recently I have been given a PC tower the only problem is Ubuntu is already on the machine with a pass word. Unfortunately the only person who knew the pass word has passed away. 

I am new to computers but am trying to teach my self as I go along.  

I think my options are: 

1) Reinstall an operating system 
2) change the hard drive over 

3) Fined a way to bypass the password so I can fined out what is on the hard drive. 

If any one has any advice for my problem it would be greatly appreciated. 

Thanks Regards Keir23.


See [link](http://www.psychocats.net/ubuntu/resetpassword) to reset the password.

If it is not your system,do you really have to access the other persons data?

Or just boot an Ubuntu Live CD and access the hard drive from there,or re-install the operating system.

Good Luck

---

### Post by mikeyphi on 2010-02-25
If you know the username you can change the password

Get a root command line - probably easiest by booting into recovery mode.

enter:
passwd username

then follow the on-screen instructions.

If you don't know the username the next way to see what is there is to use a Live-CD and browse the partition. You won't be able to run the OS.

---

### Post by undecim on 2010-02-25
> **mikeyphi said:**
> If you don't know the username the next way to see what is there is to use a Live-CD and browse the partition. You won't be able to run the OS.

This command should give you the username of the first user on the system:
```
cat /etc/passwd | grep 1000 | cut -d ":" -f 1
```

changing 1000 to 1001 should give you the second user, 1002, give the third, and so on.

---

### Post by Keir23 on 2010-03-02
> **plucky said:**
> See [link]("http://www.psychocats.net/ubuntu/resetpassword") to reset the password.

If it is not your system,do you really have to access the other persons data?

Or just boot an Ubuntu Live CD and access the hard drive from there,or re-install the operating system.

Good Luck

Thanks Plucky I followed the instructions in you're link and every thing went  well : )  

Thanks every one for your advice its much apreceated. 

Regards Keir.

---

