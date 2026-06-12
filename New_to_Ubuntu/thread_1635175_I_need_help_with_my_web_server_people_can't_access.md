---
title: "I need help with my web server: people can't access it from outside"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by atrix on 2010-12-01
Hello,

I know it has been asked quite a few times but none of the were the solution of my problem.

I just installed apache,mysql and php on my computer. everything works fine with localhost. I also registered a domain at dot.tk. When I enter it to my address bar it says the following:

**Forbidden**

 You don't have permission to access / on this server.
  Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_ssl/2.2.9 OpenSSL/0.9.8g Server at ethillion.tk Port 80 

I tried to set up something in my firewall but no success.

Could someone help me? Please?
I can provide more information

Thank you
atrix 

PS: please know that I may be a good programmator but I really suck at setting up things. so you're dealing with quite a n00b.

---

### Post by alienprdkt on 2010-12-01
seems to be a permission issue, try chmod 755 /your webroot

[http://en.wikipedia.org/wiki/Chmod]("http://en.wikipedia.org/wiki/Chmod")

---

### Post by pricetech on 2010-12-01
Probably need to have a friend do the external IP test, or use a proxy.

---

### Post by atrix on 2010-12-02
thank you alienprdkt for your reply but it didn't work :(
I also have my webroot at a folder in my Desktop not in the var/www folder. could this be the problem?

I also forgot to metion that 2-3 computers are using our router at the same time.

And I don't know what is a "proxy". (please don't laugh - I'm not even 14)

---

### Post by phillips321 on 2010-12-02
atrix,

Everyone was a beginner once, if at your age you're trying to set up a web server then you are miles ahead of anyone else your age that i know, well done!

We need to identify where the failure is first.

First lets ensure everything required is installed:
```
sudo apt-get install tasksel
sudo tasksel
```
and select **LAMP server**

Once this is done try this:
Do you get anything when you goto [http://120.0.0.1](http://120.0.0.1)
This should identify that the web server is running or not.

If you get somethign but not your website then it's likely that your website is not in /var/www , move it there.

Also the first page needs to be index.html as this is what is called by apache for / requests.

Once we have done this we will then move on to getting the website accessible from the outside world.

I'm following this post so let us know when you've done the above.

Matt (aka phillips321)

---

### Post by sandyd on 2010-12-02
I *think* I know where you made the mistake.

When you changed it to serve to the folder, did you add any virtualhosts?

it might be that localhost is pointing to your folder, but anything other than localhost is pointing to who knows where.

Run
```

sudo ifconfig | grep "inet addr"

```
That should give you your local IP address.

Can you access the site from there? (not the 127.0.0.1 address, the other one)

---

### Post by atrix on 2010-12-02
I did istall tasksel as phillips321 said. I selected LAMP server (it had a * before it) and hit enter. nothing happended. then i oppened my web browser and typed [http://120.0.0.1/](http://120.0.0.1/)
firefox said:
**The connection has timed out**

The server at 120.0.0.1 is taking too long to respond.

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.
    *   If you are unable to load any pages, check your computer's network
          connection.
    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

I also put a copy of my website into var/www and renamed index.php to index.html
no difference.

I tried
sudo ifconfig | grep "inet addr" i got:
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet addr:127.0.0.1  Mask:255.0.0.0
and the interesting part is that according to this site ([http://whatismyipaddress.com/](http://whatismyipaddress.com/)) my IP adress is 81.0.253.29

the website works very good with 192.168.1.101 (as same as with localhost)

oh and in the past i modified (according to other tutorials) the 
[B]/etc/apache2/apache2.conf
[/B][B]/etc/apache2/sites-enadled
and
[/B]**/etc/apache2/sites-available**
files/folders[B]

thank you
[/B]

---

### Post by phillips321 on 2010-12-03
ahhh my bad, i made a typo! whoops

local host on every machine is always 127.0.0.1

so from any machine to ping itself you can either use it's ip address or 127.0.0.1 (known as it's loopback address).

try [http://12](http://12)**7**.0.0.1

Right, just read the rest of your post. It seems that you can reach the website using [http://192.168.1.101](http://192.168.1.101)

Can you get to the website from another machine on the same network?

If yes then it's not a software firewall issue but instead a gateway firewall issue, this will mean you will need to set up port forwarding on your router to get around the NAT that the router provides.

---

### Post by atrix on 2010-12-03
I tried to get to my game from my brothers notebook and it worked.
I have one question:
how can I get around the NAT that the router provides?

thank you

---

### Post by Verbeck on 2010-12-03
on most home routers/adsl modems, there would be an option for NAT rule entry/portforward on their config page
go to [http://portforward.com/](http://portforward.com/) to see the instructions on how to forward the port 80 on your router

remember to skip any advertisements for programs and stuff

---

### Post by phillips321 on 2010-12-03
Right it's likely that the routers ip address is [192.168.1.1]("http://192.l168.1.1")

browse to that and look for something along the lines of port forwarding, virtual server, or something similar. 

Basically we want to tell the gateway that any connections on port 80 coming to it from the internet need to be forwarded to the internal device on IP 192.168.1.101

Port 80 is the port for HTTP connections.

If you cant find the setting under the router then let me know what type of router you have and i'll try to find it for you.

---

### Post by atrix on 2010-12-03
thank you verbeck, but that site doesn't have our router. our router is wrt 311. I guess it's because I  live in the Czech Republic. Oh and that was a tutorial for windows. are the steps on ubuntu the same?

---

### Post by Verbeck on 2010-12-03
> **atrix said:**
> thank you verbeck, but that site doesn't have our router. our router is wrt 311. I guess it's because I  live in the Czech Republic. Oh and that was a tutorial for windows. are the steps on ubuntu the same?
the router config page is accessed through the web browser, it doesn't matter what operating system you use

---

### Post by wojox on 2010-12-03
Open a Web Browser and enter [http://192.168.0.1/](http://192.168.0.1/)

---

### Post by phillips321 on 2010-12-03
link is already in post #11

(and you're sending him to the wrong class C!!!)

---

### Post by atrix on 2010-12-03
when i type 192.168.1.1 and hit enter, my browser wants a username and password. I don't know it. Do I need to contact the company that provides us internet connection

thank you

---

### Post by phillips321 on 2010-12-03
Try admin/password
admin/admin
admin/
admin/Password
admin/Password!
etc.....

The username and password might even be written on the underneath...

---

### Post by Verbeck on 2010-12-03
> **atrix said:**
> when i type 192.168.1.1 and hit enter, my browser wants a username and password. I don't know it. Do I need to contact the company that provides us internet connection

thank youdepends on the router. if its not written underneath, try calling the people who provided it.
(or google could be of help)

---

