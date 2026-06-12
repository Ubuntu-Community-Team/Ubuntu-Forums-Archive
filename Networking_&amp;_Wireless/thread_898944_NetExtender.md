---
title: "NetExtender"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by gb5757870 on 2008-08-23
This is in continuation/reference to [http://ubuntuforums.org/showthread.php?t=566019&highlight=netextender](http://ubuntuforums.org/showthread.php?t=566019&highlight=netextender)

I have installed the NetExtender GUI as we used Virtual Office and can connect to the VPN but that's as far as I can get. 

I ran an ifconfig and can see that I have an IP address on another interface:

[B]ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.100.1.101  P-t-P:192.0.2.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:64 (64.0 B)  TX bytes:40 (40.0 B)
[/B]
If I ping any clients on that network, I get a reply of "**ping: sendmsg: Operation not permitted**"

So it *almost* works.....any ideas anyone?

---

### Post by foodcoman on 2008-10-01
This used to work really well for me but something changed.  Maybe Kubuntu version caused it.  Anyway, I think I need to call Sonicwall about it.

I get a connection for a bit, then eventually packets stop sending or receiving.  I can get a RDP session to my work computer or a ibm5250 session, but it chokes after a bit then the connection is hosed.

Works fine for 1/2 minute or so.

Tried upgraded my SSLVNP firmware IE upgrading the netextender client.  No help.

---

### Post by modsbyus on 2009-07-24
I have made another post on ubuntuforums before I found this one.
I did search for anything relevant but this didn't come up then.
But, I thought that this thread would probably be better to post in considering that it already had similar responses.
Sorry for any inconvenience. 


When I try to log in with net extender I get this

Connecting to SSL-VPN Server "204.94.66.6:443". . .
Connected.
Logging in...
Login successful.
Using SSL Encryption Cipher 'DHE-RSA-AES256-SHA'
[B][COLOR="Red"]Using new PPP frame encoding mechanism
&#65533;&#65533;8j&#65533;&#65533;&#65533;&#65533; H&#65533;&#65533;SSL-VPN logging out...
SSL-VPN connection is terminated.[/COLOR][/B]
Exiting NetExtender client
JNI: LaunchNX: Exiting LaunchNX, returning (0)
Loading saved profiles...
Loaded profile: 204.94.66.6
Done.
2009-07-24 14:28:33 EDT INFO com.sonicwall.gui.NetExtenderRootPanel NetExtender disconnected
JNI: LaunchNX: mypid = 19386
JNI: LaunchNX: Launching NetExtender2
JNI: LaunchNX: Using destination IP 204.94.66.6
JNI: LaunchNX: launching NX

Connecting to SSL-VPN Server "204.94.66.6:443". . .
Connected.
Logging in...
Authentication failure: Login failed - Incorrect username/password
SSL-VPN logging out...
SSL-VPN connection is terminated.
Exiting NetExtender client
JNI: LaunchNX: Exiting LaunchNX, returning (1)
Loading saved profiles...
Loaded profile: 204.94.66.6
Done.
2009-07-24 14:28:38 EDT INFO com.sonicwall.gui.NetExtenderRootPanel Login failed - Incorrect username/password

Please pay speacial attention to the bold red text, as I believe that that is where my problem lies.
I have called SonicWALL and they did their best to troubleshoot this issue and have determined that it does work (with my username and password) in Redhat, Windows, and OSX. I also had no problems logging in and using netextender in windows.
Any help on this will be great. I have been working on this for 2 days and need this to work for my job.

---

### Post by danboy on 2009-08-04
> **modsbyus said:**
> I have made another post on ubuntuforums before I found this one.
I did search for anything relevant but this didn't come up then.
But, I thought that this thread would probably be better to post in considering that it already had similar responses.
Sorry for any inconvenience. 


When I try to log in with net extender I get this

Connecting to SSL-VPN Server "204.94.66.6:443". . .
Connected.
Logging in...
Login successful.
Using SSL Encryption Cipher 'DHE-RSA-AES256-SHA'
[B][COLOR="Red"]Using new PPP frame encoding mechanism
&#65533;&#65533;8j&#65533;&#65533;&#65533;&#65533; H&#65533;&#65533;SSL-VPN logging out...
SSL-VPN connection is terminated.[/COLOR][/B]
Exiting NetExtender client
JNI: LaunchNX: Exiting LaunchNX, returning (0)
Loading saved profiles...
Loaded profile: 204.94.66.6
Done.
2009-07-24 14:28:33 EDT INFO com.sonicwall.gui.NetExtenderRootPanel NetExtender disconnected
JNI: LaunchNX: mypid = 19386
JNI: LaunchNX: Launching NetExtender2
JNI: LaunchNX: Using destination IP 204.94.66.6
JNI: LaunchNX: launching NX

Connecting to SSL-VPN Server "204.94.66.6:443". . .
Connected.
Logging in...
Authentication failure: Login failed - Incorrect username/password
SSL-VPN logging out...
SSL-VPN connection is terminated.
Exiting NetExtender client
JNI: LaunchNX: Exiting LaunchNX, returning (1)
Loading saved profiles...
Loaded profile: 204.94.66.6
Done.
2009-07-24 14:28:38 EDT INFO com.sonicwall.gui.NetExtenderRootPanel Login failed - Incorrect username/password

Please pay speacial attention to the bold red text, as I believe that that is where my problem lies.
I have called SonicWALL and they did their best to troubleshoot this issue and have determined that it does work (with my username and password) in Redhat, Windows, and OSX. I also had no problems logging in and using netextender in windows.
Any help on this will be great. I have been working on this for 2 days and need this to work for my job.
did you ever figure this one out? I'm having a similar issue and would hate to have to spend my days in a windows vm.

---

### Post by !nkubus on 2009-12-11
Same issue here :( no solutions

---

### Post by arnoldjames on 2011-07-20
Netextender connects fine.  But it is not possible to browse into the shares/folders/directory on the host that netextender connects to.  I've looked thoroughly and it appears that it is not possible to connect, or at least anyone who has connected successfully hasn't informed how they did it.  I suspect people are simply using windows which does work in a vm as someone else posted.

---

### Post by raidoh on 2011-09-28
This looks like an old thread, but I thought I'd chime in. I just installed NetExtender 5.5.707 client on Ubuntu 10.04 x64 and it's working fine, but slow. I can browse Windows Shares from the Places -> Connect to Server configuration. Since NetExtender 3.5 wasn't installing correctly, I downloaded the latest version of NetExtender from Sonicwall via their demo website. [https://sslvpn.demo.sonicwall.com/cgi-bin/welcome](https://sslvpn.demo.sonicwall.com/cgi-bin/welcome)

Maybe a new version of the installation files would help.

Edit: I'm connecting to a Sonicwall 2400 at the office.

---

### Post by hzgone on 2011-10-22
I know this is an old post but I am having issues in 11.10

Each time I run ./install i get a message that I'm missing libssl.so.6, if i look in the /usr/lib dir and look for libssl* i see that libssl.so.6 is there along with libssl.so.7 and libssl.0.9.8  I have tried creating links to libssl.so.7 and libssl.0.9.8 and it still won't install.  I currently have version 4.0.665 of netextender and 5.something both give the same error message.

This installed no problem in 11.04 so i'm not sure if it's a problem with net extender or 11.10 any help on this would be great.  Thanks

---

### Post by raidoh on 2011-10-22
> **hzgone said:**
> I know this is an old post but I am having issues in 11.10

Each time I run ./install i get a message that I'm missing libssl.so.6, if i look in the /usr/lib dir and look for libssl* i see that libssl.so.6 is there along with libssl.so.7 and libssl.0.9.8  I have tried creating links to libssl.so.7 and libssl.0.9.8 and it still won't install.  I currently have version 4.0.665 of netextender and 5.something both give the same error message.

This installed no problem in 11.04 so i'm not sure if it's a problem with net extender or 11.10 any help on this would be great.  Thanks

As I recall, it's prompting you to approve a substitution for this libssl package and one other. I hit Yes twice and it the installation continued unphased to the question about allowing other users to use NetExtender. After the installation, you'll also need to install the latest OpenJDK-6-JRE before running the app.

---

### Post by hzgone on 2011-10-25
No prompt for anything on my install just reads to fix the missing library and stops

---

### Post by troffasky on 2011-11-09
I was having the problem with RDP sessions causing the tunnel to drop [using iperf to do a speed test was guaranteed to drop the tunnel as well] which was making administering remote servers a somewhat tedious experience. I had a suspicion it was MTU related but could never pin it down.

I have just upgraded to 11.10 and installed Net Extender 5.5.707 and the issue is resolved.

---

### Post by slicer777 on 2012-02-15
Hzgone....I am having the same problem as you. I used to have netextender running perfectly in 11.04 on a 32 bit system....and now I am running 11.10 on a 64 bit system...but I get the same error as you. Did you figure this out? Does ANYBODY have a working solution. I have symlinked and it still comes up with the same message. No prompts at all. It stops saying that I need to get the libssl.so.6 library.

---

### Post by arnoldjames on 2012-02-15
$100 to the first person to solve this.  I either use a remote desktop connection or am forced to use winXP via a virtual machine.  :confused:

---

### Post by kylebcooke on 2012-02-29
After much frustration, to install the 64 bit netExtender 5.5 client on Ubuntu 11.10/Linux Mint 12 x64 I had to create the following symbolic links:

sudo ln -s /lib/x86_64-linux-gnu/libssl.so.1.0.0 /lib/libssl.so.6 
sudo ln -s /lib/x86_64-linux-gnu/libcrypto.so.1.0.0 /lib/libcrypto.so.6

I hope this helps out others...

-Kyle

---

### Post by cyberpsycho on 2012-03-09
Kyle, thanks man! It helped a lot.

---

