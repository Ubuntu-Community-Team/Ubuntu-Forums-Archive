---
title: "Dapper Drake (6.06 LTS) aDSL Problem Please Help!!!"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by bulletshot60 on 2007-10-25
Okay I type in ifconfig for eth1 and I receive that my hardware is working.  So thats okay.  Then I type in sudo pppoeconf  and it scans my two interfaces eth0 and eth1.  Eth0 isn't configured so I'm not worried about it.  However, on eth1 which is configured, no access concentrators are found.  Also when configuring the connection via Roaring Penguin PPPoE the connection cannot be established.  All the lights are green on my modem which means there working.  I just cannot use the connection.  Please help if you have any ideas.

Computer:  Compaq
Connection Type: aDSL USB
Modem: Westell 6100
Connection: Eth1
Server:  [http://www.bellsouth.net](http://www.bellsouth.net) (i think) (if I'm wrong this is my probably my problem)

That's all the information I can think of.  If you need any more, I'm glad to give it.  :popcorn:  Thanks in advance.

---

### Post by scrooge_74 on 2007-10-25
Check this thread maybe it will help you

[http://www.ubuntux.org/pppoe-client](http://www.ubuntux.org/pppoe-client)

---

### Post by bulletshot60 on 2007-10-25
Okay the router thing isn't a bad idea, but I can't afford one right now.  I managed to get all of my settings from Windows:

IP 192.168.1.97
DHCP 192.168.1.254
DNS 192.168.1.254

I don't know how much help this can be but I am going to try to insert this into Ubuntu.  If this works, I'll post the steps I used so that if anyone else has this problem mabye it can help them.  If anyone has any other good ideas, please post.  I have no clue if this will work.  You might say I'm grasping at straws.

---

### Post by scrooge_74 on 2007-10-25
in theory, the IP you should not put it in, since it is assign automaticaly by the DHCP server of your provider.

You are suppose to only tell the system to use auto DHCP so it get the broadcast from the servers and gets an IP

As for DNS servers, I always have a bad time using the ones provided by my ISP, so I resort to [Open DNS]("https://www.opendns.com/start") and that way I am sure to get the DNS translation every time

---

### Post by bulletshot60 on 2007-11-03
Ok, the method I had originally tried didn't work.  But I found another method.  First, start the computer using Windows.  Immediately after the Windows Loading screen goes away and the win xp screen is loading.  Hold in the power button until the computer shuts down.  When it is finished, the ethernet light remains on.  Starting the computer allows you to use Ubuntu to access the internet multiple times until you start up using Windows XP.  Then you must reapply the fix.  Hope this helps.

Note:  Only tests 6.06 LTS and up.
Note:  Only tested on Westell 6100.

---

