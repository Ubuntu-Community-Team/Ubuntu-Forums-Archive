---
title: "How do you remote control Ubuntu via web browser"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by philidox on 2008-04-21
I have been dying to do this sense day one with Ubuntu.  I know how to remote my ubuntu computer from inside the network using vnc programs(thats too easy).  However I would like to be able to remote my Ubuntu machine from anywhere on the internet using my firefox/I.E.  I know its going to have to utilies some universal programming language more than likely java.  I know how to assign an ip address but if you wanna include that in your "Howto" please do.  I bascially need the Ubuntu version of logmein.com or gotomypc.com.  Although configurable i know logmein uses ActiveX by default for its remote control ability.  Unfortunately thats a microsoft owned program.  Please help!!!

---

### Post by sKAApGIF on 2008-04-21
Well the hardest part really, is knowing your IP address.  You talk about a home network so it sounds like you are using a gateway.  If this is the case you will have to determine your gateway's internet address.

Quickest is to point your browser to: [whatismyip.com]("http://whatismyip.com/").

Now that you have your public IP you can access your home gateway from anywhere in the world.

Something to look out for:  Some ISP's give their clients a dynamic IP address.  This means your ip will change every 24h or so.  You can call your isp and ask them, or compare your IP address over a couple of days using the above mentioned method. (If you have a dynamic ip adress you can let me know and I'll tell you the additional steps)

Next you'll have to configure your gateway to allow traffic from the internet to go to your pc.  Depending on the software you use you will have to forward different ports.  VNC (which is probable the program you're using) uses port 5800 and 5600.

How to exactly forward the ports will depend on your router.  Best thing is to try and find a guide on the internet.  You can try to find your router at portforward.com for detailed instructions.  Most probably you'll find a guide on how to port forward for VNC as well.  Make sure your pc has a static ip in your home network so that the ports get forwarded to the right machine.

If this is setup correctly, point your browser to your ip with a :5800 at the end.  For instance if you ip is 192.168.1.10 you will put in your browswer: 192.168.1.10:5800.  Make sure the "client" computer has java browser plugin installed.

Thats about it!

If you want to make it easier to remember your ip you can use a service such as dyndns.com.  You can get a name like: myname.selfip.com which will point to your ip so to access your computer you won't need to remember that long number but only type in: myname.selfip.com:5800

Troubleshooting...  Try to do the same with a computer on your local network.  Make sure you can use the browser of a local machine to control your ubuntu.  Check for firewalls.

Don't hesitate to ask any questions!

---

