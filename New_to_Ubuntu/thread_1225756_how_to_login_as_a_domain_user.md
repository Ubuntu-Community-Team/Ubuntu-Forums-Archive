---
title: "how to login as a domain user?"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by kevin_mon on 2009-07-28
hey guys.

i'm starting use ubuntu as my desktop.

but many things did not work out.

first. seem like ubuntu only allow local user to log in.while i want to login my account on the domain server.

then. how can i use the ISA server.
i found the ISA client connect to the server automaticly when  i log on as a domain user.no need to input everything like a account or password.but if i log on a local user.it never connect anymore.

at last.
coz many software i worked with need the windows environment. is there any software like vmworkstation in linux can make a vitrual windows machine perfectly?

BTW.
my english is not very good.
hope u know what i am talking about.

many thx to all of u.

---

### Post by llamabr on 2009-07-28
first. seem like ubuntu only allow local user to log in.while i want to login my account on the domain server.

You want to log into your ubunto machine from a remote location?  You can ssh into it, after you set up ssh server:

```
sudo apt-get install openssh-server
```

Or do you want to login to another machine, while you're sitting in front of your ubuntu box.  Easy.  just:

```
ssh -v username@remote.host
```

---

### Post by kevin_mon on 2009-07-28
thanks for your post.

but i'm sorry i think you have misunderstand my problem.
what you say is after log on and it act in a shell.right?

i need to log on to a windows domain so i can use the ISA server.
it happens before the desktop come out.
u konw? after boot when you select ur username in the list
there should be a remote user which on the domain.

in windows.you can search the user on the domain .then add it to the administrator group
then when you log on .select the log on place is the domain you have joined.
then you can use the ISA to connect the intennet.

am i say too much.
sorry.
i just want to describe it more clear.

---

### Post by llamabr on 2009-07-29
Hi.  Yes, You've described your problem clearly.  I'm sure that such a thing is possible, but I don't know windows environments well enough to help.

Could you, instead, log into your ubuntu desktop, and then log into your windows ISA Server?  This, I'm sure, is easily possible.

---

### Post by kevin_mon on 2009-07-29
Hi [llamabr.]("http://ubuntuforums.org/member.php?u=404864")
thx for your help.

all i want is connect the internet.but the truth is i must use the ISA agent
i find many place and almost tried every available buttons in system&#65288;not include command line coz i really not good at this&#65289;.
but it still work out.

may i need to install some other packet to support some protocol about ISA or windows domain &#65311;

---

