---
title: "I need to access a suse linux server."
date: 2011-04-09
forum: New to Ubuntu
---

### Post by irtazaadilyousfani on 2011-04-09
Dear All, 
 
Please tell me that how can I access a Suse linux server via STB(IPTV Device having static IP on network card). I am connected on internet and don't have static IP. Please reply to it soon as I am unable to work for it.
 
Thanks

---

### Post by taseedorf on 2011-04-09
Well....I'm confused on your question.... you want to use your STB to connect to a server? I'm not sure if most normal STB can connect to servers..

---

### Post by irtazaadilyousfani on 2011-04-10
Yes there is an static ip configured on network interface of STB and that ip is allowed on the firewall. Just tell me how can I ssh an ip on a telnet window.

---

### Post by uRock on 2011-04-10
**ssh name@IP** such as **ssh uRock@192.168.254.253**

---

### Post by irtazaadilyousfani on 2011-04-10
please tell why name. as there is just unique ip. name is not specific.

---

### Post by uRock on 2011-04-10
To use ssh you will need a username for the server, so that you can log into it. [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by AlexDudko on 2011-04-10
You must specify username. You can use command of the type:
> ssh your_SUSE_server_hostname
but you certainly must specify your login name with **-l** parameter.  
> man ssh

---

### Post by Locke_99GS on 2011-04-10
If you don't specify a username, SSH will attempt to login with the username of who invoked it. This only works if the same username exists on both sides of the tunnel, and you in fact want to long in as that user (yourself) on the remote machine.

ex:
I have user accounts on all the other machines in my house. I can simply *ssh athena-desktop.local* to log into that machine with the same username. If I wanted to log into that same machine, but as my daughter instead, I would specify her username:
*ssh [noparse]athena@athena-desktop.local[/noparse]*

So, when not explicitly giving it a username, SSH will assume $USER.

---

### Post by irtazaadilyousfani on 2011-04-15
Dear,
 
Can you tell me how can I change the password of Root. I am a super user and want to change the password. Please reply

---

### Post by uRock on 2011-04-15
Everything you need to know about root can be found here. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by AlexDudko on 2011-04-15
> **irtazaadilyousfani said:**
> Dear,
 
Can you tell me how can I change the password of Root. I am a super user and want to change the password. Please reply

Log in as root and enter:
> passwd
You'll be prompted to enter new password and then to reenter it. If they match your root password will be changed.

---

### Post by Paqman on 2011-04-15
I'm a bit confused. You're trying to SSH into a server, from a STB? And you don't have the root password, or a user account on that server? What exactly are you trying to do, and why do you need to SSH in to do it? Is it actually your own server? And why/how are you accessing it from a STB?

---

### Post by irtazaadilyousfani on 2011-04-15
Actually it is not like that. I might have made a mistake by mixing few things. All are different.  first of all I wanted to ask abt the ssh of a suse server via stb and I got the answer. then I had a question in mind regarding changing root's password which isnot linked at all with the previous question. I shud have started a new thread but didn't. sorry for inconvenience.  Thanks for response.

---

