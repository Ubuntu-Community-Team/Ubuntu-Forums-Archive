---
title: "Wireless doesn't automatically reconnect on restart or after shutdown in edgy"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by tedrogers on 2006-11-08
I've been battling with getting my Linksys WPC54G v3 pcmcia card working with my Linksys WRT54G v5 router using WPA2 encryption in Edgy.

With the help from this fabulous community I was able to get it working, particularly a user called wieman01 (big up dude!).

However, I've also come across another problem which is if I shutdown or restart the laptop then wlan0 isn't automatically reconnected. I've worked out that if I run...

```
sudo /etc/init.d/networking restart
```

...then this fixes things and my network is up and running. 

However, the trouble is while this is fine for me, for other people who use this laptop, mainly my partner, it is not so good as the terminal would scare the pants off her! I don't think I can realistically expect her to start issuing commands in the terminal...if you catch my drift. ;) 

So, I tried adding the above line into my STARTUP PROGRAMS in System > Preferences > Sessions....but this didn't do any good. I wondered how I might enter my login password to satisfy the sudo command, and I thought as I logged in it might pass my login password onto the startup programs if required, but it obviously didn't or something else stopped it.

So, have you any suggestions on how I might get this command to run automatically on login? Perhaps a script or something? 

I admit I know very little about scripts at this stage, but considering I've only been using Linux in it's various forms for a couple of months and got round all the wireless problems, editing my /etc/network/interfaces file, battling with ndiswrapper etc - I don't think I'm doing too bad so far.

But please be a little gentle with me!

Thanks everyone.

---

### Post by tedrogers on 2006-11-09
It's ok now....**wieman** came through for me again and this is what was suggested...working perfectly for me. So I hope this helps someone else who might encounter this thread.

_Create startup script:_

```
cd /etc/init.d/
sudo gedit wireless-network.sh
```

_Add 1 line & save file:_

```
/etc/init.d/networking restart
```

_Change permission (executable):_

```
sudo chmod +x wireless-network.sh
```

_Create symbolic link:_

```
cd /etc/rcS.d/
sudo ln -s /etc/init.d/wireless-network.sh S40wireless-network
```

---

### Post by omarino on 2006-11-21
Helped me to, thanks

---

### Post by tedrogers on 2006-11-21
Not bad for your 1st bean!

Glad it helped, although credit goes to Wieman01 for helping me out when I had this problem.

Welcome to the forum...where everyone is friendly and helpful.

---

### Post by karmapolice on 2006-11-21
I'm having the exact same problem as stated in the original post. When I boot, the wireless network isn't working, however if I run:

> sudo /etc/init.d/networking restart

Everything works just dandy. I created the startup script described here, but unfortunately that doesn't seem to work for me. Any ideas on what I can check?

Thanks!

---

### Post by tedrogers on 2006-11-22
Did you follow all of the sections above, including adding the line into **gedit wireless-network.sh** as described, changing permissions, creating the symbolic link and so forth?

Also on the last line you could try replacing S40 for a different value instead, like this (where you should replace '??' with a numerical value, e.g. 45):

```
sudo ln -s /etc/init.d/wireless-network.sh S**??**wireless-network
```

I have heard that this is sometimes necessary on certain machines (but don't quote me on that - I'm learning too and I don't know enough about the boot sequence to tell you exactly what this number should be!)

Although this page [http://www.linux.com/article.pl?sid=04/06/23/1734235](http://www.linux.com/article.pl?sid=04/06/23/1734235) suggests that the value could be S45 where it displays the boot sequence values as:

```
S10sysklogd       S20ppp          S99gpm
S12kerneld        S25netstd_nfs   S99httpd
S15netstd_init    S30netstd_misc  S99rmnologin
S18netbase        S45pcmcia       S99sshd
S20acct           S89atd
S20logoutd        S89cron
```

Here you can see that S45 is the sequence number that is assigned to starting your PCMCIA wireless card.

I suppose you could even try a range of values from S40 up to S88 - what's to lose as long as you put it back if it doesn't work? And you may even find that some value between S40 and S50 will do the trick.

Failing that, go back to the original thread (created by Wieman01) and post there as he is the guy who helped me get it working.

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

Sorry I couldn't be more helpful.

---

