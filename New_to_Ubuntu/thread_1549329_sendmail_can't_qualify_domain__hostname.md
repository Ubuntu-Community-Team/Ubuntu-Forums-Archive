---
title: "sendmail can't qualify domain / hostname"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by Rumpletumbler on 2010-08-09
How do I tell sendmail my hostname?

the command &quot;hostname&quot; gives me my hostname
the command &quot;domainname&quot; gives me none but I'm a stand alone desktop

I'm getting quite a few errors in the logs over this. 

/etc/hosts has

127.0.0.1 localhost

What's the best program for reading root mail? I don't want to setup Thunderbird or Evolution to do this unless there's some compelling reason to do so. edit: going to use mutt. 

Thanks.

edit: Don't know why the devil (thumbs down) icon showed up here. I didn't put it there.

edit: when running newaliases I get local host name (hostname) is not qualified; see cf/README: WHO AM I? and this says [http://www.sendmail.org/m4/whoami.html](http://www.sendmail.org/m4/whoami.html) 

Final Edit: Fixed it by putting a period on the end of the hostname in /etc/hosts

---

