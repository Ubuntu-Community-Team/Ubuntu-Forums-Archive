---
title: "Cannot ssh anything but localhost"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by steve228 on 2010-03-16
I have two different places that i want to ssh into 

The first is my school's "Orca" account which is 'username'@orca.st.usm.edu

When i type
```
ssh 'username'@orca.st.usm.edu 22
```

all I get is an error
> ssh: connect to host orca.st.usm.edu port 22: Connection refused


A while back, when I first installed ubuntu, I could use ssh with no problems.  Now all I get is the connection refused error.  I know that I am typing everything in right because when I first started using ssh to login to Orca, I wrote a bash alias so i wouldn't have to type the whole thing.  My bash_aliases file hasn't changed and nothing has changed on the Orca server.


I am also trying to ssh into my website and i have tried every way i can think of, but I get the same Connection refused error.

Has anyone else had this problem?  How can I get it to accept my connection?...  I know my ssh is working properly because I can ssh localhost and it runs fine.

[B]
ALSO, FileZilla won't let met FTP into my Orca or website account.  I know that these configurations are correct also, because I had the Orca account on my quick connect history bar[/B]

---

### Post by n0dix on 2010-03-16
Write the port is unnecessary, the default port for the Protocol SSH is 22. 
Maybe a firewall or a bad configuration can't allow you to connect. Contact with the Admin of the Orca system.

---

### Post by 2hot6ft2 on 2010-03-16
> **steve228 said:**
> 
The first is my school's "Orca" account which is 'username'@orca.st.usm.edu

When i type
```
ssh 'username'@orca.st.usm.edu 22
```

all I get is an error

The format for ssh command is like this
```
ssh -p 22 'username'@orca.st.usm.edu
```
The port is declared before the server with the -p switch.

As for why the server is denying the connection I don't know something's not right with your credentials apparently. It may just be that you put the 22 after the command and it doesn't understand it.

---

### Post by steve228 on 2010-03-16
Well my bash alias has it without specifying the port so it was

```
ssh username@orca.st.usm.edu
```

It suddenly wouldn't work anymore.

However, I found out a way to get around it.

I just did
```
ping orca.st.usm.edu
```

So it gave me the actual IP address and then i used
```
ssh -l 'username' IPaddress
```

And it worked like a charm.  I did the same thing for the website and now have them both working.  

Thank you for the replies!

---

### Post by n0dix on 2010-03-16
You can also connect using:
```
ssh 'username'@IPaddress
```
Don't forget to add Solved to the title ;).

---

### Post by steve228 on 2010-03-17
Ok new (but really the same) problem.  I left to go to work and when I  restart my computer, now I cannot connect using any method.

So now here is my bash alias entry

```
alias ssh-orca='ssh -l "username" 131.95.35.200'
```
where "username" is my actual username without any quotes

And the error code
> ssh: connect to host 131.95.35.200 port 22: Connection refused

I have tried every method I can think of.  I keep getting the same error code through both of my accounts.  

I know that my orca ssh alias is correct because when I first started using ubuntu it worked.

**The only thing that has changed is the programs I have installed... So is there maybe a server cache or some kind of cleaning I can do to start fresh?**

I can still do the ssh localhost and it work.

What could be wrong?

---

### Post by steve228 on 2010-03-21
**Figured it out!**

I have blockcontrol installed and it was preventing my attempts.

Thank you to all the responses.

---

