---
title: "Mysql"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by Frank_F on 2009-04-08
Hello

Looking to download the server and client piece together and recommendations on the command line syntax to get the latest MYSQL and associated Client ?


Thanks

---

### Post by Bobbino on 2009-04-08
full instructions on installing mysql are here. It's a pretty easy install tbh, with no config needed after the fact.

---

### Post by cariboo on 2009-04-08
If you are not running the server version, which comes without a gui, why not just use Synaptic Package Manager to install Mysql. Go to System-->Administration-->Synaptic Package Manager and type mysql in the search box. 
If your are running without a gui at the prompt you would type:

```
sudo apt-get install mysql-server-5.0 mysql-client-5.0
```

Jim

---

### Post by Temposs on 2009-04-08
They're in the repositories:

```
sudo apt-get install mysql-client
```

```
sudo apt-get install mysql-server
```

---

### Post by ibuclaw on 2009-04-08
> **Frank_F said:**
> Hello

Looking to download the server and client piece together and recommendations on the command line syntax to get the latest MYSQL and associated Client ?


Thanks
It is one thing to install MYSQL, but setting it up is the tricky bit.
What do you intend to use it for?

Regards
Iain

---

### Post by Frank_F on 2009-04-08
thanks guys that a lot of help, I intend to use it as an analytical database which I will then glue a BI product too

---

### Post by alphacrucis2 on 2009-04-08
> **Frank_F said:**
> thanks guys that a lot of help, I intend to use it as an analytical database which I will then glue a BI product too

You might also want to install the Mysql gui tools. Includes MySQL administrator and the MySQl query browser.

---

