---
title: "Unable to connect to router after factory reset"
date: 2016-09-08
forum: Networking &amp; Wireless
---

### Post by matti123456 on 2016-09-08
I had to do a factory rest on my router(tplink), after the reset i am unable to visit settings page of the router. When i try to connect [http://tplinklogin.net](http://tplinklogin.net), the page loads for a while then states "Server DNS address could not be found". The problem is just with [http://tplinklogin.net](http://tplinklogin.net), internet works fine.

---

### Post by jeremy31 on 2016-09-08
Post results for ```
route -n; cat /etc/hosts
```
Your router may have a setting to allow your previous behavior

---

### Post by 1clue on 2016-09-08
What's your ip address? Or more specific, what's your router ip address?

Can you ping it?

Try going to the page like this:

[http://192.168.1.1/](http://192.168.1.1/)

substitute the ip address for whatever your default route is.

---

### Post by 1clue on 2016-09-08
BTW you may have to use https.

---

### Post by matti123456 on 2016-09-08
> **jeremy31 said:**
> Post results for ```
route -n; cat /etc/hosts
```
Your router may have a setting to allow your previous behavior

I have downloaded my hosts-file from [http://hosts-file.net/](http://hosts-file.net/), it is a huge list, too long to post here. I assume that you meant hosts-file would block access to this site? I used Gedit search function to got through the list and found out that tplinklogin.net was on the list, tplinkwifi.net however was not on the list.

> **1clue said:**
> What's your ip address? Or more specific, what's your router ip address?

Can you ping it?

Try going to the page like this:

[http://192.168.1.1/](http://192.168.1.1/)

substitute the ip address for whatever your default route is.

I think my router ip is 91.156.88.1, i am not 100% sure. I did "route -n" and it is the first gateway-address on the list. Didn't want to post the whole list since i don't know the significance of them. Anyway, i tried both [http://192.168.1.1/](http://192.168.1.1/) and [http://91.156.88.1](http://91.156.88.1)

**91.156.90.176**[COLOR=#646464][FONT=sans] refused to form connection(my translation). [/FONT][/COLOR]Tplinklogin.net also gives this message and it is blocked by hosts-file.
**192.168.1.1/**[COLOR=#646464][FONT=sans] Could not connect[/FONT][/COLOR]

---

### Post by 1clue on 2016-09-08
I only want your internal ip, since you're inside your network.

Pretty much every home router has a web page you can reach by going to its internal ip address.  Some require http, some https, most allow a setting to determine which you need.

Sometimes there's a port you need to use. Sometimes wireless connections are rejected as a security measure.

Look at your owner's manual for the router, find out what the local administration page is. Not one with a domain name.  It will typically be 192.168.1.1 or 192.168.0.1 or something along those lines.

If you look at your linux box's ip address, it will be on the same subnet and be .1.  So if your linux box has A.B.C.D, then your linux box will be [http://A.B.C.1](http://A.B.C.1) or [https://A.B.C.1](https://A.B.C.1)

---

### Post by matti123456 on 2016-09-08
My router default ip is 192.168.0.1, both http and https give same message "did not respond in time".

I did not fully grasp your last point. Is that just another way to find router ip or something else?

---

### Post by Keith_Helms on 2016-09-08
Are you trying to connect over wifi?  The router may not allow access to the admin page over wireless unless you specifically enable that option.  Try connecting with an ethernet cable.  Once you've got the cable attached TP-Link's instructions say to "type in one of the following 192.168.1.1, 192.168.0.1 or http://tplinkwifi.net."

---

### Post by matti123456 on 2016-09-09
^I have tried wifi and ethernet.

I found a solution that worked on my WIN-laptop. [http://ccm.net/forum/affich-39778-network-connected-internet-no-dns](http://ccm.net/forum/affich-39778-network-connected-internet-no-dns)

> ipconfig /releasel 
ipconfig /all 
ipconfig /flushdns 
ipconfig /renew 

netsh int ip set dns 
netsh winsock reset

What would be equivalent procedure on Ubuntu?

---

### Post by Keith_Helms on 2016-09-09
> **matti123456 said:**
> ^I have tried wifi and ethernet.

I found a solution that worked on my WIN-laptop. [http://ccm.net/forum/affich-39778-network-connected-internet-no-dns](http://ccm.net/forum/affich-39778-network-connected-internet-no-dns)



What would be equivalent procedure on Ubuntu?

Try
```
sudo dhclient -r
sudo dhclient
```

---

### Post by matti123456 on 2016-09-09
> **Keith_Helms said:**
> Try
```
sudo dhclient -r
sudo dhclient
```

Worked. TY :D

---

### Post by Keith_Helms on 2016-09-09
> **matti123456 said:**
> Worked. TY :D

Worked meaning you are now able to access the admin page of your router?  If so, please mark this thread solved.

---

