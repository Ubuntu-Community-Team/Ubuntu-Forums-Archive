---
title: "Apache forcing a webpage to users"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by slaz on 2010-11-03
Hello,
 
I have an ubuntu server set up, running Apache. I want to have a webpage that is in my documentroot directory be serverd to the users on my LAN. Can I do this with Apache, force the user to a webpage that is on my ubuntu server? 
 
Thanks, 
Slaz

---

### Post by SeijiSensei on 2010-11-03
> **slaz said:**
> Hello,
 
I have an ubuntu server set up, running Apache. I want to have a webpage that is in my documentroot directory be serverd to the users on my LAN. Can I do this with Apache, force the user to a webpage that is on my ubuntu server? 
 
Thanks, 
Slaz

If you have Apache installed and running, you should be able to open a browser on that machine and visit [http://localhost/](http://localhost/).  You should then see the "It Works!" page.  That page is stored in /var/www/index.html.  You should also see that page from other machines on the network if you use its IP address in a URL of the form [http://10.10.10.10/](http://10.10.10.10/) or, if the machine is findable by DNS, its hostname [http://host.example.com/](http://host.example.com/).  

Replace /var/www/index.html with the HTML page you want to display and name the file index.html.  You'll need to use sudo for this since /var/www is owned by the root (admin) user.

If you're talking about forcing them to a webpage at login, then you'd need to set up the machines to launch a browser full-screen at startup that loads the URL you want to force.  Are we talking about Windows or Linux clients? 

If you mean you want everyone's browsers to open a specific webpage when launched, you can configure the home page settings in their browsers.  You'll have to lock these settings down so the users can't change them. How you'd do that would depend on the browser and the OS.

---

### Post by slaz on 2010-11-03
Hi SeijiSensei,
 
Thanks for the response, the clients would be windows clients. This sounds what I want to accomplish. As for the resolving the ip address to a hostname, could I use my DNS server to relsolve the ip address to my Ubuntu servers hostname, even though it is not actually a real domain? I was also thinking of maybe writing a script to put in the cgi-bin directory that would not allow a user past the webpage that I am forcing. If they clicked the accept button on my webpage, they would be allowed past. Can this be done like this? 
 
Thanks again,
Slaz

---

