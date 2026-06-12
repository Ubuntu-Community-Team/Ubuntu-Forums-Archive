---
title: "PuTTy"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by lovelyvik293 on 2010-08-01
I am using broadband from airtel(service provider) and my friend from other one...so if it's possible to access that computer from my computer through puTTY?

---

### Post by stlsaint on 2010-08-01
Your friend is using another what...? System or provider??
Either way you will still need a protocol in place. SSH, ftp,sftp servers, remote desktop or something must be used. Im not much a putty user so i really cant speak on what it handles but you will need an authentication method!

---

### Post by llamabr on 2010-08-01
On the "other" system, be sure to:

sudo apt-get install openssh-server

and then yes, you'll be able to ssh into it, using putty.  Or you could skip putty, and just do it right from the command line, as ssh is included in your base install.

---

### Post by tom.swartz07 on 2010-08-01
I think that we need a little bit more than just the openssh-server.

If youre trying to connect from a network outside of your own, as in; your friend is trying to connect from his home, and your computer is across town, you need to have some more setup. 

Could you verify that you have ports forwarded to your computer?
If you dont know if they are, then they aren't. You need to set it up manually before it works. 

Typically you need to open your browser and go to 
192.168.0.1 or 10.0.0.1 and configure your router to forward ports 22 to the computer in question.

Once thats set up, [http://www.whatsmyip.org/ports/](http://www.whatsmyip.org/ports/) will allow you to check if you correctly setup the port forwarding. 


After that, you need to configure DynamicDNS. Try DynDNS - this will assign a 'word' to your home network, rather than a long string of numbers for the IP. (as in lovelyvik293.com rather than 71.243.119.5)

Once thats all done, you should be good to go!
From PuTTY, you could connect from your friends computer to your computer. 
Hostname: whatever your DynDNS hostname is, lovelyvik293.com for example
Port: 22
Username: your username, haha

---

### Post by lovelyvik293 on 2010-08-01
It's another service provider and thanks all i'll give it a try....

---

### Post by tom.swartz07 on 2010-08-03
Thought so.

If youre on the same network, its REAL easy to connect.

[email]username@computername.local[/email]

boom. done

---

