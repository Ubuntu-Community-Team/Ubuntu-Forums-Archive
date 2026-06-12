---
title: "Telnet Scrpting tool"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by rajeshgovindan on 2007-05-08
I have D-Link DSL-502T Router.....I need to reboot my router using a telnet script
I used Telnet Scripting Tool (in Windows) [[URL="http://www.winsite.com/bin/Info?500000000873"]Download]("http://www.winsite.com/bin/Info?500000000873")[/URL]

First in the Terminal....typing "telnet"....I provide my IP( i.e 192.168.1.1)...then my login_id of my router and then my password...then I type "reboot" to reboot my router....

But the problem is that i need to automate this process at a preset time.....

how is this possible........

Plz. help

P.S I used this script in Windows

```
192.168.1.1 23
WAIT "login"
SEND "login_id\m" (enter your login ID here)
WAIT "Password"
SEND "login_pass\m" (enter your password here)
WAIT "#"
SEND "reboot\m"
WAIT "#"

```

---

### Post by hozefa on 2007-06-20
PART 1 : Making The Script

1. Make a file with the script below. Enter yourlogin and yourpassword. Save to DSLReboot.sh

```
#!/bin/sh
  (
    sleep 5
    echo "yourlogin"
    sleep 5
    echo "yourpassword"
    sleep 5
    echo "reboot"
    sleep 5
    echo "^d"
   ) | telnet 192.168.1.1 23
```

2. Make this file executable

```
chmod +x DSLReboot.sh
```

3. Run the script
```
 ./DSLReboot.sh
```

Note: Each step takes place in 5 secs so wait a bit when you run. You can lower/increase the sleep time if you'd like.

PART 2 : SCHEDULING THE SCRIPT

4. Installing the scheduler. 
From the menu choose Applications>Add/Remove
Make sure you select Show : ALL AVAILABLE APPLICATIONS
Search for Schedule and install it

5. Schedule will get installed in Applications>System Tools. Configuring it is fairly straightforward. 

6.For Recurrence used advanced and fill in minutes and hours only if you wish to schedule for daily occurrence.

---

