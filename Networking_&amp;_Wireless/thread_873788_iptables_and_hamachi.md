---
title: "iptables and hamachi"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by Beacon11 on 2008-07-29
Hello all. I have had wonderful success with this forum, so I thought I'd come back to you with another problem of mine. I've posted a few times about an old Dell laptop a friend gave me. I promptly put Kubuntu on it and gave it to my little brothers for them to play with (Kubuntu and Kubuntu+wine takes care of almost any LAN game we play together, believe it or not). My dad loved the idea, but he had one issue. He wasn't comfortable with my little brothers having free reign of our wireless internet. To make everyone happy, I created a startup script that added the following rules to iptables:

```

sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A INPUT -j DROP

```

   This way, they could connect to the wireless network, but it would act like internet didn't exist. I then proceeded to set knockd up, and made it listen on the wireless interface (eth1). That way, while I'm away at college, I could just unlock the laptop from my apartment, and voila, we could play a game! Then when we're done, I lock it back up. I thought this was relatively elegant and took care of my problem... until I remembered that the laptop would be behind our router. Well that won't work! The router doesn't hand out static IPs, I can't set up port forwarding. So I thought about hamachi. Now that's a pretty good idea. What if I locked everything down, like I have now, but allowed hamachi to do whatever it pleases? Then when I unlock it, I just knock on the hamachi ip, and voila!
   Now... I'm kinda reaching my limit of linux networking. I honestly am not sure how this works. I tried simply adding the following to my previous iptables code:

> sudo iptables -I INPUT 2 -i ham0 -j ACCEPT

   But... that didn't work. I didn't really expect it to, it was too simple. I found this link ([http://www.desinc.net/node/664](http://www.desinc.net/node/664)) but it was for firestarter, which I would rather not use if I can get iptables itself working. I find the ports interesting... but I wasn't sure how to get the same results with raw iptables versus his firestarter guide.
   Can anyone help me with this? It must be possible... I'm just at the end of my knowledge in this area. I appreciate any help given :) .

---

