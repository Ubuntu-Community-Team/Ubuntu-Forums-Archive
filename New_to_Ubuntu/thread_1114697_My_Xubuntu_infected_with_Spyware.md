---
title: "My Xubuntu infected with Spyware"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by faron45 on 2009-04-03
Okay,I know what they say about Ubuntu & security but,I think it's quite possible that my machine may be compromised with some sort of spyware or something.Does anyone have any suggestions as to how I can go about checking into this ? 

 And,one reason I say this is that I live in a house with a comp.geek & I'm almost positive that he's somehow gotten into my pc somehow.Either manually or remotely.Another reason I say this is the way that my comp. acts sometimes.Sometimes it responds almost as if someone else also has some sort of control over it remotely..And,also,tonight while browsing my hotmail acct.

 I was told that I would have to log back in after only an hour of non use.And,then,it even went so far as to say something to the effect of having  to refresh my browser after signing on on a diffrent computer.What's up with that ???Anybody have any suggestions ? Going to sleew now though.So will check answers tomorrow after work.Thanks all.All help much appreciated.
                Yer pal,Faron45

---

### Post by Sef on 2009-04-03
It's possible that you were hacked.    Read [Intrusion Detection]("http://ubuntuforums.org/showthread.php?t=919472") to find out how to check.

---

### Post by HermanAB on 2009-04-03
The default install of Ubuntu doesn't run any servers.  Therefore, the only way that it can get infected with anything, is if your install it yourself.

So, relax and enjoy your nice secure system.

---

### Post by lisati on 2009-04-03
A good part of computer security is don't leave your computer unattended while you're still logged on if you can help it, otherwise who knows who might sneak in and cause mischief by being nosy.....

---

### Post by kpkeerthi on 2009-04-03
Another easy way to check if you have been compromized is with the 'netstat' utility. 

Just run this command
```
netstat -antp
```
to monitor all connections IN & OUT from you computer.

---

### Post by lakersforce on 2009-04-03
It sounds more like your Hotmail account has been compromised, then your OS.

But if you are really worried that your comp.geek is leet instead of hacker, just do a fresh install, with new passwords.

---

### Post by faron45 on 2009-04-04
I received some great answers from all of you regarding this situation & I appreciate them all.Now,though,I have another question regarding this subject.kpkeerthi suggested 

 I run the netstat utility with the command "netstat -antp".Now,I ran this command.BUT-I don't know what to do with the results [in other words,I don't know exactly what the results are actually saying to me.Can anyone tell me what all this means ? After running the netstat utility this is the information which I received...

 (Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN      -

---

### Post by iponeverything on 2009-04-04
:) If your infected with spyware under linux, it would make for a good story -- As I have using linux since '93 and have never seen or heard about spyware infections under linux.

Your netstat:

Anything listening on 127.0.0.1 is nothing to worry about. It is the loopback device -- the machine uses it to talk to itself.

port 631 is cups (print server)

run "sudo lsof |grep 9050" 
to find the process using 9050.

---

### Post by overdrank on 2009-04-04
Threads merged :)

---

