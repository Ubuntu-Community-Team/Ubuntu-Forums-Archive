---
title: "remote bash shell"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by mamut0o1 on 2009-06-03
Good afternoon everyone; I have a question regarding remote administration. I have a ubuntu server at home; I'm able to ftp to it but if i need to change/modify or copy a file to my server folder I get an erorr; denied; I think is because folder permission was set that way. My question is how can I gain remote shell control so I could chmod that folder?
is this recommended?

thanks for your help
Mamut

---

### Post by hovzio on 2009-06-03
Is there an ssh-server on the machine your trying to log in to. If so then yes, if you are a owner or have proper privledes for the files. Telnet could but shouldn't be an alternative. I believe this cannot be done with ftp

---

### Post by Celauran on 2009-06-03
You really want to get an SSH server setup on the remote machine.

---

### Post by mamut0o1 on 2009-06-03
> **hovzio said:**
> Is there an ssh-server on the machine your trying to log in to. If so then yes, if you are a owner or have proper privledes for the files. Telnet could be an alternative. I believe this cannot be done with ftp

Yes; I'm the owner; I tried opening port 23 yesterday to telnet in and I didnt get through. Is this because I need to install ssh-server? or because I need to open port 23 on the ubuntu firewall? thanks for your help again!

mamut

---

### Post by Celauran on 2009-06-03
I don't recommend using telnet. SSH is far more secure. You'll need to install ssh-server and then tinker with the configuration a bit. I'd change the port from 22 to something non-standard, disable Protocol 1, and only allow key authentication.

[This](https://help.ubuntu.com/community/SSH?action=show) should get you started.

---

### Post by mamut0o1 on 2009-06-03
> **Celauran said:**
> You really want to get an SSH server setup on the remote machine.

Thank you both for your help. Ok I need to setup a shh server plus use like "putty" to connect via ssh?
Can you point me in the right direction on how to install the ssh server for ubuntu?

Thanks again!
Mamut

---

### Post by hovzio on 2009-06-03
> **mamut0o1 said:**
> Yes; I'm the owner; I tried opening port 23 yesterday to telnet in and I didnt get through. Is this because I need to install ssh-server? or because I need to open port 23 on the ubuntu firewall? thanks for your help again!

mamut

telnet and shh are two different things. Is your server running telnet? :\
You have to know what type of service/server is running and at which port to properly connect.(there also has to be a server *listening) If you are running telnet it may be a routing issue. can you describe the setup.(router, nat etc.) if i may, if you are indeed running telnet I would definatly consider looking into ssh. Its a "secure shell" that encryts data.

to install the ssh-server digit this at a prompt:

sudo apt-get install openssh-server

Make sure you google "denyhosts" and properly set up sshd.config. No root logins and so forth. Denyhosts will help ward off kiddies and co.

---

### Post by Celauran on 2009-06-03
> **mamut0o1 said:**
> Ok I need to setup a shh server plus use like "putty" to connect via ssh?
Once you've got the server set up, just use ssh from the command line.
```
ssh user@host
```

---

### Post by mamut0o1 on 2009-06-03
Hovzio; how can I check which services are running and how to prevent telnet to run..i dont want anything unencrypted for sure. is it hard to configure ssh? 

thanks again man.
mamut

---

### Post by MrWES on 2009-06-03
> **mamut0o1 said:**
> Thank you both for your help. Ok I need to setup a shh server plus use like "putty" to connect via ssh?
Can you point me in the right direction on how to install the ssh server for ubuntu?

Thanks again!
Mamut

Try this link:

[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html]("https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html")

~Bill

---

### Post by Celauran on 2009-06-03
> **mamut0o1 said:**
> how can I check which services are running
```
ps aux | less
```

---

### Post by hovzio on 2009-06-03
> **mamut0o1 said:**
> Hovzio; how can I check which services are running and how to prevent telnet to run..i dont want anything unencrypted for sure. is it hard to configure ssh? 

thanks again man.
mamut

In a default ubuntu installation there are NO running services. So if you didn't install a telnet server there is none, nevertheless to check if telnet server is installed.

```
apt-cache policy telnetd
```

Check out nmap for checking services, it is oh so reliable. The command in the above post, < ps aux | less > will give a list of many current processes but not only services. You could use:

ps aux | grep 'telnetd'

or somthing similar to filter out what your looking for.

---

### Post by pawnrocket on 2009-06-03
If you just want to check services goto System -> Administration -> Services

You can also look for them by opening a Terminal Window and entering

```
top
```

That will give you real-time data about your processes. 

And yes ssh is the way to go.

---

### Post by mamut0o1 on 2009-06-03
Thank you all; 
I will install the ssh-server tonight and try it out.

have a good day!
Mamut

---

