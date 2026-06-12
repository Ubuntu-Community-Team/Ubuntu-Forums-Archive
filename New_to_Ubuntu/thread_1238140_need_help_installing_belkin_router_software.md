---
title: "need help installing belkin router software"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by hharleywood on 2009-08-12
i have a belkin n wireless router (f5d8236-4). i cant get the software installed in my comp. i have internet, but since i put the router in, my downloads freeze and take forever. its like my comp has adhd. just cant pay attention long enough to finish downloads. i have looked for different download managers but it just really comes down to the router. can anyone help me with how to get the software installed, or at least so that i can download without feeling like i  have dial up.............

thanks

---

### Post by zerhacke on 2009-08-12
Linux isn't going to run your wireless router install software because Linux is not Windows.  It's like trying to make coffee with tea leaves.

You could get it to run the router config in WINE but given that you can't finish a download you're not going to be able to get WINE in the first place.

Doesn't matter, though.  Routers are operating system independent.  The problem is not that you don't have the router software installed, since a router doesn't know what operating system you have.  I'd check your cables, (w)NIC, and other hardware first.

Most of the time you can configure your router through a web page.  Try going to [http://192.168.1.1](http://192.168.1.1) and see if you can get anything there.  It might be that you're using a B/G wireless card and the router is set to N only.

---

### Post by MyR on 2009-08-12
If [http://192.168.1.1](http://192.168.1.1) isn't correct then right click the network icon and click connection information.

The address next to "Default Route" is the one you need. Just put it in the address bar or your browser and hit enter.

This should work no matter what brand router you have.

peace

P.S. Belkin routers are horrible and you will be much happier with linksys or another brand.

---

### Post by nhasian on 2009-08-12
the router software is garbage anyway.  any adjustments you need to make in the routers firmware can be done through your web browser after you point it to your router's ip address.

to find your ip address simply type in a terminal:

```
ifconfig
```

there's lot of information there but if you are connecting wirelessly to your router than you should pay close attention to the wlan0 section for *inet addr:192.168.1.105* or something similar.  Now enter your ip address into the web browser except put a 1 at the end.  in my example i would enter 192.168.1.1 into my web browser to access the router's config page.

Before you start messing with your router settings at all you should try to determin if your downloads are failing on both ethernet as well as wifi or is it just the wifi?  plug your computer into the router with an ethernet cable and try to download some stuff.

---

### Post by nhasian on 2009-08-12
> **MyR said:**
> P.S. Belkin routers are horrible and you will be much happier with linksys or another brand.

wow I hate linksys routers.  Ever since Cisco bought them their quality has gone downhill.  Belkins work great for me but if the user is planning on using p2p apps like bittorrent then i suggest a more expensive Netgear or D-Link.

---

### Post by Grenage on 2009-08-12
Linksys make poor routers, but Belkin top them all.  It sounds like your router has issues, and I'd personally take it back to the shop.

Look into a cheap home router from Netgear or the like.  Their Enterprise kit is terrible, but the home kit is quite good.

---

### Post by MyR on 2009-08-12
> **nhasian said:**
> wow I hate linksys routers.  Ever since Cisco bought them their quality has gone downhill.  Belkins work great for me but if the user is planning on using p2p apps like bittorrent then i suggest a more expensive Netgear or D-Link.

I was just speaking from my experience. My belkin router constantly interrupted my connections despite port forwarding.  And it had to take 30 seconds to reboot after every/any change in configuration.  Plus the configuration pages themselves were not so great.  Maybe you went with a better model.

By comparison I haven't had a single problem with my linksys.

---

### Post by Terl on 2009-08-12
> **hharleywood said:**
> i have a belkin n wireless router (f5d8236-4). i cant get the software installed in my comp. i have internet, but since i put the router in, my downloads freeze and take forever. its like my comp has adhd. just cant pay attention long enough to finish downloads. i have looked for different download managers but it just really comes down to the router. can anyone help me with how to get the software installed, or at least so that i can download without feeling like i  have dial up.............

thanks

You may want to check the manual and stuff that came with your router.  I know with my Linksys router all the configuration is done through my web browser as Zerhacke mentioned in his post.

---

### Post by Garyhans on 2009-08-12
Linksys Routers are excellent. But like most routers it's the settings that cause this. Personally I would by pass the router to a direct hookup to the modem and make sure it is the router. The modem and router must be syncronyzed.

---

### Post by Grenage on 2009-08-12
> Linksys Routers are excellent

You've not had the misfortune of using their RV series?

---

### Post by hharleywood on 2009-08-12
> **MyR said:**
> If [http://192.168.1.1](http://192.168.1.1) isn't correct then right click the network icon and click connection information.

The address next to "Default Route" is the one you need. Just put it in the address bar or your browser and hit enter.

This should work no matter what brand router you have.

peace

P.S. Belkin routers are horrible and you will be much happier with linksys or another brand.


i tried this and dont really know what im looking for. my router is wired to the comp. and still has downloads being interrupted. i cconnected the comp direct to the modem, like it was just a couple days ago, and it seems to run fine, except it disconnects from the internet all together.

---

### Post by hharleywood on 2009-08-12
ok now im sitting here looking at the web page i was sent to after putting in my ip address into the browser. i am watching it switch from connected to not connected. just going back and forth.

---

### Post by MrWES on 2009-08-12
> **Grenage said:**
> Linksys make poor routers, but Belkin top them all.  It sounds like your router has issues, and I'd personally take it back to the shop.

Look into a cheap home router from Netgear or the like.  Their Enterprise kit is terrible, but the home kit is quite good.

I'll put my Linksys running Tomato firmware up against any router :), QoS is top notch.

Bill

---

### Post by kwacka on 2009-08-12
> **MrWES said:**
> I'll put my Linksys running Tomato firmware up against any router :), QoS is top notch.

Bill

I haven't tried Tomato, but a WRT54G with OpenWRT firmware is the best router I've found.

I've resisted getting the soldering iron out to attach an SD card and turn it into a web server so far (soon be winter though).

---

### Post by MyR on 2009-08-12
> **hharleywood said:**
> ok now im sitting here looking at the web page i was sent to after putting in my ip address into the browser. i am watching it switch from connected to not connected. just going back and forth.

I doubt Ubuntu is the problem in this case.

---

### Post by hharleywood on 2009-08-12
i never thought it was ubuntu. i've been using ubuntu for about 1.5 years and love it. just hit this snag trying to put 2 comps online together. im wondering if the router is messing with the dowlader, or just the connection

---

### Post by MyR on 2009-08-12
> **hharleywood said:**
> i never thought it was ubuntu. i've been using ubuntu for about 1.5 years and love it. just hit this snag trying to put 2 comps online together. im wondering if the router is messing with the dowlader, or just the connection

I was having the same problem with my belkin, swiched routers, and have been happy ever since.

---

### Post by hharleywood on 2009-08-12
> **MyR said:**
> I was having the same problem with my belkin, swiched routers, and have been happy ever since.

any suggestions of who to go with? netgear???

---

### Post by MyR on 2009-08-12
> **hharleywood said:**
> any suggestions of who to go with? netgear???
Read the previous posts ;]

---

### Post by hharleywood on 2009-08-12
well thanks to everyone who helped. didnt mean to start the great router debate of 2009 but thanks

---

### Post by markbuntu on 2009-08-13
I don't have any problems with my belkin wireless router. I talk to it with firefox and can set up everything. There is a user manual at the belkin website that explains how to do that but it is really pretty easy and self explanatory.

I do run my two desktop machines through a $5 switch (just had it lying around and thought I should put it to use) then into the router and on to the dsl modem. The wireless part also works fine with my netbook.

One thing, if you have some of the security enabled you may need to set the mac addresses of all your machines into the router. I needed to set the wireless mac addresses for my netbook and the ethernet card mac address for when I plug it in since they are different.

I did have to stealth the wireless to keep my neighbors, who all have their own wireless routers (I can see 10 from my netbook sitting on my desk), off of mine so I could use it. When I get fios I will probably put it outside a firewall and leave it open because the bandwidth will be big enough to share.

---

