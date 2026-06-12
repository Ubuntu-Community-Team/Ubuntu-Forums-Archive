---
title: "Anonymous login proftpd"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by maksym on 2007-04-02
Hi,

have setup a proftpd ftp server on my ubuntu 6.10 using a basic config from the tutorial here on ubuntu forums. So far so good. The basic purpose of the server is to be used by anonymous users. In the config file I have put "anonymous" alias for the ftpuser I have set up in my ubuntu system. However proftpd will not accept just any password from anonymous, since every user in linux has to have a password.

Now how do I make proftpd accept ANY password from anonymous users.
Sorry if this a stupid question but I am realative new to linux..
Thank you!

---

### Post by dmizer on 2007-04-02
well my first reaction to this is ...

if you're not familiar enough with linux to be able to set up an anonymous ftp server, you probably shouldn't be setting up an anonymous ftp server.  because unless you know exactly what to look for and what to watch out for, and what log files to look at, and how to analyze the log data, and are willing to invest the time it takes to pour through and properly analyze the logs ... you're going to end up with a hacked system.

you don't indicate what howto you used, but i'm assuming it is the one in my sig.  if that's the case, i suggest starting off with a password protected ftp server (as outlined in the howto).  then hand out id's and very secure passwords to people you trust for accessing your server.

one of the easiest ways to hack into any computer (even including linux) is through a poorly configured ftp server account.  because of this, (depending on up time) your ftp server can get hundreds of probes daily even if you change the port.

---

### Post by maksym on 2007-04-02
thanks for the comment, dmizer.

I actually used this tutorial:
[http://www.ubuntuforums.org/showthread.php?t=79588](http://www.ubuntuforums.org/showthread.php?t=79588)
would be thankful if you could point me to yours as well. I used the first I stumbled upon.

You are right, now I do not know exactly where all the log files are, etc. I am going to find out. just wanted to have a quick setup and open a test ftp first before I start securing it. 

What exactly do you mean by hacking? I had Serv-U ftp server running under windows 2k for anonymous users. It ran for about a year and nothing bad happened (fortunately). 

My understanding was that as long as I lock the user in a given directory and give "read only" privileges - I should be fine. What can a "bad guy" do then?

---

