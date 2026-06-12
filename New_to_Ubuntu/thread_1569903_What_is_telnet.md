---
title: "What is telnet ?"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by Jian0203 on 2010-09-07
Can anyone tell me what is telnet ?
What is the function of telnet ? I was told to install this but I don't really understand it ~

Thanks for answering ^^
Appreciate it ~

---

### Post by mhgsys on 2010-09-07
Hello , and welcome to the world wide web
Use your mouse to click on the link below

[http://lmgtfy.com/?q=telnet](http://lmgtfy.com/?q=telnet)

;)

---

### Post by migs73 on 2010-09-07
> **mhgsys said:**
> Hello , and welcome to the world wide web
Use your mouse to click on the link below

[http://lmgtfy.com/?q=telnet](http://lmgtfy.com/?q=telnet)

;)

Amusing, but I don't think it was the kind of help that was expected?

---

### Post by pricetech on 2010-09-07
[http://www.telnet.org/](http://www.telnet.org/)

[http://en.wikipedia.org/wiki/Telnet](http://en.wikipedia.org/wiki/Telnet)

[http://www.webopedia.com/TERM/T/Telnet.html](http://www.webopedia.com/TERM/T/Telnet.html)

[http://support.microsoft.com/kb/231866](http://support.microsoft.com/kb/231866)

and many more.  Just enter "telnet" in your favorite search engine.

---

### Post by mhgsys on 2010-09-07
> **migs73 said:**
> Amusing, but I don't think it was the kind of help that was expected?

[quote=Jian0203]Can anyone tell me what is telnet ?
What is the function of telnet ? I was told to install this but I don't really understand it ~[/quote]


I'm sure the question what telnet is and what the function is is in that list.

---

### Post by bodhi.zazen on 2010-09-07
IMO you should not use telnet (although it has uses), for the most part you should use ssh.

---

### Post by Jian0203 on 2010-09-07
> **bodhi.zazen said:**
> IMO you should not use telnet (although it has uses), for the most part you should use ssh.

SSH ? I have installed OpenSSH but the network configuration trap me off ..
I am blur with SSH configuration part .. Can anyone teach me how to setup a SSH server please ?

---

### Post by bodhi.zazen on 2010-09-07
> **Jian0203 said:**
> SSH ? I have installed OpenSSH but the network configuration trap me off ..
I am blur with SSH configuration part .. Can anyone teach me how to setup a SSH server please ?

That is a very general question, see :

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

If you have a specific question, ask.

I can not tell from your post, but you may need to forward port 22 from your router.

---

### Post by Jian0203 on 2010-09-07
> **bodhi.zazen said:**
> That is a very general question, see :

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

If you have a specific question, ask.

I can not tell from your post, but you may need to forward port 22 from your router.

Now I have installed OpenSSH in Ubuntu , then i just need to follow the configuration step in the link you given ?

Installation -> Configuration -> SSH Keys ..
I try to follow the steps above , but when it comes to SSH Keys part .. I met some problem with this "ssh-copy-id username@remotehost" .
The error says the connection was refused ..

I am kinda blur with this ~ I was told by my lecturer to install this but I seem to be lost because I am new to Ubuntu ~

Things I don't know :
(1)What is the main function of setting up OpenSSH ?
(2)How does it help in Ubuntu ?

---

### Post by bodhi.zazen on 2010-09-07
> **Jian0203 said:**
> Now I have installed OpenSSH in Ubuntu , then i just need to follow the configuration step in the link you given ?

Installation -> Configuration -> SSH Keys ..
I try to follow the steps above , but when it comes to SSH Keys part .. I met some problem with this "ssh-copy-id username@remotehost" .
The error says the connection was refused ..

I am kinda blur with this ~ I was told by my lecturer to install this but I seem to be lost because I am new to Ubuntu ~

Things I don't know :
(1)What is the main function of setting up OpenSSH ?
(2)How does it help in Ubuntu ?

Open ssh has many uses, it allows, among other things, remote shell access.

In terms of your homework, please ask your instructor.

In terms of ssh keys, see

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

You have to change "username" to your log in name and "remotehost" either to your server ip address of FQDN (assuming you have registered a domain name and forwarded your port from your  router).

Last piece of advice - you should NOT be installing and configuring servers without understanding their function and security implications.

---

### Post by pricetech on 2010-09-07
Please ask a mod to merge this with your SSH thread since this is evolving in that direction.

---

### Post by Jian0203 on 2010-09-07
> **bodhi.zazen said:**
> Open ssh has many uses, it allows, among other things, remote shell access.

In terms of your homework, please ask your instructor.

In terms of ssh keys, see

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

You have to change "username" to your log in name and "remotehost" either to your server ip address of FQDN (assuming you have registered a domain name and forwarded your port from your  router).

Last piece of advice - you should NOT be installing and configuring servers without understanding their function and security implications.

Thanks a lot for your advice ^^

---

### Post by The Cog on 2010-09-07
IN brief:

Both telnet and SSH are protocols that allow a user on one computer (the client) to connect to another computer (the server) and then run commands and see their out put remotely. They give a user on the client a command-line login to the server. It is often used to connect to and configure routers or remote servers etc.

Telnet uses plain text over the network and is nowadays regarded as insecure because the network connection can be monitored (sniffed) to discover your password and see what you are doing. SSH (Secure SHell) uses an encrypted connection to prevent such eavesdropping.

You say you are installing SSH on your Ubuntu. Do you want to use Ubuntu as a client to connect to a server elsewhere, or do you want to install an SSH server on your Ubuntu so that other people can connect to your computer and log in?

To use your ubuntu computer as a client to log into another computer, you don't have to install anything extra - the ssh client software is installed by default. Just use the command **ssh x.x.x.x** where x.x.x.x is the address of the computer to connect to. 

To allow other computers to connect to yours, just use the command
**sudo apt-get install openssh-server**
to install the server. Other people will be able to log into your computer using ssh (provided they know a username and password). If the computer is accessible from the internet you will get lots of other computers trying to break in by guessing passwords so make sure that ALL accounts have good passwords, or configure the server to use keys instead. I agree with bodhi.zazen - unless it is really needed for your course work, I don't think you should be installing an ssh server without further understanding the security risks (access and damage by malicious remote users).

---

