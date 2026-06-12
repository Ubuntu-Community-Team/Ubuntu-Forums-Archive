---
title: "background internet access"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by LeafOnTheWind on 2010-06-30
I noticed that the activity lights on my wifi router were going off, so I checked my system monitor, and noticed that I was downloading between 5 and 15 KiB/s. I didn't have the internet up, and wasn't running anything that should be connecting to the internet. Is this normal? If not, what can I do to stop it?

I am running Ubuntu Lucid on a EeePC 1005ha

---

### Post by mikewhatever on 2010-06-30
Are you saying your internet connection was disconnected, but the System Monitor still showed network activity? Use 'sudo netstat -a' to investigate.

---

### Post by LeafOnTheWind on 2010-07-01
Oops. Sorry, let me clarify. My wifi connection was on, but the browser was not open, no downloads were running, online games, etc. I didn't see anything in the process list that looked like it would be the culprit. Hope this helps, I am new to the whole Linux based OS, been running windows for the majority of my life.

---

### Post by mikewhatever on 2010-07-01
Well, if you want people to look at what's going on, post the output of **sudo netstat -tunp**

---

### Post by LeafOnTheWind on 2010-07-01
Well, its not doing it as bad as it was before, peaking a 2 KiB/s

Here is the output that you wanted to see

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.1.5:43589       72.14.204.99:80         TIME_WAIT   -               
tcp        0      0 192.168.1.5:43723       91.189.94.12:80         TIME_WAIT   -               
tcp        0      0 192.168.1.5:40306       72.14.204.102:80        TIME_WAIT

---

### Post by warfacegod on 2010-07-01
I think your computer is just periodically talking to your router. My laptop does the same thing. It's no huge deal. If you were seeing speeds of 200 Kb, for example, then that would be cause for concern. Actually at that point it might be okay to go ahead and panic.

---

### Post by LeafOnTheWind on 2010-07-01
K. I live at home with my parents, and my Dad was the one who was flipping about it, so I was trying to figure out what it was to appease him.

Another question,would the output of sudo netstat -tunap help too?
I accidentally typed that in instead, and it gave me a list of what is currently accessing the network. 

What are these, and do they need to be running?


Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1016/cupsd      
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      842/mysqld      
tcp        1      0 192.168.1.5:35347       95.156.208.72:80        CLOSE_WAIT  2004/gvfsd-http 
tcp6       0      0 ::1:631                 :::*                    LISTEN      1016/cupsd      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1541/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           713/avahi-daemon: r
udp        0      0 0.0.0.0:50082           0.0.0.0:*                           713/avahi-daemon: r

---

### Post by warfacegod on 2010-07-01
That stuff looks normal to me. Grant you my knowledge in this area is limited.

Have your Dad take a look at the Network Monitor on what I am willing to bet is his Windows machine. I'm also willing to bet that his machine is doing the same thing. If it is then tell him I said he can stop freaking out.

---

### Post by LeafOnTheWind on 2010-07-02
K. I seems kinda odd to me that it would talk to the router every few seconds, but this isnt my forte either.

Thanks for the help, guess I'll mark this thread as solved.

---

### Post by theozzlives on 2010-07-02
All my computers do the same. The HD light will flash once and awhile on my Windows 7 box and I see both network and HD activity on my Linux boxes.

---

