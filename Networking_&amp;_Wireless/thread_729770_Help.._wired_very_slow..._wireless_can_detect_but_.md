---
title: "Help.. wired very slow... wireless can detect but cant connect. and weird too."
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by Snoopdoggie on 2008-03-20
i have just installed ubuntu on my laptop "Asus G1s", i cant seem to get the internet to work normally. what i mean is that i can access ubuntu forums and sites but i cant go to [www.google.com](www.google.com) or yahoo.com etc. it just gives me an error loading page. what can i do to solve it? 

also i have a real slow connection on ubuntu compared to vista or xp.. downloading updates works fine but really slow at 2xx b , max at 32kb. but on xp and vista i can reach 800kb++ ... whats the problem? weird thing also the wireless adapter works fine but when i key in the key it just prompt for the key again and again without sucessfully getting wireless at all.. its a WPA personal TKIP... duno what to do now... i am a newb with this.. >.< hope some masters could help me out. ^^

---

### Post by pedro_orange on 2008-03-20
> what i mean is that i can access ubuntu forums and sites but i cant go to [www.google.com](www.google.com) or yahoo.com etc

This does not make sense. Ubuntuforums & google are both accessed from your machine via "the internet"

> weird thing also the wireless adapter works fine but when i key in the key it just prompt for the key again and again without sucessfully getting wireless at all

This looks to me as though you have got the key or method of authentication incorrect. Check the "Show key" box so you can ensure the key you have entered is correct. 
Are you sure of the method of authentication?
Have you tried setting your router up with a WEP key and seeing how that worked? I have no problems connecting to a 64-bit hex WEP Open system.

Hope you see light at the end of the tunnel.

---

### Post by Snoopdoggie on 2008-03-20
> **pedro_orange said:**
> This does not make sense. Ubuntuforums & google are both accessed from your machine via "the internet"

yes i know.. its weird. it just timeouts... all other pages too.. except for the ubuntu forum wiki etc.... =.=

EDIT:

ok i found the culprit.. its the ipv6 thingie on hosts.. removed it and speed is back... but still cant access other pages except [http://ubuntuforums.org/](http://ubuntuforums.org/) and wiki etc.. 


> This looks to me as though you have got the key or method of authentication incorrect. Check the "Show key" box so you can ensure the key you have entered is correct. 
Are you sure of the method of authentication?
Have you tried setting your router up with a WEP key and seeing how that worked? I have no problems connecting to a 64-bit hex WEP Open system.

Hope you see light at the end of the tunnel.

yup i am sure coz there are 4 laptops on xp and vista running with the same key and authentication, and 3 desktops plugged into the switch.. currently this is the only computer here running on ubuntu.. i did the "sudo aptinit install wpaapplicant" thingie already.. but not sure what else to do..

---

### Post by dhavalbbhatt on 2008-03-20
I have seen many posts on slow internet and most of them seem to be from the past - or at least from those days when people were not aware of the ipv6 fix. For me however, my internet has been so slow (regardless of whether I use FireFox, Epiphany or Opera), and I am not sure why. I have even tried to modify the modprobe/alias file - but that has not helped either. Any clue as to what might be going on?

Thanks

---

### Post by Snoopdoggie on 2008-03-20
> **dhavalbbhatt said:**
> I have seen many posts on slow internet and most of them seem to be from the past - or at least from those days when people were not aware of the ipv6 fix. For me however, my internet has been so slow (regardless of whether I use FireFox, Epiphany or Opera), and I am not sure why. I have even tried to modify the modprobe/alias file - but that has not helped either. Any clue as to what might be going on?

Thanks

sorry bro, i cant help u coz i cant help myself either >.<

i got the internet running now... read some post about the wpa thing on sticky..

problem still exists.. 

i cant google > returns a timed out error. <--- wired ethernet. <-- now fixed after reboot. dont know if its gonna last. @@

change the wpa thingie to wpa2 on router back and forth using only alpha's then only numerics vice versa.

got the icon on top to turn to an antenna showing 98% "its blue now!" coverage on wireless but cant connect to internet still.. dont know if its connected or not. one side of the 2 gray dots is green, other side is gray.. not going anywhere,.. then turns grey again,then goes back to wired connection... i have the cable still unplugged anyway..

thx orange for the help! appreciate it very much ^^

**EDIT**

ok, i cant find a solution for this atm so i am using mac address filter atm.. hope someone with ideas can help me out thx.

---

### Post by stream303 on 2008-03-27
How's your dns?

In the dns tab of the network preference panel, does it show the primary and backup dns addresses of your ISP?

If you don't know them, you can alternately use another dns server - I prefer the ones listed at the bottom right hand page of:

[http://www.opendns.com](http://www.opendns.com)

If you like, you can also place the primary and backup dns addresses inside the router's setup page and now any machine you hook to your router will use those.

---

