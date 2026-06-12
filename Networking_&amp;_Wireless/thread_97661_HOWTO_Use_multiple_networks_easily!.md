---
title: "HOWTO: Use multiple networks easily!"
date: 2005-12-01
forum: Networking &amp; Wireless
---

### Post by seismicmike on 2005-12-01
If you're using a Broadcom Wireless Card and are looking for help to set it up. This is not the place for you. [This is]("http://www.ubuntuforums.org/showthread.php?t=25683") :)

Any of you who have tracked my posts recently will realize that I've been trying to solve a rather complex problem: namely how to set up my networking so that no matter which network I'm on (home, work or school) I can do apt-get and network configuration rather seamlessly.

Previously I was logging onto my laptop. Loading up the network configuration gui and trying to manually set everything. THen rebooting.

That evolved into me saving a copy of the interfaces file which I would copy over, and then rebooting.

Well, now I've figured it out so that no matter where I am, all I do is type ./atwork or ./athome or ./atschool and it sets everything up for me... no reboot necessary.

Interested??? Keep reading.

I frequent three networks. My home network is wireless with no proxy. My school network is wireless with a proxy, and my work network is wired with a proxy. So here goes. For each network you frequent, you will need to make three files. I'll walk you through one, and once you're finished I'm confident you can make the necessary inferences to figure out the other three. I'll be using my school network as an example. You only need to do steps 1-3 once for each network you have.

Step 1. **Figure out your network settings.** Go onto your network and manually set everything up. Once you've done that, boil down your interfaces file to the minimum content necessary to make it work just on that network. If you don't know how to set up apt-get's proxy, then read #2. Once you have your interfaces file boiled down, all you need to do is make a copy of it in your home directory.
```
:~# sudo cp /etc/network/interfaces ~/schooliface
```

Here's what mine looks like:
```
auto lo
iface lo inet loopback

mapping hotplug
	script grep
	map eth0  # not sure if this line is actually necessary for wlan0...

iface wlan0 inet dhcp
wireless-essid cedarwireless

auto wlan0
```
Obviously if your network requires a key, you would put it on the line after your essid. Just say ```
wireless-key <KEY>
```
So... Do you have a file in your home directory containing just the information for your network? Good! Step 1 is complete!

Step 2. **Setting up apt-get.** You need to figure out what your proxy configuration is. If you don't know what this is, what the heck are you doing in linux? OOPS JUST KIDDING!!! If you don't know what it is, just contact your system administrator. You will need your[LIST]
[*]Domain (if needed)
[*]username
[*]password
[*]proxy server
[*]proxy server port[/LIST]

To make apt-get work behind a proxy you have to make the file /etc/apt/apt.conf. To do this ```
:~# sudo gedit /etc/apt/apt.conf
```
You put in your proxy info like so:
```
Acquire::http::Proxy "http://DOMAIN\uname:upass@proxy.servername.host:port" ;
```
Mine:
```
Acquire::http::Proxy "http://myname:mypass@163.11.83.100:8080" ;
```
Notice that my school doesn't require the domain. Here's my work file which does require the domain:
```
Acquire::http::Proxy "http://MYDOMAIN\myname:mypass@proxy.myserver.com:80" ;
```
Made-up example[LIST]
[*]Domain = GOOGLENET
[*]Username = bozotheclown
[*]Password = funnybones
[*]Proxy server = proxy.google.com
[*]Port = 1234[/list]
Bozo's apt.conf file would look like this:
```
Acquire::http::Proxy "http://GOOGLENET\bozotheclown:funnybones@proxy.google.com:1234" ;
```

Got it?

Here's part 2 of step 2. To make it work in our example, you'll need to create a file in your home directory with these settings, much the same way you did the interfaces file. Get it set up in your apt.conf file, and then do this:
```
:~# sudo cp /etc/atp/apt.conf ~/schoolapt
```

Got it? So, we have two files in our home directory. schooliface has the network information that needs to be in the /etc/apt/interfaces file for me to connect to the internet. schoolapt contains the proxy information apt-get needs to access the network. If, like me, one of your networks has no proxy information, just make a blank file for this. My homeapt file is completely blank. The only effect this really has is to keep bash from screaming at us in Step 3.

