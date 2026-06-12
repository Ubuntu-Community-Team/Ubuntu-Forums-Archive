---
title: "Can't Get Internet Working"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by dethredic on 2007-02-09
I got an old laptop from my friend and i decided to put Ubuntu on it.

Before doing so i ran it i windows 2000 (which was already installed) and check the internet and some other things. I just had to plug in the eathernet card into the laptop and the internet worked.

During the Ubuntu installation i got some errors during the installation about DHCP. It then asked me to manually input my information so put in the same info as is on my main computer (windows XP)

Once in Ubuntu i could not connect to the internet. I played around with the settings but could not get it to work.

Here is the outcome of ifconfig

eth0 Link encap: Ethernet HWaddr --:10A4:F4:FC:FA
inet addr:24.57.211.255 Bcast 24.57.211.255 Mask:255.255.255.0
intet6 addr: fe80::a4ff:fef4:fcfa/64 scope:link
Up BROADCAST RUNNINGT MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frames:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0b) TX bytes 468 (468.0b)
Interrupt:3 Base address:0x300

lo Link encap: Loopback
inet addr 127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:216 errors:0 dropped:0 overruns:0 frame:0
TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuuelen:0
RX bytes:10800 (10.5 KiB) TX bytes 10800 (10.5 KiB)

Other information.
I have a router
I have a static IP


Hope you guys can help

---

### Post by dethredic on 2007-02-10
No one?!?!?!

---

### Post by ingo on 2007-02-10
Hi, 
> man ifconfig
should sort you out.

---

### Post by dethredic on 2007-02-10
sorry i don't understand

---

### Post by carverj on 2007-02-10
Hi,
    Can you ping the outside world?
What errors are you getting with DHCP?
Perhaps you could connect with DHCP (once you get it installed correctly) and then go static ([http://www.fileformat.info/tip/linux/dynamic2static.htm](http://www.fileformat.info/tip/linux/dynamic2static.htm))
Good luck!!

---

### Post by ingo on 2007-02-11
What I meant was that you open a shell, type "man ifconfig" and read the man page. You will then be able to tell your computer which ip address to use. This might help as well [http://www.fileformat.info/tip/linux/dynamic2static.htm](http://www.fileformat.info/tip/linux/dynamic2static.htm)

---

### Post by dethredic on 2007-02-11
I typed in man ifconfig and i got a help file thingy. (i am no linux expert)

I read it and found something call address which says it will tell me what ip i should use, but i could not get it to tell me the right ip

---

### Post by ingo on 2007-02-12
Hi dethredic,

excellent, you read it. I assume you know your ip address since you stated that you have your network so set up that you have a static ip address, right? Armed now with the information contained in the manual file for ifconfig, your ip address and the name of your network interface (in your case eth0) you could try and get on the internet with the following command:
> sudo ifconfig eth0 address your_ip_address
Having done that try to ping something on the net:
> ping [www.google.com](www.google.com)
if you are successful you will get something like the following:
ingo@dicker:~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (209.85.135.104) 56(84) bytes of data.
64 bytes from mu-in-f104.google.com (209.85.135.104): icmp_seq=1 ttl=245 time=65.5 ms
64 bytes from mu-in-f104.google.com (209.85.135.104): icmp_seq=2 ttl=246 time=63.7 ms
64 bytes from mu-in-f104.google.com (209.85.135.104): icmp_seq=3 ttl=245 time=64.4 ms
64 bytes from mu-in-f104.google.com (209.85.135.104): icmp_seq=4 ttl=246 time=63.9 ms
64 bytes from mu-in-f104.google.com (209.85.135.104): icmp_seq=5 ttl=245 time=63.4 ms
64 bytes from mu-in-f104.google.com (209.85.135.104): icmp_seq=6 ttl=246 time=62.4 ms
64 bytes from mu-in-f104.google.com (209.85.135.104): icmp_seq=7 ttl=245 time=63.9 ms

Press CTRL +C to stop pinging. Your are done, happy surfing. Should you get "network unreachable" please post the contents of your /etc/network/interfaces file. Having said that, I'm not too hot on static ip addresses, having only worked with dhcp so far...

Good luck!

---

### Post by dethredic on 2007-02-12
Hmmm, I am still stuck

I got this Error after typing in the sudo part
address: Host name lookup failure

and after pinging i got another error:
ping: unknown host [www.google.com](www.google.com)

I tried my ip address from [http://whatsmyip.org/](http://whatsmyip.org/), it did not work (Its always the same so i assumed i had static)

I tried my router ip: 192.168.1.100
                also tried 192.168.1.101
                        and 192.168.1.102
                              192.168.1.103 

On my windows computer (with WORKING internet) this is the information from network connections:
Support Tab

Address Type: Assigned by DHCP    -may be i do have DHCP (was not accually there)
IP Address: 192.168.1.100
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1


Here is my interfaces file"

#skipping the stuff at the top with these ## beside it.
auto eth0
iface eth0 inet static
[INDENT]address 192.168.1.102[/INDENT]
[INDENT]netmask 255.255.255.0[/INDENT]
[INDENT]network 24.57.211.0
broadcast 24.57.211.255
gateway 192.168.1.1
#dns -* options are implemented be the resolvconf package if installed
dns-nameservers 24.57.211.1[/INDENT]

I am pretty sure the Ip address and some of the other stuff there i put it.


Hope this helps

---

### Post by ingo on 2007-02-13
dethredic,

ok, your  IP Address: 192.168.1.100 but in your interfaces file you have a different one - I would adjust that.

As I stated, I have no experience with static ip addresses, but I'm sure a proper google and a bit of reading will see you right.

Good luck and sorry I cannot be of more help.

---

### Post by reinart on 2007-02-13
What is wrong is that you have the right ip address, but you're still in the wrong network.
Change your interface file to:

#skipping the stuff at the top with these ## beside it.
auto eth0
iface eth0 inet static

    address 192.168.1.102

    netmask 255.255.255.0

    network 192.168.1.0

    broadcast 192.168.1.255

    gateway 192.168.1.1
    #dns -* options are implemented be the resolvconf package if installed
    dns-nameservers "lookup the ip in your windows"

---

### Post by dethredic on 2007-02-13
Thanks for your help Ingo


@reinart

how do i make the changes? it only allowed me to do a save as and in the connection properties i can only change the IP, Subnet mask and Gateway address.

---

### Post by ingo on 2007-02-13
didn't do a thing, but keep plugging away and somebody who knows something will eventually come along :)

---

### Post by dethredic on 2007-02-13
well ingo, do you know how i can change the things reinart referred to?

---

### Post by ingo on 2007-02-13
well, yes, but only with kde or vim - hang on, quick google...
> sudo gedit /etc/network/interfaces
should do it for gnome :)
learn something new everyday.

---

### Post by dethredic on 2007-02-13
@reinart

I tried those changes and they didn't work

i also tried the IP with 101 at the end

---

### Post by dethredic on 2007-02-15
man this is getting very annoying

---

### Post by ingo on 2007-02-16
looks like you got to read it yourself...

[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)

---

### Post by dethredic on 2007-02-16
would that be the same for 6.10? (The version that i have)

---

### Post by ingo on 2007-02-17
Good point, but I don't think much has changed in the way of networking. Good luck and post your solution if you find one (short of a reinstall) :)

---

### Post by dethredic on 2007-02-19
Didn't help :(

---

### Post by dethredic on 2007-02-21
Guess its back to windows :(

---

