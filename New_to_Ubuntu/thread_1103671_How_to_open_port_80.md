---
title: "How to open port 80?"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by Lakeside5 on 2009-03-22
Well I am (stil) having a time trying to get my Hardy Heron server working.  I have Webmin, and can see  from it that, yes, Apache2 is running.  I used an online  portscan, and it said that port 80 was not open.  I called my ISP and they said they are not blocking me.  I have dynamic name service from DynDNS,  and have configured my router accordingly (entered dyndns hostmame, username, password) even chose 'dynamic' where it asked on the router for type of service (that is right?)  I had problems though, trying to port forward, for some reason it will not take my settings.  I typed in 'http' (name of service) port 89 to port 80,  and for forward to, there was a number 192.168.1.1__,  where I entered '00',  for 192.168.1.100 (what it showed with an ifconfig at the terminal) it  showed that address as 'inet address' beside 'wlan', so I hop that is right BUT the router would not keep these settings, whatever I typed in was gone, after I hit 'save' and I tried this ten times lol.  What could be going on, I really really want to use this server, sigh.

---

### Post by Xiong Chiamiov on 2009-03-23
I think [UFW](https://wiki.ubuntu.com/UbuntuFirewall) might be enabled by default nowadays.

First, can you access anything on that computer from [http://localhost?](http://localhost?)  What about [http://192.168.1.100?](http://192.168.1.100?)

---

### Post by Lakeside5 on 2009-03-24
Thanks Xiong Chiamiov, I knew I forgot something!  I will certainly check that out, can't host sites if my firewall is blocking port 80 now can I?! :)
Here's a strange thing too, since u ask, I cannot get localhost, and i could before, even see a website I installed into localhost (a joomla cms site) and I can't get my router at it's usual address- 192.168.1.1, but I CAN get it now at 192.168.1.**100**. hmmm

---

### Post by philinux on 2009-03-24
On a default install port 80 is coming up stealthed on my machine. Not touched anything to do with firewall since install. Could be my router though not sure.

[https://www.grc.com/x/ne.dll?rh1dkyd2](https://www.grc.com/x/ne.dll?rh1dkyd2)

---

### Post by mcduck on 2009-03-24
UFW isn't enabled by default, so unless you have installed & configured a firewall yourself there shouldn't be anything in Ubuntu restricting your connections.

If you want, you can check your firewall rules with the following command:
```
sudo iptables -L
```

You can also check if UFW is enabled or not by running this:
```
sudo ufw status
```

---

### Post by kanikilu on 2009-03-24
> **Lakeside5 said:**
> so I hop that is right BUT the router would not keep these settings, whatever I typed in was gone, after I hit 'save' and I tried this ten times lol.  What could be going on, I really really want to use this server, sigh. It sounds like you need to get your router sorted out first. No amount of fiddling with the server is going to help if you can't get your router to forward that port properly...

---

### Post by Lakeside5 on 2009-03-24
Hey McDuck :) I get this with ufw status: WARN: uid is 0 but '/var' is owned by 1000
Status: not loaded
Have NO idea what that means lol.  
and  for iptables I get this: Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
I am seriously thinking of setting my router back to it's factory settings and starting over? what do you think. Thanks for all the help so far guys.

---

### Post by lavinog on 2009-03-24
> **Lakeside5 said:**
> Well I am (stil) having a time trying to get my Hardy Heron server working.  I have Webmin, and can see  from it that, yes, Apache2 is running.  I used an online  portscan, and it said that port 80 was not open.  I called my ISP and they said they are not blocking me.  I have dynamic name service from DynDNS,  and have configured my router accordingly (entered dyndns hostmame, username, password) even chose 'dynamic' where it asked on the router for type of service (that is right?)  I had problems though, trying to port forward, for some reason it will not take my settings.  I typed in 'http' (name of service) port 89 to port 80,  and for forward to, there was a number 192.168.1.1__,  where I entered '00',  for 192.168.1.100 (what it showed with an ifconfig at the terminal) it  showed that address as 'inet address' beside 'wlan', so I hop that is right BUT the router would not keep these settings, whatever I typed in was gone, after I hit 'save' and I tried this ten times lol.  What could be going on, I really really want to use this server, sigh.

What router do you have?
It looks like the problem is with your router setup and not your ubuntu machine, although your ubuntu machine should use a static ip and not a dynamic ip, but normally this shouldn't be an issue right away (but can suddenly stop working later when your ip address changes)

Normally if you forward a range of ports you will want to list them in incrementing order (80-89 not 89-80.) If you have no need for ports 81-89 don't use them and just set port 80 to your machine. (this might be why your router wont save the changes)

---

### Post by Lakeside5 on 2009-03-24
Oh oh lavinog, that was a typo :) I meant I had it at port 80 to port 80  ;thanks

---

### Post by mcduck on 2009-03-24
> **Lakeside5 said:**
> Hey McDuck :) I get this with ufw status: WARN: uid is 0 but '/var' is owned by 1000
Status: not loaded
Have NO idea what that means lol.  
and  for iptables I get this: Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
I am seriously thinking of setting my router back to it's factory settings and starting over? what do you think. Thanks for all the help so far guys.

"not loaded" means that UFW is not running. And as all iptables rules also have policy "accept" this means that you are not using any firewall on the Ubuntu machine, all traffic is allowed.

The warning you got tells you that the /var directory is owned by wrong user (uid 1000 is usually the first user of the system) while it should be owned by uid 0 (root). Have you changed permissions of system directories? Wrong ownership or permissions on system directories can cause all kinds of problems so you should probably get that fixed..

---

### Post by Lakeside5 on 2009-03-24
wow!  I will sort that out right  away McDuck, I thought I had ownership of var,as I seem to remember 'chowning' it, in order to install my joomla site into  [www...but](www...but) apparently not.  So all I have to do is do a chown of that var folder? thanks again.
I see that the permissions are set at 755 for the var folder. I am the ONLY user on this computer/network etc. as far as I know, and I did not give myself root priveledges, I just use sudo. I am probably a bit confused about all this,  I assumed I had ownership of var, as I was able to chown www, which is IN var, would u be kind enough to tell me how to get proper ownership of var? thanks

---

### Post by mcduck on 2009-03-24
> **Lakeside5 said:**
> wow!  I will sort that out right  away McDuck, I thought I had ownership of var,as I seem to remember 'chowning' it, in order to install my joomla site into  [www...but](www...but) apparently not.  So all I have to do is do a chown of that var folder? thanks again.

The thing is that you *shouldn't* have ownership of /var. It should belong to root.

Probably you were supposed to chown /var/www which is the directory used by Apache..

edit: Assuming you only changed /var itself instead of recursively changing everything inside it, this should fix the problem:
```
sudo chown root:root /var
sudo chmod 755 /var
```

Using sudo runs the commands following it with root permissions. And the root account exists in Linux no matter if you are using it or not, it's very important part of the system itself. Even when root account is not used in Ubuntu that doesn't mean that it wasn't there, simply that logging in as root has been disabled. Every time you use sudo you are actually running things as root.

---

### Post by Lakeside5 on 2009-03-24
Ok, I just did what u suggested, and now when I run sudo ufw status I only get: Status: not loaded, and no warnings so I assume that www is ok now?

---

### Post by mcduck on 2009-03-24
> **Lakeside5 said:**
> Ok, I just did what u suggested, and now when I run sudo ufw status I only get: Status: not loaded, and no warnings so I assume that www is ok now?

At least /var is ok now. If your server is running fine I suppose /var/www is fine as well.

---

