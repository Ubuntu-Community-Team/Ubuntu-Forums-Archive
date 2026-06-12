---
title: "Apache WebServer"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by f37u5g0d on 2008-07-08
I am trying to set up an apache web server.  Right now if I run sudo /etc/init.d/apache2 reload.  The apache service reloads with no errors.  I have a dyndns host name (novak.homelinux.com or [www.novak.homelinux.com](www.novak.homelinux.com)) but when I but either of those into my browser I get either Wide Open West telling me that server is down or a blank file hierarchy thing.  I have port forwarding from 79 - 444 TCP.  Why isn't my website showing up?

---

### Post by superprash2003 on 2008-07-09
you wont be able to access your dyndns hostname from your pc.. it would be accessible only from outside your network

---

### Post by f37u5g0d on 2008-07-09
Ahhh.  After posting this I realized that might be a possibility so I instant messaged the link to a friend to try it out.  They get the same thing I get.  The good news is that there is a footer at the bottom of the page that says "apache web server 2.2.24, ubuntu linux, and then my dyndns domain".  So there is light at the end of the tunnel!  If anyone else has any help please post!  Here is a link to the website. (or lack-thereof)

[www.novak.homelinux.com](www.novak.homelinux.com)

---

### Post by f37u5g0d on 2008-07-09
By moving all of my website into /var/www/ I know can open my website from my own computer but others are still having problems.  Anybody outside of my network gets timed out when they try to view the site.  Please if anyone has any ideas post them!  Thank you for any and all help!

---

