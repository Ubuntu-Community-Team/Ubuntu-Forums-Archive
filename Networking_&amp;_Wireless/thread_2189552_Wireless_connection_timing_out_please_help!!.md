---
title: "Wireless connection timing out please help!!"
date: 2013-11-23
forum: Networking &amp; Wireless
---

### Post by tara7488 on 2013-11-23
Hi! My name is Tara and I'm freaking out because I installed ubuntu on my laptop thinking it would be better than windows and now the internet is on and off every few minutes.  This is my fourth time trying to post my concern about this because the internet keeps dropping.  This has never happened before. Please help!

---

### Post by tara7488 on 2013-11-23
I was a lot more elaborate with specifics in my last attempt to address my concerns but I only a have a few seconds before it disappears.....
Any advice or questions about my issue??

---

### Post by Number703 on 2013-11-23
What wireless card do you have? I have Ralink RT5390 and I can only get wireless on Ubuntu if I'm within ~15ft of the router. I've had problems with wireless using Mint too, especially recently. Internet's slow and disconnects every 20 minutes or so. If that's your wireless card try the solution at [http://askubuntu.com/questions/303415/ubuntu-13-04-ralink-rt5390-wont-work-after-upgrade](http://askubuntu.com/questions/303415/ubuntu-13-04-ralink-rt5390-wont-work-after-upgrade). In both Ubuntu and Mint it made things better for me, but then once I restarted I lost all ability to connect to wireless and had to undo the changes, maybe you'll have better luck. If you have a different wireless card then the solution is probably similar but I'm not entirely sure what you would do. 

When your internet disconnects can you reconnect or do you have to reboot? If you have to reboot, try
```
sudo service network-manager restart
```

instead, that's been working okay for me in Mint for now, otherwise I would have to reboot every time the Internet goes out.

---

