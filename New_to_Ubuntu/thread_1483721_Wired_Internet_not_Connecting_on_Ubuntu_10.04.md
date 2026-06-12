---
title: "Wired Internet not Connecting on Ubuntu 10.04"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by RRauh on 2010-05-14
Hi. I am a very new Ubuntu(Linux) user. I have installed a Dual-boot of the 64bit v10.04LTS in tandem with XP Professional. I am interested in Ubuntu as a solution to offer to my 50+ yo clients for daily use as opposed to Windows. I am also running an instance of Ubuntu in windows with VirtualBox. 

I can not get the dual boot to connect to the internet. Here is what I have tried from gleaned info on these forums:

1. Adjusted Power Management setting on network adapter to "not turn off adapter on power off".

2. Attempted  sudo mii-tool eth0. Result was SIOCGMIIPHY on 'eth0' failed:Operation Not Supported.

3. Attempted sudo dhclient eth0. Result was after several attempts through same port (64): No DHCPOFFERS Recieved    No working leases in persistent databse.

4. Final. I manually configured the wired connection on  IPv4 settings per the Pocket Guide offered by Keir Thomas (very useful).

I also can not get the effects to work for the desktop after several different attempts.

I am at a loss at this point. Here are my PC specs:

Custom Built 
Q6600 Intel Quad Core 
Asus Striker 680i motherboard
8800GTS Gpu Nvidia
2-Raptor WD 74gb HD
1kilo PSU 
I am not sure if you require more details on the machine if so let me know. Any help would be great. I want to be able to use this OS before implementing it with my clients, obviously.

Apologies if I rambled at all. I tried to keep it concise.

Thanks,
Bobby

---

### Post by Ozymandias_117 on 2010-05-15
What is the output of ```
ifconfig
```

---

### Post by RRauh on 2010-05-15
I ran ifconfig and this is what I got:

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:81:18:ab
          inet addr:192.***.*.*  Bcast:192.***.*.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe81:18ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:5808 (5.8 KB)
          Interrupt:33 Base address:0xc000

eth1      Link encap:Ethernet  HWaddr 00:1a:92:81:28:aa
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:34 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1582 (1.5 KB)  TX bytes:1582 (1.5 KB)

I replace my ip with stars if you need those numbers please let me know.

---

### Post by Ozymandias_117 on 2010-05-15
Could it possibly be a DNS issue? Try, in a terminal, ping 74.125.67.105  (A Google IP)

---

### Post by rck1640 on 2010-05-15
I am having a similar problem. I tried to ping google and it time out. Did a trace route. It showed a path to the DSL modem but did not go further. Where do I check the DNS entries from DHCP?

BTW -- I just did an network upgrade from 8.04 to 10.04.

---

### Post by RRauh on 2010-05-15
> **Ozymandias_117 said:**
> Could it possibly be a DNS issue? Try, in a terminal, ping 74.125.67.105  (A Google IP)

I attempted this and it could not locate the destination. I am running through a cable modem and then through a router. I am really lost with this. Could it be because I set up Ubuntu in 64bit and XP Pro is only set up in 32bit?

---

### Post by -humanaut- on 2010-05-15
Try sudo ifconfig ifup

---

### Post by RRauh on 2010-05-15
> **-humanaut- said:**
> Try sudo ifconfig ifup
What does this do? I want to know more about the way it works.  While I appreciate the advice. if you can give me an idea of what the code you are telling me to try actually does, it could help me further my understanding of this system. I want to learn this system not just beg advice or help.

---

### Post by Ozymandias_117 on 2010-05-15
> **-humanaut- said:**
> Try sudo ifconfig ifup

Er... Are you talking about ```
ifconfig eth0 up
```?


To OP: What I think he is trying to do is make sure your ethernet is enabled, which is what my previous command will do. ifconfig is the command for modifying things to do with wired network interfaces, eth0 is the name of your first ethernet port and up tells it to turn it on.


Note: The other option is ```
ifup eth0
``` but as far as I know, it's just supposed to make ifconfig easier to use... Taken from the ifup man page: >  The program does not configure network interfaces directly; it runs low level utilities such as ifconfig and route to do its dirty work.

---

### Post by RRauh on 2010-05-15
Oz, thank you for the explanation.

I tried the following:

ifconfig ifup; results "ifup:error fetching information:device not found"

ifup eth0; results  "ifup:failed to open statefile /var/run/network/ifstate: Permission Denied"

Proper Results from ping test was "Destination Host Unreachable"

When I followed the manual st up for the ip addy; subnet mask; default gateway and dns ip addy and then restarted it shows that the wired connection is active but I cannot connect through anything. I even ran the test again after the manual adjustment.
Have I done something wrong?

---

### Post by Ozymandias_117 on 2010-05-15
Sorry, I forgot to mention, you have to be root to run the commands :P so try ```
sudo ifconfig eth0 up
```

