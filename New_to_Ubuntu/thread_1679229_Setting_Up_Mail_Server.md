---
title: "Setting Up Mail Server"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by jrtboht on 2011-01-31
I have a webserver successfully set up using Ubuntu server.  I can get to multiple websites running on the server by going to [www.domainname.com]("http://www.domainname.com").  Now I would like to set up a mail server so that users can log into their mail by going to mail.domainname.com.  First, can I use the same computer for the mail server that is currently running as my webserver (and run both mail and web at the same time).  If so, I'm not sure where to start.  I know I need to install postfix and go through the configuration but it's a bit confusing.

---

### Post by HereInOz on 2011-01-31
You don't mention which version of Ubuntu Server you are using, but I refer you to this excellent server setup guide, put together by Falco.

[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2)

Pretty well covers it all apart from webmail, which I haven't tackled yet.

I have one of these servers running at the moment, and it is all very easy.

One word of warning - if you are going to do the full server setup, with ISPconfig (can make things a lot easier for configuration), do not use any special characters or upper case letters in the MySQL password which you are asked to set during the setup of MYSQL.  Just keep it simple.  

Special characters in the password can prevent ISPConfig from logging in to MySQL, and this pretty much borks the installation, and you will need to start again.

---

