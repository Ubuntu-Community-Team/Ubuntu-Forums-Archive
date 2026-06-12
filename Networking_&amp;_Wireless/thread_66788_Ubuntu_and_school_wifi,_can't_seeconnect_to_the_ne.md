---
title: "Ubuntu and school wifi, can't see/connect to the network"
date: 2005-09-18
forum: Networking &amp; Wireless
---

### Post by tofu1 on 2005-09-18
Ubuntu's wifi works *great* at home. I have an 802.11b network here.

At school I also have an 802.11b. But it's kinda different as in it doesn't broadcast the SSID. It *is* DHCP and I have the SSID and password right.

However, it's set up such that I have to connect, *THEN* put in my ID and password for school on the first page of any browser (it automatically goes to that page) before I can access the internet.

Ubuntu doesn't even see the signal at all. I have the correct SSID and code in the Network Config.

I'm guessing Ubuntu doesn't realize that I have to put in my school ID and pass before accessing the internet? Is there a way around this? I don't really want to put XP back on for this, I've just gotten used to linux.

Thanks!

I'm using a Dell 600m with Intel Wifi.

---

### Post by tofu1 on 2005-09-19
[QUOTE=tofu1]Ubuntu's wifi works *great* at home. I have an 802.11b network here.

At school I also have an 802.11b. But it's kinda different as in it doesn't broadcast the SSID. It *is* DHCP and I have the SSID and password right.

However, it's set up such that I have to connect, *THEN* put in my ID and password for school on the first page of any browser (it automatically goes to that page) before I can access the internet.

Ubuntu doesn't even see the signal at all. I have the correct SSID and code in the Network Config.

I'm guessing Ubuntu doesn't realize that I have to put in my school ID and pass before accessing the internet? Is there a way around this? I don't really want to put XP back on for this, I've just gotten used to linux.

Thanks!

I'm using a Dell 600m with Intel Wifi.[/QUOTE]
 Anyone? I don't wanna go back to XP :(

---

### Post by castrojo on 2005-09-19
I had this problem at my school also, never really got it to work until I used network-manager in breezy, now after it connects I launch the browser, it takes me to the login page, I put in my credentials, and now it just works.

---

### Post by tofu1 on 2005-09-20
[QUOTE=whiprush]I had this problem at my school also, never really got it to work until I used network-manager in breezy, now after it connects I launch the browser, it takes me to the login page, I put in my credentials, and now it just works.[/QUOTE]
 Sorry, can you explain what "network-manager in breezy" means? I'm a complete linux and ubuntu newbie. Thanks!

//edit: oooh I feel so stupid. Breezy is the preview release. I'm pretty happy with Horary right now.

The developers must know what was wrong with 5.04 to fix it in 5.1. I'm not sure about using a preview release though. Hm.

---

### Post by websurrfr on 2005-09-20
I am having this same issue.  I connect fine at home but cannot connect to my school wifi.  The login process is exactly the same as the original poster described.

---

### Post by bugmenot on 2005-09-20
[QUOTE=websurrfr]I am having this same issue.  I connect fine at home but cannot connect to my school wifi.  The login process is exactly the same as the original poster described.[/QUOTE]
 Okay guys, what you have there is likely that your school doesn't merely rely on encrypted WLAN (WEP/WPA) but also needs authentication through a so called *captive portal* (the redirection in the browser). You can only get to the portal after you have properly associated to the school's access point. You have to figure out whether the AP is using WEP or not and get associated properly *first* to retrieve an IP address over DHCP. It's quite likely that the WEP-key (for the AP) and your personal login (for the portal) differ.

I don't know how NetworkManager handles a lacking SSID broadcast, but it' supposed to make things easy with mutiple Wireless LANs. There are packages for Hoary here [http://bootlab.org/~j/NetworkManager/](http://bootlab.org/~j/NetworkManager/)

---

### Post by websurrfr on 2005-09-21
My school does not actually use WEP.  Anyone with a wifi card is able to access the school wifi however you need to enter your email address when the browser redirect pops up.

---