To check DNS issue, use ```
cat /etc/resolv.conf
``` you should have an entry or two that says > nameserver 8.8.8.8 (Or whatever your DNS is. If you want to test a different DNS you can use 8.8.8.8; It is Google's DNS server)

Edit: Just a note, I have no idea why he wants you to do this :P The fact that it shows up in ifconfig should mean it's up

---

### Post by -humanaut- on 2010-05-16
> **Ozymandias_117 said:**
> Er... Are you talking about ```
ifconfig eth0 up
```?


To OP: What I think he is trying to do is make sure your ethernet is enabled, which is what my previous command will do. ifconfig is the command for modifying things to do with wired network interfaces, eth0 is the name of your first ethernet port and up tells it to turn it on.


Note: The other option is ```
ifup eth0
``` but as far as I know, it's just supposed to make ifconfig easier to use... Taken from the ifup man page:

Thank you yes that is what I meant. opps. I used ethtools for a long time so a simple sudo eth0 up use to be sufficient.

---

### Post by RRauh on 2010-05-16
Well i did it that way and nothing happened..nothing at all.

---

### Post by Ozymandias_117 on 2010-05-16
> **RRauh said:**
> Well i did it that way and nothing happened..nothing at all.

It wouldn't show anything. As long as it didn't throw any errors, it worked.

Did you try to DNS thing?

---

### Post by pdc on 2010-05-16
try 

>  sudo ifup eth0


and enter your sudo password when asked

---

### Post by RRauh on 2010-05-16
Just did and it showed : Name server 192.***.*.* my default dns

I will try the ifup again...be right back.

---

### Post by RRauh on 2010-05-16
Sorry for the double post.
OK, the constant restarting is getting annoying.. 

sudo ifup eth0; result "interface eth0 already configured"

I am overclocking my CPU could that be causing issues?

---

### Post by Ozymandias_117 on 2010-05-16
> **RRauh said:**
> Sorry for the double post.
OK, the constant restarting is getting annoying.. 

sudo ifup eth0; result "interface eth0 already configured"

I am overclocking my CPU could that be causing issues?

It looks like your ethernet is enabled, and correctly configured (assuming your IP address DNS gateway etc. is correct). I'm not sure what else it could be... But I don't see an overclocked CPU causing problems.

---

### Post by RRauh on 2010-05-16
I pulled the ip address and dns gateway etc... stuff from the ip config and network connection details in windows.

---

### Post by RRauh on 2010-05-16
So, I guess I should uninstall it?

---

### Post by daimaru on 2010-05-16
have you checked your routing? 
```
gg@alita:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.178.0   *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         fritz.box       0.0.0.0         UG    0      0        0 eth0

```
the default (fritz.box) is my gateway. does yours show your router or your routers ip address?
if your route is not set properly do this assuming that your 
routers ip address is[COLOR=Red]:192.168.178.1
[/COLOR]```
sudo route add default gw 192.168.178.1 eth0
```

otherwise check my quick guide on manually setting up ethernet or wireless connection from terminal [here ]("http://ubuntuforums.org/showthread.php?t=641598")

---

### Post by RRauh on 2010-05-16
Thank you for the link I will spend some time this evening on this.

---

### Post by RRauh on 2010-05-17
I went through the steps here and others from your link. I have not had any success with any of them. I am not sure what else to do. I am going to attempt to remove and reinstall the 32bit version in its place as an attempt to resolve this issue. I am hopeful that this can make a difference. ( I have to admit I am not optimistic that this will work.) 

Thank you for all the feed back to help me correct this. I am a bit frustrated at this point so I will post in this thread if the reinstall does or does not work.

---

### Post by RRauh on 2010-05-17
Here is an interesting fact that I noticed.

On live CD the network adapter has ubuntu tell me it needs to install proprietary drivers, but after install of the complete system it gives no indication again of the drivers needing to be installed. After "clean" install ( I say clean b/c it came with some errors to start off and end with) I attempted everything mentioned in this thread again to no avail....still no wired connection to internet.

---

### Post by RRauh on 2010-05-18
so no ideas?

---

### Post by legatek on 2010-05-18
I was having the same problem until I blacklisted ipv6 in etc/modprobe.d/blacklist.conf. Open that file and add "blacklist ipv6" without the quotes, to the end of the file.

---

### Post by Xtian_1028 on 2010-06-22
Hello! I am also a newbie in using Ubuntu 10.04.

We have the similar problem. I also have the same response as you regarding the:

ifconfig eth0 up

and 

ifup eth0

but, when use ping the google ID, I kept on receiving 64 bytes from that ping

I'm so lost... please help. n_n

Thank You!

---

### Post by Xtian_1028 on 2010-06-22
It seems that after following the steps you have stated, Ihave managed to conclude that:

eth0 has been enabled, 

I can even get 64bytes in every 60msec when I ping [www.youtube.com](www.youtube.com),

I can see my gateway IP address when Itype <route> in the terminal...

Hmm... Basically, my original problem was that the networks manager says that I am connected using eth0, but when I type in yahoo.com in the URL, I cannot load the whole webpage of the Yahoo! website.

Meaning, it just says "logging in yahoo.com..." endlessly.

I wonder what is the problem? Thank You! 


Press **ENTER** to look up in Wiktionary or **CTRL+ENTER** to look up in Wikipedia

---

