---
title: "setting up a web server"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2011-02-20
Hi guys
Im currently experimentint with setting up a web server on a vpc with ubuntu server 10.10

I have managed to get it to show the web page when typing in the local ip address.
Now when i type in the internet ip address of my router (a netgear) i get page not found 

Im guessing i somehow need to set the router to link the wan ip with the ip of the virtual machine.

Any idea how i do this

---

### Post by yeats on 2011-02-20
This isn't really an Ubuntu question, so you might need to seek help on a Netgear forum.  I uncovered this though, that will hopefully point you in the right direction:

[http://kbserver.netgear.com/kb_web_files/n101145.asp](http://kbserver.netgear.com/kb_web_files/n101145.asp)

---

### Post by bigmonmulgrew on 2011-02-20
I wasnt sure if it was a configuration problem with the router or the server, hence posting here.

So basically your saying i need to forward ports the the servers ip address right?

---

### Post by SR_ELPIRATA on 2011-02-20
Basically yes, forward port 80 to the IP of the webserver (make sure the address is static not dynamic)

---

### Post by bigmonmulgrew on 2011-02-20
Ok well I've forwarded port 80 in my router. 
Now I'm getting the an error saying the server is taking too long to respond.

Also when reloading apache2 I get the error message
Could not reliably determine the servers fully qualified domain name

Could I have done something wrong setting it up

---

### Post by bigmonmulgrew on 2011-02-20
OK I have solved one problem
I googled 
> Could not reliably determine the server’s fully qualified 
and found this page

[http://aslamnajeebdeen.com/blog/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu](http://aslamnajeebdeen.com/blog/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu)

which ultimately says to open httpd.conf and add the line
```
ServerName localhost
```

---

### Post by degarb on 2011-02-20
I setup abyss, a bit easier than apache.

Port forwarding is obvious.  But I had to sudo start abyss, since UBuntu closes all ports under 1024 or so.   On one machine the "sudo autostart.sh" worked, for some reason didn't on two other machines.

In this day of everyone needing broadband, just to have a working OS, I don't know who wouldn't want a home webserver other than the technical knowledge to get it setup, or why this isn't unified and part of the OS.  ICQ and Opera have a home webserver to some extent, but it has been a decade since I have used ICQ and never tried Opera's, because I run a conventional server.  

I use dyndns.dk.  It took like 4  lines to write an ahk code to update on ip change.  I don't know how to write code for linux though.  Probably, days of coding.

---

### Post by bigmonmulgrew on 2011-02-20
Ok so if abyss is easier surely there is a downside?

Also I will feel a bit like I'm giving up if I change from apache to abyss

---

### Post by bigmonmulgrew on 2011-02-20
Just managed to get it working using port 8000
My ISP must be blocking it despite claiming to not do.

---

### Post by wizard10000 on 2011-02-20
> **degarb said:**
> But I had to sudo start abyss, since UBuntu closes all ports under 1024 or so.

Close - out of the box Linux doesn't listen on *any* ports but only root can open a port below 1024.  That's why you have to be root to run any daemon or application that runs on a low port.

---

### Post by bigmonmulgrew on 2011-02-21
Well in regards to my ISP blocking ports I've asked them and got this reply
> Dear David, Thank you for contacting us. We can confirm that we do not block port 80. In fact the only port that we block for you is port 25 which is for outgoing email. We could advise you to check if there is some port forwarding needed for the website. However you will need to disable the HTTP service of the bebox under Telnet if the site is to function properly. Here is how to do so: 1.Click on 'Start'> 'Run' 2.Type 'CMD' in the field 'Open', Press 'OK' 3.In the DOS box (black screen) type in: telnet 192.168.1.254 Press 'Enter'. 4.Use for username: 'Administrator', and the the appropriate password. There is no password if you have not changed it. Type in:service system ifdelete name=HTTP group=wan Type in: saveall Please let us know if you need any further assistance. Best Regards Greg / Be* Tech

I can access the website fine using port 8000.
Could the server be blockign port 80?
How do I check?

---

### Post by bigmonmulgrew on 2011-02-21
I have managed to solve the issue.

MY router was set to forward port 80 (and several others) to my xbox360.
When I created the rule to forward port 80 to my server the xbox was taking priority as it was the first in the list.

I disabled the firewall ruls relating to the xbox and now all is well.

---

