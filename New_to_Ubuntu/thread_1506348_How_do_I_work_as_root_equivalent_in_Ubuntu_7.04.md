---
title: "How do I work as root equivalent in Ubuntu 7.04"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by Yash Pal on 2010-06-10
[SIZE=2][COLOR=Blue]Can someone please let me know as to how can I work as root equivalent in ubuntu 7.04. My PC will not accept any higher version (P3- Processor, 512 Mb RAM)

It is a dual boot system with Windows XP; default boot is Ubuntu. 
When I go to terminal, this is what I get:[/COLOR]

[/SIZE]                                                 [FONT=Bitstream Vera Sans, sans-serif][SIZE=2]yashpal@yashpal-desktop:~$ [/SIZE][/FONT] 
 

 [FONT=Bitstream Vera Sans, sans-serif][SIZE=2]yashpal@yashpal-desktop:~$ Sudo[/SIZE][/FONT]
 

 [FONT=Bitstream Vera Sans, sans-serif][SIZE=2]bash: Sudo: command not found[/SIZE][/FONT]
 

 [FONT=Bitstream Vera Sans, sans-serif][SIZE=2]yashpal@yashpal-desktop:~$ su[/SIZE][/FONT]
 

 [FONT=Bitstream Vera Sans, sans-serif][SIZE=2]Password: [/SIZE][/FONT] 
 

 [FONT=Bitstream Vera Sans, sans-serif][SIZE=2]su: Authentication failure[/SIZE][/FONT]
 

 [FONT=Bitstream Vera Sans, sans-serif][SIZE=2]Sorry.[/SIZE][/FONT]
 

 [FONT=Bitstream Vera Sans, sans-serif][SIZE=2]yashpal@yashpal-desktop:~$ su[/SIZE][/FONT]
 

 [FONT=Bitstream Vera Sans, sans-serif][SIZE=2]Password: [/SIZE][/FONT] 
 

 [FONT=Bitstream Vera Sans, sans-serif][SIZE=2]su: Authentication failure[/SIZE][/FONT]
 

 [FONT=Bitstream Vera Sans, sans-serif][SIZE=2]Sorry.[/SIZE][/FONT]
[FONT=Bitstream Vera Sans, sans-serif][SIZE=2]
[/SIZE][/FONT]
[FONT=Bitstream Vera Sans, sans-serif][SIZE=2][COLOR=Blue]Also, when I type in the password (the one which was set at the time of initial set up), the cursor does not move as if the password is not being typed in.[/COLOR][/SIZE][/FONT]
[FONT=Bitstream Vera Sans, sans-serif][SIZE=2][COLOR=Blue]I am at my wits' end (see how small is my wit). The black letters are the terminal output.
[/COLOR][/SIZE][/FONT]
[FONT=Bitstream Vera Sans, sans-serif][SIZE=1][SIZE=2][COLOR=Blue]I shall be very grateful for any clarification.[/COLOR][/SIZE]
[/SIZE][/FONT]

---

### Post by exodus_ on 2010-06-10
Hey there,

The command you are looking for is sudo, all lower case.

you also put the command you want to run directly after sudo like this.

```
sudo apt-get update
```

This above command would update your apt list.  You need to use your own password, not root, and it's normal that it does not echo anything in the password field.  This is done as a security measure so people can't look over your shoulder and guess your password based on it's length.

Take a look at [RootSudo]("https://help.ubuntu.com/community/RootSudo") from the ubuntu community help wiki.  It should help explain everything, including the rationale behind using sudo instead of the root account.

---

### Post by Paddy Landau on 2010-06-10
> **Yash Pal said:**
> My PC will not accept any higher version...
Check out [Lubuntu]("http://lubuntu.net/"). It may be right for your old PC. It's much [lighter than Xubuntu]("http://www.linux-mag.com/cache/7520/1.html").

---

### Post by limestone on 2010-06-10
sudo /bin/bash

---

### Post by 3rdalbum on 2010-06-10
A P3 with 512mb of RAM can still run regular Ubuntu 10.04. But the other poster is right - you don't use 'su' on Ubuntu, and you only use 'sudo' as part of a command.

If you specifically want the behaviour of 'su', use this:

```
sudo -i
```

---

### Post by Yash Pal on 2010-06-12
Thanks to Exodus, Paddy Landau, pont.andersson, 3rdelbum for all the help. I hope you enjoyed my joke (with poetic licence) about myself .

---

### Post by Paddy Landau on 2010-06-12
> **Yash Pal said:**
> I hope you enjoyed my joke (with poetic licence) about myself.
Maybe I'm a bit slow, but I don't get the joke!

Anyway, if this has solved your problem, please mark the thread as solved (use Thread Tools near the top of the page).

---

### Post by wilee-nilee on 2010-06-12
> **Paddy Landau said:**
> Maybe I'm a bit slow, but I don't get the joke!

Anyway, if this has solved your problem, please mark the thread as solved (use Thread Tools near the top of the page).

I think the joke was there were no problems but a bored youth.

---

