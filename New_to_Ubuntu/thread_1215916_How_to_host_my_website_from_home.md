---
title: "How to host my website from home?"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-07-17
I am using ubuntu 9.04 and i recently read somewhere that we can host our own website from our system.I dont own any website but i am intrested in knowing how it is done.Sorry but i dont know any html  or php or such things but would use microsoft frontpage in wine to create a html file easily and i also dont like to work in command line,Can some one teach me how to host a website for a guy like me :D:D:D. 
Please help me learn this one.i am really intrested in it.

---

### Post by cariboo on 2009-07-17
You can install the LAMP stack by going to System-->Administratiom-->Synaptic Package Manager-->Edit-->Mark Packages by Task.

The LAMP stack consists of:

[list]
[*] Linux
[*] Apache2 - the web server
[*] Mysql - a data base
[*] [Php5]("http://en.wikipedia.org/wiki/PHP")
[/list]

Once you have installed the LAMP stack point your web browser to:

[http://localhost](http://localhost)

You should see a page that says It Works!.

---

### Post by t4thfavor on 2009-07-17
Then you will need to make all of your pages with something like frontpage (I cannot remember the linux alt, nvu maybe) copy all the files to your apache root, and see how it looks in your fav browser..

I'm not sure frontpage files will look right when hosted on an Apache server, so it may be just some trial and error. 


After you get it all set up on your machine, and looking corret, We will work on hosting it to the world...

Any more questions? I will be glad to answer.

---

### Post by ravi_buz on 2009-07-17
> **cariboo907 said:**
> You can install the LAMP stack by going to System-->Administratiom-->Synaptic Package Manager-->Edit-->Mark Packages by Task.

The LAMP stack consists of:

[list]
[*] Linux
[*] Apache2 - the web server
[*] Mysql - a data base
[*] [Php5]("http://en.wikipedia.org/wiki/PHP")
[/list]

Once you have installed the LAMP stack point your web browser to:

[http://localhost](http://localhost)

You should see a page that says It Works!.
But i read some where and install apache2 and now it self i can see it works! so what is the difference with installing other packages

---

### Post by ravi_buz on 2009-07-17
> **t4thfavor said:**
> Then you will need to make all of your pages with something like frontpage (I cannot remember the linux alt, nvu maybe) copy all the files to your apache root, and see how it looks in your fav browser..

I'm not sure frontpage files will look right when hosted on an Apache server, so it may be just some trial and error. 


After you get it all set up on your machine, and looking corret, We will work on hosting it to the world...

Any more questions? I will be glad to answer.
thanks , can you tell me where the apache folder where i have to paste the html file and one more thing i see my website in localhost but how can i make others see it.

---

### Post by t4thfavor on 2009-07-17
A LAMP stack is for applications in PHP (recommended if you actually want to do stuff other than show content), these offer much more than HTML. The default html dir is /var/www for apache2. Paste in a regulat html file and call it index.html Note you will need elevated privelages to write to the www diretory.

---

### Post by ravi_buz on 2009-07-17
i just saved a web page as index.html and replaced the old one , but still i see only IT WORKS!

---

### Post by t4thfavor on 2009-07-17
You may need to restart the apache service.

sudo gives you the privelage to restart a service, and the rest is done by init.
```

sudo /etc/init.d/apache restart

```

---

### Post by DanYoSon on 2009-07-17
> **ravi_buz said:**
> i just saved a web page as index.html and replaced the old one , but still i see only IT WORKS!
try deleting the cache/history in the web browser

---

### Post by t4thfavor on 2009-07-17
Or pressing SHFT+F5 instead of just the refresh.

---

### Post by ravi_buz on 2009-07-17
> **t4thfavor said:**
> You may need to restart the apache service.

sudo gives you the privelage to restart a service, and the rest is done by init.
```

sudo /etc/init.d/apache restart

```
ravi@ravi-desktop:~$ sudo /etc/init.d/apache restart
sudo: /etc/init.d/apache: command not found
ravi@ravi-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ] It worked 
Now how to make others see my web pages since i can only see it in local host,

---

### Post by MontelEdwards on 2009-07-17
NOOOOOOOOOOOO
Dont use Apache
its sucks dude compared to Lighttpd
oh, 
and if you're using SQL install PHPMyAdmin

---

### Post by ravi_buz on 2009-07-17
> **MontelEdwards said:**
> NOOOOOOOOOOOO
Dont use Apache
its sucks dude compared to Lighttpd
oh, 
and if you're using SQL install PHPMyAdmin
Can you tell me whether they need any html/php etc knowledge because i dont know any thing about those ,that's why its difficult for me to use high level softwares

---

### Post by aysiu on 2009-07-17
If you want to host it for only local computers on your network to see, that's probably fine.

If you want it to be hosted for the outside world to access, you may want to double-check your ISP's terms of service to make sure that hosting a server through their connection doesn't violate your contract.

---

### Post by DanYoSon on 2009-07-17
> Now how to make others see my web pages since i can only see it in local host,this is where it can get complicated. first you need to register a domain name. then figure out if you have a static ip address. if you dont then you have to use another site like [www.dyndns.com]("http://www.dyndns.com/") to forward the requests to your ever changing ip. also you will probaly have to set up port forwarding within your internal network. you also have to think about security. you dont want someone to get into your personal files and possibly change your site to something you dont want.

my opinion you should learn some html at least and spend some time on google learning about web sites and how they work. also i would recommend haveing a dedicated computer for the server that will not be turning on and off very often.

this is a good site for learning html/php etc. [www.w3schools.com  ]("http://www.w3schools.com")

also research the diffrent servers and decide which one is best for you.

---

### Post by ravi_buz on 2009-07-17
no problem with my isp and i have a static ip too what what next .:confused:

---

### Post by Viva on 2009-07-17
I don't recommend hosting a website on your desktop unless it is for testing purposes. There are so many free/Cheap web hosts available these days that it is not worth hosting it on your computer. Not to mention the obvious security concerns of hosting a website on a desktop without any professional help.

---

### Post by MontelEdwards on 2009-07-17
There is nothing wrong with it.
I host my blog
[http://monteledwards.com]("http://monteledwards.com/") and it runs great.
There is no reason that you cannot host it on your desktop


OP: No, you do not need to know any HTML
I would guess that you are going to  be installing some kinda blog program
I would reccomend wordpress

---

### Post by DanYoSon on 2009-07-17
> **ravi_buz said:**
> no problem with my isp and i have a static ip too what what next .:confused:

start by reading [this]("http://www.boutell.com/newfaq/creating/hostmyown.html") it will give you a good idea of how the whole process works (even though it is written more for windows)

---

### Post by ravi_buz on 2009-07-17
yes as i said in the first post i am just very much intrested in it , and thats why trying to learn it but have no idea of hosting my blog/site now but this might come in handy one day

---

### Post by ravi_buz on 2009-07-17
> **DanYoSon said:**
> start by reading [this]("http://www.boutell.com/newfaq/creating/hostmyown.html") it will give you a good idea of how the whole process works (even though it is written more for windows)
yes i was inspired about that after reading that too but that was too complicated for me but made me understand the needs for doing this and risks involved

---

### Post by ravi_buz on 2009-07-17
> **MontelEdwards said:**
> There is nothing wrong with it.
I host my blog
[http://monteledwards.com]("http://monteledwards.com/") and it runs great.
There is no reason that you cannot host it on your desktop


OP: No, you do not need to know any HTML
I would guess that you are going to  be installing some kinda blog program
I would reccomend wordpress
nice webpage , so you keep your system running all day!!!

---

### Post by NullHead on 2009-07-17
> **ravi_buz said:**
> thanks , can you tell me where the apache folder where i have to paste the html file and one more thing i see my website in localhost but how can i make others see it.

If you want others on the web to be able to see your website, you'll need to open port 80 on your router first. 

You'll also need to know your external IP address. [http://whatismyip.net](http://whatismyip.net) will tell you what your IP is. 

I also recommend signing up for a free domain at [http://dyndns.com](http://dyndns.com)

---

### Post by ravi_buz on 2009-07-17
> **MontelEdwards said:**
> NOOOOOOOOOOOO
Dont use Apache
its sucks dude compared to Lighttpd
oh, 
and if you're using SQL install PHPMyAdmin
I cant find those in synaptic ?? where to get it

---

### Post by SunnyRabbiera on 2009-07-17
You may want to hold out to get a secondary computer, setting up a website from home is easy but to make sure you dont have outages or anything a secondary computer is a good idea.

---

