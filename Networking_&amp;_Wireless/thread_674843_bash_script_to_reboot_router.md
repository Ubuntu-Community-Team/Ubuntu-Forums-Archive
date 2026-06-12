---
title: "bash script to reboot router"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by PhatBob55 on 2008-01-22
Hi folks

I have been having trouble with my router / isp. I have been asked by tech support to bouce the router a few times a day until they can sort out some line sync issues. Anyway, forgetting about the reasons, as it seems to be helping my internet connection, I want to create a cron job that will reboot the router for me.

I can reboot the router using a telnet session, but I want to create a bash script that I can add to my crontab to reboot it. 

The commands that I need to run from the command line that work are:


curl --basic --user admin:my_secret_password! [http://@192.168.0.2/setup.cgi?todo=debug](http://@192.168.0.2/setup.cgi?todo=debug)  

(this then returns debug enable!

telnet 192.168.0.2

I then get a # prompt, (no user / password authentication.

Issue command 'reboot'. Jobs done.

How can I script this?

Any help is appreciated.

---

### Post by PhatBob55 on 2008-01-22
I have started to have a play with bash scripting and come up with the following code:

```

#!/bin/bash
# Router reboot script
#
# For Netgear DG834 series routers / switches
#
# Bob Wylie 
#

# Define Variables

router_ip=192.168.0.1
username="admin"
password="my_secret_password"
router_url="http://@$router_ip/setup.cgi?todo=debug"
# Set router into debug mode - to enable telnet access

curl --basic --user $username:$password $router_url

# Wait for router
sleep 2

# Start telnet session
(sleep 2; echo "reboot"; sleep 2) | telnet $router_ip

```

Only problem is that it seems a bit hit-or-miss when I run it in cron. My crontab entry is 

```
45 5,10,13,17,19,22,00  * * *   root    /home/bob/reboot.sh
```

(Nothing fancy, just a random selection of hours to reboot at)

Sometimes works, sometimes, doesn't. It's as if the curl command doesn't work, as it gives the same output as it would if there was a space or somthing at the end of the url.

Not really sure, I think I am on the right lines though.

---

### Post by kevdog on 2008-01-22
Could you use wget rather than curl??  Just wondering since I know the two provide a lot of the same functionality.

---

### Post by PhatBob55 on 2008-01-23
I am struggling to get wget to work. It only returns invalid user name, although the details are correct. 

I've tried:
```
wget --user=$username --password=$password $router_url
```
and:
```
wget --http-user=$username --http-password=$password $router_url
```

---

