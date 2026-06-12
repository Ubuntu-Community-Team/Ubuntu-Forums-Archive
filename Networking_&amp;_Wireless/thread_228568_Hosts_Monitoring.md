---
title: "Hosts Monitoring"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by Kurdt on 2006-08-03
Hi, 

What can i use to monitor hosts connectivity on a network? I mean, a program that sends ping packets and when response is not given sends me and email or an alert?

Maybe someone knows it, i am looking for something similar to [Axence nettools]("http://www.axencesoftware.com") but for linux.

This is different to solutions like cacti, because i do not need statistical information, just an email alert if hosts are down.

Maybe you can tell me what do you use :)

Thanks

---

### Post by cantormath on 2006-08-03
> **Kurdt said:**
> Hi, 

What can i use to monitor hosts connectivity on a network? I mean, a program that sends ping packets and when response is not given sends me and email or an alert?

Maybe someone knows it, i am looking for something similar to [Axence nettools]("http://www.axencesoftware.com") but for linux.

This is different to solutions like cacti, because i do not need statistical information, just an email alert if hosts are down.

Maybe you can tell me what do you use :)

Thanks

Hi Kurdt,

Could you restate the question, maybe name some general functionality that you want this program to do.  You want it to email you or not to email you?  Im sure there is something out there that will be to your liking.

---

### Post by cantormath on 2006-08-03
Also,

cacti is in the ubuntu repository

look for it:
laptop:~$ apt-cache search cacti
cacti - Frontend to rrdtool for monitoring systems and services
cacti-cactid - Multi-Threading poller for cacti

you may need to add universe repository if it does not show up.

if you see it, install it.
laptop:~$ sudo apt-cache install cacti cacti-cactid

---

### Post by Kurdt on 2006-08-03
I thought that i was clear, sorry if not, 

this is what i want:

ping host x, if host x is down, send email to desired email address to alert me.

Nothing complex.. I could develop the app myself but maybe some other guy made it before.

Edit: as i said, I DO NOT need cacti, i already have it for statistical purposes.

Thanks

---

### Post by cantormath on 2006-08-03
Sorry,

It was clear, I guess I just wanted more info. Im sure it has been written by someone else.

Have you seen AdventNet Linux Manager
[http://www.cleansofts.com/get/824/44...x_Manager.html](http://www.cleansofts.com/get/824/44...x_Manager.html)
Edit/Delete Message

---

### Post by bdk on 2006-08-07
I had always been a fan of BigBrother ([http://www.bb4.org](http://www.bb4.org)) since it was what I used in my previous career monitoring a network the size of the State of Alaska; oh wait. I **did** use it to monitor hosts & services while working for the State of Alaska, silly me.

All kidding aside I just setup Nagios ([http://www.nagios.org)](http://www.nagios.org)), not as an Ubuntu Package either because only version 1.3 is available when Nagios is available in a stable 2.5 from their website.

I had to totally dump what I knew and my pre-conceived notions (Read: BigBrother) of how to set it up and ran. I read their online manual and was steadfast in getting things setup and running. I've got it testing externally facing services AND a remote daemon that'll check things like hdd size, processes, logs, users, system load, etc and report back to the main display server and this is just on my own network. There are a lot of configuration options and different ways you can setup the config files that the pure over-load of options may seem daunting but if you stick with it, you'll figure it out.

I did initially use BigBrother on my own network years ago but could never really work out the nuances of it. Other things that further convinced me to get away from BigBrother is that they're no longer developing it or adding to it so it has become stale and that it isn't free to use commercially.

We use Nagios at where I work too and it monitors A LOT!

HTH

*-bdk*

---

### Post by RichJacot on 2006-08-08
It sounds like a quick shell script my be your easiest solution, however you may want to take a look at nagios.  I've been using it for years and it is a great application.  From your description though, nagios also sounds like overkill.  (my 2 cents)

---

