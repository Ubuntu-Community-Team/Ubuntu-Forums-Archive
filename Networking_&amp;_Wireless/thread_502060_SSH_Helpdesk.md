---
title: "SSH Helpdesk"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by uber_n00ber on 2007-07-16
I guess my question is kind of network related, and to prove I searched the forums before-hand, I did find this thread that is along the lines of what I am wanting to do, but not quite:

[http://ubuntuforums.org/showthread.php?t=5012](http://ubuntuforums.org/showthread.php?t=5012)

(Edit: I guess I copied the wrong forum link, the above link is not the one I remember!)

I have installed Feisty on my parent's laptop (dual-booting with XP) and I want to move them completely over to Ubuntu so I can cut down on my support requests from them ;). They are currently on dial-up which has been a complete pain-in-the-*** to try and get going (blame winmodems) but I think I have finally convinced them to get broadband.

In order for me to admin their computer, I'm thinking I'll set-up ssh-server on their laptop, but since they'll be accessing the net with a router that has a changing public IP address, how can I find out the IP to SSH to?

Now, I don't know much about linux, so feel free to laugh at me if my thinking is pure fantasy, but is there a way for me to set up a script or something that automatically runs when an Internet connection is found? Could it email, or instant message me the IP address? What security considerations should I be aware of?

As I said, I don't know if this is possible, and even if it is, this may or may not be a good way to do it. Let me know If there is a better way to achieve what I'm trying to do.

So, to recap:[LIST=1]
[*]I want to help out the parents.
[*]SSH and port-forwarding on the router can be setup.
[*]??? (How do I get their IP address)
[*]Profit![/LIST]

---

### Post by tonym on 2007-07-16
Google for Dynamic DNS

---

### Post by McNils on 2007-07-16
My idea is to create a script that uses wget (curl or wathever) to query the router for the public ipaddress. This should work if the router supports it.

---

### Post by uber_n00ber on 2007-07-16
Thanks for the idea about Dynamic DNS. For other people and completeness:

[http://en.wikipedia.org/wiki/Dynamic_DNS](http://en.wikipedia.org/wiki/Dynamic_DNS)

I didn't think of this approach since they won't be using a domain name. After a bit of digging I found a list of Dynamic DNS clients here that I might be able to use/modify:

[http://freedns.afraid.org/scripts/freedns.clients.php](http://freedns.afraid.org/scripts/freedns.clients.php)

---

### Post by uber_n00ber on 2007-07-16
> **McNils said:**
> My idea is to create a script that uses wget (curl or wathever) to query the router for the public ipaddress. This should work if the router supports it.

Another good idea! I think I have enough now to work on for a while, thanks for the ideas. I'll post back later if I get stuck ;)

---

### Post by uber_n00ber on 2007-08-11
Okay, I finally had a bit of time to have a go at this, so I've dived into my first bash script :)

I'm not sure how this forum handles long posts, so I might break it up, I've named the following queryRouter.sh. I've commented the script pretty heavily, both for my own and others benefit. Hopefully somebody else might be able to adapt it for use with their own router.

Obviously, since this is my **very first** attempt at scripting with Linux, please excuse any newbie programming errors ;) Any corrections or suggestions are welcome.

```
#!/bin/bash

# Script to extract the public/WAN address from a router
# Tested with a D-Link DSL-502T
# Firmware Version :  V3.00B01T01.TX.20060517
# requires curl

# Set some variables
routerUsername=xxxxx
routerPassword=xxxxx
routerStatusPage=http://10.1.1.1/cgi-bin/webcm?getpage=../html/status/deviceinfofile.htm
routerPOSTVariables="getpage=../html/status/deviceinfofile.htm&var:mycon=connection0&var:conid=encaps0"
routerHTML="$HOME/routerip/routerHTML.txt"
routerIPAddresses="$HOME/routerip/routerIPAddresses.txt"
routerIP=unknown

# Get the HTML page from the web management interface for the router
# -s: to suppress the progress meter from curl (just for formatting)
# -d: to pass POSTed form variables from the referring page
# -u: to pass HTTP authentication as a username:password pair
# -o: to output to a text file
curl -s -d $routerPOSTVariables -u $routerUsername:$routerPassword $routerStatusPage -o "$routerHTML"

# Since my router contains two IP addresses on the status page (LAN & WAN),
# use grep to search for the text "IP Address" in the HTML
# -n: to add line numbers (for debugging purposes)
# -a: used because my router returned a binary "text" file with curl (I think it was using an unrecognized charset)
# -A 4: to print the following 4 lines after the target text
grep -n -a -A 4 "IP Address" $routerHTML > $routerIPAddresses

# Use egrep for a regular expression to match an IP address (999.999.999.)
# (I know IP addresses are in the 0-255 range, but 0-999 serves for my purposes)
# Since I am only interested in the last address (WAN), the output of egrep
# is piped to tail to only show the last line
routerIP=$(egrep "([0-9]{1,3}\.){3}" $routerIPAddresses | tail -n 1)

# To further refine it (remove the leading line numbers, spaces and tabs),
# the line is sub-stringed from position 7 to the end of the line.
routerIP=${routerIP:7}

# Show the IP!
echo $routerIP
```

---

### Post by uber_n00ber on 2007-08-11
Now that I have a method of extracting the public IP address from the router, the next step is to email it to myself. Since I have access to some PHP hosting, I set up a page that expects a password (I don't want to be spammed by somebody if they just browse to the page!) and the IP address. If the password matches, an email is sent off with the IP address. Also, since this script will be running as a cron job every minute, I want to cache the IP and only have an email if it changes.

(I guess I could send an email directly from Ubuntu, but I didn't investigate if sending mail is something built-in and I want to keep my parent's computer with as little going on as possible.)

The following is called getIP.sh. This and the previous file are located in a folder called routerip in the users home directory, but you can change the variables to put it anywhere you want.

```
#!/bin/bash

cacheFile="$HOME/routerip/ipAddressCache"
queryRouterFile="$HOME/routerip/queryRouter.sh"
mailURL="http://some.domain.com/index.php?password=xxxxx&ip="

if [ $(cat $cacheFile) ]; then
	echo "Cache found"
else
	echo "Cache not found"
	echo "None" > $cacheFile
fi

cacheIP=$(cat $cacheFile)
routerIP=$(exec $queryRouterFile)

echo "cacheIP:  $cacheIP"
echo "routerIP: $routerIP"

if [ $cacheIP = $routerIP ]; then
	echo "Router IP address matches the cache"
else
	echo "Router IP address does not match the cache"
	
	# Update the cache
	echo $routerIP > $cacheFile
	
	# Send it to me
	curl "$mailURL$routerIP"
fi
```

---

### Post by uber_n00ber on 2007-08-11
Finally, I set this up as a cron job (type "crontab -e" from a terminal).

```
* * * * * /home/xxxxx/routerip/getIP.sh > /home/xxxxx/routerip/cronOutput
```

For monitoring purposes I wrote the output from the cron job to a file. One "gotcha" that got me: use absolute paths with cron!

That's it, I hope someone else can modify it for their own setup.

---

