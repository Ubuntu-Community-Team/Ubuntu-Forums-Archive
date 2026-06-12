---
title: "[SOLVED] how to stop kids knocking at my ssh?"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by kaiju on 2008-07-11
is there anything i could do against script kiddies hanging at the entrance of my ssh server all the time?
i get lots of this:
```

$ sudo lastb -ai -5
walker   ssh:notty    Fri Jul 11 09:57 - 09:57  (00:00)     66.240.222.197
walker   ssh:notty    Fri Jul 11 09:57 - 09:57  (00:00)     66.240.222.197
jonathan ssh:notty    Fri Jul 11 09:57 - 09:57  (00:00)     66.240.222.197
jonathan ssh:notty    Fri Jul 11 09:57 - 09:57  (00:00)     66.240.222.197
jordan   ssh:notty    Fri Jul 11 09:57 - 09:57  (00:00)     66.240.222.197

```

i have 'PermitRootLogin no' and 'MaxAuthTries 0' in my sshd_conf, so i guess the danger isn't really overwhelming, but i still find it very annoying to see all the failed login attempts from all these addresses (there were over 70 in june alone). just some distinct addresses from the output of 'lastb -ai | grep Jun', so you see what i mean:

```

motoka   ssh:notty    Mon Jun 30 20:39 - 20:39  (00:00)     218.106.193.130
mysql    ssh:notty    Sun Jun 29 00:30 - 00:30  (00:00)     193.251.95.129
rares    ssh:notty    Sun Jun 29 00:18 - 00:18  (00:00)     86.121.209.52
root     ssh:notty    Sat Jun 28 22:26 - 22:26  (00:00)     211.43.202.150
linux    ssh:notty    Sat Jun 28 14:03 - 14:03  (00:00)     218.84.26.250
desktop  ssh:notty    Sat Jun 28 05:57 - 05:57  (00:00)     202.51.30.154
root     ssh:notty    Sat Jun 28 02:36 - 02:36  (00:00)     66.113.100.148
aaron    ssh:notty    Thu Jun 26 00:40 - 00:40  (00:00)     220.227.149.90
guest    ssh:notty    Wed Jun 25 03:07 - 03:07  (00:00)     85.5.93.56
admin    ssh:notty    Wed Jun 25 02:58 - 02:58  (00:00)     222.184.14.199
andrew   ssh:notty    Wed Jun 25 01:53 - 01:53  (00:00)     200.27.235.214
root     ssh:notty    Tue Jun 24 21:41 - 21:41  (00:00)     81.200.31.8
root     ssh:notty    Tue Jun 24 21:02 - 21:02  (00:00)     89.111.144.170
sorin    ssh:notty    Tue Jun 24 16:42 - 16:42  (00:00)     86.104.228.111
ftp      ssh:notty    Tue Jun 24 13:56 - 13:56  (00:00)     217.76.44.216

```
i think i have a good password, but with all that trying, who knows? it would really suck to have to set up a password three sentences long...

---

### Post by squaregoldfish on 2008-07-11
I switched the port for ssh to a non-default one, beyond 10000. I haven't had an attempt to break in since.

To change the port, edit /etc/ssh/sshd_config. The first non-comment line should be Port, which you can change to whatever you want. Restart the ssh server, and you're done.

To connect, you'll need to add the -p <port> option to your ssh command.

Steve.

---

### Post by kaiju on 2008-07-12
yeah, you're right, squaregoldfish. changing the port number seems to be the only solution.

the other thing is, i wonder if there's any way to report these break-in attempts. i mean that's what i'm sure anyone would want to do after seeing that someone has tried to pick the lock on their front door...
just a way to make sure the user of the ip will get a warning. from what i've read, most of these attempts could come either from zombie machines (in which case a warning should get the user to do a check and clean it up) or from kids that have nothing better to do (in this case too, it would be useful to remind them that what they're doing is illegal, hopefully before they get themselves into real trouble).

a did some whois checks and even sent an email to the isp of one of the addresses from my region but never got a reply...

any ideas on what could be done?

---

### Post by squaregoldfish on 2008-07-12
I'm not sure that anything can be done, unfortunately.

I have no idea how seriously ISPs take reports of attempted hacking attempts, but I suspect that they won't do anything unless they get lots of reports for a single user. If you choose to keep your SSH on port 22, I would suggest attempted break-ins should still be reported, but you may find that you have better things to do with your time.

Clearly SSH is reasonably secure if you choose good user names and passwords, because a lot of people in the world are happy with it. However, if you're not providing a public service, you might as well make your system that little bit more secure and move the port.

Steve.

---

### Post by mal on 2008-07-12
Another solution is to use an application called denyhosts.  This monitors /var/log/auth.log and locks out any IP addresses that have multiple unsuccessful login attempts.  There are some instructions in the forums to help set this up.

Mal

---

### Post by kaiju on 2008-07-12
i installed denyhosts on arch. it didn't come with a man page, but the config file is pretty self-explanatory anyway. in addition, the default configuration seems to fit my needs very well, so i didn't even tweak anything.
later on i'll probably just change the port the ssh server listens on, but not before configuring my sister's sftp client so that she can connect to my box without having to change settings herself :p

problem solved, i guess. but i still wish i knew what those folks are trying to achieve with all their dictionary attacks (already 12 this month, that's less than two weeks)...

---

### Post by SabreWolfy on 2008-08-11
*lastb* returns nothing on my system. I've done some searching and have set permissions on the *btmp* file to 600. Should failed logins via *ssh* be logged? Why are they not being logged? Any suggestions?

---

### Post by kaiju on 2008-08-11
> **SabreWolfy said:**
> *lastb* returns nothing on my system.

i always run lastb as root (otherwise i get 'lastb: /var/log/btmp: Permission denied'), but it seems you've already solved the permission problem.
does last say anything?

---

### Post by SabreWolfy on 2008-08-12
> **kaiju said:**
> i always run lastb as root (otherwise i get 'lastb: /var/log/btmp: Permission denied'), but it seems you've already solved the permission problem.
does last say anything?

Hi,

Nope, I get the following output whether I run it as root or not. I log out and then "ssh" back in and enter the wrong password three times. I then log in again via "ssh" and run "lastb".

```

btmp begins Tue Aug 12 08:20:27 2008

```

---

### Post by ukjimbow on 2008-08-15
> **SabreWolfy said:**
> Hi,

Nope, I get the following output whether I run it as root or not. I log out and then "ssh" back in and enter the wrong password three times. I then log in again via "ssh" and run "lastb".

```

btmp begins Tue Aug 12 08:20:27 2008

```
[http://thinkhole.org/wp/2006/10/30/five-steps-to-a-more-secure-ssh/](http://thinkhole.org/wp/2006/10/30/five-steps-to-a-more-secure-ssh/)

Here is some great info I found on securing SSH

---

