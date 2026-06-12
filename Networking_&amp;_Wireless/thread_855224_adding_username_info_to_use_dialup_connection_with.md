---
title: "adding username info to use dialup connection with Ubuntu"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by wpshooter on 2008-07-10
Are the following instructions given at "**dialup modem how to ****setup dialer**" regarding adding "usernames" to dip and dialout groups still valid and required to get a dialup account to work under Ubuntu ?

And if so, is the "username" the user name as per the ISP dialup account or the Ubuntu/login "username" ?

**NetworkAdmin, in System => Administration => Networking **

[B]kppp 
and gnome-ppp (vwdial graphical frontend). 
With all these tools, to establish a dialup connection, the user has to be member of the "dip" and "dialout" groups, so put all users who are supposed to connect via dialup into these groups: 

 $ sudo adduser USERNAME dip
 $ sudo adduser USERNAME dial, outwhere of course USERNAME has to be substituted.[/B] 



Thanks.

---

### Post by Vorian Grey on 2008-07-10
I didn't have to do any of that with 8.04. I just added the necessary information in gnome-ppp and it worked first time. The same holds true for Kppp when I tried it in the past. Of course, I had to use Wvdial first to get online to get Gnome-ppp. 

The username you want to use is your Ubuntu username.

---

### Post by df6269 on 2008-07-10
Please use rp-pppoe if you want to dial up via pppoe mode.

---

### Post by wpshooter on 2008-07-10
> **df6269 said:**
> Please use rp-pppoe if you want to dial up via pppoe mode.

Is this program installable thru Synaptic ?  

How is it different from gnome-ppp ?  

Which would be the preferred program to use if I am using an external serial dialup modem ?

Thanks.

---

