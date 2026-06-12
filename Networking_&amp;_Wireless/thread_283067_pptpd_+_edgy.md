---
title: "pptpd + edgy?"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by CyberAngel on 2006-10-23
I installed pptpd on an Ubuntu Edgy Server but whe a client tries to connect to it I am getting the following error...

```
Oct 23 23:40:12 trinity pptpd[4541]: CTRL: Client 10.17.111.37 control connection started
Oct 23 23:40:12 trinity pptpd[4541]: CTRL: Starting call (launching pppd, opening GRE)
Oct 23 23:40:12 trinity pppd[4542]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so is for pppd version 2.4.3, this is 2.4.4
Oct 23 23:40:12 trinity pptpd[4541]: GRE: read(fd=6,buffer=8058640,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Oct 23 23:40:12 trinity pptpd[4541]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Oct 23 23:40:12 trinity pptpd[4541]: CTRL: Reaping child PPP[4542]
Oct 23 23:40:12 trinity pptpd[4541]: CTRL: Client 10.17.111.37 control connection finished

```

Any solution?

---

### Post by CyberAngel on 2006-10-24
OK I fixed my problem :KS 

I downloaded the source of pptpd (apt-get source pptpd) and I changed the version of pptpd-logwtmp from 2.4.3 to 2.4.4
After the recompilation everything is working fine!!!

Quick HowTo:
```
cd
sudo apt-get install libwrap0-dev debhelper
sudo apt-get source pptpd
cd pptpd-1.3.0/plugins
sudo vi patchlevel.h
```
And change the line:
```
#define VERSION         "2.4.3"
```
to
```
#define VERSION         "2.4.4"
```
Save the file and do the following
```
cd ../..
sudo apt-get -b source pptpd
sudo dpkg -i pptpd_1.3.0-1ubuntu1_i386.deb
sudo dpkg -i bcrelay_1.3.0-1ubuntu1_i386.deb
```

Finish :D

---

### Post by crblack on 2006-10-27
Wow! I can't tell you how much this post has helped me.  Running a half hour late to work out of frustration dealing with this problem.  I can verify that the instructions above are dead on.  Worked like a charm! Thanks again.

---

### Post by CyberAngel on 2006-10-27
> **crblack said:**
> Wow! I can't tell you how much this post has helped me.  Running a half hour late to work out of frustration dealing with this problem.  I can verify that the instructions above are dead on.  Worked like a charm! Thanks again.

I`m glad that my post was helpful for others too :D 

Also much easier is to download the already compiled (as I described above) by me pptpd-logwtmp.so that I am attaching right now and replace that file on /usr/lib/pptpd/.
I did that so dpkg don`t always prompt me of a package update  ;)

---

### Post by bobyang on 2006-11-11
You are genius, how come you figure it out?

---

### Post by CyberAngel on 2006-11-12
> **bobyang said:**
> You are genius, how come you figure it out?

Thank you, I don`t think that I am that genius but ut was just the moment :D 

```
Oct 23 23:40:12 trinity pppd[4542]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so is for pppd version 2.4.3, this is 2.4.4
```

The above was the error so I downloaded the source, checked it out and changed the version. Compiled it again and it worked!
Probably It would never work if there were other major changes too between the two versions ;-)

---

### Post by snakeman on 2006-12-08
Thanks,
It worked for me also,



snakeman

---

### Post by ElTurkoGrande on 2006-12-13
Worked for me too, with an OSX client talking to a Ubuntu pptpd server.

---

### Post by diablo668 on 2007-03-08
super, couldn't get the damn pptpd working, followed this and worked like magic;

nice work

---

### Post by littletinymonkey on 2007-06-01
Same here... couldn't get it to work, performed this fix -- now it works perfectly.

thanks!

---

### Post by cshabazian on 2007-06-22
Much easier solution....  Simply change the string in the file:

perl -pi -e 's/2.4.3/2.4.4/' /usr/lib/pptpd/pptpd-logwtmp.so

Worked just fine for me.

---

