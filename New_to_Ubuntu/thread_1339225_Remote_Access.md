---
title: "Remote Access"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Azrael3000 on 2009-11-27
Hi!

I have a question regarding Remote Accessing a Ubuntu computer in an Intranet.

So the problem schematics are:

Client -> Login Server -> Target

I can get to the Login Server via SSH that is no problem. But what I actually want is a VNC connection from Client to Target (or any other connection to the Desktop that is not console only). The target is within the intranet and can not be accessed from outside.

I didn't have much time to look for a solution since my time is limited. Anyway any help is appreciated.

Thanks,
Arno

---

### Post by albandy on 2009-11-27
System --> preferences --> remote desktop

---

### Post by Azrael3000 on 2009-11-27
Well remote desktop on the target machine is enabled.

My question is how to connect to it.

---

### Post by DanYoSon on 2009-11-27
Your best bet would be to tunnel the VNC through the ssh connection

here is a tutorial 
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

hope this helps

---

### Post by cj13579 on 2009-11-27
VNC will give you a GUI if thats what you want. To connect via VNC from the internet you will need to use port-forwarding on the router that the computer is connected to. The standard VNC port is 5900. You will also need to know the public ip-address of the router. This can be found from within the router or from [http://www.whatsmyip.net](http://www.whatsmyip.net)

---

### Post by bodhi.zazen on 2009-11-27
> **DanYoSon said:**
> Your best bet would be to tunnel the VNC through the ssh connection

here is a tutorial 
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

hope this helps

Your best bet would be [s]to tunnel the VNC through the[/s] ssh connection.

I fixed that for your. What is wrong with ssh -X ?

To connect VNC :

the default port is 5900. It varies by client, some clients you use

ip_address:5900

Others just :0

The second most common problem would be firewalls.

Third, if you are using vino , the default in Ubuntu, you need to be logged into Ubutnu in order to connect from remote.

---

### Post by Azrael3000 on 2009-11-27
Thank you:

I tried this actually but it didn't work. Maybe because I used the wrong commands. In detail I did:
```
user@client:~$ ssh user@login-server
user@login-server:~$ ssh -R 5900:localhost:5900 user@target

```

The error I got was:
```
Warning: remote port forwarding failed for listen port 5900

```

Then I should be able to connect to the target via vinagre (to localhost:59000)

Any mistakes you can find?

---

### Post by Azrael3000 on 2009-11-27
Ok solved :)

ssh -X ftw

The solution:
```

user@client:~$ ssh -X user@login-server
user@login-server:~$ ssh -X user@target

```

then execute any program from commandline, e.g. nautilus:
```

user@target: nautilus &

```

Thanks for the help.

---