### Post by superprash2003 on 2008-07-09
if you said you saw the apache 2.x linux server.... at the bottom of the page then its successfully configured and when you move your website to the /var/www folder it should work.. ensure that your port 80 is still open [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by f37u5g0d on 2008-07-09
I forwarded the port 80 to my ip address and I even disabled blocking of anonymous internet requests in my linksys router but the website you gave me still reports that my (outside world) ip isn't repsonding on port 80.  I am using dhcp (yes I know it might change) could that be the problem?

---

### Post by dmizer on 2008-07-09
can you view the site from another computer inside your local network?  you'll have to look at it by ip address, but if you can access it from another computer (even by ip address) that means there is either a problem with your dynamic host setup, or with your router.

---

### Post by f37u5g0d on 2008-07-09
From another computer on the network when I type in the servers ip or my dyndns domain I get this page:

"Not Found

The requested URL / was not found on this server.
Apache/2.2.8 (Ubuntu) Server at 192.168.1.102 Port 80"

But from the server if I put in my dyndns domain I get the site.

---

### Post by dmizer on 2008-07-09
do you have a firewall running on the ubuntu server?

---

### Post by f37u5g0d on 2008-07-09
I do not believe so.  I think that there is no firewall in ubuntu set-up by default and I never set one up and there isn't a process listed for it in the system monitor so I'm going to go with no.

---

### Post by dmizer on 2008-07-09
i wonder if your isp is blocking port 80 at the modem.  if this is the case, then you'll have to use a different port.  you should be able to configure this through your dynamic host so that the alternate port is invisibile to browsers.

---

### Post by superprash2003 on 2008-07-10
i dont think his isp is blocking port 80(see post no 3). 

please use static ip.. also disable that filter in your router for the time being and then try

---

### Post by f37u5g0d on 2008-07-10
Well I actually I am at the same time learning how to use ssh and x forwarding (which dmizer also helped me a great deal with) and just a few moments ago I connected to my server from this client (at work) using my dyndns domain and my password through port 22.  Port 22 and port 80 were both forwarded the same way but when I used the port tester found on dyndns's site it reported that 22 was open while 80 was blocked.  I also tried port 75 which is open and dyndns suggests that I create another domain that uses port 75 (or any other open port) and use the orginial to webhop to the second so that I can use the original domain on a new port seamlessly to the user.  I think though that I will just create a new domain on port 75.  I haven't really given out the old domain yet so it won't be an issue for anybody.  However do I have to use static ip routing for a webserver to work?  Can I DHCP my two other machines and static only the server machine all on one router/network?

---

### Post by f37u5g0d on 2008-07-10
Just thought I'd bump this and update.  Right now when I go to my dyndns domain ( novak.homelinux.com ) from outside the server's network my browser loads and loads and loads.  It never displays anything and has yet to time out (going on 2 minutes!).

---

### Post by bradhamilton on 2008-07-10
> **f37u5g0d said:**
> Just thought I'd bump this and update.  Right now when I go to my dyndns domain ( novak.homelinux.com ) from outside the server's network my browser loads and loads and loads.  It never displays anything and has yet to time out (going on 2 minutes!).

Your site is "ping"-able, but an attempt to connect via port 80 is rejected silently.  Does your ISP allow the ability to connect via port 80?

---

### Post by f37u5g0d on 2008-07-10
I don't know for sure but I don't think so.  I can successfully connect ssh (on port 22) with the exact same domain.  And I have tried websites that scan ports all of them have told me that port 80 is blocked even though I set up my router to forward it.  Is there anything else that would be blocking port 80 besides my isp?

---

### Post by f37u5g0d on 2008-07-10
I told my apache server to listen on port 75 (via ssh) and reloaded it with no errors.  Now if I type in my dyndns domain into the url bar of firefox and :75 it gives me this site.

Not Found

The requested URL / was not found on this server.
Apache/2.2.8 (Ubuntu) Server at novak.homelinux.com Port 75

Which is awesome cause it clearly got through to my server!  But why didn't it load the website that I have in var/www/ ??

---

### Post by dmizer on 2008-07-10
actually, you should try a much higher and unassigned port, or port 8080 (the official alternate http port).

remember ... var/www/ is different than /var/www/  are you sure you have your web files in the correct location?

you will have to do some tweaking to your apache configuration files to support a different port.

[http://www.apachefriends.org/f/viewtopic.php?t=20376&sid=c8a4f300b07ca4a5148bdffc2c78c36d](http://www.apachefriends.org/f/viewtopic.php?t=20376&sid=c8a4f300b07ca4a5148bdffc2c78c36d)

---

### Post by f37u5g0d on 2008-07-11
I firguered it out!  I had to use port 75 (maybe I'll switch to 8080 we'll see)  And I had to make a htdocs folder in /.  I know it was really weird.  But I figuered it out from the var/logs/apache/error.log file.  Anyway up and running now.  Thank you for all your help!

novak.homelinux.com:75

---

### Post by dmizer on 2008-07-11
dyndns has the ability to invisibly support your port 75.

go to "my hosts" > select your novak.homelinux.com domain

under "service type" select "WebHop redirect".  a "Redirect URL" blank will appear.  in that blank, enter novak.homelinux.com:75 put a check mark in the "Yes, cloak this page." and put novak.homelinux.com under "Cloaked title"

---

### Post by f37u5g0d on 2008-07-11
I am also using novak.homelinux.com to connect to my server via ssh.  That connects on port 22.  Will having the novak.homelinux.com:75 cloacked under novak.homelinux.com screw up ssh because it specifies the port like that?

---

### Post by linux6994 on 2008-07-11
If you have a router such as a Linksys you should open up port 80 and port forward it to your server.

---

### Post by dmizer on 2008-07-11
> **f37u5g0d said:**
> I am also using novak.homelinux.com to connect to my server via ssh.  That connects on port 22.  Will having the novak.homelinux.com:75 cloacked under novak.homelinux.com screw up ssh because it specifies the port like that?

try it.  it's a simple matter to un-cloak it.

i don't think it will make a difference here, for the same reason that "ssh user(at)novak.homelinux.com" doesn't go to port 80.  if you have problems when the url is cloaked, try this: "ssh user(at)hovak.homelinux.com -p 22"

---

### Post by f37u5g0d on 2008-07-14
I got my webserver up and running but I have a strange problem.  I looked in the error logs (var/logs/apache2/) to get it up and I learned that I had to have a /htdocs folder that contains everything I want to be avaialable on the site.  I created one that was nothing but a link to a folder in my home directory so that I could alter the website without using root permissions but I still have to re-apply the "others" access permissions everytime I move something into that folder.  I have search and searched but none of the apache configuration files mention /htdocs.  I have search the following files.

apache2.conf
httpd.conf
0000-default in sites enabled
default in sites availabe

This is an issue for me because in the var/logs/apache folder only the error log does anything.  The access logs are both blank (and I know people have accessed the site).  The two "default" config files both point the root dir to /var/www.  What is going on here?

---

### Post by dmizer on 2008-07-14
just alter the home page with root permissions.  this is extremely important.

read here for why this is so vital: [http://ubuntuforums.org/showthread.php?t=688979](http://ubuntuforums.org/showthread.php?t=688979)

best message board i've found: [http://cutephp.com/](http://cutephp.com/)

don't know what to tell you about your logs.  i've never had a problem with it, so i can't imagine why you wouldn't be getting yours.

words of advice: you really shouldn't be using a computer with gui to host your website.  this will make you a much easier target. the more things you have running, the more things you have available for a hacker to exploit.  just use an old junk machine and don't put a gui on it.  lock down everything that could possibly be used to gain access to your box (wget, ftp, anything that could be used to download something to your machine).  it won't take much to host your own site.  i've been hosting mine on a 500mhz pIII with 512 meg of ram for years now, so you should be able to pick something up for free or close to free.

if you must have your gui laptop hosting your site, please look into vmware.  install a cli server version of ubuntu, and keep your gui desktop separate from your web server.

---

### Post by f37u5g0d on 2008-07-15
I understand permissions in general but I don't understand what it means to alter the home page with root permissions.  How do I do that in gui and in cli?  By homepage do you mean my index.html file of my website?
Thanks for the tip about the message board but I want to learn how to write the code myself.  I do not have a spare computer lying around but maybe I will in the future.  Until then I am just going to have to assume the risk.  Fortunately I back my data and I don't have anything much worth stealing on my computer anyway.

---

### Post by dmizer on 2008-07-15
if you don't have a spare computer, consider virtualization through vmware for your server.  running a cli server version of ubuntu will cost you very little in the way of performance.

with virtualization, you will basically be running two operating systems on one computer at the same time.  you will have a host and a guest operating system.  your host is already installed.  the guest operating system will run your web server.  both the host and the guest will have separate ip addresses, so your host computer will be completely shielded and safe from potential hacking.

another advantage to this is that if and when you do get a dedicated server, you can create an install image from your virtual machine.  also, entire server backups are as easy as copy/paste.

more information here: [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

remember, gleaning information from your computer is not the only reason your server will be a target.  if your machine can be compromised, then your web server can be used as a launch pad for a variety of nasty things.  so even if you think you have no enticing data, you're still a juicy target.

here's to edit your files as root both in gui and in cli ...

in gui:
```
gksudo gedit /var/www/index.html
```
in cli:
```
sudo nano /var/www/index.html
```
this will work on any of your files.

---

### Post by f37u5g0d on 2008-07-15
Thank you for your help.  I am familiar with virtualization.  I am currently virualizing a winXP machine using virtualbox.  Thank you for the explination on how to change the permissions I still have two questions though.  1 I don't have a /var/www/index.html.  My website is located it htdocs.  (IDK why but that's where apache wants them.  I can't find any mention of htdocs in any of the config files.  They all point to /var/www).  Anyway I'll just run the gksudo command on my /htdocs/index.html My second question is - Do I just open them up with that command and then save them and their permissions will be changed?  What is the difference between sudo and gksudo?
Thank you again and I think I will virtualize.

---

