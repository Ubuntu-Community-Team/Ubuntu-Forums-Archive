---
title: "No internet with 8.0.4"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by Joor on 2008-06-14
I been using 7.10 since january and its been great . But after a clean install of 8.0.4 its impossible to connect to the internet ?
It the Asrock 939SLI32-eSATA2 motherboard with a Realtek RTL8168/8111 PCI-E netcard .. roaming and DHCP - no luck :(

---

### Post by Joor on 2008-06-14
I can see im not the only one with this problem.
I guess wired connections is bugged in hardy ?

---

### Post by guy2il on 2008-06-14
i can't with cable connection also.

---

### Post by rlzyoner on 2008-06-14
Have you tried manually assigning an IP address rather than DHCP
Also maybe enter the DNS server addresses.

---

### Post by Joor on 2008-06-14
Assigning IP address manually didnt help either

---

### Post by superprash2003 on 2008-06-14
once you manually assign ip.. go to the terminal and try pinging your router..and post results here.. to ping router.. type **ping 192.168.1.1** where 192.168.1.1 is the ip of your your router

---

### Post by Joor on 2008-06-14
I dont have a router, its a speedstream 4100 adsl modem.

---

### Post by Joor on 2008-06-14
This is annoying, since it only happens after the 8.0.4 release

---

### Post by dacorr on 2008-06-14
I am aware some flavors of Linux have issues with DNS servers particular if the Modem and or Router are only DNS forwarders.

When booted use terminal to type this in

sudo gedit /etc/resolv.conf

You should see something like this

           nameserver 208.164.186.1
           nameserver 208.164.186.2

If not add them, i have sometimes had to use the DNS servers of the ISP themselves to correct this.

Also note that the above file is populated at boot every time. If it works then you know what the problem is.

Dac

---

### Post by dacorr on 2008-06-14
should mention the IP of the name server should be the ISP nameserver if you are using a ADSL modem however adding the modem to the list if it is an ADSL router/modem will be needed giving you 3 nameservers.

Dac

---

### Post by Joor on 2008-06-14
Just did the;  sudo gedit /etc/resolv.conf

Added 
nameserver 193.162.153.164
nameserver 194.239.134.83

Still no connection

---

### Post by superprash2003 on 2008-06-14
try pinging your modem then.. also type ping google.com in your terminal and post output here

---

### Post by Joor on 2008-06-14
I cant ping anything.

---

### Post by guy2il on 2008-06-14
hi

i have my router forward the data, assign ip adress + dns servers 

setting them all manualy, make no difference.

if pinging 66.249.93.99 get me the same time as pinging [www.google.com](www.google.com)

then it sais i have dns setup ok.

else i would not get reply from the name [www.google.com](www.google.com)

-------

i wander if it is an IPV6 issu, since i disabled it. or maybe i just think i did ?!

-------

another thing, i CAN use every thing onside my network... including surf to the apache on the mac.

---

### Post by Joor on 2008-06-14
Maybe its a driver problem ?
How do I install this one ;
[ftp://210.51.181.211/cn/nic/r8168-8.006.00.tar.bz2](ftp://210.51.181.211/cn/nic/r8168-8.006.00.tar.bz2)

from
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

---

### Post by guy2il on 2008-06-14
wow ... the same linux machunes, on a different network with a different router....

thet work just fine !!!??

how can it be ?

---

### Post by rogier.de.groot on 2008-06-14
Most ADSL modems I'm aware of use DHCP - try setting your network connection to dhcp again. Try opening a terminal windows and doing
"sudo /etc/init.d/networking restart" afterwards. See if you can connect to anything. If you can't run the command "ifconfig" and please post the output.

---

### Post by Joor on 2008-06-14
Think im going back to 7.10 since that was working perfect.

---

### Post by Joor on 2008-06-15
My /etc/network/interfaces looks like this;

auto lo
iface lo inet loopback

Is that correct ?

---

### Post by Joor on 2008-06-15
Ifconfig :

eth0      Link encap:Ethernet  HWaddr 00:13:8f:93:7c:25  
          inet6 addr: fe80::213:8fff:fe93:7c25/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:75 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:276 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:13085 (12.7 KB)  TX bytes:0 (0.0 B) 
          Interrupt:250 Base address:0xc000 

eth0:avahi Link encap:Ethernet  HWaddr 00:13:8f:93:7c:25  
          inet addr:169.254.5.148  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:250 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1636 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1636 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:87325 (85.2 KB)  TX bytes:87325 (85.2 KB)

---

### Post by Pjotr123 on 2008-06-15
This is a possible cause:
[http://ubuntutip.googlepages.com/nointernetconnection](http://ubuntutip.googlepages.com/nointernetconnection)
(number 2 )

---

### Post by Joor on 2008-06-15
No its not the duel boot issue.

Hes what happend when I restart network;
* Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 6584
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:13:8f:93:7c:25
Sending on   LPF/eth0/00:13:8f:93:7c:25
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 80.166.137.121 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:13:8f:93:7c:25
Sending on   LPF/eth0/00:13:8f:93:7c:25
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by ekh on 2008-06-15
I have similar problems.

I have hesitated updating my workstation running 7.10 while in the middle of a project, but 4 days ago I had no choice.

I have a server running 8.04 lts server with Gnome destop installed also.

This fileserver is connected to the internet and is running a dual firewall between the internet and my local net.

All local computers can access files on the server, this works perfectly all the time on all computer on the local net.

However my workstation began failing to connect to the internet. First I could get it to work by disconnecting the cable or by rebooting, but after 2 days it did not work, so I updated to Hardy. Until now it have been connected only once yesterday on Hardy, where I ran the Update manager and updated.

Now multiple attempts to get the workstation on the internet has been without success.

Today both my portable  Medion 40100 running 7.10, my Lenovo T23 running 7.10, and my Lenovo T41 running 8.04 failed to get on the internet, but they got on without problems while my problem started with the workstation.

Today I have tried to connect the t23 and the Medion directly to my internet cable, also no internet connection.
The T23 has not been used for months, so it has no recent updates.

The only two devices able to connect to the internet is my server and my IP phone connected to my local net.

I have tried searching for a solution, but I did not succeed solving the problem, Any Ideas ?

---

### Post by Dawgwalker on 2008-06-15
I installed ubunto 8.04 alternate version on a older Celeron based HP that was running W2000 Professional that was networked through my Linksys wireless g router on a hardwire port.  I had done a clean W2000 install and worked through several issues that got me to a running network with two Vista machines and a network printer.  A printer was slaved and shared by the Celeron across the network.

This is my first experience with ubuntu.  My first install with Hardy Heron? wouldn't complete because I didn't have but 2meg of ram so I finally got a good install with alternate ubuntu, separate partition, dual boot with W2000.

The install would not recognize my network and configure automatically.  

I believe this was because Power Managemnet was on in W2000.

I've changed the W2000 PM option from suggestions found by googling.

I am using auto DHCP and setting nameserver IP manually using my router IP 192.168.1.1 and DNServer IP from my ISP.

Cannot PING any IP address and no server IP's I set with Administration GUI are there when I return to them.

Cannot network and cannot get to the internet like the others in this thread.

---

### Post by rogier.de.groot on 2008-06-15
Why is there no configuration for eth0 in your /etc/network/interfaces files? Shouldn't there be something like:
auto eth0
iface eth0 inet dhcp
And do "sudo /etc/init.d/networking restart" after adding those lines. Run "sudo ifconfig" again to see if you have an IP adres now.

---

### Post by dillthedog on 2008-06-15
> **dacorr said:**
> 

Also note that the above file is populated at boot every time. If it works then you know what the problem is.

Dac

I've just updated from 7.10 to 8.04 and had this problem. Fixed by copying my resolv.conf.dpkg-old  into /etc/resolv.conf, but I suspect that it will get overwritten on next reboot. Is there any way to stop that happening?

---

### Post by dillthedog on 2008-06-15
hmmm, I'm sure it's not the *right* way to do it, but I can't figure out the right way. But a wander around /etc/resolvconf/resolv.conf finds my original resolv.conf file in a file called _original_. There's a file there called *base* that's empty. Copied my original into base and it seems to work fine. Either reboot or run **resolvconf -u** (as root).

---

### Post by ekh on 2008-06-15
My problem is now solved.

When I looked at the output of:

sudo /etc/init.d/networking restart

I found out that the dhcpserver was not my Ubuntu server connected to the internet, but an older mandriva server previously serving as firewall and DHCP server, but now only acting as fileserver ( I thought ).

But after a power failure the mandriva restarted its DHCP service again, so it was now competing with my Ubuntu server.

After disabling the mandriva DHCP, and ensuring it will not start at the next boot, all is OK.

@rogier.de.groot, Thank you for giving me a hint to solve my problem :-)

---

### Post by c4bjenglacious on 2008-06-28
I am sorry to butt in but I am new to Ubuntu and I was running 7.10 and decided to upgrade to 8.04 but I have had some crazy problems. I got all of them fixed except one. I can connect to a wireless network fine but I can not get on the internet. My signal strength is 90% and I click on mozilla and I cant find google.com or anything. Please help. Also try to explain the best you can. 


Thanks,

---

### Post by alicemoon on 2008-06-29
I am having similar problems with a wired network - I can connect via wireless, I can do google searches via the wired connection but cannot access websites - see my thread so far [http://ubuntuforums.org/showthread.php?t=837413]("http://ubuntuforums.org/showthread.php?t=837413")

---

### Post by Joor on 2008-08-11
*bump*
I wanted to try linux again, but when the internet isnt working...
There is still no access , and I been looking at other threads - its something with the r8169 driver?

---

