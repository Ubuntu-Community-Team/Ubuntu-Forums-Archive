---
title: "use my ubuntu laptop as a &quot;router&quot;"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by djberndt on 2006-12-27
hi everyone!

I don't have a router at home, and my ubuntu laptop is **wired** to the internet. Sometimes my girlfriend want to use internet on her own laptop, so she steals the cable from my computer and puts it into her own. that's kinda annoying :mad:

the two laptops have both wired and wireless lan. one solution could be to share the internet connection through my laptop via the wireless card.

something like this: internet (wired) --> my laptop --> internet (wireless) --> gf's laptop.

Is this possible? I have read [_this_]("http://ubuntuforums.org/showthread.php?t=91370") thread, but couldn't find out if it works with wireless sharing..

thanks
/daniel

---

### Post by MrHorus on 2006-12-27
Yes, so long as you can get an Ad-Hoc/Point to Point wireless connection running then I don't see why it shouldn't work.

---

### Post by matthew on 2006-12-27
[This is an old thread]("http://ubuntuforums.org/showthread.php?t=73406") but it may give you some ideas. 

Some time back I did something moderately similar using my laptop as a router. I plugged a desktop computer that was on the other side of the house into the ethernet port on the laptop and used the wireless card on the laptop to connect to the internet. What you want to do is essentially the same only in reverse.

---

### Post by n3gbz on 2006-12-27
**firestarter**, with Internet Connection Sharing set, should work also 
-- **[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)** --

My set-up had wired and wireless switched from yours but **firestarter** did do the job.

---

### Post by djberndt on 2006-12-28
thanks for the answers, but non of it helped.. it seens like it it is a little more difficult to share internet wireless, than with a cable. I'll try to find a cheap router insted.

---

### Post by amo-ej1 on 2006-12-28
i think the easiest will be inserting a small wireless router, like a de facto standard linksys wrt54g wich you can get for <70 euro/dollar a piece in every pc store.

---

### Post by hectare on 2006-12-28
Hello ,

Type these cmd in terminal. Replace red items with what ever you have.

1. Set your wireless card to ad-hoc
**sudo iwconfig [COLOR="Red"]wlan0[/COLOR] mode ad-hoc **

2. Set the ip address of your wireless card 
** ip addr add [COLOR="Red"]192.168.1.1/24[/COLOR] dev [COLOR="Red"]wlan0[/COLOR] brd + **

** ip link set dev [COLOR="Red"]wlan0[/COLOR] up **

3(a). Lets say your gateway ip is [COLOR="Red"]10.1.1.1[/COLOR] , 
** sudo iptables -t nat -A POSTROUTING -o [COLOR="Red"]eth0[/COLOR] -j SNAT --to  [COLOR="Red"]10.1.1.1[/COLOR] **

OR

3(b). If you are using ppp(pppoe,etc) , then 
** sudo iptables -t nat -A POSTROUTING -o [COLOR="Red"]ppp0[/COLOR] -j MASQUERADE **

4. Last Step.
** sudo nano /proc/sys/net/ipv4/ip_forward **
^^ opens the editor and replace 0 with 1 and press ctrl x to save and exit the file.

5. Thats it you are done , now laptop will forward the packets.


YOUR GF LAPTOP

1. Set her wireless card to AD-HOC mode 
2. Set ip addrress of her wireless card **[COLOR="Red"]ip=192.168.1.2,subnet=255.255.255.0[/COLOR]**
3. Set her gateway to **192.168.1.1** and DNS to whatever your ISP gave you.

Thats is , you both should be online .

Good Luck.

---

### Post by djberndt on 2006-12-30
great! I'll try that as soon as I get home :)
thanks!

---

