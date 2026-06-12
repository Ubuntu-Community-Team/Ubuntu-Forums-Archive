---
title: "Netgear WG311T"
date: 2005-04-10
forum: Networking &amp; Wireless
---

### Post by escuchamezz on 2005-04-10
r

---

### Post by escuchamezz on 2005-04-11
comeon someone must know    
 :cry:  [-o<

---

### Post by bobmitch on 2005-04-11
Can you at least 'ping' your router/default gateway?

(If it`s netgear, it will probably be 192.168.0.1 )

---

### Post by escuchamezz on 2005-04-11
nope ping doesn't work either (although it does in SUSE 9.2)
what do you suggest i should do, install madwifi?

---

### Post by bobmitch on 2005-04-11
[QUOTE=escuchamezz]nope ping doesn't work either (although it does in SUSE 9.2)
what do you suggest i should do, install madwifi?[/QUOTE]

Well, I have a wg311v2 - which works out of the box with dhcp - but in warty, it didn`t, but I had no problem using ndiswrapper, so that is probably your best bet.

There are countless guides on the forum, but if you need a hand, let me know, I`ll help if I can.

---

### Post by sophomERIC on 2005-04-13
I had the same problem and most of the other ideas I found on the forum did not work either. Here is what I did to get my card working :

Terminal :
sudo ifdown ath0
nano -w /etc/network/interfaces

        broadcast 192.168.1.255
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid Cerberus
        # dns-* options are implemented by the resolvconf package, if installed
        wireless-key1 [key in hex here]
        wireless-defaultkey 1

sudo ifup ath0


for some reason it needed those defaultkey and key1 values where it previously just have wireless-key. When I just had the wireless-key value the DHCPDISCOVER requests would not locate my DHCP server. Kind of weird, but its working and I'm happy.

---

### Post by escuchamezz on 2005-04-14
what is this broadcast ip address, is that the ip of the router?

thanks a lot dude, i'll try that

---

### Post by bobmitch on 2005-04-14
[QUOTE=escuchamezz]what is this broadcast ip address, is that the ip of the router?

thanks a lot dude, i'll try that[/QUOTE]

The broadcast address isn`t the router ip address / default gateway address.

[Here](http://www.linktionary.com/b/broadcast_address.html) is a decent explanation.

---

### Post by escuchamezz on 2005-04-14
ok i understand, thanks

---

### Post by woodpecker on 2005-04-15
Hi

I have the same networkcard. If your problem still occurs and you do not have to use the dhcp, try using a static ip. Mine works just fine with static ip.

---

### Post by escuchamezz on 2005-04-16
I can't get the Internet working when i use static ip, i turned DHCP off in the router settings, and manually set 192.168.0.2 to be the static ip for the computer (gateway left blank) and the router even shows that the internet is connected but i can't access any website - very strange, when i turn DHCP back i can access the world wide web again (this is all in windows xp). how do i get this sorted so it works with static? once this works i'll try static out in ubuntu.

---

### Post by escuchamezz on 2005-04-16
ok i got static ip working now (in windows xp), but it still fails to ping the router in ubuntu. How did you configure it, are you using gnome or kde?

---

### Post by escuchamezz on 2005-04-18
I got it to work in kubuntu with dhcp  :-) 
but the speeds suck squirel balls, but i guess that's another story  :???:

---

