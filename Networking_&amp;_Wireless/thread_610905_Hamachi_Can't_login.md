---
title: "Hamachi: Can't login"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by P4VV37 on 2007-11-12
I can't log in to hamachi:

$ sudo modprobe tun
$ sudo tuncfg
tuncfg: already running
$ sudo hamachi start
Starting Hamachi hamachi-lnx-0.9.9.9-20 .. ok
$ sudo hamachi login
Logging in .... failed

upx didn't help me,
I've got Ubuntu GG 7.10, and I've installed hamachi this way:
[http://ubuntuforums.org/showthread.php?t=135036](http://ubuntuforums.org/showthread.php?t=135036)

All I know is that hamachi can't login. I can't find hamachi log files and I don't know what else should I say.

Sorry for my English:)

---

### Post by P4VV37 on 2007-11-14
Bump

---

### Post by khanjal on 2007-11-15
I have this exact some problem. I followed several guides but when I hit the login that is the first thing that fails. I verified all the previous components were installed and working. 

I can get hamachi to login through my other machines (xp & win2k) but not ubuntu. Kinda frustrating but I will keep trying and hopefully someone may respond with some tips.

---

### Post by techno-wiz on 2007-12-05
I'm having the same problem. Able to login from the same network on a XP machine. Hope someone out there can clue us in!

---

### Post by reidman on 2008-02-24
Also having this problem. Two weird things:
[LIST]
[*]I was able to login to hamachi with both my laptop and this machine on my home network, so I know that hamachi works fine.
[*]Now that I'm on a new network, I can't login with this machine. HOWEVER, the really weird thing is that I brought my laptop with me (running XP via Parallels), and it logs into hamachi just fine.
[/LIST]

So this is probably not a network issue or an issue with my hamachi installation...It's gotta be something with Ubuntu, but I can't even figure out where to start. I tried restarting and reinstalling hamachi with no luck. I'm considering doing a reformat.

Anyone have any idea what might be going on? Thanks in advance for your help!

---

### Post by jhetrick62 on 2008-02-24
What do  you guys see when you run an ifconfig?  Is the ham0 interface defined?

Jeff

---

### Post by terenctb on 2008-02-26
Semi new problem? Using Feisty Fawn

I have had hamachi running for a while and then had to reboot the machine (I configured all the scripts to boot properly prior and tested them...

BUT...now hamachi refuses to login...

It used to do exactly what was being done above...

have no luck in running it in debug because nothing appears after I run it...no logs at all

a hamachi login simply fails with no reason given.

The ham0 interface is there, I can ping my VPN ip fine

The thing is that this was working for over 6 months and suddenly it craps out...
Hamachi on Windows still works..

If this doesn't work out...going to be force to reinstall the machine on windows..

---

### Post by tarekeldeeb on 2008-03-02
> **jhetrick62 said:**
> What do  you guys see when you run an ifconfig?  Is the ham0 interface defined?

Jeff

I have the same problem .. but the ham0 interface is not defined .. how can i bring it up ?

Thanks in advance.

---

### Post by venome on 2008-03-04
Not sure if this would help, but I recently came into the same trouble. My hamachi installation was workin all right, for more than a year. Last week, I needed to use hamachi, I ran
sudo tuncfg with elevated privileges, finished all right.
hamachi start ... no response
hamachi login ... no response
hamachi whatever ... no response.

So I installed the[ version that is dedicated to "older computers"]("http://files.hamachi.cc/linux/hamachi-0.9.9.9-20-lnx-pentium.tar.gz") (althought I have pretty recent one), installed (had to copy some crypto library to other location.).

I deleted ~/.hamachi directory
sudo tuncfg
... seemed all right
hamachi-init
... generated keys and all the stuff
hamachi start
... was finally talking to me
hamachi login
... logging in ... > login failed
? strange though, so I googled and so, but none of the solutions was working.
then a tried to run
sudo ifconfig ham0 up
sudo hamachi login
... and there i was, i got logged in. Not sure if this can help any of you, but to me it works and I can replicate it.

---

### Post by Metastable on 2008-05-21
Had this problem, and the problem seems to be with the firewall. Hamachi uses udp for all communication, so you need to make sure that the firewall is configured to allow UDP packets both in and out for the machine that you want to put on the Hamachi network.

The output below is two *consecutive* attempts to login, and the only thing different is that I changed firewall settings to allow UDP packets to my machine.

analytica@shango:/var/run$ sudo hamachi -c /etc/hamachi login
Logging in ....>.... failed
analytica@shango:/var/run$ sudo hamachi -c /etc/hamachi login
Logging in ....>....... ok

Hope this helps.

---

### Post by bippi on 2008-06-26
Ok, so basically what I'm have happening with 8.04 LTS (upgraded from a working 6.10...yeah, pretty far back) is that when I go to login, it just STALLS.  It doesn't error-out on me, it doesn't do anything.

I basically copied a vmware image, generated a new vmware ID so it didn't conflict with my old box.  I boot it up, everything is good.

I initially go, 
>tuncfg 
>hamachi start
>hamachi login
Logging in..

...and there it will hang.

So I generate a new with hamachi-init -f and force a new hamachi ID.

I check my iptables with iptables -l:
Chain INPUT (policy ACCEPT)
target prot opt source            destination

Chain FORWARD (policy ACCEPT)
target prot opt source            destination

Chain OUTPUT (policy ACCEPT)
target prot opt source            destination

upx /usr/bin/hamachi

I try again:
> Hamachi stop
> Hamachi start
Hamachi is already started.
> ifconfig ham0 up
> Hamachi stop
Shutting down .. ok
> Hamachi start
Hamachi is already started.

...and it wants to be a bugger to me.

At any rate, the important thing that I notice here is that hamachi start doesn't seem to be bringing up ham0, or with any semblance of an IP address.

---

