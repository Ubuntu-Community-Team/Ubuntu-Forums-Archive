---
title: "What to setup to access ubuntu server connected on same network?"
date: 2014-03-06
forum: Networking &amp; Wireless
---

### Post by eakDev on 2014-03-06
Hi Everyone,
GOAL: Setup Ubuntu Server as a webserver for a local network, where only the ones connected on the same network can access it.

STATUS: Im done with installing Ubuntu Server, installed webmin also.

PROBLEM: I can't access my Ubuntu server on a computer connected on the same router.
DETAILS:
[LIST=1]
[*]My desktop(ubuntu server) and laptop is connected on the same router
[*]My router is using DHCP, my server gets a new ip address everytime i restart (ex. 192.168.1.4)
[/LIST]

QUESTION: what do I configure? Do I need to do something with my router?

I have limited knowledge on networking, a help would be great.

---

### Post by Lars Noodén on 2014-03-06
There should be an option somewhere in your router's administrative menus to set a fixed ip address on your LAN for your server.  The details vary from model to model and brand to brand so there's not a generic solution.  But the router menus are usually not that complex and a few minutes of poking around will turn up something.

Once you have a permanent address on the LAN for your server, then many possibilities open up.

---

### Post by eakDev on 2014-03-06
> **Lars Noodén said:**
> There should be an option somewhere in your router's administrative menus to set a fixed ip address on your LAN for your server.  The details vary from model to model and brand to brand so there's not a generic solution.  But the router menus are usually not that complex and a few minutes of poking around will turn up something.

Once you have a permanent address on the LAN for your server, then many possibilities open up.

Okay so there was a portion on my router setting "Manually Assigned IP around the DHCP List", I did assign it and was able to tell my router to set 192.168.1.20 as the static IP for my server. Tried to restart my server and IP does not change.

What's next please?

---

### Post by Lars Noodén on 2014-03-06
How do you want to access it and what do you want to do with that access?  

If you are thinking about file sharing, one LAN-only option is Samba.  An option that works over both LAN and the Internet is SFTP.  For the latter, there are a lot of graphical clients like your File Manager.  There are also specialized tools like SSHFS, which works transparently over SFTP.

---

### Post by eakDev on 2014-03-06
UPDATE:
After setting my router to give a static IP to my server, I am able to use ssh user@remote_hosts. I think this means I am able to connect to it. my question is how do i do tha with webmin?

---

### Post by Lars Noodén on 2014-03-06
I can't help with webmin but with the ssh connection you can already do a lot.  Bring up your file manager, go to the location bar, and then enter the URI for your server: *sftp://user@remote_hosts/home/user/*  That should open up a window on your server and you can drag and drop files and otherwise operate as if it were local.  Because this uses SSH, it is both secure and can operate over the Internet, not just the LAN, if you set up the router so.

---

### Post by eakDev on 2014-03-06
Hi Lars,

My main goal is to host(only for the ones connected on the network) my DJANGO website (django+gunicorn+nginx+postgresql) on the UBUNTU SERVER. Now I installed postgres as well during the server installation because i will be using it.
What would you suggest as my next move? Since I am able to connect to my server how do I host my internal website? 

Thanks a lot.

---

### Post by Lars Noodén on 2014-03-06
Your next step is probably to install the web server nginx, if that is what the guides you are following suggest.  That will put one virtual host on your machine and you can change the configuration by editing /etc/nginx/sites-enabled/default   nginx puts the html documents in /usr/share/nginx/html by default, but I prefer to change that to /var/www/  I guess it depends on the instructions you have.

Wherever you have your files, you'll have to set write permissions for yourself there.

---

### Post by eakDev on 2014-03-06
first off, your suggestion about using file manager worked :)

second, I'm not really following specific instructions right now, all I have right now is that I have a working django+postgre+gunicron on a virtualenvironment. If you could point or suggest a way to host this on the server it would be great again.

---

### Post by Lars Noodén on 2014-03-06
One of the easier ways to work with servers is via the terminal, at least for some tasks.  One reason is that it is easy to type instructions for the terminal in these and other forums. ;)

I can get you started with nginx but then with django you'll probably have to start a new thread and find someone with experience with it.

Installing nginx is easy over ssh.

```

sudo apt-get update;
sudo apt-get install nginx;

```

Then you should be able to connect with your web browser and see the default page.  

As mentioned nginx puts stuff by default in /usr/share/nginx/html/ 
If you are the only user of that server, you can just take ownership of that directory and thus be able
to write to it and the files in it.  

```

sudo chown -R eakdev /usr/share/nginx/html/

```

If you make changes to the nginx configuration file, you'll have to restart it for the changes to take effect.

```

sudo service nginx reload

```

Be sure to make a backup copy of the configuration file before making changes.

Also, my preference is to move the web server's root from /usr/share/nginx/html/ to /var/www/ or something like that.

