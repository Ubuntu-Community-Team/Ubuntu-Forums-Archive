---
title: "Server WoL by Laptop"
date: 2013-12-26
forum: Networking &amp; Wireless
---

### Post by StuartKicks on 2013-12-26
Hi

I was wondering if anyone could point me in the direction of achieving the following.

I have a media server that I would like to be turned on automatically when my girlfriend turns on or opens the lid of her laptop. I've had a google but couldn't find anything useful.  Both computers are visible on the network to each other, both run 13.10 and have statically assigned addresses on the network. 

The media server is wired, laptop is wireless and I WoL works via Android to Server.

Thanks in advance.

---

### Post by sanderj on 2013-12-26
It would help if you would mention what you've found and why you say it's not useful.

My approach would be:
1) create a command to send a manual WoL to your media server (possibly [http://manpages.ubuntu.com/manpages/hardy/man8/etherwake.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/etherwake.8.html) )
2) as soon as that works: make sure that command is issued when you open the lid. Or: as long as the lid is open.

---

### Post by StuartKicks on 2013-12-26
Thanks for the response. I've basically found descriptions of how to construct CLI commands and an app I can install via software centre to manually wake. 

I guess I'm going to have to do some reading up on making scripts.

---

### Post by tgalati4 on 2013-12-27
You can create a script and put it in /etc/pm/sleep.d similar to this:  [http://askubuntu.com/questions/92218/how-to-execute-a-command-after-resume-from-suspend](http://askubuntu.com/questions/92218/how-to-execute-a-command-after-resume-from-suspend)

Install *wakeonlan*; open a terminal:

```
sudo apt-get install wakeonlan
```

Log onto your server and get the hardware MAC addresss:

```
ifconfig
```

Make a script, give it executable privileges and put it in /etc/pm/sleep.d

```
cd /etc/pm/sleep.d
sudo nano 20_Super_Cheesy_Wake-on-Lan_Script.sh
```

Cut and paste:

```
#!/bin/sh
# Super Cheesy script to wake a server during resume
# 
#  Called in triplicate to improve wakeup reliability
case "${1}" in
    resume|thaw)
        wakeonlan 00:00:00:00:00:00
        sleep 2
        wakeonlan 00:00:00:00:00:00
        sleep 2
        wakeonlan 00:00:00:00:00:00
        ;;
esac

```

Control-o (return) Control-x (to exit nano)
Add executable privileges:

```
sudo chmod +x 20_Super_Cheesy_Wake-on-Lan_Script.sh
```

Put your machine to sleep then wake and be amazed.  Change the 00's to your server's actual hardware MAC address.  Keep a large jug of water handy in case there is smoke.

One of these days I will try to implement this, but I'm too lazy to write the script.

Let us know if it works.

---

