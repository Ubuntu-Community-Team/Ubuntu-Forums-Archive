---
title: "Firestarter and teamspeak server"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by drewk1 on 2006-10-02
I have a teamspeak server running on my ubuntu box which i can access via my network connection ok ( I know the server is working ) but no one can access from the internet.

I have installed Firestarter to share my internet connection and addded the policy Allow service 8767 everyone.

I tried grc.com shields up to see if the port is open but it reports it stealthed?

Does anyone have any ideas?

thanks

---

### Post by darth_vader_ca on 2006-10-02
are you behind a router, if you enable the port on the router.

cheers.

---

### Post by drewk1 on 2006-10-02
i'm running the teamspeak server on my unbuntu box which connects to the internet through an ethernet adsl model ( speedtouch 530 ) so no router.

I'm stumped now, oh well time for sleep and another play around tomorrow](*,)

---

### Post by darth_vader_ca on 2006-10-02
Thomson/Alcatel SpeedTouch 530 ADSL seems to have a port forward option available. you should call your isp and get the directions on how to enable port forwarding. check your gateway address. if its 192.168.1.1 the speedtouch 530 seems to have routing and nat capabilities. attempt to use admin and admin for the password and un for the device.

cheers.

---

### Post by drewk1 on 2006-10-03
thanks for the reply i'll check those options

---

### Post by drewk1 on 2006-10-04
I think I have found the problem.
The modem is acting as a router and needs to be switched into bridge mode so the Ubuntu box sees the IP assigned by my ISP rather than the IP of the modem/router.

I think this sounds plausable, I've just got to find details on how to get the modem into bridge mode. 

I await Alcatels response.

If anyone has an Alcatel 530 and has switched it into bridge mode I would appreciate some advice.

Andy

---

### Post by halfvolle melk on 2006-10-06
I don't think you need to set it to bridge, I think you just need to forward the appropriate port to your back-end network. All ST modems that I know of can be configured at 10.0.0.138

---

