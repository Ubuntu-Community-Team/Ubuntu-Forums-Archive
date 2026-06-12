---
title: "I can't find /etc/init.d/squid"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by MindController on 2010-11-06
If I start the squid like
```

sudo /etc/init.d/squid start

```
i've got the error "command not found".I can't stop either. When I stop it say Squid is already running! Process ID ID's number. How can i solve the problem. 

Thanks

---

### Post by bioterror on 2010-11-06
> **MindController said:**
> If I start the squid like
```

sudo /etc/init.d/squid start

```
i've got the error "command not found".I can't stop either. When I stop it say Squid is already running! Process ID ID's number. How can i solve the problem. 

Thanks

Does this work

```
sudo service squid stop
```

Using service is the new ubuntu (maybe many others) way to handle daemons.

---

### Post by MindController on 2010-11-06
It doesn't work. I've got the error: 
> 
stop: Unknown instance:

But my squid server is still running. Thanks for helping brother.

---

### Post by sikander3786 on 2010-11-06
> **MindController said:**
> It doesn't work. I've got the error: 

But my squid server is still running. Thanks for helping brother.
It is giving unknown instance because I think it is not running.

Try

```
sudo service squid start
```

or

```
sudo service squid status
```

to see if it is running or not.

---

### Post by MindController on 2010-11-06
When I tried
```
sudo service squid start
```
The error message is start: Job failed to start

When I tried
```
sudo service squid status
```
The message said squid stop/waiting

But my clients can surf the internet via squid. That's why I said my squid server is still running.:(
Pls

---

### Post by sikander3786 on 2010-11-06
> But my clients can surf the internet via squid. That's why I said my squid server is still running.

How is that possible? Are you sure there is no other proxy server on the network that they are browsing from? Or they don't have direct access to internet?

You can check squid access.logs to see if any of them actually connected to your proxy server.

Which version of lubuntu are you using?

What is the output of

```
sudo /etc/init.d/squid status
```

---

### Post by karthick87 on 2010-11-06
What is the version of squid you use..?

---

### Post by sikander3786 on 2010-11-06
> **getyourkarthick said:**
> What is the version of squid you use..?
Yeh it might be squid3. I forgot that one. :-)

---

### Post by MindController on 2010-11-06
My ubuntu version is 10.10 server version. My squid version is 2.7 stable version. Sorry for the output 
```

sudo service squid status

```
coz my squid server is down for some cases. Thanks for all.

---

### Post by karthick87 on 2010-11-06
> **sikander3786 said:**
> Yeh it might be squid3. I forgot that one. :-)


If you are using squid3 you should use the following

To see your squid cache version:
```
squid3 -v
```

To restart:
```
sudo /etc/init.d/squid3 restart
```To Stop:
```
sudo /etc/init.d/squid3 stop
```To Start
```
sudo /etc/init.d/squid3 start
```

---

### Post by macclepg on 2011-03-01
I too have this same problem. no squid file at all in /init.d

---

### Post by qstraza on 2011-03-23
> **macclepg said:**
> I too have this same problem. no squid file at all in /init.d

Same here. "Statusing" via service also does not work.

---

