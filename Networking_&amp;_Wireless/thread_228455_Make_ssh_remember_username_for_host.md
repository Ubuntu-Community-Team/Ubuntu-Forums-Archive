---
title: "Make ssh remember username for host"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by witboy on 2006-08-03
Hi,

How do I make ssh remember my username for a specific host?

My specific problem is that at home I use Ubuntu with my username *witboy*. I use ssh to access my uni's unix server *uniserver.host* with another username, lets say *uni_user*. I also use ssh to access my website provider's server *webserver.host* with username *websiter_user*. Whenever I want to access my uni I do:
```
ssh uni_user@uniserver.host
```
And when I want to access my webserver I do:
```
ssh website_user@webserver.host
```
If I would have the same username at home, at uni and on the webserver, I could just use, without the username:
```
ssh [webserver.host or uniserver.host]
```
Unfortunately this is impossible, so my question is if I can somehow make ssh _remember_ my username for each webserver, so that I only have to use the above command without the username?

If not, could I get around it by using aliases or something?

---

### Post by witboy on 2006-08-04
Just so you know, I found a way to do it:
As I'm using tcsh I simply used the **complete** command to save a completion for ssh where a certain username was directly associated with a server.

W x

---

### Post by ape on 2006-08-04
An easier way to do this is to add a 'Host' entry in your ~/.ssh/config file.  You would add a host specific entry for the hosts that you want to use a different username as.  Within this host section Just add the 'User' keyword with that hosts username as the value.  You will then connect in as that user everytime you attempt to connect to that host.

See 'man ssh_config' for more information.

---

### Post by harisund on 2006-08-04
[http://ubuntuforums.org/showpost.php?p=1193100&postcount=2](http://ubuntuforums.org/showpost.php?p=1193100&postcount=2)

---

