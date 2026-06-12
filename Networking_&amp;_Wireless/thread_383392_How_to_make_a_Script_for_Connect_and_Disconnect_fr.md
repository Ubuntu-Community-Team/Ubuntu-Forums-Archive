---
title: "How to make a Script for Connect and Disconnect from Internet???"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by metaltux on 2007-03-13
Hi... I have a question...

How I can do a Script to Connect and Disconnect from internet, using eth0...

I have two Script, one for connect and the other for diconnect...

```
Connect.sh:

pon dsl-provider 

------------------------- * ----------------------
```
```
Disconnect.sh

poff -a

------------------------- * ----------------------
```
How can I unify this???

Please help me...

Regards... :)

---

### Post by apjone on 2007-03-13
this should help

```

#!/bin/bash
#Variable - if eth0 is connected returns 1 else returns 0
status=`ifconfig | grep eth0 | wc -l`
#Get UID
id=`id -u`
#Check to ensure uid is 0 (super user / root)
#If not quit
if [ $id != 0 ]; then
        echo "This script must be run as root"
        exit 1
fi
#Is eth0 up ?
if [ $status == 1 ]; then
  #if eth0 is up
  ifdown eth0
  exit 0
else
  #if eth0 is down
  ifup eth0
  exit 0
fi

```

---

### Post by metaltux on 2007-03-13
Thank you...

I do a Script with the commands you give me, but it don't work...

Wath is wrong???

Please help me... I'm new on this...

---

### Post by apjone on 2007-03-13
```

#!/bin/bash
#Variable - if eth0 is connected returns 1 else returns 0
status=`ifconfig | grep eth0 | wc -l`
#Get UID
id=`id -u`
#Check to ensure uid is 0 (super user / root)
#If not quit
if [ $id != 0 ]; then
        echo "This script must be run as root"
        exit 1
fi
#Is eth0 up ?
if [ $status = 1 ]; then
  #if eth0 is up
  ifdown eth0
  echo "eth0 Disconnected"
  exit 0
else
  #if eth0 is down
  ifup eth0
  echo "eth0 connected"
  exit 0
fi

```


Had one to many = signs in the second if statement.

This script just connects and disconnects eth0

---

