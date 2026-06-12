---
title: "MRTG: need help for install and config"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by couzin2000 on 2008-06-14
I have been looking for a way to monitor the amount of data I transfer on a monthly basis (see thread _[http://ubuntuforums.org/showthread.php?t=817047]("http://ubuntuforums.org/showthread.php?t=817047")_). The reason for this is because I am capped at 100Gbs up/down combined, and I wanna make sure that every month I don't go overboard with downloading.

In my previous thread (above), someone recommended that I use Nagios. Managed to install the whole thing, works like a charm. But when I got to monitoring router traffic, I saw that Nagios needed to run with [MRTG]("http://oss.oetiker.ch/mrtg/doc/mrtg-unix-guide.en.html"). So I went ahead and took a look at what the documentation said. _I can't understand a word of this_. The Nagios instructions were step-by-step, the best I've seen. So I tried looking inside Synaptic and found the [FONT="Courier New"]mrtg[/FONT] packages. Downloaded, installed all is good, but I don't even know where to start using it: not sure if the daemon is running, not sure how to access the graph, how to configure the cfg file (or where it is for that matter).

If anyone has MRTG running on Hardy, please either point me to the right thread or post the documentation here. I would be very greatful!

---

### Post by couzin2000 on 2008-07-04
I found this file going on about MRTG, in a Debian help site: [http://www.debianhelp.co.uk/mrtg.htm]("http://www.debianhelp.co.uk/mrtg.htm"). This seems to be the best help for me right now.

There are a few snafus I've encountered. In the text I read as follows:
> Now you need to restart the snmp service

#/etc/init.d/snmpd restart

The configuration file creating using

#cfgmaker public@localhost > /etc/mrtg.cfg

Creating a configuration file for a device using

#cfgmaker public@192.168.0.1 >> /etc/mrtg.cfg

With the configuration file created correctly there's only one other thing you have to do and that's to use the indexmaker utility to create the summary home page. Since you have to re-run this command every time you make certain changes to the /etc/mrtg.cfg configuration file,

Creating index file for the webserver using

#indexmaker /etc/mrtg.cfg > /var/www/mrtg/index.html

Now you need to reboot your system wait for five minutes or so and then take a look at your summary home page. If your Debian system's IP address is 172.16.0.20 then you'd type in the following in the address bar of a browser running on a system on the same network:

[http://172.16.0.20/mrtg/](http://172.16.0.20/mrtg/)

Your summary home page should come up with a graph for each target entry in the configuration file. If a graph looks like there's no data on it, click on it and check the statistics to see if any traffic is being seen. Small amounts of traffic won't show up on the graphs because we used the Unscaled statement 

So I've tried creating a config file by typing in ```
sudo cfgmaker public@localhost > /etc/mrtg.cfg
```yet I get the answer > bash: /etc/mrtg.cfg: Permission denied.
I also tried the next line:```
sudo cfgmaker public@192.168.0.1 >> /etc/mrtg.cfg
```with the same results.
Last I tried creating the index with the line```
sudo indexmaker /etc/mrtg.cfg > /var/www/mrtg/index.html
```and still the same error message.

I am sudo'ing into all these commands, so why am I locked out? Is it because the daemon is running and locked down the files I call up?

Those are the last steps into configuring everything I need - once I'm done with this I can monitor the router traffic and tie it in with Nagios. Someone please help!

---

### Post by couzin2000 on 2008-07-09
Anybody?

---

### Post by toorima on 2008-07-21
not sure if you solved it or not but if not do
sudo bash 
and then run the commands

---

### Post by alynx on 2008-08-18
How did this go , im also gonna start up with a mrtg project atm and im gonna try the link you posted earlier in this thread if that works

---

### Post by alynx on 2008-08-18
> **toorima said:**
> not sure if you solved it or not but if not do
sudo bash 
and then run the commands

This is correct , and i got it up and running i no time when i tried it.  Thanks alot mate. :popcorn:

---

### Post by Captain Colonoscopy on 2008-09-09
I am also trying to get this working. When I past in the 

> cat /etc/cron.d/mrtg 0-55/5 * * * * root if [ -x /usr/bin/mrtg ] && [ -r /etc/mrtg.cfg ]; then env LANG=C /usr/bin/mrtg /etc/mrtg.cfg >> /var/log/mrtg/mrtg.log 2>&1; fi

to the console I get:

> bash: syntax error near unexpected token `then'

I tried doing the "sudo bash" thingy and I gots no love.

Anyone trying this at all? Got any ideas. I had MRTG running on an Ubuntu box about a year ago. Need to get it running on a new box that is also running NAGIOS successfully.

Thanks.


 [[IMG]http://www.hardfolding.com/ftag1.php/mem/148779.png[/IMG]](http://www.hardfolding.com?go=38&id=148779)

---

### Post by alynx on 2008-10-03
Hi

I got a new "problem" at hand.

I dont want every single site to be shown in the localhost/mrtg when i view them in my browser.

I tried to make a new folder home/***/mrtg and put all my mrtg.conf files in there.  This means site1.cfg site2.cfg site3.cfg and so on.

then i made indexmaker for all the new cfg files and that works out aswell.  The problem is that the cron job is set to do /etc/mrtg.cfg.   DO i have to make a cron job on every single cfg file ?  Or is it any easier way to do this ?

Thanks in advance
Alynx

---

### Post by mrtg.saitove.info on 2008-11-04
yes, you have to make different cron jobs for every cfg file.

---

### Post by alynx on 2008-11-04
hi

The case was solved this way 

[http://ubuntuforums.org/showthread.php?t=936782](http://ubuntuforums.org/showthread.php?t=936782)

---

