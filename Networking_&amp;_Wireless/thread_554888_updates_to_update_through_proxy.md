---
title: "updates to update through proxy"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by Hanskristian on 2007-09-19
Ok I have read a couple of threads on how to change your system to allow you to update through a proxy. But I guess I'm not really understanding. Can someone give me a step by step process for a complete noob.

Thank you very much.

---

### Post by bapoumba on 2007-09-19
Look at the /etc/apt/apt.conf file:
[http://linux.die.net/man/5/apt.conf]("http://linux.die.net/man/5/apt.conf")
I use a proxy at work and no proxy at home, with the same laptop ;)

Please post back if you have any questions.

---

### Post by Hanskristian on 2007-09-19
Still not sure how to access that file.

---

### Post by bapoumba on 2007-09-19
You need to create or edit the file.

Here is what I have in mine, I do not need an authentication
```
[noparse]Acquire::http::Proxy "http://Blah.blah.fr:3128";[/noparse]
```
You need to adapt to your specs.

To edit the file:
```
sudo nano /etc/apt/apt.conf
```
nano is a small text editor working from the terminal.
CTRL-O to save the file, CTRL-X to exit nano.

Once your proxy is properly declared in /etc/apt/apt.conf, updates will go through.

---

### Post by Hanskristian on 2007-09-19
I did that and I got a: Could not resolve @ (my proxy ip)
I put in the Domain under System - netowork and got a 407 access denied.

Is it possible for the 3128 port to be blocked on the ISA Server, and I somehow have to create a rule to open that port?

---

### Post by bapoumba on 2007-09-19
Do you need authentication?
Would it be an ISA proxy?

Also please post the file:
```
cat /etc/apt/apt.conf
```

---

### Post by Hanskristian on 2007-09-19
I tried auth and still no go.

cat /etc/apt/apt.conf
     
gives me my code that I just put in.

---

### Post by bapoumba on 2007-09-19
Hmm.. Do you know if this is an ISA proxy ?
Edit: sorry, I did not see your edit in a previous post. There are post on UF regarding this, I'll have a look.

---

### Post by Hanskristian on 2007-09-19
Thank you. and here is the error.

407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

P.S I hate ISA server 2004!

---

### Post by bapoumba on 2007-09-19
ntlmaps, this is what I was looking for. Hope this helps.
[http://ubuntuforums.org/showthread.php?t=183093&page=3]("http://ubuntuforums.org/showthread.php?t=183093&page=3")

---

### Post by Hanskristian on 2007-09-19
Well its more interesting now. I still get the 407 error.

I went through and did everything suggested and they do not go through. If I copy the address and put it into Firefox its then ok to download. 

I tried to /etc/init.d/ntlm restart 
and it says it does not exist.

Yet when I type in the code:ps aux | grep ntl
it tells me its up and running.

any suggestions.

2nd thought, should i then go through and turn off the proxys in network and in synaptic package manager?

Im also trying to go through port 8080 if that helps.

---

### Post by bapoumba on 2007-09-19
> **Hanskristian said:**
> 
2nd thought, should i then go through and turn off the proxys in network and in synaptic package manager?
Yes.
> **Hanskristian said:**
> 
Im also trying to go through port 8080 if that helps.
This I'm not sure, I never had to use an ISA proxy (my corporate network runs on debian stable with squid proxy).

---

### Post by Hanskristian on 2007-09-19
Well I went through and turned off the network proxy and turned off the proxy through synaptic package manager. Tried to update. and got same error. tried in command window and they didnt download either.

Not sure what else to try.

---

### Post by bapoumba on 2007-09-19
Try to log off your session and log back in.

---

### Post by Hanskristian on 2007-09-19
Thank you for all the help!

---

### Post by Hanskristian on 2007-09-19
rebooted and this is the error I get.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-amd64/Packages.gz) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by bapoumba on 2007-09-19
Hmm. It's quite late here, let me think this over. May be someone else will come by to help you out :)

---

### Post by Hanskristian on 2007-09-20
I tried everything I can think of, anyone out there have any other suggestions?

---

### Post by bapoumba on 2007-09-21
> **Hanskristian said:**
> I tried everything I can think of, anyone out there have any other suggestions?
I'm sorry, I had no time to look around. I'll do it today, and will post back if I find something.

---

### Post by bapoumba on 2007-09-21
[http://ubuntuforums.org/showpost.php?p=3340662&postcount=25]("http://ubuntuforums.org/showpost.php?p=3340662&postcount=25")
May be here ?

---

