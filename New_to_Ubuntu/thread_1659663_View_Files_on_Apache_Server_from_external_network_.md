---
title: "View Files on Apache Server from external network - how? :S"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by nitstorm on 2011-01-04
Installed lamp-server on my Ubuntu machine (10.04 Lucid Lynx). My question is how do we get to view the file/files that show up when I type [http://localhost/](http://localhost/) on my address bar in the browser on other computers in another network?

More clear, broken-down version of my question:

I installed lamp-server using the command, tasksel lamp-server . There are two files strings.php and a folder called sandbox. I can view them when I type [http://localhost/](http://localhost/) in the address bar of my browser. I want my friend in another city to view these files and kind of use the things in that folder to share amongst friends. But when they try to put in my ip-address, they can't seem to view the files, they get an error... 

The error is >  A username and password are being requested by [http://ipaddress](http://ipaddress). The site says: "DSL Router"
When they do type in my Ubuntu username and password, it doesn't work, and they are redirected to a page that says >  401 Unauthorized Authorization required.

Question ultimately: How do I make my friends look at the files strings.php & sandbox from an another city??

Thanks for your help and patience.

Cheers!

---

### Post by Verbeck on 2011-01-04
looks like you need to forward the port 80 on your router to your lan ip
whats the router make/model?

---

### Post by nitstorm on 2011-01-04
I have no idea what that means :P Yes, I am a newbie :P  It's a "Beetel 220BXI ADSL2+Modem" (That's what is printed on top of the modem) :P

---

### Post by bodhi.zazen on 2011-01-04
Normally your router acts as a firewall and thus you can not connect to your server from outside.

When you "port forward" you open a connection in that firewall.

See:

[http://portforward.com/](http://portforward.com/)

It appears you have activated connections to your router, the web interface, to the outside, this is not good. IMO you should only be able to connect to your router from your home computer.

Log into your router and configure it =)

---

### Post by nitstorm on 2011-01-04
> **bodhi.zazen said:**
> 
It appears you have activated connections to your router, the web interface, to the outside, this is not good. IMO you should only be able to connect to your router from your home computer.

Log into your router and configure it =)


So should I just let it go? If so, how do I de-activate the connections to my router?? I am totally overwhelmed by this whole networking thing, fascinating, but way too complicated :P

---

### Post by bodhi.zazen on 2011-01-04
> **nitstorm said:**
> So should I just let it go? If so, how do I de-activate the connections to my router?? I am totally overwhelmed by this whole networking thing, fascinating, but way too complicated :P

It is overwhelming at first , keep reading.

Basically you need to log into your router and configure it to allow the connection.

Here is a blog that may help, looks like a similar router =)

[http://blog.prashanthellina.com/2007/12/10/accessing-your-home-computer-from-the-internet/](http://blog.prashanthellina.com/2007/12/10/accessing-your-home-computer-from-the-internet/)

---

### Post by nitstorm on 2011-01-04
Awesome link bodhi :) Will work on it and post back as soon as i do so. Thanks :)

---

### Post by nitstorm on 2011-04-14
And it worked!!!!!!!! Thanks a mil guys. And super-duper thanks bodhi for the super-duper link :D 

Thread Solved! 
Cheers!

---

