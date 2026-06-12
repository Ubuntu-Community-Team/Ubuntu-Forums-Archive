---
title: "[SOLVED] Scripting internet connection"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by Arcnsparc on 2008-09-02
So I have a few scripts that access the internet, but I dont want them to start until the connection has established else they return weird errors.  Here is what I am thinking, but i know its not right...

```
ping  www.webpage.com
if (ping result positive
then
run internet dependent scripts
else
repeat in 10 seconds, x number of times
fi
```

I am just starting to understand the whole coding thing so any pointers are very appreciated!

---

### Post by pytheas22 on 2008-09-02
I think it would work to do something like this:
```

if (ping -c 3 webpage.com)
then sh script1.sh; sh script2.sh; sh script3.sh...
else sleep 10; sh this-script.sh
fi
```

In other words, if the website responds to the ping (it gets three tries), then the dependent scripts get run.  If there's no ping response, then we sleep for ten seconds, then run this script again (so the script calls itself, which is probably the easiest way to do a simple kind of loop like this).

Let me know if this helps.

---

### Post by Arcnsparc on 2008-09-02
```
if (ping -c 3 www.google.com)
then sh /home/jake/Scripts/testresulter.sh
else sleep 10; sh pinger.sh
fi

```

I tried this as I was reading your reply and I am grateful but it doesnt seem to be working.
Via terminal I got this:
```
jake@MultiVAC-2:~$ ping -c 5 www.google.com
PING www.l.google.com (72.14.205.103) 56(84) bytes of data.

--- www.l.google.com ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4020ms

and then for good measure:

PING www.l.google.com (72.14.205.104) 56(84) bytes of data.

--- www.l.google.com ping statistics ---
100 packets transmitted, 0 received, 100% packet loss, time 99166ms


```

I tried this too:
```
jake@MultiVAC-2:~$ ping -c 5 http://www.google.com/
ping: unknown host http://www.google.com/

```

Still stumped...
Thanks for the help!

---

### Post by pytheas22 on 2008-09-02
Are you connected to the Internet?  The script definitely works for me, but it looks in your case like you had no connection when you tried to run the script.  Do you get a ping response if you run this command by itself:
```

ping google.com
```

(leave out the www part; it shouldn't hurt anything but it's not necessary).

---

### Post by Arcnsparc on 2008-09-07
```
n=1
iwconfig wlan0 > wireless.txt
m=`grep -c MGHS /home/jake/Scripts/wireless.txt`
o=`grep -c NMU /home/jake/Scripts/wireless.txt`
while [ $n -le 20 ]; do
	echo $n & sleep 30
	let n++
	if ping -c 1 www.google.com
		then sh /home/jake/Scripts/netdepsu.sh
	elif [ "$m" = 1 ]
		then sleep 15; sh /home/jake/Scripts/netdepsu.sh & echo "MGH"  && break
	elif [ "$o" = 1 ]
		then sh /home/jake/Scripts/netdepsu.sh & echo "NMU" && break
	else echo "no internet"
	fi
done
```

This is what I ended up with.  MGH (where I work) and NMU (my college) both have disabled pings so I had to get around it by looking for those network names in the iwconfig output.  Complicated I know, but it worked like a charm.  I hope this is use to some one else too!

---