Step 3. **Making it work.** Ah, the juicy part :). This part makes a script that will set up those files. Create file #3 and call it something. I called mine "atschool". Here's what my atschool file looks like:
```
#!/bin/bash
# atschool

# Sets the network interface and proxy settings for apt for configuration at school
# Run as Root!

echo "setting up interface"
echo "..."
echo ""
sudo cp ~/schooliface /etc/network/interfaces
echo "done"

echo "setting up proxy"
echo "..."
echo ""
sudo rm /etc/apt/apt.conf
sudo cp ~/schoolapt /etc/apt/apt.conf
echo "done"

echo "resetting network"
echo "..."
echo ""
sudo ifdown -a
sudo ifup -a
echo "done"

echo "updating repositories"
echo "..."
echo ""
sudo apt-get update
echo "done"

exit 0
```

This file does 4 things.[LIST=1]
[*]It copies the interfaces file we created in the home directory to replace the interfaces file
[*]It replaces any apt.conf file in existance with the one we created in the home directory
[*]It restarts the network
[*]It does an apt-get update to check the repositories.
[/LIST]
The lines that begin "echo" just print stuff to the screen.

To make it run you have to make it executable:
```
:~# sudo chmod 555 atschool
```

Then run it
```
:~# sudo ./atschool
```

Step 4. **Using it.** From now on, all you have to do is type the above command once you boot your computer to set up the network. If all goes well, you should now be able to connect to the internet and apt-get anything you want. No rebooting necessary.

If it *doesn't* work, I suggest one of the following problems:[list]
[*]Your interface isn't configured properly
[*]Your proxy information isn't right
[*]Your /etc/apt/sources.list file isn't right[/list]

If it's the sources.list file, here's mine:
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

**NOTE:** You still need to set Firefox's proxy settings. This script does no good for that!

Once you've got this done, all you need to do is repeate it for each network you're on. I have 3, so I have 3 interfaces files - homeiface, workiface and schooliface. I have 3 apt files - homeapt, workapt, schoolapt. And I have 3 executable files athome, atwork and atschool.

If you have any further questions, post them here and I'll do my best to answer them :)

---

### Post by seismicmike on 2005-12-01
I'll even one-up myself!

I wrote the following script. Basically it prints out a list of network locations with which it knows how to deal, and then asks which on I'm on. I type a 1, 2 or 3 corresponding with the appropriate one, and then it calls the appropriate file I made above (you know the at<suchandsuch>). 

Have fun..... 

To add more to it, all you have to do is follow the directions above and make the three neccessary files. MAKE SURE YOU DON'T FORGET TO CHMOD THE SCRIPT! and then add an extra if condition and option to this script. Here it is (I called it netsetup):

```
#!/bin/bash
# netsetup

# Setup Network
# Run as Root!

# Find out which network I'm on
echo "Where are you?"
echo "1. Home"
echo "2. Work"
echo "3. School"
read loc

#run appropriate script
if [ "$loc" == "1" ] 
then 
	echo "Setting up Home Networking"
	sudo ./athome
elif [ "$loc" == "2" ]
then 
	echo "Setting up Work Networking"
	sudo ./atwork
elif [ "$loc" == "3" ]
then 
	echo "Setting up School Networking"
	sudo ./atschool
else 
	echo "ERROR110: UNKNOWN ENTRY"
fi

exit 0
```

To use it, make it executable:

```
:~# chmod 555 netsetup
```

and then run it:

```
:~# ./netsetup
```

---

### Post by seismicmike on 2005-12-01
One More Amendment, Guys

Some proxy servers may require you to visit an off network website in a browser  for apt-get to work. I actually forgot about this. I have to authenticate to the proxy server through the web browser first.

For those networks, I suggest omitting the section of the "atsuchandsuch" script code that automatically does the apt-get update. Everything else will set up fine. Go to an off site web page, then do apt-get update.

---

### Post by zasf on 2005-12-16
Thank you for the nice script, i find it very useful and i'll try it later when at home.

Other than configuring scripts for each network, it would also be nice to choose one of the networks your card sees with iwlist.

For example, I type ```
sudo iwlist eth1 scan
``` and i get a list of all the active networks nearby. Is it possible to read iwlist output and choose one?? How would you script this?

Thank you

---

