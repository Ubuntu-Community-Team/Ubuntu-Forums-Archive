---
title: "remove zeroconf slows system?"
date: 2016-11-10
forum: Networking &amp; Wireless
---

### Post by Kris_M on 2016-11-10
16.04.1

I removed zeroconf with
  	 	 	 	   [FONT=Liberation Mono, monospace][SIZE=2]sudo apt-get remove avahi-autoipd && sudo apt-get autoremove

Now it seems that FF is slower accessing the internet.  Am I imagining things?
[/SIZE][/FONT]

---

### Post by Hadaka on 2016-11-10
Hi removing Avahi was probably not a good idea without noting what other
things depend on it.,,and there are several.
I would advise re-installing it,hopefully from a recent backup. and then to
keep it from running...do..
```
sudo /etc/init.d/avahi-daemon stop
```
Then to prevent Avahi running automatically on start-up modify the /etc/default/avahi-daemon file
```
cd /etc/default
gksudo gedit avahi-daemon
```
*Comment [COLOR=#ff0000]# [/COLOR]out ~OR~ modify, =[COLOR=#ff0000]0 [/COLOR]the line that activates it, as in example below.
*Example
```
* /etc/default$ cat avahi-daemon
# 1 = Try to detect unicast dns servers that serve .local and disable avahi in
# that case, 0 = Don't try to detect .local unicast dns servers, can cause
# troubles on misconfigured networks
[COLOR=#ff0000]#[/COLOR]AVAHI_DAEMON_DETECT_LOCAL=[COLOR=#ff0000]0[/COLOR]
```
Save and close gedit
boot and test.
thanks.

---

### Post by Kris_M on 2016-11-10
> **Hadaka said:**
> Hi removing Avahi was probably not a good idea without noting what other
things depend on it.,,and there are several.
I would advise re-installing it,hopefully from a recent backup. and then to
keep it from running...do..
```
sudo /etc/init.d/avahi-daemon stop
```
Then to prevent Avahi running automatically on start-up modify the /etc/default/avahi-daemon file
```
cd /etc/default
gksudo gedit avahi-daemon
```
*Comment [COLOR=#ff0000]# [/COLOR]out ~OR~ modify, =[COLOR=#ff0000]0 [/COLOR]the line that activates it, as in example below.
*Example
```
* /etc/default$ cat avahi-daemon
# 1 = Try to detect unicast dns servers that serve .local and disable avahi in
# that case, 0 = Don't try to detect .local unicast dns servers, can cause
# troubles on misconfigured networks
[COLOR=#ff0000]#[/COLOR]AVAHI_DAEMON_DETECT_LOCAL=[COLOR=#ff0000]0[/COLOR]
```
Save and close gedit
boot and test.
thanks.

Hi and thanks for your reply, and sorry for the delay in my answering - errands, endless errands, and then researching your answer.

I had done a Clonezilla image so I am currently running avahi.

avahi seems to open a port to the outside. I think.

Behind my router I am invisible (GRC). bypass the router and it sees port 22 though it's closed. I have not done any ftp yet with Ubuntu so haven't dealt with doing that behind the router, but that's another prob for another day. Don't need it at the moment. And that has nothing to do with avahi.

So the question is, what, that I need, depends on avahi.
I did do
sudo /etc/init.d/avahi-daemon stop
but it didn't seem to do anything (I assume that will only work for the current boot.)

I need to close this and do a reboot at the moment so will get back to this.

---

### Post by Kris_M on 2016-11-10
okay, went off and did some stuff.  The port 22 thing is the fault of my new IPS as it appears on both Ubuntu and win7.
I also installed FileZilla and found that FTP up and down works just fine with default and no special rules: (I use GUFW)
```
kris@kris-Z97X-UD3H:~$ sudo ufw status verbose
[sudo] password for kris: 
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip
kris@kris-Z97X-UD3H:~$ 

```

I am also now suspecting that the "slowness" I "felt" was probably due to them playing with their DNS server, and nothing to do with avahi.

In any case, I will keep your suggestions in mind, though at the moment I have avahi at the state before I did anything to it (thank you Clonezilla!).

I will mark this solved as I will wait a week for their DNS server dust to settle before trying anything more.

Thanks again!

---

### Post by Hadaka on 2016-11-10
Hi, glad you have it sorted out !
Smart move on using clonezilla and Thank YOU
for marking your thread Solved.

---

### Post by Kris_M on 2016-11-11
the herring and squid pizza with clam sauce sounds excellent!!!   don't know about the anchovies... :D

---

