---
title: "Port Forwarding?"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by umwhat on 2011-04-12
There's this game I'm trying to play, but I have to run it under wine. I asked if it even works under wine and I was told it worked fine. Problem is, to play it, I need to open a port or something. I have no idea how to do that. I ran the portforward checker and it says, "Your port is NOT OPEN or not reachable!"

This is the game, btw: [http://ace-spades.com/](http://ace-spades.com/)
maybe one of you guys could try it and tell if it works or not for you?

The client launches itself when you click one of the server links on that page. It doesn't do anything in FireFox, but in Chrome it brings up this box telling me I could be attacked, gives me some strange address, and that's all it does. When I try it with FireFox under wine I get, "Could not connect to server."

tl;dr
How do I port forward and/or disable my firewall?

---

### Post by josephmills on 2011-04-12
first what kind of router do you have?

---

### Post by umwhat on 2011-04-12
uuum... I'm not exactly sure. It's a router I got from Verizon. I don't know jack about any of this stuff.

---

### Post by josephmills on 2011-04-12
ok on the router its-self it should tell you. the router is the thing that is connected into your phone line/cable/fiber optics.  this is what a router looks like [http://www.google.com/images?client=ubuntu&channel=cs&q=router&um=1&ie=UTF-8&source=og&sa=N&hl=en&tab=wi&biw=1024&bih=627](http://www.google.com/images?client=ubuntu&channel=cs&q=router&um=1&ie=UTF-8&source=og&sa=N&hl=en&tab=wi&biw=1024&bih=627)

---

### Post by umwhat on 2011-04-12
Verizon Actiontec MI424WR Rev. F?

[http://upload.wikimedia.org/wikipedia/commons/9/95/Actiontec_MI424WR_Verizon_back.png](http://upload.wikimedia.org/wikipedia/commons/9/95/Actiontec_MI424WR_Verizon_back.png)
It's that one. Is that what you're looking for or is there something else?

---

### Post by josephmills on 2011-04-12
> **umwhat said:**
> Verizon Actiontec MI424WR Rev. F?

[http://upload.wikimedia.org/wikipedia/commons/9/95/Actiontec_MI424WR_Verizon_back.png](http://upload.wikimedia.org/wikipedia/commons/9/95/Actiontec_MI424WR_Verizon_back.png)
It's that one. Is that what you're looking for or is there something else?

yes that is what I was looking for. you are going to have to log into your router and change the port forwarding options. To log into your router first go up to your network connections and right click then select connection info. a new box will pop up with info. One of those pieces of info is your default route. Now open firefox or what ever browser that you would like and where you would put [www.whatever.com](www.whatever.com) put in your default route number (don't forget the the dots) a page will come up and it will ask for a password it is admin or password or passwd by default. Unless you have a business account with you internet service provider. If you dont know much abouyt this I would not do it but look into it some more find a pdf manual file of your router. or you could go to [http://portforward.com/](http://portforward.com/) I think they charge  money now (not sure)  I am not a gamer so I dont know if that game works, but port forwarding is used for a lot of thing but mainly to remote view stuff. hope this helps

---

### Post by umwhat on 2011-04-12
That worked! Thank you!
I still can't connect, though. Portforward was able to pick up everything too. I'm guessing it's because the client.exe won't even start up. When I try to start it I get, "The program client.exe has encountered a serious problem and needs to close." Not sure where to get help with this. The wine forums seem pretty dead. Any idea what the problem could be? The server creator works. Maybe I need to configure wine? I wouldn't know what to do, lol. :(

---

### Post by Zookalicious on 2011-04-14
umwhat, my first question, are you green or blue? Because if you're blue, GET OUT OF HERE!

Just kidding. You don't need to forward a port for AoS unless you're hosting a server. 

Check the WINE page for more details. [http://appdb.winehq.org/objectManager.php?sClass=application&iId=12965](http://appdb.winehq.org/objectManager.php?sClass=application&iId=12965)

I wrote up a How-To near the bottom of the page that should help you get started. Let me know if you have any questions.

---

