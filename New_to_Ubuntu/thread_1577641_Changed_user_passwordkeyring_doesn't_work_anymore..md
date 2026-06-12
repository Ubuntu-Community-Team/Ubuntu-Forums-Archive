---
title: "Changed user password/keyring doesn't work anymore."
date: 2010-09-19
forum: New to Ubuntu
---

### Post by aloprot on 2010-09-19
Hello, I have two accounts on my machine. One with custom rights and one with limited access. I changed the custom username's password. All well and fine till I wanted to start empathy. I wrote my account and then it ask me for something like this:"The password you use to log in to your computer no longer matches that of your login keyring." I try my new username's login password, doesn't work. What is this keyring, and what's the password to it? I thought the username's password is.


Thanks in advance!

---

### Post by benhard on 2010-09-19
hello aloprot,, :D
the keyring which yous say is password of your root user..the password same like u want to login as root autentification on the terminal using "sudo su"

just try it ! bye... :D

---

### Post by aloprot on 2010-09-19
That's what I'm saying, root password doesn't work. I tried several times but it doesn't work.

---

### Post by donato roque on 2010-09-20
> The password you use to log in to your computer no longer matches that of your login keyring." I try my new username's login password, doesn't work. What is this keyring, and what's the password to it? I thought the username's password is.

There are applications that keeps your login details so it can authenticate to services in the web automatically when you open them.  e.g. Evolution,Gwibber,Empathy. They get these login details from Password And Encryption Keys (Seahorse).  This information is encrypted so it has a password.  

Now normally your login password and this encryption password is the same.  When you change your login password this encryption password stays the same.  You can bring back the status quo by changing the encryption password too.  

Type:  ALT+F2.  SEAHORSE. ENTER.

Modify by: Right-click.  Change Password.

---

