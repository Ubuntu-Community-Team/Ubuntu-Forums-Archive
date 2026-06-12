---
title: "I can connect to my router but cannot display internet pages HELP!!!!!!!!!!!!"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by dalek963 on 2009-10-05
I have a huge problem with my laptop running Jaunty, wherever i connect to my router the laptop shows that I have connected to it but when I open firefox (or aything else that uses the internet) it will not connect to any webpages and i cant even connect directly to my router home page
 
SOMEBODY PLEASE HELP ME, I AM FORCED TO USE WINDOWS!!!!!!!
 
also please bear in mind that I am brand new to ubuntu (moved from mac) so please make things as simple as possibe for me

---

### Post by aesis05401 on 2009-10-05
Somewhere in your router setup will be a spot to assign two DNS servers.  These addresses ponit to servers that hand out 'directions' to get to different web-sites.  Your DNS server addresses are usually provided by your ISP and are essential if you want to be able to get out to the internet.  

Does your router have DNS addresses entered?  If so, does your router have a 'Diagnostics' tab that allows you to attempt name resolution or ping outs?  For example, my home netgear router has a Diagnostic tab in the setup that lets me input host names like 'www.google.com' and the router will attempt to contact the DNS servers to get the IP address.

---

### Post by Jason Cook on 2009-10-05
A few questions for you.
 
 1. Is your connection wired or wireless. Some routers don't allow access to the router page when you have a wireless connection. If you are connected via a wire then try resetting the setting on the router. Then try to access the router page.
 2. Do you have the proper settings to connect to the internet enabled for your router?
 3. Do you use a modem, if so try plugging that into you computer and see if you can connect.

---

### Post by dalek963 on 2009-10-05
Sorry I forgot to add i was using it last night and it was working fine
and my other computers on the network are working just wine its all wireless by the way

---

### Post by aesis05401 on 2009-10-05
Alright, 

Did you disable networking using the network manager system tray icon for any reason?  That makes the network stay off even across reboots.  Additionally, can you open a terminal and type in : ```

ifconfig -a

```

Paste the output here.  The ifconfig -a command will show us all of your network interfaces along with some info about how they are configured.

---

### Post by running_rabbit07 on 2009-10-05
Does your Linksys have a encryption assigned? If so you will need to set it in your wireless settings.

Go into your network settings by right-clicking the icon and go to the tab for wireless, click edit or add, enter the name of your router, click on the wireless security tab and set which encryption is being used on your router, then give it the password. 

Also, DHCP may be turned off in your router. If so you will need to go to the edit wondow mentioned above and go to the IPv4 tab and enter the IP information it asks for. If you router is a Linksys, the default gatway should be 192.168.1.1, give yourself an IP address, 192.168.1.110 for subnet mask, enter 225.225.225.0 The DHCP asked for at the bottom should be the same as the default gateway. You may want to find all of these numbers on your Windows machine and write them down to enter on you Ubuntu. Just note that no two machines can have the same IP at the same time.

---

### Post by dalek963 on 2009-10-05
[EMAIL="tim@Tim:~$"]tim@Tim:~$[/EMAIL] ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:ba:88:dd:f6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
pan0      Link encap:Ethernet  HWaddr 1a:dc:88:f8:10:1d  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
wlan0     Link encap:Ethernet  HWaddr 00:1f:e1:d9:1f:9d  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e1ff:fed9:1f9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33316 (33.3 KB)  TX bytes:1220 (1.2 KB)
wmaster0  Link encap:UNSPEC  HWaddr 00-1F-E1-D9-1F-9D-66-39-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by miegiel on 2009-10-05
What's the IP# of your router ?

---

### Post by dalek963 on 2009-10-05
192.168.2.1

---

### Post by running_rabbit07 on 2009-10-05
From what I see, you have an IP, you subnet is there, which means you are talking to your router.

Can I ask you to run? ```
netstat -r
``` And post the outcome.

Also run ```
ping 192.168.2.1
``` and see if it shows errors or connections? Should look something like this ```
rabbit@Rabbid-Rabbit:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.704 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.602 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.563 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.597 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.579 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.574 ms

```

---

### Post by miegiel on 2009-10-05
> **dalek963 said:**
> 192.168.2.1

Well, that's the right range. If you run *route -n* in a terminal in linux you can see if it's using 192.168.2.1 for the route to the gateway.

```
:~$ route -n
Kernel IP routing table
Destination     **Gateway**         Genmask         Flags Metric Ref    Use Iface
192.168.122.0   **0.0.0.0**         255.255.255.0   U     0      0        0 virbr0
169.254.0.0     **0.0.0.0**         255.255.0.0     U     1000   0        0 eth0
10.0.0.0        **0.0.0.0**         255.0.0.0       U     1      0        0 eth0
**0.0.0.0         [COLOR="Red"]10.1.1.4[/COLOR]        0.0.0.0         UG    0      0        0 eth0**
```

Or what **running_rabbit07** said :D

---

