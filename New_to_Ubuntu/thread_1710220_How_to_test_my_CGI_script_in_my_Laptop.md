---
title: "How to test my CGI script in my Laptop"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by romy.mathew on 2011-03-19
I was tring to learn the perl CGI scrippting, I did a research and found I need to have a server to have before testing CGI, I installed APACHE2 on my machine but i am not able to test any script so far, 

My question is 

1. How to set up the apache2 for cgi scripting..?

2. Do I need to own a website to learn CGI scripting...?

when I tested apache2 I got the following result

[COLOR="Red"]romy@romy-laptop:/usr/lib$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 3556) already running[/COLOR]

---

### Post by cariboo on 2011-03-19
Apache2 auto starts on boot. To check if it is working point your browser to [http://localhost](http://localhost).

As far as your other questions go, the only place I've ever seen cgi scripting used is for web pages, depending on what it is you want to do, a web page of some sort would be useful.

---

### Post by vivek.pandey on 2011-03-19
k friend here is what you need
your cgi script
any server ,i use apache server.
save your script in /usr/lib/cgi-bin
chnge the permission of the file . eg if my file is hello.pl
then
sudo chmod +x /usr/lib/cgi-bin/hello.pl
go on your browser type localhost/cgi-bin/filename

bingo here yu go :-)

---

### Post by vivek.pandey on 2011-03-19
> **romy.mathew said:**
> 
My question is 

1. How to set up the apache2 for cgi scripting..?

2. Do I need to own a website to learn CGI scripting...?

when I tested apache2 I got the following result

[COLOR="Red"]romy@romy-laptop:/usr/lib$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 3556) already running[/COLOR]

i guess instead of 127.0.0.1 you have set your server on 127.0.1.1 so check the configuration file and set it back to either localhost or the ip address i gave 

secondly you DONT NEED TO OWN A WEBSITE. all you need is server text editor and obviously codes

thirdly apache2 is already configured for cgi..if you have any problem feel free to ask again

good luck.hope this helped :-)

---

### Post by romy.mathew on 2011-03-20
> **neo_aryan said:**
> k friend here is what you need
your cgi script
any server ,i use apache server.
save your script in /usr/lib/cgi-bin
chnge the permission of the file . eg if my file is hello.pl
then
sudo chmod +x /usr/lib/cgi-bin/hello.pl
go on your browser type localhost/cgi-bin/filename

bingo here yu go :-)
Thanks neo_aryan,

That worked ....now i can watch the cgi script output in my browser

---

### Post by vivek.pandey on 2011-03-20
better thanx r_senior.. he once taught me how to run cgi and configure apache for it :-)

---

### Post by romy.mathew on 2011-03-20
if I need to watch my cgi output i need to paste the url 

"http://192.168.1.8/cgi-bin/cgi1.cgi"

I tried to access this page from other system connected to the lan but when i tried to access the url from different location may be outside the location my home it seems an internal error.....

why this problem occur...?

---

