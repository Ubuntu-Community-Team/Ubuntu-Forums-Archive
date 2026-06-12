---
title: "server edition - remotely administrating the server"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by anewguy on 2009-01-12
I dived into a simple server using the server edition a few weeks ago.  When I installed it asked if I wanted to manage with Landscape - so I said yes.  Today I was trying to figure out how to use Landscape when I found you have to purchase support to get it.  So, I've been using putty but would really like some form of graphical interface I can access remotely to make sure it is kept up to date (I assume things like apt-get update and apt-get upgrade ???).  I would prefer if it was some sort of web based utility, and very preferably free of charge.

Can anyone tell me of a product or 2 that might "fit the bill"?

Thanks in advance!

Dave :)

---

### Post by whoop on 2009-01-12
use webmin

---

### Post by Dr Small on 2009-01-12
> **whoop said:**
> use webmin
I second the motion for Webmin.

---

### Post by Iowan on 2009-01-12
**ebox** is another option, but [this]("http://ubuntuforums.org/showpost.php?p=6539405&postcount=4") post suggests it may have problems with Intrepid.

---

### Post by yknivag on 2009-01-13
Webmin is the way forward, imho.

There are instructions on the webmin site for adding their repository to apt too so that it updates with everything else.

---

### Post by anewguy on 2009-01-13
Thanks everyone!  I'll check out webmin!

Thanks again!
Dave :)

---

### Post by anewguy on 2009-01-13
Hey guys!  That works great!  Just what I was looking for!

Thanks again!

Dave :)

---

### Post by handydan918 on 2009-01-13
Putty?! 
Only if you are "adminning" from a windows box. 
ssh will give you full access to the command line, as well as allowing you to forward X if it is running...

I fail to see the attraction to all these weird third party solutions when it's all in the repos...

---

### Post by hyper_ch on 2009-01-14
I'd advise against using webmin for the moment. Get yourself confortable administrating the server from the cli. Once you master that, look at things like webmin.

---

### Post by blackened on 2009-01-14
> **hyper_ch said:**
> I'd advise against using webmin for the moment. Get yourself confortable administrating the server from the cli. Once you master that, look at things like webmin.

+1

You'll definitely benefit by learning to administrate the server via commandline. It's much more efficient than trying to accomplish the same tasks via a GUI, and sometimes it's the only way to do some things.

As far as updating packages, apt-get or aptitude are all you really need.

---

### Post by anewguy on 2009-01-15
I *think* ( and that hurts!! :) ) that I can probably handle the command line stuff ok - it's more a matter of starting from scratch on a simple server and trying to grow it and hence learn more in order to do so.  Since things have been running okay with the server, I just finished installing apache, mysql and php5, as I seem to remember have a lamp server was supposed to be a good idea.  Where I'm at right now is that I needed to do a lot of research to find out how to configure and use them.  I'm comfortable using the command line, it's just that right now I don't even really know what to do anyway. :)

Webmin works good for the other things I need to look at the server for.

Thanks again!  I'm sure I probably have some more posts later as I try to learn more about the server MySql and PHP.  MySql  I do have some experience in from the Windows side, but will need to learn the Linux side.  PHP - well, all I know about it at this time is that it is supposed to allow a more dynamic web site, and includes using CSS (which I also have no experience with).  I've done plenty of web sites on my own with just an editor and a good understanding of html, but CSS, PHP - that's all completely new to me.

So you see, I have a LOT of research to do on my own just to try learn more on these and try using them.

Dave :)

---

