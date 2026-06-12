---
title: "Constant disconnection or something alike?"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by tiachopvutru on 2007-11-23
Well, I'm currently using wireless disconnection. Although the access point, the router, is pretty far away, I'm pretty sure I didn't use to get this problem when I was using Windows XP (well, still am using XP, just barely). 

When I chat using pidgin with my friend and cousin, they told me that I log out and log in consistently.  Given that I barely notice any of that, and actually do not realize it until they told me, I'm just wondering if I have some kind of connection problem, that's all.

---

### Post by mellowd on 2007-11-23
Run a continuous ping to a remote site. see if it drops every now and again

---

### Post by tiachopvutru on 2007-11-23
> **mellowd said:**
> Run a continuous ping to a remote site. see if it drops every now and again

It does..

I did **ping google.com**  and every now and then, it would wait for very long before getting to the next ping. Once in a while, it'd drop it completely.

---

### Post by tiachopvutru on 2007-11-24
<bump>

---

### Post by mellowd on 2007-11-24
Hmmm.  There seems to be an ongoing problem with wireless cards disconecting automatically. I remember it happening to me a while back using 7.04. Right now I'm not using wireless so I can't offer much advice. There are a number of threads in the network section that deals with this specific matter. As I said, it's quite common.

---

### Post by seventynine on 2007-11-24
Used to happen to me too. I bought a cheap antenna (see here: [http://www.newegg.com/Product/Product.aspx?Item=N82E16833147115](http://www.newegg.com/Product/Product.aspx?Item=N82E16833147115)) and now my wireless connection is always steady and solid.

If you're using Network manager Applet, try to get a reading of your signal strength (by hovering your mouse over the signal bars next to the system clock). If your signal strength is less than 30% it may be time to get an antenna.

---

### Post by mellowd on 2007-11-24
> **seventynine said:**
> Used to happen to me too. I bought a cheap antenna (see here: [http://www.newegg.com/Product/Product.aspx?Item=N82E16833147115](http://www.newegg.com/Product/Product.aspx?Item=N82E16833147115)) and now my wireless connection is always steady and solid.

If you're using Network manager Applet, try hovering your mouse over the signal bars next to the system clock. If your signal strength is less than 30% it may be time to get an antenna.

It seems to be a problem with Ubuntu though. And I'll tell you why. This was the beginning of this year and I always used to disconnect in Ubuntu. In Windows XP though I never disconnected once. This leads me to believe there is nothing wrong with the hardware.

---

### Post by seventynine on 2007-11-24
> **mellowd said:**
> It seems to be a problem with Ubuntu though. And I'll tell you why. This was the beginning of this year and I always used to disconnect in Ubuntu. In Windows XP though I never disconnected once. This leads me to believe there is nothing wrong with the hardware.

Yeah probably....I had the same experience too. I never needed an antenna until I switched to ubuntu. But I think you're giving more creidit to hardware manufacturers than they deserve. Most hardware is usually poor quality that is compensated by software. For example, most wireless cards dont have a flash to store firmware. Instead the manufacturers rely on the OS to load the firmware each time the pc boots. Maybe XP had better error correction algorithms that compensated for a weak signal. I'm an electrical engineer so I know that you *can* improve a poor signal to some extent by running better algorithms. Could be some other problem as well. 

But I can share one experience from ubuntu, that is, when my signal strength is above 30% it never disconnects. So, antenna atleast relieves the problem permanently even if it doesn't treat the underlying cause.

---

