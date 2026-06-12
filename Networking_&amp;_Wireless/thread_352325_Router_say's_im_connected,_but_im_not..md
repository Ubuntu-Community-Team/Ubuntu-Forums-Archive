---
title: "Router say's im connected, but im not."
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by Psyphre on 2007-02-03
Hi, I installed ubuntu on my laptop a short while back and everything worked perfectly. Ive gotten more accustomed to ubuntu so I decided to install it on my desktop (dual booting with XP).
Unfortunately the internet doesnt work at all.

Im using an Asus P5N32-SLI motherboard which onboard wifi and 2 gigabit LANS.
When I do *iwlist scanning* it can see my router and then I type the essid in the settings (there is no security on the router whatsoever), I use my laptop to log into the router to see if it shows my desktop's name in the client list - it does. Yet I am unable to use the internet!

I tried resorting to using old fashioned wires, but that doesnt work either.
I've even tried plugging in a usb BT VOYAGER 1020 wireless device (which is the usb version of my laptop's wifi), but that doesnt work either.

Im completely lost and dont want to go back to xp, but if I cant resolve this im going to have to :( 

Thanks in advance.

---

### Post by danielph on 2007-02-03
Hi

I would suggest plugging in your wired connection first as this should be easier to get working. (It sound like wireless driver is loaded which is good)

When plugged in goto System, Administration, Networking and check that the wireless is off and that DHCP is set in wired. Toggle the wired connection off and then on and wait. It should tell you it is configuring.

Tools you may need:
Open up terminal and type ```
ifconfig
```You should see eth0 device and an IP address. If you do you should be able to ping the router. Of course you will need to know your routers ip address eg ```
ping 192.168.0.1
```Let us know what results you get.

---

### Post by Psyphre on 2007-02-03
thx for the reply!

I tried it however i dont get an ip address when i type ifconfig.
I know what the router's ping is so I tried "ping" followed by the ip but it just says this:
*connect: Network is unreachable*

I looked at the MAC address provided with ifconfig and checked in the router's client list. My desktop is defintely listed there, so it is somehow connected.

---

### Post by danielph on 2007-02-03
OK so you are not getting an IP address. This could be down to the router not giving you one or the client not asking for one correctly. To confirm that the client works enter a manual IP address for the wired network with the correct subnet mask and default gateway, check ifconfig again and then try the ping.

If your router is 192.168.0.1 then 192.168.0.50 should be ok with mask of 255.255.255.0. Gateway is routers IP

---

### Post by Psyphre on 2007-02-03
Ok I tried that, I was excited when I saw a flash in the network icon. Usually the only item that shows in there is "lo", but now "eth0" is also present. When I opened up firefox, it seems to be loading,  but nothing ever shows; just a blank white page and the cursor has the busy icon. It is an improvement however, since usualy I get a "page cannot be displayed" message in firefox.

---

### Post by danielph on 2007-02-03
Did the ping work? If it did it is most likely a DNS issue, try adding the DNS address in the network settings. Use the router address for DNS

---

### Post by Psyphre on 2007-02-03
Yeh tried pinging aswell, that has improved a little aswell. Instead of 1 line of text, it goes on a whole array of sequences. All of which still result in "Destination Host unreachable" however.
The first thing I did when the internet wasnt working was enter the DNS in.

---

### Post by danielph on 2007-02-03
Some routers don't except pings. You could try typing the routers ip in firefox:

[http://192.168.0.1](http://192.168.0.1) for example.

Try restarting the network with the current settings```
sudo /etc/init.d/networking restart
```and watch for errors

---

### Post by Psyphre on 2007-02-03
Sorry for hte delay I have no idea whats going on now. It now takes 15 minutes just to login (used to take 2 seconds). A while ago the keyboard stopped working, now my ubuntu is REALLY slow. Why is it being so difficult.

Anyway I know this router accepts pings since Im doing it on my laptop right now.
typing the router address into firefox doesnt work, it just says "unable to connect", and restarting the network brings up a whole array of errors. Unfortunately I cant copy and paste since theres no internet on the desktop (obviously), but something im seeing alot is "no such device". These appear for ath0's and wlan1 and eth2. As far as im aware i dont have eth2 or wlan1 anyway.

---

### Post by danielph on 2007-02-03
That doesn't sound so good. Did your networking work on the Live CD on this machine? What network card are you using?

```
lspci
```

I have to go out for a bit, but will be back later to try and help if you are still having problems.

---

### Post by Psyphre on 2007-02-03
No i didnt really try it with the liveCd. The card is one that came with the motherboard. In XP I was really impressed with it since in the past getting wifi working was such a pain, but with this wifi, it worked straight away with no hassle.

Anyway thx alot for the help I appreciate it. If you dont mind maybe speak over msn or something later? Would be alot easier and quicker than this forum.

For now my ubuntu has gotten ridiculous. Its really really slow, which is strange because it only applies to anything ubuntu related. If i open up my windows partition in ubuntu, it loads instantly. Open my home folder and it takes like 5 minutes. I think im going to have to reinstall it.

---

### Post by danielph on 2007-02-03
yeah sure give me a shout on yahoo, but I am not sure what I can do if it is all on a go slow :(.

---

