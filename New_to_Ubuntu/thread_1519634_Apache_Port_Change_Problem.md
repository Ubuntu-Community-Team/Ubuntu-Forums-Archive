---
title: "Apache Port Change Problem"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by astrosmokewf on 2010-06-28
Well I have installed Apache/PHP 5 on this box for general web use and I must admit, it's also to learn.  Basically I wanted to setup a server for me and one other person to use, but I keep having this problem.
When I change the port in apache, through
```
sudo gedit /etc/apache2/ports.conf
```
and change the listening port, I open the port through my router, and restart apache.   It does not work.

Could someone help me out?
Am I doing something horribly wrong?

---

### Post by cariboo on 2010-06-28
When you change the port, you also have to tell your browser to use that port, for example if you changed the port to 8080, you would access it by typing in your browser:

```
http://example.com:8080
```

If you just want to check to see if the port is open to the world, use [canyouseeme]("http://www.canyouseeme.org/").

---

### Post by astrosmokewf on 2010-06-28
Oh, so I can't change the port for security measures without using :XXXX on the end of my address?

---

### Post by bodhi.zazen on 2010-06-28
> **astrosmokewf said:**
> Oh, so I can't change the port for security measures without using :XXXX on the end of my address?

Nope, that is the downside of changing the port, you would need to specify the port in your url.

Changing the port, IMO, does not increase apache security. Apache is intended to be public.

---

### Post by astrosmokewf on 2010-06-28
so, what form of security would you advise?

---

### Post by bodhi.zazen on 2010-06-29
> **astrosmokewf said:**
> so, what form of security would you advise?

That is an extremely broad question. What are you serving with Apache ? To who ? What kind of connections do you wish to allow ? Which connections do you want to deny ?

Apache itself is fairly secure, it is the modules and extensions you have to watch. Do you use perl ? PHP ? Java ? 

What application are you running ? Wordpress ? 

Are you running mysql as well ??

You get the idea ....

[http://www.google.com/search?q=how+to+secure+apache&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=how+to+secure+apache&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