### Post by seismicmike on 2006-03-13
[QUOTE=zasf]Thank you for the nice script, i find it very useful and i'll try it later when at home.

Other than configuring scripts for each network, it would also be nice to choose one of the networks your card sees with iwlist.

For example, I type ```
sudo iwlist eth1 scan
``` and i get a list of all the active networks nearby. Is it possible to read iwlist output and choose one?? How would you script this?

Thank you[/QUOTE]

hmm... I'm not exactly sure how you would do that zasf:-k 

I suppose there should be a way to do it with grep.... I'll have to look into that

---

### Post by seismicmike on 2006-03-13
\\:D/ \\:D/ \\:D/ 

YOU CAN ALL OFFICIALLY KISS MY @$$!!!

I finally figured it out. After months of deliberation and having to type in a number half way through boot up, I finally wrote a scrip that had my computer automatically detect the network and configure it!!

Want to know how???

Well.... you need to set up the files like I had you do before: remember I had a copy of each interface file I wanted: homeiface, workiface and schooliface. Then I had a copy of the apt proxy info for each: homeapt, workapt and schoolapt. The third script file is no longer necessary.

**_Step One_**: Rename each of these files so they are in sequence (preferably the one you visit most should be a lower number), and **make sure they are in the root directory**:

```
:~$ mv schooliface /iface1
:~$ mv homeiface /iface2
:~$ mv workiface /iface3
:~$ mv schoolapt /apt1
:~$ mv homeapt /apt2
:~$ mv workapt /apt3
```

**_Step Two_**: Modify the startup file: Find the networking file in the startup folder: /etc/init.d/networking. Scroll down to where it says 

```
case "$1" in
    start)
	doopt spoofprotect yes
        doopt syncookies no
        doopt ip_forward no
```

Delete everything that follows in the file and put the following code in its place:

