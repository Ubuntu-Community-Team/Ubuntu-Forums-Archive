---
title: "SSH over http protocol"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by FolkeY on 2008-11-26
I'm siting here in school and cant access my server from here over SSH. After further investigation about the network here i can only use http and https.

So my question is, can i get SSH to work over the http or https protocol?

Also, it's didn't work having SSH to work on port 80 or any other port. I will have to force it to use http/https probably with a proxy isn't this right?

Thanks in advise.

FolkeY

---

### Post by SpaceTeddy on 2008-11-26
not entirely... for http yes - you do have to use the http protocol, as a proxy can check what you are doing. 

https is a different issue. Since this is an encrypted protocol, the server cannot check what is being sent (that would kind of defeat the purpose of an encrypted protocoll if anybody inbetween could read what is being sent) - it can only check that stuff is sent that is encrypted. Since both, https and ssh are based on SSL/TLS the connection look the same from the proxies point of view. There the SSL/TLS Handshake (this the proxy can see and check for) and then there is an encrypted connection that the proxy cannot inspect. 
So, in other words - if you reconfigure your ssh server to listen on tcp port 443, you can use ssh from school. should not be a problem.

hope it helps :)

---

### Post by mrjerryk on 2008-11-26
use Ajaxterm.  I run it so I can SSH from work.  It works great.

[https://help.ubuntu.com/community/AjaxTerm](https://help.ubuntu.com/community/AjaxTerm)

---

### Post by FolkeY on 2008-11-26
> **SpaceTeddy said:**
> So, in other words - if you reconfigure your ssh server to listen on tcp port 443, you can use ssh from school. should not be a problem.


> **mrjerryk said:**
> use Ajaxterm.  I run it so I can SSH from work.  It works great.

[https://help.ubuntu.com/community/AjaxTerm](https://help.ubuntu.com/community/AjaxTerm)


Thanks guys, i will try this next week when iam back in school (holidays). Will give you a update then.

---

### Post by FolkeY on 2008-12-01
Update:

It worked to add the line Port 443 to the server. I would like to thanks you guys for the help :popcorn:

---

### Post by MarkoCro on 2011-03-21
Hi. AjaxTerm is slow and ugly. What I use is [Shell In A Box]("http://code.google.com/p/shellinabox/"). Here is my howto for setting it up on Ubuntu with https and HTTP authentication:

[http://www.techytalk.info/remote-cli-access-to-ubuntu-pc-using-web-browser-through-authenticated-https/]("http://www.techytalk.info/remote-cli-access-to-ubuntu-pc-using-web-browser-through-authenticated-https/")

Cheers!

---

