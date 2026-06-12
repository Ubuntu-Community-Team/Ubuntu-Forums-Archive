---
title: "[open] postfix + SASL Auth Daemon + dovecot"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by flafaille on 2009-11-18
Hi everybody this is my first post and I would like to say that I very like Ubuntu os since I installed it on a old pc.
 
I am a web programming and wanted to have a dev environement at the office. I need to have email working to code php script and try since yesturday and almost there but there is only one probleme.
 
So every setup is fine, I have thunderbird installed and can send mail without error, but I just cannot get (received email that I send locally)
 
My environement is:
 
3pcs - 2 running XP and 1 running ubuntu desktop 9.10
 
I already have xampp working fine with virtual folder
I already have setup bind9 as my DNS server
but now have to have email working.
 
I have do all the necessary to have email working
1- install postfix
2- install dovcot
3- install sasl auth daemon
4- squirrelmail
5- thunderbird
 
I can connect to [http://mail.mydomain.god/](http://mail.mydomain.god/) (that's open squirrelmail) I can login with both user that I have create. The message is sending properly but to both user but when I go into the inbox of both user nothing appear
 
Can someone helpl me
 
Fred

---

### Post by spikyjt on 2009-11-18
Did you manage to fix this? I'm afraid there isn't enough info here to help debug the problem, but do you really need that massively complex email setup to test your web services? I usually install ssmtp and set it to use my main MTA (you could use your ISP's). Its really easy to set up.

---

### Post by flafaille on 2009-11-18
> **spikyjt said:**
> Did you manage to fix this? I'm afraid there isn't enough info here to help debug the problem, but do you really need that massively complex email setup to test your web services? I usually install ssmtp and set it to use my main MTA (you could use your ISP's). Its really easy to set up.
 
 
Thanks but as Iam a newby with Ubuntu, I think it was the only way to do that kind of stuff. Now everything is fine and it's running as I expected. I haved a config error.
 
But if you would like to tell me more about a easyer way to do What I want I will appreciate you to give me more info.
 
tell me more about how to setup with my isp's because when I php sendmail it is not working. But this it is now
 
Sorry for my bad english written.
 
 
The french guy.

---

