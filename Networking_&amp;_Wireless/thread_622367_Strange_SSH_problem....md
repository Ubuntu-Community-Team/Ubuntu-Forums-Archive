---
title: "Strange SSH problem..."
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by bigbob6383 on 2007-11-24
well I'm trying to simply SSH into my website "site.org" but can't ever get it to work.
I can use PuTTY or WinSCP on my Windows partition and it works fine, but on either of my Linux partitions I give it the command and nothing happens.

I'm sure none of my commands are wrong or anything so I have no idea what's going on...
I mean this is what I put in the terminal:
```
~$ ssh user@site.org
```

I was looking around for some solutions, but mine seems a little more out of the ordinary than the issues I've seen.

I hope you guys can help - thanks

___________________________________________________________________________________________________________________
**SUM UP OF EVERYTHING**

Okay, so here's the sum up of everything:
- No computers on my network can connect to the SSH/FTP site
- All computers on my network can connect to any other SSH or FTP site
- My friend has gotten his SSH to the site to work without any issues at all

---

### Post by dmizer on 2007-11-24
do you have firestarter installed on your linux partitions?

---

### Post by bigbob6383 on 2007-11-25
> do you have firestarter installed on your linux partitions?

not that i know of - i just installed ubuntu yesterday so i didn't install it. But if it comes preinstalled then maybe.. but wouldn't that only be important if it was installed on the server computer???

**[POSSIBLY IMPORTANT]** y'know, i forgot to mention that the first time i tried to SSH into the site via Linux (with the SSH wizard or whatever in a LiveCD of BackTrack2) it actually worked, but then every time after that that i tried, it would just completely stall like it still does even though i've tried it the exact same way...
Did it mysteriously learn to reject communication from Linux or what?!?!? i'm so confused:confused:

---

### Post by raghav_p on 2007-11-25
Could you try ssh'ing with the '-v' option on? i.e.:

```

$ ssh -v user@site.org

```

---

### Post by bigbob6383 on 2007-11-25
-v option didn't work...

it's gotta be something with the server. i'll have to check it out on friday when i can talk to the guys that *do* have access to it...:?

---

### Post by raghav_p on 2007-11-25
Sorry, I should have been more specific. The '-v' option tells SSH to give you more detail about what exactly it is doing. So, I would use the -v option and post everything that SSH tells you here. That may help decipher what exactly is going on.

---

### Post by bigbob6383 on 2007-11-25
oh.....okay....
well here ya go:

```
$ ssh -v user@site.org
OpenSSH_4.6p1 Debian-5build1, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to site.org [199.xxx.xxx.xxx] port 22.
debug1: connect to address 199.xxx.xxx.xxx port 22: Connection timed out
ssh: connect to host site.org port 22: Connection timed out
```

---

### Post by bigbob6383 on 2007-11-25
hey! i think i figured out the problem!

the terminal resolves the IP of the "site.org" to a different site ("site.net") which does *not* have an SSH, thus causing it to not be able to ever connect!

But does anyone have any ideas on how i could resolve this issue?

---

### Post by LinuxGuy1234 on 2007-11-25
> **bigbob6383 said:**
> oh.....okay....
well here ya go:

```
$ ssh -v user@site.org
OpenSSH_4.6p1 Debian-5build1, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to site.org [199.xxx.xxx.xxx] port 22.
debug1: connect to address 199.xxx.xxx.xxx port 22: Connection timed out
ssh: connect to host site.org port 22: Connection timed out
```

> 
Connection timed out


That's the error. I've sshed to it:
```

$ ssh -v user@site.org
OpenSSH_4.2p1 Debian-7ubuntu3, OpenSSL 0.9.8a 11 Oct 2005
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to site.org [65.254.50.130] port 22.
debug1: Connection established.
debug1: identity file ~/.ssh/identity type -1
debug1: identity file ~/.ssh/id_rsa type -1
debug1: identity file ~/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host

```

Now it connects... but the connection closes.

---

