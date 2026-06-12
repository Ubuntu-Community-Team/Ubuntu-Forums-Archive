---
title: "Slow internet after fresh install."
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by balls on 2008-04-26
Hello all.

I upgraded to Hardy earlier today and got my connection to the internet up and running rather quickly, but found out that my connection was outrageously slow (either a minute plus to load a page or page not found).  I tried changing the IPv6 as well as modifying my DNS servers, but have had no luck so far.
Any suggestions would be appreciated.

Thanks.

---

### Post by tamoneya on 2008-04-26
test your internet speed here: [http://www.dslreports.com/speedtest](http://www.dslreports.com/speedtest).  Also see if there is any difference if you use a different browser.  Try Opera or something.  Also please post the result of ifconfig.

---

### Post by balls on 2008-04-26
Latency is 34 ms, download speed is 5434 kb/s, and upload speed is 434 kb/s.  I don't think my connection is the problem, since I'm on my laptop right now with no problems at all.

output from ifconfig is as follows ```
eth0      Link encap:Ethernet  HWaddr 00:04:4b:02:62:5c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:04:4b:02:62:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:222 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8433 (8.2 KB)  TX bytes:8433 (8.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:9b:73:a2  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2087 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1544 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1069210 (1.0 MB)  TX bytes:165182 (161.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-9B-73-A2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by tamoneya on 2008-04-26
are you sure it is not just the site you were trying to visit.  The DNS servers should be fairly accurate.  How does google load?

---

### Post by balls on 2008-04-26
I've tried loading the mozilla webpage, google, and the ubuntu homepage, all of which are slow.

---

### Post by balls on 2008-04-26
I ran ipconfig/all on my windows machine and noticed that it has a line about an IPv6 address, and nothing about IPv4.  Does this necessarily mean that I need IPv6 enabled?

---

### Post by balls on 2008-04-26
Update:

I did a fresh install of Hardy, disabled IPv6, added openDNS to my DNS servers, and still no luck.

Executing host [www.google.com](www.google.com) results in a connection time out with no servers reached.

Any advice would be very helpful.

Thanks

---

### Post by jjf on 2008-04-26
I'm having this problem too.  The problem occurs under both Gutsy and Hardy on my Dell Inspiron 530.  I made no changes to IPv6 or to my DNS servers, but those changes don't seem to have done balls any good, anyway.

I did some simple timing tests to illustrate the point.  I timed various pages loading in Vista and in Ubuntu.  I used Firefox 3 Beta 5 in both OS's.

reddit.com
Vista: 2 seconds
Ubuntu: 12 seconds

rottentomatoes.com
Vista: 15 seconds
Ubuntu: gave up after 2 minutes of no activity

blockbuster.com
Vista: 2 seconds
Ubuntu: gave up after 2 minutes of no activity

wikipedia.org
Vista: 2 seconds
Ubuntu: 17 seconds

I notice that in Firefox's status bar, "Looking up (site)" takes a few seconds, and "Connecting to (site)" is where I get the big delay.

So here's one more voice looking for help on this issue.  My Internet is basically non-functional right now.  It's bad enough that I find myself sitting at my GRUB menu, feeling strange new stirrings -- a desire to *boot into Windows Vista*. :shock:

---

### Post by balls on 2008-04-27
Going through the forums, it seems like a very common problem.

What surprises me is that Ubuntu (being a "beginner's" distro) has not attempted to change any of the default settings.  I'm not sure how the average Windows user would be able to figure this out.

But I can almost guarantee that once I get this problem fixed, I will be using Linux a heck of a lot more; enough that I might uninstall XP.  So far, I'm very impressed with the layout of the distro, but this one issue is holding me back...

---

### Post by balls on 2008-04-27
Have previous releases of Ubuntu had this problem?  If not, I think I might just go use Gutsy.

---

### Post by zeronothing on 2008-04-27
Did you try and disable the IPv6 module. you could do this by adding the IPv6 module to the blacklist. open up terminal and type in:

sudo gedit /etc/modprobe.d/blacklist

after that add this quote to the bottom of the blacklist file:

# IP V6 disabled, Not needed at the moment
blacklist ipv6


Then just save the document and restart your computer. also don't forget to disable the IPv6 in firefox. to do this open up firefox and in the address bar type in:

about:config

click on the box that says something like "yes I will be carefull." next up top their is a address bar to search for the different settings. in the address bar type "ipv6" and you should see something dealing with "network dns ip6v." click on that line to make it true. then just close down firefox and open it back up to make the changes take affect.

---

### Post by Sav on 2008-04-27
I have the same problem.

My hardware specs are:

athlon thunderbird 2500+

1 gb ram

nforce2 mobo, with integrated lan

geforce 5200

I had ubuntu on this box since the 6.06 with no problems at all.

I installed the first hardy beta and I was very happy.

The slowdown connection problem happened upgrading to the first rc.

Now I'm unable to surf my own lan.

---

### Post by balls on 2008-04-27
> **zeronothing said:**
> Did you try and disable the IPv6 module. you could do this by adding the IPv6 module to the blacklist. open up terminal and type in:

sudo gedit /etc/modprobe.d/blacklist

after that add this quote to the bottom of the blacklist file:

# IP V6 disabled, Not needed at the moment
blacklist ipv6


Then just save the document and restart your computer. also don't forget to disable the IPv6 in firefox. to do this open up firefox and in the address bar type in:

about:config

click on the box that says something like "yes I will be carefull." next up top their is a address bar to search for the different settings. in the address bar type "ipv6" and you should see something dealing with "network dns ip6v." click on that line to make it true. then just close down firefox and open it back up to make the changes take affect.

Yes, I think I even looked at your post at [http://ubuntuforums.org/showthread.php?t=589011&highlight=ipv6+dns](http://ubuntuforums.org/showthread.php?t=589011&highlight=ipv6+dns) :)

I've also tried enabling the openDNS servers but had no luck.

---

### Post by gambituk on 2008-04-27
sounds like a problem with mtu change it to 1432 or 1400 for your active network connection.

goto sudo gedit /etc/network/interfaces

and add the line mtu 1432 or mtu 1430 to the end,
this should improve the issue.

There may be more commands to do this. i'm just a beginner. but this is a typical internet issue and can be a problem with windows etc.

hope this helps.

---

### Post by jchengj on 2008-04-28
Changing the MTU helped alittle, but it didn't solve the problem completely.
After adjusting the MTU, my download speed got up to around 30 kb/sec, compared to 150 kb / sec when I was using XP

---

### Post by phreakaholic on 2008-04-28
that also happen when i'm accessing internet through USB CDMA modem. to resolve, i reconfigure my wvdial.conf a couple of time until get the fastest connection. :D

---

### Post by njparton on 2008-04-28
I think you guys need to log this as a bug in launchpad (you may even find that it's already there).

---

### Post by clyde9999 on 2008-04-28
I have a fresh install of 8.04 and Firefox is slow as molasses in winter time. I am using SeaMonkey as a temporary solution till the issue can be resolved. Firefox works fine on my lappy though, just slow on this PIII (unusably slow). SeaMonkey works just fine on it though.

---

### Post by Sav on 2008-05-02
I tried on my imac g5, too.
Is really slow.

---

### Post by Sav on 2008-05-04
I got it.
The problem is caused by the router.
Mine has a firmware modified by the internet provider.

I edited the /etc/sysctl.conf, inserting the following lines:

net.ipv4.tcp_syncookies=1
net.ipv4.tcp_window_scaling=0
net.ipv4.tcp_ecn=0

(it needs a restart)

Now all is working.

---

### Post by DonKaron on 2008-05-04
I had slow internet response to clicks on links and page loading throughout my (very brief) time with Ubuntu.  I think I solved it.

Go to Network Manager-> Manual Configuration-> Hosts tab and delete all references to IP v6.  Click 'Close'

In FireFox type 'about:config' in the address line.  Then type 'ipv6' in the 'Filter' box.  Find network.dns.disableIPv6 and double click that line.  Its value will change from false to true (and the typeface changes to bold to show that the user changed this line).

Ta-da, it runs as fast now as it does in XP.  

Additionally, I find it quicker to use OpenDNS instead of the default DNS servers.  Do this by clicking Network Manager-> Manual Configuration-> DNS.  Add the following two DNS Servers:  208.67.222.222 and 208.67.220.220. (Note: you have to end  entering each DNS address by hitting the 'Enter' key or they are not recorded.)  Drag these two new DNS addresses to the top of the list so they will be chosen first.  Click 'Close'.

Worked for me.

         Don

---

### Post by DonKaron on 2008-05-04
> **balls said:**
> Hello all.

I upgraded to Hardy earlier today and got my connection to the internet up and running rather quickly, but found out that my connection was outrageously slow (either a minute plus to load a page or page not found).  I tried changing the IPv6 as well as modifying my DNS servers, but have had no luck so far.
Any suggestions would be appreciated.

Thanks.

Not sure my prior post got posted.  Go to Network Manager, Manual Configuration, select Hosts tab, delete all references to IPv6.  This seems to have been the key thing to speeding up my Internet connection.

         Don

---

### Post by onesojourner on 2008-05-05
this is a bug and its a beast for an lts.

try this:
```
sudo iwconfig wlan0 rate 54M
```

wlan0 is the name of your wireless interface. Yours might be differnt.

---

### Post by pgdave on 2008-05-07
> **onesojourner said:**
> this is a bug and its a beast for an lts.

try this:
```
sudo iwconfig wlan0 rate 54M
```

wlan0 is the name of your wireless interface. Yours might be differnt.

Great! Solved my problem. Internet speed test at [www.speedtest.net](www.speedtest.net) changed from 350kb/s to 6721kb/s!

---

### Post by pgdave on 2008-05-07
[http://ubuntuforums.org/showthread.php?p=4902804#post4902804](http://ubuntuforums.org/showthread.php?p=4902804#post4902804)

Solved the problem for me. Now working fine.

---

### Post by pgdave on 2008-05-07
Oops! spoke too soon. After an hour, the data rate started varying - going down to 10Kb/s, and then back up to 500kb/s. After about 3 hours, it permanently slowed to less than 10kb/s for downloads.

iwconfig shows wlan0 at 54M bit rate.

Rebooted, and iwconfig shows 1Mb rate. So I set it to 54M again, and watched a download go at an incredible 128 bytes/second. Back to the seventies!

Then it just picked up again, to around 500Kb/s.

Weird. Needs fixing. Help!

---

### Post by mahfouz666 on 2008-05-08
okay this is ridiculous

after following alll the suggestions i still dont get proper speeds

speedtest.net shows that i have a download speed of 415kb/s. in reality im getting 2 kb/s - 8 kb/s. i switch to vista and get my normal speeds (about 40)

the weird thing is that i just installed KDE4 remix and the download speeds were perfect (actually faster than vista) but i fresh installed hardy heron yesterday and the speeds vanished.

HELP!

---

### Post by SE77EN on 2008-05-08
Hi

I have just this code in the terminal "sudo iwconfig wlan0 rate 54M" then I check it with "iwconfig" which say 54M and it works like a speed train on rocket fuel faster download then XP or any windows I used.

Then when I restart I check "iwconfig" and its back to 1M which it is suppose to be 54M so I have to enter the "sudo iwconfig wlan0 rate 54M" command again.

Is there anyway I can get it to keep the 54M without keeping the command please.

---

### Post by NEUR0M4NCER on 2008-05-08
Yes, there is a way... only problem is I forgot where I saw it. Have a hunt around the Installation & Upgrades section, there's a little bit of code that will set it to 54M on boot. Worked for me.

I just had a look for it, and can't for the life of me remember where it was, but it's definitely in there somewhere - sorry I couldn't be of more help.

Regards

**EDIT**

Found it: [Slow Wireless on 8.04](http://ubuntuforums.org/showpost.php?p=4804938&postcount=9)

This should do it for ya.

---

### Post by mahfouz666 on 2008-05-09
okay so i know what to do when i use a wireless connection, but im not on wireless...

---

### Post by ushills on 2008-05-09
Add the following to your /etc/network/interfaces file, under the wlan interface 

```
# make sure that you get full bit rate
iwconfig wlan0 rate 54M
```

similar to this

```
[# wireless configuration, change wlan0 where applicable
iface wlan0 inet static

# set the static ip configuration, these will depend on your network
address 192.168.1.9 
gateway 192.168.1.1
dns-nameservers 192.168.1.1
netmask 255.255.255.0
broadcast 192.168.1.255

# bring the interface down, this makes it start correctly
pre-up ifconfig wlan0 down 

# enter correct key below
wpa-psk KeyGeneratedAfterRunning_wpa_passphrase_WithoutQuotes
wpa-key-mgmt WPA-PSK
wpa-proto WPA

#enter your SSID name below
wpa-ssid YOUR_SSID

# wait for 20 seconds to bring interface up
pre-up sleep 20

# make sure that you get full bit rate
iwconfig wlan0 rate 54M

# start interface
pre-up ifconfig wlan0 up
# make it start automatically
auto wlan0
```

---

### Post by NW2190 on 2008-05-10
I have this same problem but with a wired connection... Is there any way to fix that?

---

### Post by pgdave on 2008-05-12
I tried the 'sudo iwconfig wlan0 rate 54M' trick, and it worked for a day, but then slowed down again - download speeds varied from merely painfully slow (10kps) to even 8 BYTES/second at one point. 'iwconfig' showed 54M at all times.

This morning I tried following this suggestion: [http://ubuntuforums.org/showpost.php?p=4797723&postcount=17](http://ubuntuforums.org/showpost.php?p=4797723&postcount=17)

I had to get the linux-headers first, though, before the first make would work. I forgot the 'sudo apt-get install rutilt' until too late, so I couldn't actually fetch it, having disabled the connection.

After a reboot, I get no network connection. Ho Hum. So I reversed the whole process, re-instating the bad rt2500pci driver, and rebooted. Result? No network available at all. Backward progress. 

I clicked on the network manager icon, disabled roaming mode, and did a manual setup. Result was a reasonably fast internet once more.

Running 'iwconfig' shows the card varying wildly between 1Mbs and 54Mbs within seconds, and the quality varying from 39% to 86% (Gutsy stayed on 70-75%). Previously, as I said, merely setting the card rate to 54M left it at 54Mb/s.

Download speeds are now about 500kB/s, not the best I've had, but acceptable. These seem quite independent of the card rate. Measured internet speeds are now 7,000kbps download, but only 380 upload.

So *maybe* just manually configuring your card from network manager might solve the problem, at least until a patch comes along. Hope this helps someone.

EDIT: Ok, so I lied :0)

lsmod shows both rt2500pci and rt2500 in the modules list. Both of them are being used as far as I know (i'm no expert here). I've installed rutilt, and all is wonderful. Download speeds are now 800KB/s. I think I'll leave it alone...

---

### Post by SINternet on 2008-05-15
I have the dreaded rt2500 card WMP54G. 

After a fresh install I applied these files only and got the Internet Speed out of my system I was used to seeing with Windows.

Paste applicable contents from each file.

My additions to the sysctl.conf

To open for editing "sudo gedit /etc/sysctl.conf"

#increase TCP maximum buffer size
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216

# increase linux autotuning TCP buffer limits
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216

# don't cache ssthresh from previous connection
net.ipv4.tcp_no_metrics_save = 1

# recommended to increase this for 1000 BT or higher
net.core.netdev_max_backlog = 2500
net.ipv4.tcp_timestamps=0
net.ipv4.tcp_moderate_rcvbuf=0
net.ipv4.tcp_window_scaling=0

to apply immediately after editing "sudo sysctl -p"

Good source of info here. [http://www-didc.lbl.gov/TCP-tuning/TCP-tuning.html](http://www-didc.lbl.gov/TCP-tuning/TCP-tuning.html)


Nice Info here.......[http://www.extremetech.com/article2/...2114124,00.asp](http://www.extremetech.com/article2/...2114124,00.asp)

Info on sysctl.conf parameters..[http://frankmash.blogspot.com/2005/1...imization.html](http://frankmash.blogspot.com/2005/1...imization.html)

check your parameters by dumping the sysctl info to a file.
sudo sysctl -A > ~/Desktop/sysctl_settings

rc.local has some redundancy to syctl.conf

paste before the exit 0 at the bottom. For Wired Connections leave out the iwconfig command line.

/sbin/iwconfig wlan0 rate 11M

echo 256960 > /proc/sys/net/core/rmem_default
echo 256960 > /proc/sys/net/core/rmem_max
echo 256960 > /proc/sys/net/core/wmem_default
echo 256960 > /proc/sys/net/core/wmem_max

echo 0 > /proc/sys/net/ipv4/tcp_timestamps 
echo 1 > /proc/sys/net/ipv4/tcp_sack 
echo 1 > /proc/sys/net/ipv4/tcp_window_scaling

"11M" worked fine for my connection. Play with that rate till you find your sweet spot (because not every place has the same basic speed nor does everyone pay for more speed like Business Class)

Most people say make a backup of the original but I say make a backup of your edited file as well!

SIN

---

### Post by DVANDERM on 2008-05-18
> **onesojourner said:**
> this is a bug and its a beast for an lts.

try this:
```
sudo iwconfig wlan0 rate 54M
```

wlan0 is the name of your wireless interface. Yours might be differnt.

This worked for me! I'm so glad too because I was getting upset with the new distro. 

Kudos to you for thinking this one up. :KS

---

### Post by Leecifer on 2008-05-19
> **onesojourner said:**
> this is a bug and its a beast for an lts.

try this:
```
sudo iwconfig wlan0 rate 54M
```

wlan0 is the name of your wireless interface. Yours might be differnt.

Thank you sir, this fixed my slow network performance. If we ever meet, I owe you a beer. :KS

---

