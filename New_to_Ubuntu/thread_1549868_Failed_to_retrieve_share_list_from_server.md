---
title: "Failed to retrieve share list from server"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by raceon4 on 2010-08-10
Ok,  I have searched and found multiple threads on this issue but I am still completely lost on what is going on.  I can see all of the computers that I can connect to when I go to places-network but I keep getting this error message.

Unable to mount.  Failed to retrieve share list from server.

I have no idea where to go from here.  I think that there is a password on the server which I know.  I have no idea where to enter a username or password or anything like that.  Is there anyone who can help me without just referring me to previous threads?  Like I said they aren't making sense to me.  Thank you.

---

### Post by Morbius1 on 2010-08-10
Not a lot to go on from your description.

All of these other machines on your network - are they Windows or Linux ?

If your other machines are Linux how are you sharing sharing the folders?

If you're using Samba - what method of samba?

Let's say for example that one of the machines you're trying to access is a Linux box. Post the output of the following command so we can see how you're sharing it:

```
net usershare info
``````
testparm -s
```

---

### Post by raceon4 on 2010-08-10
Sorry I had forgotten to mention that all of the other computers are running windows.  The main computer that the network runs is also a windows computer.  I have samba and smbf installed as well but am still without luck.  I'm not really sure what to do with either of those either.

---

### Post by Morbius1 on 2010-08-10
The first thing I would do is pick a particular windows machine ( hopefully one that is not running Win7 which has it's own problems to deal with ) and disable it's firewall. Then see if you can connect to a share.

IF not then run the following command from your linux box to see if it gives you any error messages:
```
smbtree
```There's one phrase which I don't quite understand:
> The main computer that the network runs is also a windows computer.All of the machines on your network are connected to a router directly, right?

---

### Post by raceon4 on 2010-08-10
Yes, they are all connected to a what I think is a Netgear router.  I guess I am not quite sure exactly how to disable the firewall using windows.  I was a Mac user before coming over to Ubuntu.

---

### Post by Morbius1 on 2010-08-10
> **raceon4 said:**
> Yes, they are all connected to a what I think is a Netgear router.  I guess I am not quite sure exactly how to disable the firewall using windows.  I was a Mac user before coming over to Ubuntu.
I'd suggest one of these:

[http://www.lmgtfy.com/?q=xp firewall disable]("http://www.lmgtfy.com/?q=xp%20firewall%20disable")

[http://www.lmgtfy.com/?q=vista firewall disable]("http://www.lmgtfy.com/?q=vista%20firewall%20disable")

---

### Post by raceon4 on 2010-08-11
Just curious is there a way to do this without disabling the firewall?

---

### Post by Morbius1 on 2010-08-11
We need to determine if the windows ( or Linux ) firewall is getting in the way.

I suppose you can issue the following command from from Ubuntu:
```
nmap -sT 192.168.0.100/22
```[COLOR=Blue]Change 192.168.0.100 to the ip address of the Ubuntu machine. [/COLOR]

That should list all the machines on your network by ip address and all the open ports. That will tell you if a firewall is in the way. Of course it could be that you aren't connected to the network either so it's not definitive.

---

