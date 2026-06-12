---
title: "Vague error in NX Nomachine"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2008-10-22
I am having an error connection to an NX Server. Here is the error I receive on the client side:
```
Display Type             Session ID                       Options  Depth Screen         Status      Session Name

------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

1077    unix-gnome       4FE3F9CCD851A161F09DF1627E22FEA1 FRD--PSA    32 1280x1024      Suspended   Whatever                     

 

NX> 148 Server capacity: not reached for user: tempdude

NX> 105 Restoresession --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Whatever" --type="unix-gnome" --geometry="1280x994" --fullscreen="1" --client="winnt" --keyboard="pc102\057en_US" --id="4FE3F9CCD851A161F09DF1627E22FEA1" --resize="1"

NX> 596 NX> 596 ERROR: NXNODE Ver. 3.2.0-11  (Error id e2AB1E9)

NX> 596 NX> 596 ERROR: resume session: run commands

NX> 596 NX> 596 ERROR: execution of last command failed

NX> 596 NX> 596 last command: /bin/bash --login -c 'kill -USR2 13945'

NX> 596 NX> 596 exit value: 1

NX> 596 NX> 596 stdout:

NX> 596 NX> 596 stderr: /bin/bash: line 0: kill: (13945) - No such process

NX> 596 NX> 596 init: stdin arguments: user=tempdude,userip=192%2e168%2e1%2e134,uniqueid=4FE3F9CCD851A161F09DF1627E22FEA1,display=1077,images=64M,cache=16M,client=winnt,media=0,backingstore=1,encryption=1,strict=0,clipboard=none,shpix=1,rootless=0,composite=1,session=Whatever,shmem=1,type=unix-gnome,virtualdesktop=1,resize=1,keyboard=pc102%2fen_US,id=4FE3F9CCD851A161F09DF1627E22FEA1,fullscreen=1,geometry=1280x994,link=adsl,render=1,subscriptionid=None,productid=LFE,balance_host=192%2e168%2e1%2e123,encryption_mode=3,connection=local

NX> 280 Exiting on signal: 15
```

I went through the NX site but did not find anything.


Any ideas on what to do from here?

---

### Post by styg on 2009-02-04
I had the same problem after power failure.

Simple stop and start the nx server:

sudo /etc/init.d/nxserver stop

sudo /etc/init.d/nxserver start

This resolved the problem of mine.

Hope this helps.

---

### Post by hugoheden on 2009-02-16
Another solution is running

**```
sudo /usr/NX/bin/nxserver --history clear
```**

Not sure if that has pretty much the same as restarting the server, though a bit nicer if others are currently logged in..?

See 

**```
/usr/NX/bin/nxserver --help
```**

for more information.

Regards

Hugo Heden

---

