---
title: "Help put right info -router, for server"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by Lakeside5 on 2009-01-14
Trying again to host a site with my Hardy Heron server on here, and want to make sure I put the right info in the right place.  I have a Linksys router. Here are screenshots of the info (from Dyndns where I got a free dynamic domain) and of my router. I just want to know where I put what. (it asks for host name etc.) So say my user name was whirdle, and the password for the dyndns account was lake (which it is not), where would that go?  and would SassWebs.selfip.com be the `host`, or is that my server- and not sure what my server name is, maybe localhost. Also, how to enter port 80 in my router, port forwarding
[http://i34.photobucket.com/albums/d104/thortess/Screenshot-1-1.png](http://i34.photobucket.com/albums/d104/thortess/Screenshot-1-1.png)
[http://i34.photobucket.com/albums/d104/thortess/Screenshot-DynDNScom-MyAccount--MyS.png](http://i34.photobucket.com/albums/d104/thortess/Screenshot-DynDNScom-MyAccount--MyS.png)
[http://i34.photobucket.com/albums/d104/thortess/Screenshot-1.png](http://i34.photobucket.com/albums/d104/thortess/Screenshot-1.png)
<a href="http://s34.photobucket.com/albums/d104/thortess/?action=view&current=Screenshot-1.png" target="_blank"><img src="http://i34.photobucket.com/albums/d104/thortess/th_Screenshot-1.png" border="0" alt="Photobucket" ></a>

Don`t know if I should do upnp forwardng..or enable anything: <a href="http://s34.photobucket.com/albums/d104/thortess/?action=view&current=screenshot5.png" target="_blank"><img src="http://i34.photobucket.com/albums/d104/thortess/th_screenshot5.png" border="0" alt="Photobucket" ></a>
and what about `Port Triggering`? thanks again

---

### Post by spiderbatdad on 2009-01-14
ServerName sasswebs.selfip.com

On your router Http  80  80  Both <ip on LAN>

Your password at DynDns wont go in any of your config files. It is just for you to access your account with DynDns on their site...for example you can create multiple dynamic names and use apache's virtual hosts to access different home pages or applications...like squirrelmail. Or periodically you may need to login to your account at DynDns.

---

### Post by Lakeside5 on 2009-01-14
Thanks spiderbatdat (what a cool name lol). Makes sense, but in the third screenshot, there is a place for password, and user name, so I was putting the username and password from my DynDns account. Or would I leave that blank? Here is a screenshot of what I did at your suggestion, I also set up ftp so I can ftp my site up there. The ip address of my router is the same as that except it ends in a 1. Not sure if that is the right ip I have there.

---

### Post by Lakeside5 on 2009-01-14
I`m having a problem when I try to enter the info into the router.
I put in (at Applications and Gaming)  the http 80 80 both and click SAVE settings and..it is all blank again. It won`t save the settings, I`ve done this over and over. What could be wrong please?
thanks

---