### Post by dalek963 on 2009-10-05
> **running_rabbit07 said:**
> From what I see, you have an IP, you subnet is there, which means you are talking to your router.
 
Can I ask you to run? ```
netstat -r
``` And post the outcome.
 
Also run ```
ping 192.168.2.1
``` and see if it shows errors or connections? Should look something like this ```
rabbit@Rabbid-Rabbit:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.704 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.602 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.563 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.597 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.579 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.574 ms

```
 
[EMAIL="tim@Tim:~$"]tim@Tim:~$[/EMAIL] netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.2.0     *               255.255.255.0   U         0 0          0 wlan0
link-local      *               255.255.0.0     U         0 0          0 wlan0
default         192.168.2.1     0.0.0.0         UG        0 0          0 wlan0
[EMAIL="tim@Tim:~$"]tim@Tim:~$[/EMAIL]

---

### Post by dalek963 on 2009-10-05
With the ping it just keeps saying
 
```
 ping: sendmsg: Operation not permitted 
```

---

### Post by miegiel on 2009-10-05
Try these 2 pings :
```
ping ping.xs4all.nl
ping 194.109.21.51
```
If the 2nd works and the 1st doesn't it's a DNS problem. If they both don't work I think it's the wireless security.

---

### Post by running_rabbit07 on 2009-10-05
There is something wrong for sure. I am not sure what else it could be if you are signed in with the router's name and encryption password.

If anyone else has input, please give it a try. I haven't used wireless on Ubuntu, so I am not proficient in troubleshooting it.

---

### Post by dalek963 on 2009-10-05
> **miegiel said:**
> Try these 2 pings :
```
ping ping.xs4all.nl
ping 194.109.21.51
```
If the 2nd works and the 1st doesn't it's a DNS problem. If they both don't work I think it's the wireless security.
 
 
1st one said command not found the other started but gave the error above

---

### Post by miegiel on 2009-10-05
> **dalek963 said:**
> 1st one said command not found the other started but gave the error above

Check your wireless security/authentication settings in linux. (right click the icon in the notification area > Edit Connections > Wireless > and edit your network)

---

### Post by dalek963 on 2009-10-05
Yes all of the authentication settings are correct i have doubble and tripple checked them

---

### Post by miegiel on 2009-10-05
> **dalek963 said:**
> Yes all of the authentication settings are correct i have doubble and tripple checked them

Did you copy and paste any of the settings? I've had problems with that, but once I typed the stuff by hand it did work. Also, if your router has a web interface it might give you some info on the connection to your pc.

---

### Post by aesis05401 on 2009-10-05
Going off info I read elsewhere - try flushing your iptables rules.  
```

iptables -F
iptables -X

```

If this works then you need to rewrite some of your firewall rules.  Can I ask about the other adapters listed in your ifconfig?  Did you add all those yourself or were they installed by programs?

---

### Post by dalek963 on 2009-10-05
Sorry for my late reply I tried the last onand neather worked and i always type in passwords byhand the thing is i am fully connected and the router confirms that i am connected  just cant get the internet at all

---

### Post by aesis05401 on 2009-10-05
I'm sorry I don't have better answers for you.  I can recreate your experience by removing the DNS entries from my gateway router, or by blocking with a firewall.  Other than that I don't know.  

If you hadn't indicated that the connection was working I would suggest looking for MAC filtering on the router, but that would have stopped you in the first place. 

I don't know how many times you have rebooted, but you could try :
```

sudo /etc/init.d/networking restart

```

... Just in case an earlier command that was issued is munging things up.  Anyone else have ideas?

---

### Post by miegiel on 2009-10-05
My last ideas before I crash.
[LIST]
[*]Check your router's setup, especially the things **aesis05401** mentioned.
[*]Restart the router (don't think it will help since it works with windows, but you never know).
[*]If your router has a wired network connection try that. I know it's not the setup you want, but maybe it helps in discovering where things are going wrong.
[*]Your router might hate linux (google should help figuring this out).
[/LIST]
Good luck.

---

### Post by running_rabbit07 on 2009-10-05
In the editing wireless connections window, is there anything in the DNS Servers box?

The only other things you can check out are the settings in your router. You said you can get into your router on Windows by inputting your router's address in the address bar in a web browser. That is where you will need to fish around and find what is wrong. I am guessing you don't have a DNS server listed on your Ubuntu or there is one, but not the right one.

Are you using a Cisco router?

---

### Post by dalek963 on 2009-10-06
> **aesis05401 said:**
> I'm sorry I don't have better answers for you. I can recreate your experience by removing the DNS entries from my gateway router, or by blocking with a firewall. Other than that I don't know. 
 
If you hadn't indicated that the connection was working I would suggest looking for MAC filtering on the router, but that would have stopped you in the first place. 
 
I don't know how many times you have rebooted, but you could try :
```

sudo /etc/init.d/networking restart

```
 
... Just in case an earlier command that was issued is munging things up. Anyone else have ideas?
 
right I tried that code and i got the error message
 
```
 command not found 
```

---

