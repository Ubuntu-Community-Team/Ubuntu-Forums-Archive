---
title: "Need a guide"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by charlier653 on 2010-01-29
Can anyone point me to a guide/tutorial for installing an apache webserver ***without*** mysql/php?

My website is not set up as a database. Had been running it on windows, but had extreme problems with windows on the computer.
Upgraded that box with new MB etc, for my wife, and am trying to install the website on her old box.

Have installed Karmic on an older box (HP pavilion 521c: AMD Athlon XP 1700+, 768MB ram)

Am having trouble getting the website up and running. Unable to follow the twisted (that's the way it appears to me, anyway) official apache docs. Can't find a darned thing in there.

All I can find with a google search is LAMP installs, which I don't need.


As a side note, how can I search for a phrase on these forums?" every time i input more than 1 word, the search function separates each word and treats them as separate searches. cannot find anything that way.

---

### Post by milton1 on 2010-01-29
The lamp server install will be eaasy and include apache

```
sudo tasksel install lamp-server 
```

however, if you really only want apache, this should do it:

```
sudo apt-get install apache2 
```

Then place your webpage files in /var/www

---

### Post by milton1 on 2010-01-29
Also, if you haven't already, open the port for others to see your website:

```
 sudo ufw allow 40 
```

---

### Post by mörgæs on 2010-01-29
> **charlier653 said:**
> As a side note, how can I search for a phrase on these forums?" every time i input more than 1 word, the search function separates each word and treats them as separate searches. cannot find anything that way.

The search function in Ubuntuforums is not the best I have seen. I always use Google.

If you add ```
site:[http://ubuntuforums.org/](http://ubuntuforums.org/)
``` in the search field in Google, you will only get results from here.

---

### Post by mörgæs on 2010-01-29
> **milton1 said:**
> Also, if you haven't already, open the port for others to see your website:

```
 sudo ufw allow 40 
```

Shouldn't it be port 80?

---

### Post by charlier653 on 2010-01-29
> **milton1 said:**
> 



Then place your webpage files in /var/www


have installed apache2, placed webpage files in /var/www

got nothing, not even on localhost, or 127.0.0.1 loopback.

tried ```
sudo /etc/init.d/apache2 restart
```, got error, "no apache MPM installed.

did ```
sudo apt-get install apache MPM
```, got "no package found"

went to synaptic, found and installed apache2-mpm-worker

restarted apache2. now have home page showing on localhost, however, internal webpage links do not work. error "permission denied".

did ```
sudo ufw allow 80
``` (which *is* the port apache uses by default. no joy. cannot be accessed even within my own home network, with the local net address.

Where are the settings that allow the world to see the site?

---

### Post by milton1 on 2010-01-29
Yeah, it should be 80. Sorry, not fully awake yet.

---

### Post by milton1 on 2010-01-29
I don't think the permission denied error is a firewall issue. More likely the webpage is trying to access a folder that does not belong to the webserver group. Check your file permissions.

(Sorry, I don't know the specifics of the server group off the top of my head)

---

### Post by charlier653 on 2010-01-29
All files in /var/www are owned by root, including the index.html that runs the homepage. Is that the way it needs to be?

Would it make a difference if the main index.html was made in dreamweaver? However, the a href  links are still as I had hand coded them. The only thing Dreamweaver did was code the image placement on the home page.

---

### Post by milton1 on 2010-01-29
silly, basic question; are the href pointers absolute or relative?

---

### Post by HarrisonNapper on 2010-01-29
> **charlier653 said:**
> All files in /var/www are owned by root, including the index.html that runs the homepage. Is that the way it needs to be?

Would it make a difference if the main index.html was made in dreamweaver? However, the a href  links are still as I had hand coded them. The only thing Dreamweaver did was code the image placement on the home page.

Check group access rather than user access. As long as webserver group has read access, should be fine afaik.

---

### Post by milton1 on 2010-01-29
follow-up silly question; do any of the href pointers point to files outside of /var/www? This will almost certainly throw a permission denied error, unless the webserver group has read access to those outside files.

---

### Post by charlier653 on 2010-01-29
website internal links=

```
<center><a href="kitchen/kitchen.html><h2>Kitchen</h2></a></center>
```

as an example.

I would say that they are absolute, as I am not running a database type webserver.

all internal links point to the respective folders, and the html doc inside.

Permissions on all files are root:root. I don't know what group the webserver is supposed to  be.

Looking at the basic, it says files in each folder are unreadable. I am not logged in as root.

---

### Post by milton1 on 2010-01-29
root:root is ownership, not permission. try changing the permissions for all files in /var/www to read access:

```
sudo chmod -R 755 /var/www/* 
```

---

### Post by charlier653 on 2010-01-29
Ok that worked for local access. Thanks. However, there is still the problem of web access. There is still none outside my lan.

That also showed up the case sensitive problem......   .jpg v. .JPG

So I have a bit of work to do correcting that.

---

### Post by milton1 on 2010-01-29
for access to the machine, allowing 80 (or 443 if https) should do it. Beyond that, you will need to forward the port from your router.

If the router is forwarding, it may be that the ufw command didn't work because ufw is not yet running.

```
 sudo ufw enable

sudo ufw allow 80
```

---

### Post by milton1 on 2010-01-29
```
sudo ufw status
```

will show you which ports are open

---

### Post by charlier653 on 2010-01-29
Just did that, thank you.
am logged in as root on that machine, thus:

```
# ufw enable
firewall is active and enabled on system startup
# ufw allow 80
# ufw status
status active

to                action         from
-------------------------------------
80                allow          anywhere
```


still no access from outside lan, router/firewall is set to port forward 80 to that box.

---

### Post by charlier653 on 2010-01-29
router settings for that box

```
webserver-desktop  Web Server  -   TCP   80  70.230.173.220
```

---

### Post by charlier653 on 2010-01-29
As this is the only website hosted on that box, do I need to have anything set for "virtual host"?? Or should apache be serving the pages as is?

---

### Post by milton1 on 2010-01-29
Apache should serve the pages as-is. At this point, I think you've got me stumped. Could there be an earlier rule in the router that is superceding the open port 80?

---

### Post by milton1 on 2010-01-29
Can you access the website from another computer on the same LAN?

---

### Post by charlier653 on 2010-01-29
I can access the website only on the lan, by using the lan address.

When I type in the URL ([http://jens-home-renovation.no-ip.info](http://jens-home-renovation.no-ip.info)) I get the time - out error, website is taking too long to respond.

---

### Post by milton1 on 2010-01-29
What happens when you enter your WAN ip address directly, instead of the no-ip address?

---

### Post by charlier653 on 2010-01-29
Just thought of something....

Is there a script or some kind of way to make sure the DUC is actually running?

That might be the final problem here.

---

### Post by charlier653 on 2010-01-29
checked the ip address in no-ip.com, and looked again at the router......noip2 is not updating to their website.

I got my website by typing in the public ip address....


so now I need to get the dynamic update client working like it should.

---

### Post by charlier653 on 2010-01-29
Thank you all for the ***_great_*** help you've been!

---

