---
title: "Failing to start squid htttp proxy"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by asianman on 2009-06-20
Hey,

I am trying to start the squid proxy that I made using this guide: [http://ubuntu-tutorials.com/2009/06/18/create-anonymous-squid-proxy-for-iranian-election-protestors/](http://ubuntu-tutorials.com/2009/06/18/create-anonymous-squid-proxy-for-iranian-election-protestors/)

I have followed all of the steps just as they say it in this guide. I have never used squid before so this issue isn't some sort of interference with another squid program.

I have been able to do everything fine up until the very last command which comes back as this when I copy and paste:

colin@colin-laptop:~$ sudo /etc/init.d/squid start
[sudo] password for colin: 
 * Starting Squid HTTP proxy squid                                       [fail] 
colin@colin-laptop:~$ 

and this when I type it in manually:

colin@colin-laptop:~$ sudo /ect/init.d/squid start
sudo password for colin:
sudo: /ect/init.d/squid: command not found

I go to where the file is located and I see that it is there. When I double click on it or choose any of the different ways to open it such as run in terminal and just plain run nothing happens at all.

I am running Ubuntu Jaunty

If you need more information on the computer settings or something just tell me how to do it and I will get it to you.
All help will be much appreciated!
Thanks.

---

### Post by spillin_dylan on 2009-06-20
Well I'm no squid expert, but when you're typing it in manually, make sure you have the path correct.  In your example you have "/etc/" versus "/ect/".  Maybe it's just a typo, but it could be worth noting.

---

### Post by asianman on 2009-06-20
Fixed it by stopping all of my programs and stuff and restarting. Everything works fine now!

---