### Post by bigbob6383 on 2007-11-25
uhhhh LinuxGuy1234 what are you trying to say?
i can't really understand the point you're trying to make...
I realize the problem is that it's timing out - it's because there is no SSH server on the IP it's trying to connect to (my problem exactly (see above)) and it keeps trying to connect for a couple minutes until it times out.

---

### Post by bigbob6383 on 2007-11-25
actually sorry - i just tried it in windows (i havent been on it in a while :)) and it turns out it doesn't work there either...

and the worst part is, is that i just told my friend to try on his computer (since he also has an account on the SSH) and it worked for him!

so i thought maybe i'd have to change some of my router settings, but they all look fine! I don't know what to do :cry::cry::cry:

**UPDATE:** I also tried to connect from another computer from my network behind the router and it didn't work so it's definitely got something to do with the router...

___________________________________________________________________________________________________________________
**SUM UP OF EVERYTHING**

Okay, so here's the sum up of everything:
- No computers on my network can connect to the SSH/FTP site
- All computers on my network can connect to any other SSH or FTP site
- My friend has gotten his SSH to the site to work without any issues at all

---

### Post by dmizer on 2007-11-25
are you trying to ssh into your site from within your own network?

example:
- both your site server and the ssh computer are connected to the same router
and
- you use the command "ssh [email]user@mysite.com[/email]" to ssh to your box, instead of "ssh user@serverip"

---

### Post by bigbob6383 on 2007-11-25
> are you trying to ssh into your site from within your own network?

no, i'm not trying to connect to something in my own network. It's on the web...
(see my "SUM UP OF EVERYTHING" above for all the info)

---

### Post by dmizer on 2007-11-25
just double checking.  it's true you said:

> - No computers on my network can connect to the SSH/FTP site

but i was not certain if the ssh/ftp site was on your local network or not.

try rebooting your router.  just turn off your computers, unplug the power to the router, plug the power back in, wait for the router to boot, and turn the comptuers back on.  this /may/ fix your problem.

otherwise, post the make, model, and hardware version of your router.

---

### Post by bigbob6383 on 2007-11-27
sorry for the late reply, but anyway.....

i have a Linksys WRT54G with Firmware Version: v1.00.4 (i haven't ever upgraded it - nor have i really ever done anything to my router except port forward some stuff)

now i'm beginning to think, though, that there's actually something banning me from the server (not that i've done anything O:)), and when i can talk to the guys with physical access to the server on Friday, i'll be sure to ask them about it.
--I'm thinking my IP's been blocked, because my entire network cannot connect - that all is behind the same IP, so in the meantime i'll just have to suffer with no SSH :cry:

**UPDATE:** Yeah, this is definitely it because I tried connecting with my laptop at school and everything went fine... oh well. One more day till Friday...

---

### Post by cherry316316 on 2007-11-29
where can I find my ip address, I use the wireless network provided to me by my college.
when I do
“ifconfig”
I get
eth1 inet addr:10.XXX.XXX.XXX
and
lo inet addr:XXX.XXX.XXX.XXX

now from remote, when I try
ssh @10.XXX.XXX.XXX
its refuse to except my password.

also, from the other blog, i edited /etc/ssh/sshd_config file and I added line
AllowUsers

but its still not working. which IP address I am suppose to use.
also, when I open a website, which gives IP address, it shows my IP address as
127.XXX.XXX.XXX
which is different from 10.XXX.XXX.XXX which i get using “ifconfig”

I logged into my college network from ssh'ing from my linux and then i tried to log back to my computer using ssh and this is the outpu
```

 ssh -v cherry@10.XXX.XXX.XXX
OpenSSH_3.4p1, SSH protocols 1.5/2.0, OpenSSL 0x009060df
debug1: Reading configuration data /software/etc/ssh_config
debug1: Rhosts Authentication disabled, originating port will not be trusted.
debug1: ssh_connect: needpriv 0
debug1: Connecting to 10.XXX.XXX.XXX [10.XXX.XXX.XXX] port 22.


```

Thanks

---

### Post by bigbob6383 on 2007-12-04
Alright I really have no idea what happened, but after like 2 weeks or something it finally works again.
I forgot to talk to the server guys, but it just started working again... so, y'know i'm not complaining.

oh well, whatever :roll:

---

