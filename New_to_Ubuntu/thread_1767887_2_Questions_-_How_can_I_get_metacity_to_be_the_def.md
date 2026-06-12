---
title: "2 Questions - How can I get metacity to be the default on bootup and another thing"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by egervari on 2011-05-26
I always have to press ALT-F2 and type "metacity --replace" whenever I boot into linux. This one is far less buggy than compwiz. How can I tell ubuntu to just do this for me? Since 11.04, compwiz is very buggy as it deletes the minimize/maximize windows randomly over and over. It also prevents me from re-arranging my task window bar at the bottom to my liking :(

My second question is, what is a package for tabbed command like consoles? I like the ubuntu console, but it would be nice to have a tabbed version that I can use for Ruby development, as it's common to use 'Rails server', 'autotest', etc. all at the same time.

Thanks!

---

### Post by matt_symes on 2011-05-26
Hi

Not running Unity today so i am not sure of your first issue.

> 
My second question is, what is a package for tabbed command like  consoles? I like the ubuntu console, but it would be nice to have a  tabbed version that I can use for Ruby development, as it's common to  use 'Rails server', 'autotest', etc. all at the same time.For your second issue, have you considered screen. It not tabbed but it allows you to have multiple pseudo terminal sessions running in one terminal.

```
sudo apt-get install screen
```You start up the terminal and type screen. You then get a welcome message. Hitting <enter> will remove it. 

Pressing ctrl + a together and then c will create a new pseudo terminal session. You can do this a number of times. 

You can switch between the pseudo-terminals by pressing ctrl + a at the same time and a number after.  That number will correspond to the pseudo terminal sessions you want.

screen has a number of very niffty features. It can be used over ssh to have multiple pseudo terminal sessions on one connection. You can detach from the screen session and stop the ssh connection. Later when you reconnect to the computer using ssh, you can reconnect to the screen session and still have all the open processes that you start previously.

Might be worth a look. I use it all the time.

[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)

Kind regards

---

