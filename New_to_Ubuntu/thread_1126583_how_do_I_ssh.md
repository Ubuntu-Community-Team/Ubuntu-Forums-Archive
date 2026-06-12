---
title: "how do I ssh?"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by civillian on 2009-04-15
I recently bought myself a new phone (the nokia E71) which I found out has support for/available for it a symbianOS version of PuTTY (ssh client)

For a telnet/ssh newbie, could someone please enlighten me as to how I would use ssh to connect my phone to my desktop computer? It's connected to the internet directly through the router I have in my house, its not on a LAN or anything like that, just a simple, direct connection.

Thanks!

---

### Post by urvaius on 2009-04-15
if it is not installed you need to install openssh-server
sudo apt-get install openssh-server
test it by typing
ssh localhost
then enter your username and password
then type "exit" to back out
you need to open port 22 on your router. to connect remotely

I would however change port 22 in /etc/ssh/sshd_conf to a different port number and open that one on your router.

---

### Post by civillian on 2009-04-15
I have changed the port the port in the ssh conf file to one I know to be open, but how do I access my pc from my mobile?

---

### Post by urvaius on 2009-04-15
you will have to install the putty program on your phone then start it up. I havent used it on a phone but you will enter your ip address and the port you opened up in the putty program. then connect. it will ask you for user name and password. If you have a dynamic ip address I would maybe go to dyndns.com and get a free domain name and register your current ip in there. that is what I use. your router may be able to use the dyndns information in it as well my linksys does.

---

### Post by civillian on 2009-04-15
got it working, just a few final bugs (errors in PuTTY, like errors connecting, but those can be figured out with the help of google :D).
Thanks for the help in getting it all set up :)

---

### Post by civillian on 2009-04-15
*update*
I keep getting socket error (-34) when attempting to log in to [email]civint@xxx.xxx[/email].x.x
what does this mean?

---

### Post by urvaius on 2009-04-15
it is going to be something with that putty program connecting. make sure the port number is correct. Test it from your computer directly

at command prompt type 
in ssh [email]civint@xxx.xxx[/email].x.x:"port number"
to ssh to yourself. if that works it is setup correct. 
and must be something with the phone putty. there are other programs for your phone that will work as well.

---