```
      log_begin_msg "Configuring network interfaces..."
      # remove past configurations
      ifdown -a >/dev/null 2>&1
      rm /var/run/dhclient.wlan0.leases >/dev/null 2>&1
      rm /var/run/dhclient.eth0.leases >/dev/null 2>&1
      cp /blankfile /etc/network/interfaces
      cp /blankfile /etc/apt/apt.conf
      
      # variables
      numWaps=`grep -c iface /* | grep -c :2`
      numTry=0 
      leases=0
      
      type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 120" || true
      if [ "$VERBOSE" != no ]; then
         while [ "$numTry" -le "$numWaps" ]
         do
            let "numTry += 1"
            ifdown -a >/dev/null 2>&1
            iFile=iface${numTry}
            aFile=apt${numTry}
            cp /$iFile /etc/network/interfaces
            cp /$aFile /etc/apt/apt.conf
            rm /var/run/dhclient.wlan0.pid >/dev/null 2>&1
            rm /var/run/dhclient.eth0.pid >/dev/null 2>&1
            
            ifup -a
   
            if grep -q wlan /var/run/dhclient.wlan0.leases
            then
               leases=1
               break
            elif grep -q eth /var/run/dhclient.eth0.leases
            then
               leases=1
               break
            else
               continue
            fi
         done  

         if [ $leases -eq 0 ]
         then
            ifdown -a >/dev/null 2>&1
            cp /loiface /etc/network/interfaces
            cp /blankfile /etc/apt/apt.conf
            ifup -a
            echo "No Network Detected"
         fi
      else
         while [ "$numTry" -le "$numWaps" ]
         do
            let "numTry += 1"
            ifdown -a >/dev/null 2>&1
            iFile=iface${numTry}
            aFile=apt${numTry}
            cp /$iFile /etc/network/interfaces
            cp /$aFile /etc/apt/apt.conf
            rm /var/run/dhclient.wlan0.pid >/dev/null 2>&1
            rm /var/run/dhclient.eth0.pid >/dev/null 2>&1
            
            ifup -a >/dev/null 2>&1
   
            if grep -q wlan /var/run/dhclient.wlan0.leases
            then
               leases=1
               break
            elif grep -q eth /var/run/dhclient.eth0.leases
            then
               leases=1
               break
            else
               continue
            fi
         done  

         if [ $leases -eq 0 ]
         then
            ifdown -a >/dev/null 2>&1
            cp /loiface /etc/network/interfaces
            cp /blankfile /etc/apt/apt.conf
            ifup -a >/dev/null 2>&1
            echo "No Network Detected"
         fi
      fi
      type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 15" || true
      log_end_msg $?
      ;;
    stop)
        if sed -n 's/^[^ ]* \([^ ]*\) \([^ ]*\) .*$/\1 \2/p' /proc/mounts | 
          grep -q "^/ nfs$"; then
            log_failure_msg "NOT deconfiguring network interfaces: / is an NFS mount"
        elif sed -n 's/^[^ ]* \([^ ]*\) \([^ ]*\) .*$/\1 \2/p' /proc/mounts |  
          grep -q "^/ smbfs$"; then
            log_failure_msg "NOT deconfiguring network interfaces: / is an SMB mount"
	elif sed -n 's/^[^ ]* \([^ ]*\) \([^ ]*\) .*$/\2/p' /proc/mounts | 
          grep -qE '^(nfs[1234]?|smbfs|ncp|ncpfs|coda|cifs)$'; then
            log_failure_msg "NOT deconfiguring network interfaces: network shares still mounted."
        else
            log_begin_msg "Deconfiguring network interfaces..."
            if [ "$VERBOSE" != no ]; then
                ifdown -a --exclude=lo
            else
                ifdown -a --exclude=lo >/dev/null 2>&1
            fi
	    log_end_msg $?
        fi
	;;
   force-reload|restart)
      doopt spoofprotect yes
      doopt syncookies no
      doopt ip_forward no

      log_begin_msg "Reconfiguring network interfaces..."
      ifdown -a --exclude=lo
      # clear past leases
      rm /var/run/dhclient.wlan0.leases >/dev/null 2>&1  
      rm /var/run/dhclient.eth0.leases >/dev/null 2>&1
      
      # variables
      numWaps=`grep -c iface /* | grep -c :2`
      numTry=0 
      leases=0
      if [ "$VERBOSE" != no ]; then
         while [ "$numTry" -le "$numWaps" ]
         do
            let "numTry += 1"
            ifdown -a >/dev/null 2>&1
            iFile=iface${numTry}
            aFile=apt${numTry}
            cp /$iFile /etc/network/interfaces
            cp /$aFile /etc/apt/apt.conf
            rm /var/run/dhclient.wlan0.pid >/dev/null 2>&1
            rm /var/run/dhclient.eth0.pid >/dev/null 2>&1
            
            ifup -a
   
            if grep -q wlan /var/run/dhclient.wlan0.leases
            then
               leases=1
               break
            elif grep -q eth /var/run/dhclient.eth0.leases
            then
               leases=1
               break
            else
               continue
            fi
         done  

         if [ $leases -eq 0 ]
         then
            ifdown -a >/dev/null 2>&1
            cp /loiface /etc/network/interfaces
            cp /blankfile /etc/apt/apt.conf
            ifup -a
            echo "No Network Detected"
         fi
      else
         while [ "$numTry" -le "$numWaps" ]
         do
            let "numTry += 1"
            ifdown -a >/dev/null 2>&1
            iFile=iface${numTry}
            aFile=apt${numTry}
            cp /$iFile /etc/network/interfaces
            cp /$aFile /etc/apt/apt.conf
            rm /var/run/dhclient.wlan0.pid >/dev/null 2>&1
            rm /var/run/dhclient.eth0.pid >/dev/null 2>&1
            
            ifup -a >/dev/null 2>&1
   
            if grep -q wlan /var/run/dhclient.wlan0.leases
            then
               leases=1
               break
            elif grep -q eth /var/run/dhclient.eth0.leases
            then
               leases=1
               break
            else
               continue
            fi
         done  

         if [ $leases -eq 0 ]
         then
            ifdown -a >/dev/null 2>&1
            cp /loiface /etc/network/interfaces
            cp /blankfile /etc/apt/apt.conf
            ifup -a >/dev/null 2>&1
            echo "No Network Detected"
         fi
      fi
      log_end_msg $?
      ;;
   *)
	log_success_msg "Usage: /etc/init.d/networking {start|stop|restart|force-reload}"
	exit 1
	;;
esac

exit 0
```

If you want to know exactly what it's doing, let me know

---

