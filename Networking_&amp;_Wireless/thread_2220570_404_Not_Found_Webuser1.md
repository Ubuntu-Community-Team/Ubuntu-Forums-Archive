---
title: "404 Not Found Webuser1"
date: 2014-04-28
forum: Networking &amp; Wireless
---

### Post by Jordan_Hickin on 2014-04-28
Hi guys

I was following the information on this: [http://www.techsupportalert.com/how-to-set-up-your-own-web-server.htm](http://www.techsupportalert.com/how-to-set-up-your-own-web-server.htm)

I get as far as testing the webuser site. (192.168.0.7/webuser)

All i get is a 404 Not Found.

my basic 192.168.0.7 is showing as the default ubuntu page.

Where am i meant to be saving the html files. the user setup details are as follows:

```


root@webserver1:/etc# cd /var/www
root@webserver1:/var/www# mkdir webuser1
root@webserver1:/var/www# useradd webuser1 -p **** -d /var/www/webuser1 -s /bin/false
root@webserver1:/var/www# chown webuser1 webuser1
root@webserver1:/var/www# passwd webuser1
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated sucessfully


```


I connect via the terminal on my laptop. Running Ubuntu.

I know how to put items on there.. but i am unsure where to put the html file. 

Wouldn't it come up with something anyway rather than 404 Not Found.... 

Please Help

---

### Post by m_duck on 2014-04-29
Yep, a 404 would be expected. Apache in Ubuntu uses /var/www as the document root, so if it is listening on 192.168.0.7 (local network) it will serve the contents of /var/www when you ask it to. It will serve index.html or index.htm if it exists when you request a folder name (e.g. 192.168.0.7 or 192.168.0.7/webuser1). Also it will try and serve index.php etc. if you have PHP or other scripting languages installed and configured.

If /var/www/webuser1 is an empty directory, requesting 192.168.0.7/webuser1 will return a 404 (not found) error. This is because your request translates looking in the /var/www/webuser1/ folder for a file named index.html, index.htm (or index.php etc.). When Apache can't find it, it returns a 404. If you put something like the following in /var/www/webuser1/index.html it should be output when you next surf there.
```
<html>
  <body>
    <p>Hello!</p>
  </body>
</html>
```

---

### Post by lisati on 2014-04-29
Which version of Ubuntu server are you using? The default folder for placing the index.html or index.php file used to be /var/www. I believe in recent versions it was changed to /var/www/html.

---

