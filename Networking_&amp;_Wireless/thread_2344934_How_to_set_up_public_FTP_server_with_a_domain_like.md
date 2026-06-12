---
title: "How to set up public FTP server with a domain like ftp.example.com"
date: 2016-11-29
forum: Networking &amp; Wireless
---

### Post by sebastiaan5 on 2016-11-29
Hello,

First of all I know this way is not secure, I already have vsftpd and ssh. The main reason why I ask this is because I can't find it on google (as deep as I searched) and it would look nice to have a public ftp server. My main question is that I don't know how to set up an FTP domain, do I need to register this with a third party? Or can this be done freely? As a sub question which ftp-server package should I install for this?

Greetings

---

### Post by slickymaster on 2016-11-29
*Thread moved to **Networking & Wireless**.*

---

### Post by TheFu on 2016-11-29
If people use IPs and your ISP doesn't care, then you don't have to register with anyone.

**Anonymous FTP** has all sorts of subtle security issues.  All the popular FTP servers have had back doors introduced previously and ran that way for months without anyone knowing.  Bad guys on the internet will locate an anonymous FTP server and use it to trade files - all sorts of files - some are likely illegal to have in your location.  I would rather NOT have the FBI come to my home because I ran an anonymous FTP server ... just sayin'.  Running this server on a cheap VPS will still get the FBI to show up at my door, BTW.  

Anyway, I'm not your Dad, do what you want, but be prepared for the legal repercussions.  
[https://help.ubuntu.com/lts/serverguide/ftp-server.html](https://help.ubuntu.com/lts/serverguide/ftp-server.html)
[https://www.digitalocean.com/community/tutorials/how-to-set-up-vsftpd-for-anonymous-downloads-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-vsftpd-for-anonymous-downloads-on-ubuntu-16-04)

If you want people to access the site using a name, there are 2 ways to accomplish this.
a) tell them the static IP and have them put that into their own /etc/hosts file.
b) use normal internet standards of a domain registrar, DNS, and run the FTP server (or any other service you like).  

These are specific to having a website, but just replace web server (apache/nginx/litehttp) with FTP server. Same steps apply. 
** [http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site](http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site)

So you'll need a DNS provider and will need to setup CNAME and A records.  Nothing hard about that.

---

### Post by sebastiaan5 on 2016-11-29
Thank you for your answer.

It all depends on your configuration, security hardening and so on in my honest opinion. No, I don't have cheap VPS, I have a very high standard about security, I have real hardware servers which are very secure. But what I want to experiment with is an open FTP server (public).

---

### Post by TheFu on 2016-11-29
The code used for the service has the most impact on security. All software has bugs. Some known, some unknown, some known only to the underbelly of the internet.  Also, the hardware used really doesn't matter, unless it allows other back doors like IPMI connections too.  I assume everything can be hacked and work from that assumption.  

Open FTP is the same as "anonymous FTP".  That is the answer provided above. Using a public name, means paying a registrar and DNS provider and possibly hosting provider.  Sorry if that wasn't clear above.

---

### Post by sebastiaan5 on 2016-11-29
I completely follow you, everything can be hacked, everything has bugs, NSA is watching us, Ebiometrics is a fact. I am not being sarcastic. You can always patch (or think you've patched it) , there is however no patch to human stupidity which is a totally different thing but it's relevant to say in this context (and this is mostly the case in hacks/backdoors).

 But what about sites like [http://ftp.gnu.org/](http://ftp.gnu.org/) ftp.kernel.org and so on, they must be secure? Yes I know the can be hacked and they have been, but having a public ftp is really handy don't you think?


Sorry for my stupidity around anonymous FTP and open FTP I was confused for no reason.

---

### Post by TheFu on 2016-11-29
If I want to allow anonymous uploads, I don't use plain FTP.  I use a webserver and move the uploaded files somewhere else immediately.  Never use the same domainname for both upload and downloads. If the uploads are media (pictures/audio/video), then always transcode them to remove unwanted/undesirable additions.  [https://en.wikipedia.org/wiki/Same-origin_policy](https://en.wikipedia.org/wiki/Same-origin_policy)

Allowing downloads is very different from allowing uploads on FTP.  But if you just want to share stuff, using a webserver is easier to secure than FTP because firewall rules for HTTP/HTTPS traffic are easier.  FTP data uses a nearly random port that has to be opened at all the firewalls along the way.  Using passive FTP means plain HTTP would be similar.

Plus the likelihood that someone will accidentally enter their normal password over a non-encrypted channel makes me avoid plain FTP.

Just sayin'.

I've run a few public services and have for 20+ yrs now.  I do not run plain FTP and haven't since around 1999. sftp OTOH, I use almost daily, but only with authenticated logins.

There is no patch for human stupidity and sometimes the dumbest things are what we do.  I usually do something dumb every day. ;)

---

### Post by sebastiaan5 on 2016-11-29
Thanks again, great advice. I really appreciate your posts on this forum :)

---

