---
title: "wireless connection works, but only for firefox"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by heroes_on_a_half_shell on 2008-02-25
hey guys,

so i've got a wireless internet connection up and running on my dell inspiron 8100/D-link wireless adapter w/ Ubuntu Gutsy,  everything was working smoothly for a while,  however, a recent issue has arisen where firefox and aptitude can both utilize the connection whereas pidgin and thunderbird cannot.  the problem doesn't exist when i am using a wired connection.  i really dont know where to start. any ideas?

the only other info i can think to include is that i only have access to one wireless source which just so happens to be my university's access and requires login info.  however, i've only been able to connect to the 'guest' accounts which do not require login. i think the frustrating part about this problem is that it appeared and i was unable to associate it with any change i might have made.

thanks

---

### Post by spd106 on 2008-02-25
Does your Uni network require you to use a proxy to connect to the Internet?

If so you'll have to tunnel any non-http traffic through http(s). Most IM clients can do this, but it is protocol dependent. Email will be tricky unless you use an encrypted tunnel such as the one I think Google (gmail) supports. So you're going to have to stick with webmail or perhaps use the Uni provided system.

---

### Post by heroes_on_a_half_shell on 2008-03-11
<bump>

hey guys, i know this is kind of a strange problem but i still can't seem to work around it.  the strange part of it is that all of my programs worked at one time on the university's wireless access.  thunderbird and pidgin being unable to connect is a development.  also, having had the opportunity to use a different (home) wireless connection recently, i now know that this only occurs on the nomad-based system at school.  also, whenever i connect to the university's network via wired connection (resnet system), everything works fine. so i don't think it's a proxy issue. 

thanks in advance

---

### Post by heroes_on_a_half_shell on 2008-03-16
well guys, everything works again.  but i have no idea what fixed it.  thread is closed for now.

for anyone who may be experiencing similar issues - the only thing i did differently is that i took no shortcuts in setting up the wireless connection in the terminal

```
$sudo ifconfig ath0 down
$sudo iwconfig ath0 essid "ncsu"
$sudo ifconfig ath0 up
$sudo dhclient ath0
```

where ath0 is the name for my wireless connection interface and "ncsu" is the ssid for the desired wireless connection.  to have such code run at startup, just add it into your /etc/rc.local file.

```
$gksu gedit /etc/rc.local
```

for a wireless connection, it may also be useful to precede those lines of code with

```
$sudo ifconfig eth0 down
```

this will disable your wired connection. however, if you place this line in your rc.local file, then whenever you decide to use a wired connection again you will have to open a terminal and type

```
$sudo ifconfig eth0 up
```

---

### Post by scottwuzhear on 2008-04-17
I am at NCSU as well, heroes_on_a_half_shell.

The problem is that NCSU blocks all ports, except 80, on the 'ncsu-guest' wireless APs.  The only
way around this is for you to connect to the 'ncsu' AP.  I too have had problems connecting to 'ncsu', and I don't really know why.  Sometimes it works, but mostly it doesn't.  Hope this helped.

-Scott-

---

