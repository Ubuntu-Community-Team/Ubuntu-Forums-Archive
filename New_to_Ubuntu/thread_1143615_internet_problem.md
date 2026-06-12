---
title: "internet problem"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by snake444 on 2009-04-30
Hi, i installed in my second computer as a second os Ubuntu 9.04 (this is where the internet problem).
that computer has XP and the internet in xp runs well
In my first computer there is XP and the internet is ok.
the two computers connected to switch(i think it called that) and the modem connected to the switch too.
the modem is B Focus 270pr but i did in his settings in the page 192.168.1.1 that it will connect automaticly to the isp with the user and pass so i think now its became router?
my problem is that in ubuntu when i open firefox i cant connect to any site i tried not google even.. it like loads the page and the bar is stuck in loading mode and no page is loading.
but i can ping every site i want and it gives response
what can i do to make the internet work well?

---

### Post by Sef on 2009-04-30
How are you connecting to the internet?  (cable, dsl, dial up, other)

---

### Post by nhasian on 2009-04-30
you said your ubuntu computer cannot access the ethernet network.

1) is the lan cable connected to the pc and router?  are the link lights on?  

2) is the computer getting an IP address from the dhcp server in the router?  To check, open up a terminal and type:

```
ifconfig
```

Tip your network adaptor is most likely eth0 and you should look for the line "inet addr: xxx.xxx.xxx.xxx" where x is your ip number

3) if you are receiving an ip address, can you communicate with the router? type:

```
ping -c 3 192.168.1.1
```

Finally, if your are not able to ping your router, and you are not being assigned an IP address from the dhcp server, give us the output of the following command:

```
lshw -C network
```

---

### Post by snake444 on 2009-04-30
im connecting with adsl
the pc that has ubuntu has also XP which the internet works in it
the pc connected to the lan and the light works
here is the ifconfig output:
[http://img257.imageshack.us/my.php?image=74650640.png](http://img257.imageshack.us/my.php?image=74650640.png)
and here is the ping output:
[http://img2.imageshack.us/my.php?image=58766127.png](http://img2.imageshack.us/my.php?image=58766127.png)

i forgot to say that the site [www.firefox.com](www.firefox.com) works in ubuntu and i can browse it

---

### Post by nhasian on 2009-05-02
well it looks like your computer is getting an ip address from the router which is good.  from the picture you posted, you can see that firefox is only loading a local file.  it isnt getting the page from the internet.

please show us the output of these terminal commands:

ping -c 3 192.168.2.1

that will check to see that you are communicating with the router.  then do:

ping -c 3 yahoo.com

this will check to see if you can talk to yahoo.com  if that fails try:

ping -c 3 209.191.93.53

this will try to reach one of the yahoo servers directly instead of being resolved through the DNS server.  If this works but yahoo.com doesnt then you know you have a problem with your DNS setting or with the DNS server.

---

### Post by snake444 on 2009-05-02
leonid@leonid-desktop:~$ ping -c 3 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms

leonid@leonid-desktop:~$ ping -c 3 yahoo.com
PING yahoo.com (69.147.114.224) 56(84) bytes of data.
64 bytes from b1.[www.vip.re3.yahoo.com](www.vip.re3.yahoo.com) (69.147.114.224): icmp_seq=1 ttl=54 time=181 ms
64 bytes from b1.[www.vip.re3.yahoo.com](www.vip.re3.yahoo.com) (69.147.114.224): icmp_seq=2 ttl=54 time=185 ms
64 bytes from b1.[www.vip.re3.yahoo.com](www.vip.re3.yahoo.com) (69.147.114.224): icmp_seq=3 ttl=54 time=177 ms

--- yahoo.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 177.970/181.421/185.029/2.883 ms
leonid@leonid-desktop:~$ ping -c 3 209.191.93.53
PING 209.191.93.53 (209.191.93.53) 56(84) bytes of data.
64 bytes from 209.191.93.53: icmp_seq=1 ttl=53 time=206 ms
64 bytes from 209.191.93.53: icmp_seq=2 ttl=53 time=204 ms
64 bytes from 209.191.93.53: icmp_seq=3 ttl=53 time=215 ms

--- 209.191.93.53 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 204.013/208.695/215.096/4.685 ms

this is the ouptput for 3 commands, as i see the ubuntu doesnt communicate with the router...
so how does he able to connect to [www.firefox.com](www.firefox.com) ??
and how can i make him to communicate with the router?
thanks.

---

### Post by nhasian on 2009-05-02
Hello snake444,

good news, based on your results form the pings we can conclude that your computer can communicate properly on the internet.  The router didnt respond to the pings perhaps due to some firewall or security feature.  

I dont know why firefox is not connecting to web pages, but i bet if you went to System->Administration->Update Manager, it would successfully check for updates on the internet and install if there were any.  can you try that? and let me know how if it works successfully?

Please also check to see if firefox is in offline mode under File->Work Offline.  make sure the box is NOT ticked.

Also check in Firefox in Edit->preferences->Advanced->Network->Connection Settings and select the option Use system proxy settings.

If none of those settings in firefox fix your problem, I'd like to test a direct connection from your ubuntu computer to your ADSL modem.  take your router out of the way temporarily to see if this will work.  let us know the results.

---

### Post by grungedoobie on 2009-05-27
I've come across a very similar problem like this.

Ifconfig wouldn't autostart at boot.  I could force ifconfig to start, but then knetworkmanager refused to come out of offline mode.

I came across this bug report:

[https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/154581](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/154581)


I followed the directions posted there by "opm8" and all is right again.

Here are the instructions I used in case you don't feel like chasing the bug thread:

1) Comment out all but the following from your /etc/network/interfaces:
auto lo
iface lo inet loopback

2) Add the user to the netdev group:
sudo adduser your_username netdev


For clarification, "your_username" in step 2 is your login name only.

Hope this helps,


The Grunge  :D

---

