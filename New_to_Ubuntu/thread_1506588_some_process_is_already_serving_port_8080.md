---
title: "some process is already serving port 8080"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by 007casper on 2010-06-10
How do you find and kill multiple process on ports?

I got Tomcat Java server port issues. I have installed Tomcat Java server over a year ago.  I have updated from 9.04, to 9.10, then 10.04

the server used to work when I was on 9.04 flawlessly.  Now, after updating to 10.04, I get... 
> 
java.net.BindException: Address already in use

The app I am using is bundled with tomcat, and the server set up is tomcat java server.  After fixing, jdk issues.  I found out that it has to do with port issues.

It comes out that this is usually in regards to improper app shutdown, or multiple launches close to each other that hangs ports, or having more than one Tomcat process running at a time.


I shutdown the server, and tried again.  Same problem.


The only thing I can think of is that Tomcat Java server is taking over the port.  However, I cant locate it, so there isnt anyway to kill the process.

I tried> 
netstat -anp | grep 8080
unix 3 [ ] STREAM CONNECTED 8080 1464/bonobo-activat

I am not sure what that is... and it doesnt seem like it is running any process.

Same server set up used to work on 9.04... 

Please, advise.  Thank you.

---

### Post by tom.swartz07 on 2010-06-10
This is a little bit out of my area of expertise, but I know for a fact that port 8080 is reserved for http requests, almost like an alternate port for a web browser.
Perhaps you were running a web browser at the time, and traffic was being routed through there?

---

### Post by 007casper on 2010-06-10
you are right.  I did have the browser open.  It will be great if that is the issue.  I am going to try without having the browser open. 

I am not in front of the server right now.  I need to list all the possible solutions, so I can trouble shoot at one shot.

However, when I looked around online, it seems it is usually due to running multiple insances of tomcat.  I wonder if this is the problem for me, because I am running a tomcat java server, and the app I am running is bundled with tomcat.
ref> 
[http://java-monitor.com/forum/archive/index.php/t-22.html](http://java-monitor.com/forum/archive/index.php/t-22.html)

just in case, how can I kill all the ports?  And then restart the ports?

I wonder if disabling the network adapter, and then enabling help. 

please, advise.  Thank you.

---

### Post by 007casper on 2010-06-10
what is the proper way to disable network adapter, and then enable it again from the terminal?... or kill all ports, and then make them live again.

I guess I can do netstat -a on the terminal, and find a port that isnt being used, and give the free port number to the app.  However, since it worked before without a problem, I would like to kill ports, and relaunch it.

Please, advise. Thank you so much.

---

### Post by 007casper on 2010-06-10
***bump***

any proper way to disable, and enable ports, or network adapter?

thank you.

---

### Post by 007casper on 2010-06-11
in the logs I saw that pulseaudio was blocking my app to start.  It will state module-x11-xsmp.c: module-x11-xsmp may no be loaded twice

I try to kill -9 pid

it kept moving around.  Finally I removed pulseaudio from synaptic.  I checked again, it still have a process running.  Then kill it again from system monitor.  Checked via terminal, it was still alive.  Killed it through root kill -9 5026, then it seemed like it worked. Exit root.  Then, I was moving around to the app, and the server froze.  Turn off server. Turn on server.

I tried to launch my app.  Still the same message 

> java.net.BindException: Address already in use 

netstat -anp | grep 8080
unix 3 [] STREAM CONNECTED 8080 1492/bonobo-activat

I cant find bonobo-activat anywhere.  Is it part of pulseaudio?  Why pulseaudio is taking over port 8080?

please, advise.  Thank you so much.

---

### Post by 007casper on 2010-06-11
after reboot... reinstall pulseaudio.  I dont need pulseaudio, however, I cant seem to find what the problem is... 

I looked at system monitor it is giving -11 on Nice level for pulseaudio.  It has higher priority than other processes. Zero (0) is normal. Why is on -11?

please, advise.

---

### Post by gmargo on 2010-06-11
Use "sudo lsof -i :8080" to find who has that port open.

---

### Post by 007casper on 2010-06-11
I am going to check who has that port open.  I am not in front of the server right now.  Thanks for that command.

I was wondering what is the difference between these three different commands?
sudo netstat -nlp
netstat -paln
sudo netstat -lp

and what is bonobo-activat?

I am trying to locate all the ports.  I want to make sure it isnt some security issue.

thank you.

---

### Post by gmargo on 2010-06-11
You are misinterpreting the output of netstat.  "8080" in this case is the inode number of a Unix domain socket.

Try something like "sudo netstat -anlptu" to only see TCP and UDP Internet domain entries.  See the netstat(8) man page for more info.

If you look at the full output of netstat (instead of using grep) you will see the two tables (internet-domain and unix-domain) and the column headers for each table.

---

