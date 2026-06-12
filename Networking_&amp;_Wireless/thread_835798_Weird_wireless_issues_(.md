---
title: "Weird wireless issues :("
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by MissingLink on 2008-06-20
First off, hello to everyone in the community!

Second, I need some help. Been using Ubuntu for about a year or so, since 7.04. Never did need to post because every problem I encountered (Ubuntu-related, of course) I always managed to solve it through means of searching for a solution on this community. But now I stumbled upon something weird and, so far, haven't been able to solve it. I'm feeling frustrated, since I found Hardy Heron to be quite useful and a pleasant experience but now I'm feeling the urge to go back to Gutsy.

So, here's the thing:

Since I upgraded to Hardy, I noticed Firefox was a bit slow. So I tried using Opera, SeaMonkey and Midori. Download speeds were normal, but browsing was SLOW. I asked my housemate if he noticed any slowdowns but he didn't, everything was normal (Vista user). I thought maybe I needed to mess with the configuration a little bit but before that I tried to connect at my parent's place. Browsing was normal, fast as always and so were the download speeds even though it was the same computer but connected to a different router.

Began searching through these forums, tried another network manager (Wicd), used another browser, tried changing the wireless rate in my pc but to no avail. Since then, I updated to Firefox 3 and Opera 9.5 thinking the problem would go away. I checked my router's firewall and everytime I browse anything it starts prompting messages like "SYN Flood to Host", "Drop invalid PPPoE-Session packet coming before PADS", "Smurf", "TCP-SYN with data", "IP Zero Length", "TCP Null Scan" and so on. I'm guessing I might have some kind of malware or something but the strange thing is, everytime I hook up my laptop at my parent's place it's everything normal! It's getting really annoying, so I would appreciate any help I could get. By the way, I'm currently using a Belkin F5D7632-4 and I use a Linksys WAG200G at my parent's house.

Cheers!

P.S.: Sorry for the long post :P

---

### Post by nickdbliss on 2008-06-21
Its ok for the long post. 

Ok did u try disabling ipv6? To do that, in the terminal type:
#sudo gedit /etc/modprobe.d/aliases 
It ll shows aliases. You can disable ipv6 here.Find  alias, alias net-pf-10 ipv6
and change to
alias net-pf-10 off #ipv6

Cheers

---

### Post by MissingLink on 2008-06-21
Tried just that but nothing changed. Thanks for the tip though. 

Cheers

Edit: I'm going to try the LiveCD and see if there's any difference. If there is, I fear I might have to format my laptop.

---

### Post by nickdbliss on 2008-06-22
That ll be worth a try. Can u give me the output of #lshw -c network
#ifconfig
and #iwlist scan ?

---

### Post by MissingLink on 2008-06-22
Here they are. The "lshw -c network" didn't show any usful information, the output just showed some options to use with the command.

Thanks for the help!

Cheers

---

### Post by nickdbliss on 2008-06-22
is that ur router with ESSID Hidden?

---

### Post by MissingLink on 2008-06-22
Yes, I always set to hidden ESSID on both routers, never gave me any problems and it's somewhat safer. Do you think there's something to it?

Edit: Oh no wait! I'm sorry I misled you, my network is the one listed in Cell03. I just noticed that now :\

---

### Post by MissingLink on 2008-06-24
I refrained from using Firefox since yesterday and, so far, didn't have any slowdowns. Guess the problem really was Firefox, don't know how but for now I'm stuck with Opera.

---

