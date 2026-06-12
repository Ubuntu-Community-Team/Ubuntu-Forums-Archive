---
title: "ssh connection stalls after a short while"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by androssofer on 2011-08-20
Hi, 

I hav 2 ubuntu boxes, both 11.04. I have an ssh server and squid proxy(prob not important, but best to get all the info :-) ) on 1 of them. 

ssh runs on a non default port. lets pretend its 2222 (i like being cryptic ;-) ), i use public key authentication...

is used the commands:

```
ssh -p 2222 -L 8080:localhost:3128 -X -C username@domainname
```

and:

```
ssh -p 2222 -L 8080:localhost:3128 -C username@domainname
```

and

```
ssh -p 2222 -C username@domainname
```

and

```
ssh -p 2222 username@domainname
```

all of which stalled up on me after about 10 mins. 

i noticed it when i was forwarding my interwebz thru ssh. then it stooped. so i open up the terminal its running on. and try a few commands... nothing. so tried all the different ssh commands to c if any of the options effected it (port forwards etc) and it seems to happen regardless... any ideas?

---

### Post by dave01945 on 2011-08-20
i had a similar problem when i first started using ssh and it was the timeout setting i can't remember exactly where the config is but if you search the man pages for ssh config or sshd config it should be in there

---

### Post by androssofer on 2011-08-20
> **dave01945 said:**
> i had a similar problem when i first started using ssh and it was the timeout setting i can't remember exactly where the config is but if you search the man pages for ssh config or sshd config it should be in there

had a look into it and found this [thread]("http://forums.knownhost.com/showthread.php?t=708") on it. 

ther is a number of timeouts, 

1 is for login.. which isnt it as i'm logged in when it happens. 

another is the connection itself. which it cant be as i log in from work using a Mac and it stays fine all day... and i have TCPKeepAlive set to yes...

as Mac works ok, it could be a client issue? but as i use the same commands, i dnt get how it could be.. unless ubuntu has different defaults than Mac on its ssh clients?

---

### Post by dave01945 on 2011-08-20
not sure what to suggest i dont have access to a mac right now but it is very possible they do have different defaults as mac like's to implement things there way

---

