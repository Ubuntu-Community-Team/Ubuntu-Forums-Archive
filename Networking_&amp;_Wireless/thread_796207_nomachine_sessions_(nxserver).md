---
title: "nomachine sessions (nxserver)"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by MemoryDump on 2008-05-16
hi all,

I'm trying to connect to my hardy box using my nxclient and I'm getting this error message this morning:

```
NX> 203 NXSSH running with pid: 536
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 127.0.0.1 on port: 2222
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-7 - LFE
NX> 105 Hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: memdmp
NX> 102 Password: ********
NX> 103 Welcome to: chaos user: memdmp
NX> 105 Listsession --user="memdmp" --status="suspended\054running" --geometry="1600x1200x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
1025    unix-gnome       6C2B67E28AD86354EB4B34CA90586C1A -RD--PSA    32 1280x1024      Suspended   nx1                           

NX> 148 Server capacity: not reached for user: memdmp
NX> 105 Restoresession --link="adsl" --backingstore="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="nx1" --type="unix-gnome" --geometry="1280x1024" --client="winnt" --keyboard="pc102\057en_US" --id="6C2B67E28AD86354EB4B34CA90586C1A" --resize="1" 
NX> 596 NX> 596 ERROR: NXNODE Ver. 3.2.0-5  (Error id e891792)
NX> 596 NX> 596 ERROR: resume session: make commands
NX> 596 NX> 596 ERROR: NXNODE: ERROR: cannot get property monitor.pid for session 'chaos-1025-6C2B67E28AD86354EB4B34CA90586C1A'.
NX> 596 NX> 596 init: stdin arguments: user=memdmp,userip=192%2e168%2e30%2e1,uniqueid=6C2B67E28AD86354EB4B34CA90586C1A,display=1025,images=64M,cache=16M,client=winnt,media=0,backingstore=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=nx1,shmem=1,type=unix-gnome,virtualdesktop=1,resize=1,id=6C2B67E28AD86354EB4B34CA90586C1A,keyboard=pc102%2fen_US,geometry=1280x1024,link=adsl,render=1,subscriptionid=None,productid=LFE,balance_host=192%2e168%2e30%2e5,balance_host_realip=192%2e168%2e30%2e5,encryption_mode=1,connection=local
NX> 280 Exiting on signal: 15

```
this has been working flawlessly and only started today :(
I deleted both .nx folders on my linuxbox and windowsbox running the client.

any ideas?

---

### Post by MemoryDump on 2008-05-16
even thought I tried restarting the nxserver manually I ended up having to reboot the system completetly to bring it back to life. Kinda lame

---

### Post by alexsid on 2008-09-29
I met the same problem after my remote host hanged because of hardware failure, I had to reboot it.

Session info is stored at /usr/NX/var/db. There were files in running/ subdirectory, after purging then I was able to connect.

Cheers,
Alex

---

### Post by bwestover on 2009-10-01
I had to hard reset my machine the other day, and I had NX sessions running.
After that, I got the error above even after rebooting.

Removing the files in that directory fixed me up! Thanks alot.

---

### Post by phanter on 2010-03-01
GREAT !! Thanks a lot this solve my problem all the way!!! Thanks again!!!! :D :D :D

And other thing, thought i'm using Fedora Core 10 this actually works too!!

!!! \\:D/

---

