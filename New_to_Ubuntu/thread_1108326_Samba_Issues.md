---
title: "Samba Issues"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by dvdhaar on 2009-03-27
Hi there,

I'm having some troubles with samba. I basicly followed this guide:
[http://tech.waltco.biz/2008/01/26/private-and-guest-no-password-prompt-samba-shares-with-securityuser/](http://tech.waltco.biz/2008/01/26/private-and-guest-no-password-prompt-samba-shares-with-securityuser/)
and it works like a dream. 

But.. If I want to watch a movie or DVD through samba via a windows pc it's really slow and it has hiccups so to speak. I don't have this issue on my other ubuntu pc, works fine there. Both on XP and Vista machines it is very slow, browsing through folders is OK... but watching a movie is just not doable.

I've done alot of research and noticed it is quite a commen problem, some people suggest editing the registry of windows. Others suggest tweaking the smb.conf file ( [http://ogre.ikratko.com/archives/347](http://ogre.ikratko.com/archives/347) ), and I have tried both but I keep having troubles. Currently reading through the smb.conf man pages, but its HUGE! 

Server is running Ubuntu 8.10
HTPC is running XP MCE
Laptop is running Vista SP1
Virtualbox machine is running XP SP3

An other issue I have is that there are a number of folders (which i've recently copied over) which show up strange over samba. Locally they have their regular name, but when you're browsing through samba they look like this:

CRNAV4~1
HQY9GD~7
etc..

Hope there's somebody who can help, I'll keep on searching in the meantime

Thanks in advance,

---

### Post by cariboo on 2009-03-29
I was seriously considering going to another distribution because of slow file transfer speeds in Hardy, but in Intrepid it got a little better, and in  Juanty I now get 70-80Mbps transfer rates. I would suggest testing you transfer speeds on your internal network by using a utlity called iperf. I perf is in the repositories. Install it on your server and on your desktop, there is a windows version [here]("http://www.noc.ucf.edu/Tools/Iperf/").

The windows version and the linux version both have to run from the command line.

On your server at the prompt type:

```
iperf -s
```

then on your window computer go to Start-->Run and type cmd and hit enter, this will open a dos window. At the prompt type:

```
iperf -c <servername>
```

See the screenshots for the results. BTW my windows installation is running in VirtualBox so the result are of a bit.

Jim

---

### Post by dvdhaar on 2009-03-29
Thanks for your reply, I appreciate it :)
Very cool program!

Here are the results:

```
daniel@server:~$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.100 port 5001 connected with 192.168.1.70 port 49186
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  23.9 MBytes  20.1 Mbits/sec
[  5] local 192.168.1.100 port 5001 connected with 192.168.1.70 port 49187
[  5]  0.0-10.0 sec  23.8 MBytes  20.0 Mbits/sec
[  4] local 192.168.1.100 port 5001 connected with 192.168.1.71 port 34025
[  4]  0.0-10.1 sec    114 MBytes  94.3 Mbits/sec
[  5] local 192.168.1.100 port 5001 connected with 192.168.1.71 port 41449
[  5]  0.0-10.1 sec    114 MBytes  94.4 Mbits/sec
[  4] local 192.168.1.100 port 5001 connected with 192.168.1.76 port 1095
[  4]  0.0-10.0 sec    110 MBytes  92.2 Mbits/sec
[  5] local 192.168.1.100 port 5001 connected with 192.168.1.76 port 1096
[  5]  0.0-10.0 sec    110 MBytes  92.2 Mbits/sec
[  4] local 192.168.1.100 port 5001 connected with 192.168.1.70 port 1053
[  4]  0.0-10.0 sec  72.1 MBytes  60.6 Mbits/sec
[  5] local 192.168.1.100 port 5001 connected with 192.168.1.70 port 1054
[  5]  0.0-10.0 sec  72.1 MBytes  60.6 Mbits/sec

```

The first two lines are from my Vista notebook (Wireless N)
The second two lines are from my Ubuntu workstation (100mbps cable)
The third two lines are from my XPP running virtually on my Ubuntu workstation
The fourth two lines are from my HTPC running XP MCE (100mpbs cable)
The fifth two lines are from an XPP notebook (Wireless G)

These two are from a XP machine running SP3 (100mbps cable):

```
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.100 port 5001 connected with 192.168.1.70 port 1243
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  76.1 MBytes  64.0 Mbits/sec
[  5] local 192.168.1.100 port 5001 connected with 192.168.1.70 port 1244
[  5]  0.0-10.0 sec  77.0 MBytes  64.7 Mbits/sec

```

If I recall correctly, 20mbits per second means around 2.5 MB per second right? Shouldn't that be enough to stream a simple avi file? Or even a DVD?

---

### Post by dvdhaar on 2009-03-31
The issue regarding the slow transfer speeds with iperf is due to the fact that I have two routers. Since one router isn't good enough to cover the whole house with wireless, I've hooked up another one to it. 
Now if both machines are connected to the same router iperf will give me +/- 95 mbit/s. 
Even though I connected one of the XP machines to same router as the server (having +/- 95 mbit/s) I can't seem to stream video without any problems. There are hickups when playing a simple .avi every 20/30 seconds. Browsing through the shared folders in samba is pretty fast.

The strange thing is, I used to share movies with my Ubuntu workstation using the nautilus context menu thingy 'share this 
folder' and that worked great: I was able to stream DVD's from my HTPC (which has 60mbit/s according to iperf). Obviously... because thats more then enough to stream DVDs right?

So what I'll try to do as I come home is to post my current smb.conf. And once again try to share a movie using nautilus, seeing if it works, then checking the smb.conf on that machine.

In the meantime, any tips, hints?!

---

### Post by dvdhaar on 2009-04-07
So far I haven't been successful yet...

Maybe it has to do with the filesystem?
When I used to share files from my NTFS drive there where no problems. Now I'm using ext3.

---

