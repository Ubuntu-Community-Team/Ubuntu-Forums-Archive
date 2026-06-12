---
title: "Any reason I can't use my Linksys router with DSL modem?"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by BetterSense on 2008-03-04
I have a Linksys with DD-WRT. I can connect with the DSL modem but when I plug in the router, it doesn't work either through the wireless or wired. What settings in the Router control webpage do I need to change to get it to work with my DSL modem?

---

### Post by mozetti on 2008-03-04
Whatever information you use on your computer to connect using the DSL modem, like username/password, need to be put into the router. Instead of your computer "dialing" and supplying the username/password, the router will do it.

Also make sure the DSL modem is plugged into the WAN port on the back of the router.

---

### Post by BetterSense on 2008-03-04
It's weird though, because I booted into Windows and used the setup disc to setup the DSL. Then I booted back into ubuntu and it just worked without my having to input a username and passwd. And still does; when my router doesn't work I just swap the cables to go straight to the DSL modem and reconnect. I tried putting my ATT username and passwd into the router's control panel and it still didn't work.

---

### Post by tl3000 on 2008-03-04
> **BetterSense said:**
> It's weird though, because I booted into Windows and used the setup disc to setup the DSL. Then I booted back into ubuntu and it just worked without my having to input a username and passwd. And still does; when my router doesn't work I just swap the cables to go straight to the DSL modem and reconnect. I tried putting my ATT username and passwd into the router's control panel and it still didn't work.

This is not an Ubuntu networking issue and should be addressed in more applicable forums such as:

[http://www.dslreports.com/forum/ilec,swbell](http://www.dslreports.com/forum/ilec,swbell)

Brief explanation:
Your DSL modem is probably setup to perform PPPoE login and DHCP, that's the reason why your connection works as you've described.  The modem must be placed into a bridged mode in order for you to use the router.  Then, you can put the login ID and password into the router to have it do the PPPoE login and DHCP instead of the modem.  This setup is independent of the OS you're using.  You'll find that you would have the same problem under Windows trying to run with an added router.  Thus, you should check with your DSL provider's help resources and/or the forum listed above to change the modem to operate in a bridged mode.

HTH...

---

### Post by stream303 on 2008-03-05
Or, make sure that your router isn't using the same address as your modem!  disconnect the router from the modem, and try to use the router setup page to check the address.

---

### Post by klick.here on 2008-03-05
I have a similar problem.  I can get online with ubuntu fiesty fawn fine if I plug in to the DSL modem and i can use the linksys router to see my windows network but i can't use them both at the same time.  I have to unhook from the router and plug the ethernet cable directly into the modem to get online.  Windows computers can use the router to access the modem to get online fine.  Any suggestions? I'm brand new to Linux and I think it's really cool.  Thanks :)

---

### Post by steveneddy on 2008-03-05
> **klick.here said:**
> I have a similar problem.  I can get online with ubuntu fiesty fawn fine if I plug in to the DSL modem and i can use the linksys router to see my windows network but i can't use them both at the same time.  I have to unhook from the router and plug the ethernet cable directly into the modem to get online.  Windows computers can use the router to access the modem to get online fine.  Any suggestions? I'm brand new to Linux and I think it's really cool.  Thanks :)

Seems as if you have your PC dialing in instead of the router.

Disable any PPOE software, then hook up the router to the PC and the modem to the router, in the WAN slot.

This is really just basic networking, fellas.

If you have a network of PC's that have to access the internet, make the router keep the connection, not a PC on the network.

Read the Linksys manual about setting up your connection.

You will put your user name and password in the router so it keep the connection alive.

---

### Post by klick.here on 2008-03-05
Thanks i didn't get a manual with my router it was a hand me down.  I don't know much about networking because windows wizards did it all for me in the past.

---

### Post by klick.here on 2008-03-05
Also i have alwys plugged in the modem into the slot labled "uplink" and not wan.  i have already put my username and password into the router.  I will try switch that and see what happens.  Sorry to be such a NOOB but I'm trying to learn here.  Thanks

---

### Post by klick.here on 2008-03-06
ok it's fixed.  The dsl modem had to be disconnected from the pppoe internet conection and then the router was able to connect through it.  It didn't matter that the router and the modem had the same IP address.  It's funny that windows didn't really care that i had it it hooked up wrong.

---

### Post by steveneddy on 2008-03-06
> **klick.here said:**
> ok it's fixed.  The dsl modem had to be disconnected from the pppoe internet conection and then the router was able to connect through it.  It didn't matter that the router and the modem had the same IP address.  It's funny that windows didn't really care that i had it it hooked up wrong.

Glad to see you got it working.

Please mark this as solved.

---

