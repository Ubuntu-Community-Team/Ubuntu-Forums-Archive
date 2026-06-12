---
title: "What do I need to accomplish all of this?"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by macmike on 2010-05-11
What I need from someone, customized to my needs, is a list of do this  with these commands, make these directories and etc. Here is what I am  trying to do:


I want to Virtual Name host three sites as follows through my one IP  address:
1. [www.wilmingtoncoc.com](www.wilmingtoncoc.com) - Host as a WordPress site. Use Word press to  put content on it.
2. [www.mikealrhughes.com](www.mikealrhughes.com) - Host by putting files up using some kind of  ftp server by way of Dreamweaver.
3. [www.biblematters.net](www.biblematters.net) - a Mailman mailing list of my closed mailing  list.

Right now my [www.wilmingtoncoc.com](www.wilmingtoncoc.com) is forwarded to my public IP address.  I don't know if that is the way it needs to remain or not. Someone can  tell me that. Also I want to install Webmin to control all of this.  Especially if I want to add another site to the mix in the future. I am  trying to do all of this with Ubuntu 10.04. Also need to know what I  will need to do DNS wise to make it work. I went to Dyndns.com and  couldn't make heads or tails to what I needed from them.  Any help by  anyone appreciated.

Thanks,

Mike Hughes

---

### Post by Bachstelze on 2010-05-11
You will have to make all the domains point to your public IP address in your DNS system. Then you can configure Apache to serve the correct website depending on the URL the user typed in his browser. I can't help you do that in Webmin, though.

---