---

### Post by eakDev on 2014-03-06
> **Lars Noodén said:**
> One of the easier ways to work with servers is via the terminal, at least for some tasks.  One reason is that it is easy to type instructions for the terminal in these and other forums. ;)

I can get you started with nginx but then with django you'll probably have to start a new thread and find someone with experience with it.

Installing nginx is easy over ssh.

```

sudo apt-get update;
sudo apt-get install nginx;

```

Then you should be able to connect with your web browser and see the default page.  

As mentioned nginx puts stuff by default in /usr/share/nginx/html/ 
If you are the only user of that server, you can just take ownership of that directory and thus be able
to write to it and the files in it.  

```

sudo chown -R eakdev /usr/share/nginx/html/

```

If you make changes to the nginx configuration file, you'll have to restart it for the changes to take effect.

```

sudo service nginx reload

```

Be sure to make a backup copy of the configuration file before making changes.

Also, my preference is to move the web server's root from /usr/share/nginx/html/ to /var/www/ or something like that.

Dude this is awesome, you have no Idea how informative this is. I will do your suggestions and preference and come back if ever i have problems hehe. I'm grateful.
"Google is great, but sometimes you just have to talk and ask someone"

---

### Post by eakDev on 2014-03-06
Hi Lars,

One last thing, I am reading a tutorial and it mentions this
"I’m also assuming you **configured your DNS to point a domain at the server’s IP**. In this text, I pretend your domain is example.com"

QUESTION: Do I need to configure a DNS? do i need that for my local website? As I've mentioned before all I want is for the website to be available to the network. If yes, how do I dot that?

---

### Post by Lars Noodén on 2014-03-06
If you're only going to access it over your LAN, you do not need to hire a DNS registrar to register your hostname.  You can use the local IP number just fine over the LAN.  That's also why you set the router to dole out a fixed number to the server.  

There is a trick where you can put an entry in your client's */etc/hosts* file for your server.  That would give it a name, but only known to that one client and only while that client is on the same LAN.  

You could even access it from the Internet via your router's external IP number, if you have ports 22, 80 and 443 forwarded to your server.

---

### Post by yoog on 2014-03-06
> **eakDev said:**
> UPDATE:
After setting my router to give a static IP to my server, I am able to use ssh user@remote_hosts. I think this means I am able to connect to it. my question is how do i do tha with webmin?

To access webmin
[https://ipaddress:10000](https://ipaddress:10000)
example (in my case) [https://192.168.1.117:10000](https://192.168.1.117:10000)
Hope this helps.

---

### Post by eakDev on 2014-03-06
Okay that clears things up. I installed nginx as you instructed, now you said 
"Then you should be able to connect with your web browser and see the default page." - how do you access it on a browser exactly? tried accessing my ip on browser no luck
also, nginx uses 
/usr/share/nginx/www/ already not /usr/share/nginx/html/, am I correct to assume that files I put on these directory will be available on the network through a browser?

---

### Post by Lars Noodén on 2014-03-06
Yes, files put in that directory should be visible via the web server.  It looks like nginx has changed default locations in the recent release of Ubuntu.  I'm running Trusty Tahr beta for what that's worth. 

One thing to check might be the firewall.  I can't remember the defaults on ubuntu server

```

sudo ufw allow ssh
sudo ufw allow http
sudo ufw allow https
sudo ufw enable
sudo ufw status verbose

```

That should let in your web actvity as well as your remote access via ssh/sftp.

---

### Post by Lars Noodén on 2014-03-06
Also, is nginx running?

```

service nginx status

```

---

### Post by eakDev on 2014-03-06
yes, its says *nginx is running, so for example on the .../nginx/www/ directory there is a file called index.html. 

how do i open that on a browser on my laptop? do i use htpps://<ip_address> or there's more?

---

### Post by Lars Noodén on 2014-03-06
Yes.   That file should say "Welcome to nginx!" plus some other stuff.  

Try http first.  https requires that you set up a certificate.  Try in your broswer on your desktop machine (not server) an address like this:

```

http://192.168.1.20/

```

Or whatever you set the server to be.

---

### Post by eakDev on 2014-03-06
Dude again your great, http seems to work. But why not https?

---

### Post by Lars Noodén on 2014-03-06
http is unencrypted and needs no further setup.

https is http over tls/ssl.  You have port 443 (https) open, but the server needs to be set up to listen there and use https first.  That means setting up a certificate.  

This one gives a decent overview of the steps:

[https://library.linode.com/web-servers/nginx/configuration/ssl](https://library.linode.com/web-servers/nginx/configuration/ssl)

The redirect is not needed.  Just remember that the same host address is really two different web sites one on port 80 (http) and another on port 443 (https)  It's not hard to do, just picky about the steps.  And once it is set up you can forget about it and let it run.

---

