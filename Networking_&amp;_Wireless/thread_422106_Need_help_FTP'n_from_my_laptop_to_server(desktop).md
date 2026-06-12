---
title: "Need help FTP'n from my laptop to server(desktop)"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by mowjo13 on 2007-04-24
Hi, I am rather new to using forums, so sorry if I offend anyone with silly questions.  I am working with Ubuntu 6.06 Dapper Drake.  I am trying to ftp from my laptop to my desktop server which is running Ubuntu 6.06 server.  I set up vsftpd on each and modified the config and everything.  I believe that isnt the problem, since I followed rather well put together tutorials.  Anyway,  I don't know the basica ftp commands and such.  I am trying to connect to the server 192.168.0.104.  so from terminal on my laptop what would i type.  i have enabled anonymous to be able to modify, create, delete.  any help you can offer?  or maybe suggestions on how i could better suit individuals with useful information so they can further advise me?

Much appreciated all!..
Regards

---

### Post by mowjo13 on 2007-04-25
I should also mention i am using a wireless belkin g router.  also using belkin g notebook and desktop cards.  I've tried to use this to connect to my desktop from laptop but it says unavailable hostname.  i also cant seem to access ftp from my desktop which i've tried to setup the ftp server on.
ftp>  open 192.168.0.104    

thought i should mention that too.  thanks.

---

### Post by Emerzen on 2007-04-25
Is ftp a necessity or would SSH suffice?  If it would, check out [this thread]("http://ubuntuforums.org/showthread.php?t=420880")

---

### Post by mowjo13 on 2007-04-25
Yes that would work i think... i've tried that but had difficulties also.  I am looking for a very simple way to transfer a dummy text file back and forth from laptop to desktop.  i will read that post much thanks

---

### Post by Super_6_4 on 2007-04-25
I use a belkin g router to connect my two laptops. I just started playing with ssh/sftp and had the same *unrecognized host* problem. To fix that, you should just have to add the ip and host name to your system>network>hosts (tab). After I did that, I could ssh/sftp back and forth - no problems. Sry, if I'm repeating something you've already done.

---

### Post by mowjo13 on 2007-04-25
Thanks thats helpful, however using my ubuntu server i only get command line..  any help there on how i might need to set it up? i will do that on my laptop thx

---

### Post by mowjo13 on 2007-04-26
Ok, I guess what I am wondering is do i have to do anything on the server side to get it to work properly.  or will it be up and running by default and then all i have to do is connect to it via my laptop?  thanks for all your replies

---

### Post by Emerzen on 2007-04-28
Hmm, not really sure about Ubuntu server.  In the desktop version, when you install a server service, it will run automatically, so my guess is it would be the same for the server.  I'd also make sure your firewall will allow it (incoming connections) if you have one running.  Is your laptop running Windows.  If it is, I found the easiest GUI solution yet [here]("http://winscp.net/eng/index.php") .

---

