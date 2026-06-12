---
title: "Proxy bypass"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by mthalis on 2008-02-12
I want to know about Proxy bypass tool which can use in UBUNTU 7.10

---

### Post by wieman01 on 2008-02-12
What sort of bypass are we talking about? For Synaptic or Firefox? Possibly FTP?

---

### Post by mthalis on 2008-02-12
Synaptic and  FTP. I want to bypass these two specially FTP

---

### Post by wieman01 on 2008-02-12
Easy one... Open a terminal and type:
```
sudo export http_proxy=http://user:password@hostname:port
sudo export ftp_proxy=ftp://user:password@hostname:port
```
Then do:
> sudo apt-get update
**Alternatively edit:**
> sudo gedit /etc/apt/apt.conf 
And add:
```
Acquire::http::Proxy "http://username:password@proxy:port";
Acquire::ftp::Proxy "ftp://username:password@proxy:port";
```
> sudo apt-get update
Does that help?

---

### Post by mthalis on 2008-02-12
I don't have good knowledge about this field if you can clarify it's very useful for me.

http_proxy=http://user:password@hostname:port
In here what is mean about : 
http_proxy
user
password
hostname 
port

---

### Post by wieman01 on 2008-02-12
Ah, OK. 

You certainly have a username & a password for Internet connection that let's you bypass the proxy. If not, you need to contact your network admin.

The hostname is the IP address of your proxy, port is its port number. Again, your network admin can advise here. 

Leave 'http_proxy' unchanged, the simply replace 'user', 'password', 'hostname', and 'port' with the stuff your network admin advises you.

---

### Post by mthalis on 2008-02-12
without knowing user name & a password can't we do this i want that sort of answer.

---

### Post by wieman01 on 2008-02-12
> **mthalis said:**
> without knowing user name & a password can't we do this i want that sort of answer.
Without knowing user name & a password, you cannot do this. It's the same user name & password that you use when you open an Internet browser in order to browse the web. If you don't have them, you have no chance connecting.

---

### Post by mthalis on 2008-02-12
Imagine I use cafe then what happen

---

### Post by wieman01 on 2008-02-12
> **mthalis said:**
> Imagine I use cafe then what happen
The cafe does provide you with a user name and a password I imagine, correct? Otherwise you could not user their internet. That's usually the type of credentials that you use to bypass the proxy.

Anyway, if you don't have them, it's a no-go.

---

### Post by mthalis on 2008-02-12
Are there any software?

---

### Post by wieman01 on 2008-02-12
> **mthalis said:**
> Are there any software?
I am not quite following... What type of software? To bypass the proxy? 

Anything you do to bypass it without the owner's explicit permission, is illegal. So a user name & a password are a must, otherwise you are in trouble and we won't support that type of action. Just to make it very clear.

---

