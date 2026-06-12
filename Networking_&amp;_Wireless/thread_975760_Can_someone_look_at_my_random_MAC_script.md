---
title: "Can someone look at my random MAC script?"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by svguy on 2008-11-08
Originally I wanted to make a script that changed my MAC address to something at random and then I discovered that connected to my wireless my logs still showed my hostname 'wabbit' in the LAN logs.  I wanted it to look like a different client was connecting each time the script was run.  I found a way to change the hostname so that it reflects in LAN sections of routers, but I've run in to a few other quirks.

After this is run though I'm unable to open new windows in xserv. Any attempt will net this output
```

wascally@wabbit:~/bin$ sudo gedit nmtoggle
sudo: unable to resolve host holier
No protocol specified
cannot open display: 

```
'holier' is the random hostname that was generated

Then I simply run the script again and choose the "normal" option which sets everything back to the way it was, and windows open fine.

I'm very much a noob to bash scripting but would really appreciate some help here.

```

#!/bin/bash
# A script to randomly change the eth1 MAC address and the host name 

OPTIONS="Anonymous Normal Quit"
num1=$(echo $RANDOM | cut -c 1-2)   
num2=$(echo $RANDOM | cut -c 1-2)   
num3=$(echo $RANDOM | cut -c 1-2)   
prefix=$(cat /home/wascally/bin/prefixes | grep $((RANDOM%34+1000)) | awk '{print $2}' )
echo This will change your MAC address, hostname,
echo and hopefully IP address. Normal will set
echo everything to defaults.

select opt in $OPTIONS; do
    if [ "$opt" = "Quit" ]; then
        echo goodbye
        exit
    elif [ "$opt" = "Normal" ]; then
        echo wabbit > /proc/sys/kernel/hostname
        ifconfig eth1 down hw ether 00:0e:35:b3:63:c2
        ifconfig eth1 up
        dhclient eth1
        PID=$( ps -A | grep conky | awk '{print $1}' )
        kill -HUP $PID
        exit
    else [ "$opt" = "Anonymous" ]
        cat /usr/share/dict/wordtest -n | grep $((RANDOM%89999+10000)) | awk '{print $2}' > /proc/sys/kernel/
hostname
         ifconfig eth1 down hw ether $prefix:$num1:$num2:$num3
        ifconfig eth1 up
        dhclient eth1
        PID=$( ps -A | grep conky | awk '{print $1}' )
        kill -HUP $PID
        exit
    fi
done


```

---

### Post by fvds on 2008-11-08
Looks to me, you should also write the new hostname to /etc/hosts as 127.0.0.1 newhostname to make sure the xserver knows which host wants to open a screen.

---

### Post by svguy on 2008-11-08
That was my first thought too, but it still happens.  I wasn't sure if it mattered which one I changed in hosts so I changed both entries. I've also tried it either or.

```

wascally@wabbit:/etc$ more hosts
127.0.0.1	cohabitation
127.0.1.1	cohabitation

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
wascally@wabbit:/etc$ hostname
cohabitation
wascally@wabbit:/etc$ sudo gedit /home/wascally/bin/nmtoggle
No protocol specified
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.

```

PS: cohabitation is the random hostname this time.

---

### Post by fvds on 2008-11-10
Shouldn't localhost be in /etc/hosts too?

---

### Post by svguy on 2008-11-10
It is. I've tried changing it in /etc/hosts and /etc/hostname and it still can't resolve.

---

### Post by cariboo on 2008-11-10
When you change the hostname you have to reboot for it to take affect. you should also have:

```
127.0.0.1  localhost
```

set permanently, or some other services will not run without it.

Jim

---

### Post by svguy on 2008-11-10
My 127.0.0.1 is definitely localhost and I'm not really changing that one after my one experiment.

So hmmm,  xserv won't work after changing the host name unless I reboot?  That's gonna put a damper on this little thing.

---

### Post by JeppeM on 2008-11-10
I dont think you need to restart the entire system, just the applications you need to tell about this change... For example, when i edit my hosts file with some new things, i need to restart firefox before they take affect...

---

### Post by svguy on 2008-11-10
the problem is I can't restart anything because nothing will open.  
Everything you try to open generates the "display" error.

---

### Post by cariboo on 2008-11-10
You could try just restating networking to see if that helps. TO restart networking press Ctrl-ALt-F1 to get to a console then type:

```
sudo /etc/iit.d/networking restart
```

Jim

---

### Post by svguy on 2008-11-12
Just tried the networking restart and no go. It still says it can't resolve the host.
I then went and tried manually changing the hostname in /etc/hosts and /etc/hostname to match and then restarting networking, x11-common and running /etc/init.d/hostname.sh and it still doesn't work.  However in all of those scenarios, after manually making the hostnames match I get this error instead:

```

wascally@wabbit:/etc/init.d$ firefox
No protocol specified
Error: cannot open display: :0.0

```

nothing about not being able to resolve.

---

### Post by cariboo on 2008-11-12
You have to use the**hostname** command to change the hostname. If you do it manually you run into the problems you are experiencing. Have a look at:

```
man hostname
```

Jim

---

### Post by svguy on 2008-11-12
I've tried using the command to set the hostname and it still gives me the error that it's unable to resolve hostname: *whatever*

And now for some reason the contents of my personal bin have gone missing.  Good thing I pasted it on here.

---

### Post by svguy on 2008-11-13
Just confirmed that when I run the command hostname with whatever hostname I like it only changes it in /proc/sys/kernel/hostname   /etc/hostname and /etc/hosts still reflect the old hostname.

So running the command hostname isn't working either.

---

### Post by svguy on 2008-11-22
bump. I still haven't figured this out

---

### Post by svguy on 2008-11-22
Ok, played around a little more.
With my script it will successfully change the host name. Sudo commands in a terminal will spit back "unable to resolve host" lines, but it still does the command (I can live with that).  

I found that if I restart Xorg then I can open windows and I won't get the "unable to open display" error.  The only problem with this is that I lose any open windows I had, and I have to log in at a log in screen. Otherwise that fixes it.

I'm going to see if there's somewhere in Xorg that I can update it with the changed hostname without having to fully restart it.

---

### Post by svguy on 2008-11-26
Ok, I know I'm pretty much just talking to myself here, but here's what I ended up doing.

I still haven't found anything cleaner than just restarting Xorg, but I knew that 'sudo' wasn't resolving the host unless the name was in /etc/hosts.  So, I just made the script append the new hostname to the end of /etc/hosts, and then when I want to return back to normal, I have an original copy of /etc/hosts that I just replace the current one with.

So, now, no errors, and everything works. You just have to suffer through restarting Xorg. The whole process takes about 25 seconds.

---

