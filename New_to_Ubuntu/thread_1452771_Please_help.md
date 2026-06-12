---
title: "Please help"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by mroy1300 on 2010-04-12
I really need a little help. I am setting my own server mostly for fun and I dont understand the blank.com part of my host name or how to figure it out. when setting up the server i used the host name "server1" i know to use "ifconfig" and "route -n" but if my ip adress is 192.168.1.8 then can I set that as my static ip. im very new to the server thing but i am going to school to be a network admin so i wanted to get a jump start on things any help would be great.

---

### Post by wojox on 2010-04-12
Are you behind a router, then yes you can set that as your static ip and enable port forwarding from the router.

---

### Post by mroy1300 on 2010-04-12
What about the host name I know it would be server1.something.com I used whatsmyip.com and that told me is was my external ip.dns.mn.us.charter.com or something g like that so would my host name be server1.dns.mn.us.charter.com? For the router forwarding do I just need to tell my router that I'm setting a static ip and what it is? I have a netgear router.

---

### Post by Gone fishing on 2010-04-12
For lots of things such as squid the server will need a fully qualified domain name in hosts like:

192.168.1.8 server1.mroy.com

you can add more such as 192.168.1.8 server1.mroy.com serve1

---

### Post by e4uforums on 2010-04-12
What kind of server is this?  What is your endgame?  Depending on what you're trying to accomplish we'll have some different (more specific) advice for you.

What kind of server are you trying to setup?
Who will be accessing your server?
Will you need to access your server when you are not on your local LAN (for example should your server be visible to the rest of the world, or just you at home?)?
What software are you using to setup your server?

---

### Post by mroy1300 on 2010-04-12
ok so how would i go about making it that 192.168.1.8 server1.mroy.com or whatever. I installed ubuntu server 9.10 and so far I can SSH with it but for the rest of the setup i need the host name ip address and gateway. and the only thing im missing is my host name I know the way its set up it needs to be like server1.example.com

---

### Post by mroy1300 on 2010-04-12
I want a home server and basicly i want to have a external HDD on the server where i will put all my files. 

I am using ubuntu server 9.10. 

I will be accessing the server right now but possibly other family members etc. in the future.

I want to be able to access my server no matter where I am or what computer I am on. However I would like to stay away from paying for a domain name or something like that.

Maybe this will help

---

### Post by wojox on 2010-04-12
What does this tell us:

```
cat /etc/hosts
```

```
cat /etc/hostname
```

---

### Post by e4uforums on 2010-04-12
Ok, so you want a home file server that you can access from anywhere to access your files.

There are a couple of ways to do this.  This can be done through FTP or HTTP.

For FTP use something like FileZilla - there are plenty of tutorials on setting up a FileZilla FTP server.

For HTTP, use Apache, there are plenty of tutorials for setting up Apache to serve files.

Configuration for both:

Sign up for a dynamic dns service.  I use [http://www.dyndns.com/](http://www.dyndns.com/) but there are many out there.  They will give you a generic domain name (like yourname.homeip.net or something) and a client that will update your domain name with your ip address from your ISP.  Most of these services are free of charge for the basic DNS service (which is all you need).

Now you have to configure your router.  For FTP forward port 21, for HTTP forward port 80.  You'll need to access your home router and configure it to forward the port needed to your computer.  There are many tutorials on this as well, a good place to start is [portforward.com.]("http://www.portforward.com")  They have tutorials for many different brands of routers.

Let me know if you have other questions.

---

### Post by mroy1300 on 2010-04-12
I am looking at DynDNS.com and when it does the ip address part i have a question I am on my workstation and the server has no GUI or as far as i know internet application so it tries to use the ip of my workstation. also it uses external ip address so how do I figure the ip of my server. all i know is ifconfig maybe im missing something

---

### Post by e4uforums on 2010-04-12
If your workstation and your server are both behind the same router, then your external IP address will be the same.

If this is the case, then go to [www.whatismyip.com]("http://www.whatismyip.com") and use the ip address on that page.

---

### Post by halitech on 2010-04-12
if you are behind a router, then DynDNS.com will use the external IP to direct traffic to your external IP address (the router). You will also need to tell the router that traffic directed to your external IP is to be forwarded to the servers internal IP address (ie. 192.168.x.x) Normally if you do 
```
sudo ifconfig
```
it should give you the internal IP address of the server. that will be the IP you will tell the router to forward requests to.

---

### Post by mroy1300 on 2010-04-12
It may do better help if you knew more what i am doing i am following this guide [http://www.howtoforge.com/perfect-server-ubuntu-9.10-karmic-koala-ispconfig-2-p3](http://www.howtoforge.com/perfect-server-ubuntu-9.10-karmic-koala-ispconfig-2-p3) and i am stuck at 
**7 Configure The Network**

could someone please clearify how would i know the server1.example.com part or would i use the information from dyndns.com to do this.

---

### Post by e4uforums on 2010-04-12
I believe you would use the domain name you got from DynDNS.

---

### Post by mroy1300 on 2010-04-12
my last question would be what ports should i open for this setup?

---

### Post by e4uforums on 2010-04-12
Ok, I read through the first page of the tutorial also, and again, it will depend on which service you're going to use to serve up the files.  It will most likely be either 21,22,80 or 443.  Start with 21, if that doesn't work, try 22 and so on.  Little bit of trial and error should get you there.

---

