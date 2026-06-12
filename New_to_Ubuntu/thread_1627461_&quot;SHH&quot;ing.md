---
title: "&quot;SHH&quot;ing"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by Avidanborisov on 2010-11-21
Hello everyone.
I use ssh between my computers and iPod touch and I have a question that I know the answer is possible. How can I turn this: [HTML]ssh user@ip.address[/HTML] to something like this: ```
ssh iPod
```
?

---

### Post by matt_symes on 2010-11-21
Hi

Read 

[http://principialabs.com/beginning-ssh-on-ubuntu/](http://principialabs.com/beginning-ssh-on-ubuntu/)

See section: Stop Typing the Stupid IP Address All Day, Will You?

Kind regards

---

### Post by Joeb454 on 2010-11-21
Edit your /home/**user**/.ssh/config file (where **user** is your username), and add something like this:

```

Host ipod
    Hostname    192.168.1.256
    User        myUsername
    Port        22

```

That will allow you to do it without DNS resolution etc.

**Note:** you don't need to enter the port value if you are using a standard port.

---

### Post by matt_symes on 2010-11-21
Hi

and could you mark the thread as solved when and if this solves your issue. :)

Kind regards

---

### Post by Avidanborisov on 2010-11-21
> **Joeb454 said:**
> Edit your /home/**user**/.ssh/config file (where **user** is your username), and add something like this:

```

Host ipod
    Hostname    192.168.1.256
    User        myUsername
    Port        22

```

That will allow you to do it without DNS resolution etc.

**Note:** you don't need to enter the port value if you are using a standard port.

> **matt_symes said:**
> Hi

and could you mark the thread as solved when and if this solves your issue. :)

Kind regards

It is not completely solved... How can I make it remember the password?

---

### Post by CharlesA on 2010-11-21
> **Avidanborisov said:**
> It is not completely solved... How can I can I make it remember the password?
Check out ssh-agent.

---

### Post by Avidanborisov on 2010-11-21
Actually now I've noticed that I don't have the config file in the folder ".ssh" . just known_hosts file
====================================================**_EDIT_**=====================================================
It worked after I created a file named config. And, what do I do with "ssh-agent"?

---

### Post by matt_symes on 2010-11-21
Hi

Just create a new file.

Kind regards

---

