---
title: "Apache from local to public"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by fromscratch on 2011-01-18
Hello everyone. 

Today I **just** decided to move from Windows to Linux. :)

I  would like someone else outside my house and from another computer to  access a webpage that I host on Apache under Linux Ubuntu 10.10.

For now the only steps I did were the following:
 
*** I installed Apache2 via the taskbar: **

System
   Administration
       Synaptic Package Manager 

*** Then I opened Firefox and reached [http://localhost](http://localhost) and I obtained the It works page displaying the following.**

**     [COLOR=Blue]"It Works[/COLOR]**[COLOR=Blue]
     This is the default web page for this server.      
The web server software is running but no content has been added, yet."[/COLOR]

* With gedit I modified and saved the var/www/index.html in order to display something else so now [B][http://localhost](http://localhost) displays
[COLOR=Blue]
[/COLOR] [/B][COLOR=Blue]**     "Hello World!**
     This is the default web page for this server that I edited with gedit. 
The web server software is running but no content has been added, yet.[/COLOR]"

Can  somebody explain to me the other steps that will allow any person using  a computer and a browser to see the exact index.html that I just  modified. I mean what other files do I have to edit to tell Apache to  let the index.html to be accessible online?

Also I am not sure but is it possible that the solution would include  the IP adress of my computer?

Thank you in advance.

---

### Post by wojox on 2011-01-19
Hey and welcome to the forums. :p

You will need to log on to your router and set up port forwarding to allow users outside your network to view your site. Then use your ip from [whatsmyip]("http://www.whatsmyip.org/") to view it.

---

### Post by kg87 on 2011-01-19
as wojox said, you need to find your ip but....

if your router supports it, [http://www.dyndns.com/]("http://www.dyndns.com/"), will automatically update your ip to a domain name, that way you dont need to know the IP all the time. 

so that combined with correct portforwarding will be a tidy webserver set up. 

Id suggest some basic security though!

---

