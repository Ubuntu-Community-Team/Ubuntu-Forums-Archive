---
title: "Very odd network problem!"
date: 2005-09-13
forum: Networking &amp; Wireless
---

### Post by leezer3 on 2005-09-13
Hi guys,
I seem to have a very odd network problem on my hands-
I've just set up a new network, running through a DSL 504T modem router, for the new broadband connection. On Windoze, all runs fine, but on Linux I cannot get domain names to resolve either in Firefox or Synaptic.
Both ping & dig seem to work OK, as does accessing pages directly through IPs in Firefox. (Can't seem to get the ubuntu updates url to resolve thou)
To be quite honest, I'm stumped :(

Any thoughts?

-Leezer-

---

### Post by s_p_a_r_k_y on 2005-09-13
seems like you have no DNS servers entered in your /etc/resolve.conf file. This should be done automatically if youh have DHCP but sometimes I guess things get fscked up. Try adding the name servers your see in windows ```
 ipconfig /all
``` to your resolve.conf file

---

### Post by leezer3 on 2005-09-13
Checked there already  :???: 
I've got this:
> nameserver 192.168.1.1
which is the same nameserver as in Windoze- The way it should work, is that the router acts as a DNS forwarder, forwarding the query to the appropriate NS. I've also tried specifiying a couple of DNS servers fished of the portforward list, but the same result.
Also, the fact that dig will resolve names suggests to me that the problem lies elsewhere.

Cheers

-Leezer-

---

### Post by guivega on 2005-09-13
Mhh, I'm having exactly the same problem but with dlink dsl-g604t, which is basically the same than the 504 plus dsl modem.

it seems to me that the router is not able to translate the IP addresses to ubuntu, Azureus bittorrent works just fine and anything I ping also works fine.
The funny thing is I can ping "www.google.com" from terminal or from the router ping utility, but when I type that in the browsers it never gets there, or it takes ages.

I also noticed that the router cannot recognize ubuntu's  name, it finds my windows computer name but it shows "unknown" for the ubuntu computer. (I think I named it "Ubuntu"), though the IP is correct.

I add my ISP dns IP to the network setting utility but they disappear next time I re-open it.

Any suggestions?

---

### Post by leezer3 on 2005-09-13
Snap!
From a bit of Googling, it seems that the firmware for the DSL-504T is buggy, and the suggestion is to add your IPs DNS to resolve.conf, but as far as I can see it doesn't go through the router. (Ping & dig stop working altogether, suggesting that its failing at translating from the router to the net)

I've also seen a suggestion to disable IPv6; How do I do this?

EDIT: Just opened a thread at the unofficial D-Link support forums- [http://www.dslreports.com/forum/remark,14353447](http://www.dslreports.com/forum/remark,14353447)

Suggestions?

Cheers

-Leezer-

---

### Post by leezer3 on 2005-09-13
Most recent update on these probs:

From Googling, I've found there is a bug in the V1x D-Link T series firmware. specifically with the DNS proxy. If you are in the US/ Australasia, then you are in luck- Update the firmware with that from the D-Link site, if not you will have to wait for the 2x firmware to get to the UK/ Europe.

Some places I've found on the net seem to suggest that it is possible to flash with the 2x firmware from a US/ AU model, but I wouldn't reccomend this, unless you are prepared to bust your router.

Cheers

-Leezer-

---

### Post by leezer3 on 2005-09-13
[QUOTE=guivega]Mhh, I'm having exactly the same problem but with dlink dsl-g604t, which is basically the same than the 504 plus dsl modem.

it seems to me that the router is not able to translate the IP addresses to ubuntu, Azureus bittorrent works just fine and anything I ping also works fine.
The funny thing is I can ping "www.google.com" from terminal or from the router ping utility, but when I type that in the browsers it never gets there, or it takes ages.

I also noticed that the router cannot recognize ubuntu's  name, it finds my windows computer name but it shows "unknown" for the ubuntu computer. (I think I named it "Ubuntu"), though the IP is correct.

I add my ISP dns IP to the network setting utility but they disappear next time I re-open it.

Any suggestions?[/QUOTE]
Just checked the D-Link site, and 2x firmware is available for your model!
Update & your issues should be gone.
Wonder how long it will take for my DSL-504T to be done  :roll: 

-Leezer-

---

### Post by guivega on 2005-09-13
I didn't mention it but I already had the last Australia dlikn update, I'm in Malaysia and that was the suggested update for me (through googling). 

Now it connects way better with the ISP, but that NAT  problem, (or whaterver it is) hasen't been solved 100%. I'll try with static IP and then let you know. Today I wont have time for that, but I'll do it tomorrow.

Thanks

---

### Post by guivega on 2005-09-14
Well, it is working right now, but I'm not really sure if what I did solved it or the router has decided to start working by itself!

Lets see:

1) I logged in as root in gnome, (do a search in ubuntuforums to know howto)

2) Then I opened System>Administration>Networking

3) Make sure  you select or add a location, I selected ubuntu (it was already there but for some reason it is not selected by default)

3) Add a host: Ip=127.0.0.1 and my computer name (ubuntu)

4) add dns: (check your isp dns servers) mine are 202.188.0.133 and 202.188.1.5

5) Then apply. ok, logout and login as my normal user

and everything was working

Now, the weired thing is that If I do System>Administration>Networking again it takes a while to start and all the settings are gone, so, i don't dare to go there again! (if anyone has a solution for that... shout it!)

I'm not saying this is the solution, but it is something to try.

I also use DMZ for the ip of the ubuntu computer, and to make sure that the router uses always the same ip for my ubuntu computer I enter the MAC address for the ethernet card and the IP that I want for it in the HOME>DHCP>STATIC DHCP SERVER of the dlink router web configuration manager.

try it and let me know if it makes any difference in you machine

Guillermo

---

### Post by chinaski on 2005-09-23
I've had same problem with same router (g604t) and my solution was to change router.

I managed to connect with firefox with the trick of disabiliting IPv6 support (type about:config in ff url window and you get all settings) but nothing else worked, only http.

so I changed router, it's sad but I could not find solution for this issue anywhere.

---

### Post by leezer3 on 2005-09-27
Have a look at my D-Link router howto- There is a bug with the DNS proxy in these routers, which means that Linux apps don't work. Basically, what you need to do is to set up a static IP, & enter your ISP's DNS servers into resolve.conf, as detailed in my howto.

Cheers

-Leezer-

---

### Post by cosine7 on 2006-05-10
i am having exactly the same problem, i have upgraded the firmware on the dlink, but to no avail, ipv6 disable in firefox worked, but cannot get anything else to work. is there any way to disable ipv6 in ubuntu?](*,)

---

### Post by Xurtzem on 2006-05-18
hmhm...i don't think the nameserver that u hve in ur resolv.conf is right...i had mine as 203.94.27.243 chck out urs..and update it .

---

### Post by cosine7 on 2006-05-18
You are right. Once i manually configured /etc/resolv.conf and /etc/network/interfaces and made the computer static, all my internet problems went away. Oh and make sure u edit them in nano etc, every time i did it in the gnome gui it did not work.

---

