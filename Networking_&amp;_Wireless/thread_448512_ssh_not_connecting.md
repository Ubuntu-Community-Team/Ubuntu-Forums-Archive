---
title: "ssh not connecting"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by kikazaru on 2007-05-19
Do you have any suggestions for debugging ssh?

I have a laptop and a desktop (both Feisty) on an ethernet switch connected to a broadband modem. I can ping one computer from the other:

ping 192.168.3.1
ping 192.168.3.2

Funnily enough the unused ports also return the ping sometimes, but I'm sure I can at least reach each computer:

ping 192.168.3.3

My desktop responds with "Connection refused" but the laptop doesn't respond at all...

I do have sshd running on both computers, and I did manage to ssh from my laptop when I had windows installed on it, using the PuTTY ssh program, but that might have been before I upgraded the desktop from edgy.

Any suggestions very much appreciated!

---

### Post by Psicolonia on 2007-05-19
can you ssh in loopback? does anyone ssh's anyone? (computerwise...)

i'm confused. any machine is running windows???

---

### Post by kikazaru on 2007-05-19
I can ssh to myself. It works no problem.

Bizarrely I now appear able to ssh from my laptop to my desktop, but I don't know why... because I didn't change anything... but I still get a permission denied when I try to ssh back to the laptop from the desktop. -Both are Ubuntu 7.04. I mentioned windows because I previously had that on my laptop...

---

### Post by Psicolonia on 2007-05-19
hummmm.... both machines ssh themselves but the desltop does not access the laptop even though it pings it.... have you tried different log ins, like logging as root?

---

### Post by kikazaru on 2007-05-20
Don't know hat happened there... I wrote a reply but it didn't appear.

Anyway, no real difference with root. I get a response using root in the cases that I can otherwise login as a user, but can't log in directly as root. 

laptop->laptop OK
desktop->desktop OK
laptop->desktop OK
desktop->laptop Permission Denied

---

### Post by Psicolonia on 2007-05-20
if you restart the deamon sshd on anothr port, can you login?

---

### Post by kikazaru on 2007-05-20
Sorry... I'm not sure how to change the port?

---

### Post by Psicolonia on 2007-05-20
try sshd -p PORTNUMBER and restart deamon

---

### Post by kikazaru on 2007-05-20
Ok, I tried the command you suggested, but I guess I'm not quite there:

>sudo sshd -p 10001
sshd re-exec requires execution with an absolute path

However, I found this line in /etc/ssh/ssh_config

#   Port 22

I uncommented it, changed the port, and ran 

sudo /etc/init.d/ssh restart

When I try to connect, it still fails. I get no response.

Another interesting thing is, I'm now at work, and my laptop is on another network. Now I can ssh to it from my *work* desktop machine... but I can't ssh back to my work desktop machine from the laptop.

Unless something magically changed, the laptop is rejecting an ssh from my desktop at home, but not from my desktop at work for some reason. 

Do you have to specify IP addresses to allow ssh connections from or something?

---

### Post by Psicolonia on 2007-05-21
oh boy... so it's kind of selecting the machines on its own... :)

I'm sure the answer is really simple but i can't find it...everything looks normal except for you home desktop. I'm starting to think that maybe it ain't your laptops fault but desktop.

I've making experiments and searching the manuals but didn't find anything. There is no ip Range. only a list of alowed users wich does not fit your case...
sorry...

keep trying somebody  else will give you an answer. If needed make a new post ;)

---

### Post by kikazaru on 2007-05-21
Ok, thanks for your help!

---

