---
title: "Remote Shutdown on Cable Network"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by ansh on 2008-03-21
Remote Shutdown on Cable Network 

--------------------------------------------------------------------------------

Im a new user to linux (edubuntu). I dont know much about this OS so when you're providing help please try to make it specific. 

So there are two computers connected together, both containing edubuntu. My task is to use one computer to shut down the other, and want to know how this is possible. Please include information, if I have to use a program already provided in OS or download one..and state the steps on how this could be done.

THX A LOT! 

And i  cant access the internet in any way.

Edit:
Is ssh already on the OS or not??

The 2 machines are connected and  i open ssh and type the following commands?
"ssh <username>@<computer name or ip_address>"
then"
I type the shutdown command"

What will this do and what is the shut down command and will this shutdown my pc aswell?

Im lost...somebody help me

---

### Post by ansh on 2008-03-21
anyone?

---

### Post by beren.olvar on 2008-03-21
> The 2 machines are connected and i open ssh and type the following commands?
"ssh <username>@<computer name or ip_address>"
then"
I type the shutdown command"


that should turn the remote pc off
just try that, if you have any trouble post it here

cheers!

---

### Post by ansh on 2008-03-21
what is the shutdown command :confused:

and i have to let it shutdown normally.

also this might be a dumb question the first step where it says the username if the computer edubuntu username? and the ip address.
Thankyou

---

### Post by beren.olvar on 2008-03-21
ok, probably there is some more elegant way to do this, but try
```

ssh remote.username@remote.adress sudo shutdown -h now

```
this will ask you 2 passwords...
one for loggin in and other for executing the shutdown
in both you should enter the same password,
and if you have the priviledges to shutdown the remote machine, then that should work

Note: if that works then you should try
```

ssh remote.username@remote.adress shutdown -h now

```
without the "sudo"
that will save one password prompt.

cheers

---

### Post by ansh on 2008-03-21
thankyou ill try this, any more suggestion are greatly appreciated.

---

