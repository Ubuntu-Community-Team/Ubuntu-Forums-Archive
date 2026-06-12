---
title: "cannot access  linksys wap54g"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by Throbbing Gristle on 2010-02-16
This would be easy I suppose if I had a windows computer but I don't. So the easy install windows CD is not going to help. This is a new router I cannot access the admin page. Any body got a link to a  tuitorial? I googled for 3 hours now? I need to know what to do to my IP address at the comp to see the router. I am on 9.04 Juanty. I have not messed with a linksys so I am not familiar? Thanks!

---

### Post by hobo14 on 2010-02-16
Use **ifconfig** in a terminal to find the gateway IP.

It's usually 192.168.0.1 or 192.168.1.1

Type the correct one into your browser address bar.

---

### Post by 2hot6ft2 on 2010-02-16
> **Throbbing Gristle said:**
> This would be easy I suppose if I had a windows computer but I don't. So the easy install windows CD is not going to help. This is a new router I cannot access the admin page. Any body got a link to a  tuitorial? I googled for 3 hours now? I need to know what to do to my IP address at the comp to see the router. I am on 9.04 Juanty. I have not messed with a linksys so I am not familiar? Thanks!
In the address bar of your web browser enter 192.168.1.1 and hit Enter
Username: admin and Password: admin

---

### Post by v1ad on 2010-02-16
got beat too it....

yes precisely. the installation cd is a waste of time and disk space. default gateway is 192.168.1.1 username: admin             password: admin

---

### Post by 2hot6ft2 on 2010-02-16
With a new router it sometimes helps to unplug everything from the modem and router.
Wait a minute or 2.
Plug in the cable or dsl line to the modem and the ethernet cable to both the modem and router then plug in the modem.
Wait for it to fully power up and show that it's online.
Plug in the router and give it a minute before trying to connect to it.

---

### Post by Throbbing Gristle on 2010-02-16
If only it was that simple. If the computer will not connect to the said router the address bar will not work. Its been a three hour tour and this minnow would be lost [me]. I can connect to other linksys routers vie the address bar. Yet I cannot with this one as it is a bran new router. I found some talk of manually matching up the DNS in a static way for linux .

 How ever the 9.04 seams to have a hick up there. When I go to wired network I cannot change it to match the land line to the wap54g? My choices are not highlighting etc. Like my IP 192.168.1.1 and 255.255.255.0 Stumped here?

---

### Post by Throbbing Gristle on 2010-02-16
> **2hot6ft2 said:**
> With a new router it sometimes helps to unplug everything from the modem and router.
Wait a minute or 2.
Plug in the cable or dsl line to the modem and the ethernet cable to both the modem and router then plug in the modem.
Wait for it to fully power up and show that it's online.
Plug in the router and give it a minute before trying to connect to it.


I should not have to connect it to my modem? I had intended on using it as a repeater, and hop fully get to play with some firmware! Oh yeah looking at the wap54g it only has one port on the back for a modem. I am thinking this would not be a plug and play item over the air for security reasons so I remain stumped.

---

### Post by Throbbing Gristle on 2010-02-17
[http://taufanlubis.wordpress.com/2008/03/01/setting-up-linksys-wireless-g-wap54g-with-firefox-in-ubuntu/](http://taufanlubis.wordpress.com/2008/03/01/setting-up-linksys-wireless-g-wap54g-with-firefox-in-ubuntu/)

Found this link and since I got frustrated with the 9.04 I used BT3. Thanks for the help I in it now! Now the real head ache firmware I be back... I just know it! Thank for the quick replies!

Followed the command line instructions there they would not work on 9.10 or 9.04 until I learned that Konqueror web browser in BT3 does it perfectly all day long. Firefox would not go figure hope this helps somebody!!! It will work with Konq in 9.10 and 9.04 now!!

---

