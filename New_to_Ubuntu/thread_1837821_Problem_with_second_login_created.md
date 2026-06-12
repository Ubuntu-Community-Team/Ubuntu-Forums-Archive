---
title: "Problem with second login created"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by katochd46 on 2011-09-02
Hi,

I am already having one login on my system. Some problem I am facing please suggest what to do.

login ID - ABCDEF
Password - 123456

Same password work for sudo.

1. How can i login as ROOT at start up only ?

2. Also i have created a new user account using following command
    useradd
    passwd

    login ID - XYZ
   Password - [FONT=monospace]7689

  When i login using above ID, 
  No folder is created in home directory for above user
  Also i get lot of error at start up
  Also Desktop is shown blank on GNOME

Please suggest for above two problems.
  
[/FONT]

---

### Post by LukeMorrison on 2011-09-02
I am uncertain of the answer to your first question. However to answer your second question, I would look at this link.
 
[http://www.go2linux.org/useradd-vs-adduser](http://www.go2linux.org/useradd-vs-adduser)

---

### Post by grahammechanical on 2011-09-02
I am assuming that you are using Ubuntu 11.04 as you do not give this information. As to this question

> 1. How can i login as ROOT at start up only ?

On Ubuntu we do not login as root at any time. We do not need to. The sudo command gives us all the authority we need to make changes to the system without the need for being root. The difference is that as root you or anyone using that session will have administrator privileges until you log out of that session. Whereas the sudo command gives us administrator privileges for the action we want to do or for a limited time. Then we revert automatically to being a normal user. It is safer this way.

Otherwise I think the command you are looking for 

> sudo su

Please wait for others to correct me if I am wrong.

Regards.

P.S. Please study this link

[http://www.linfo.org/su.html]("http://www.linfo.org/su.html")

---

### Post by Menschenfresser on 2011-09-02
What grahammechanical said is true, you don't *need* the root account, but if you really want, it can be activated. See [this page]("https://help.ubuntu.com/community/RootSudo#Enabling_the_root_account")

---

