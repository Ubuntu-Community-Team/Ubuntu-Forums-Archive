---
title: "Ubuntu 22.04.3 LTS Destination host unreachable only on LAN"
date: 2023-12-05
forum: Networking &amp; Wireless
---

### Post by akkynescu on 2023-12-05
Hello there, 

I'm new to Linux and I mostly operate my Ubuntu server based on what I find on the internet (please explain to me as you are talking to a dog :D). I don't know if this post has to be on here or on the new-to-Ubuntu one :-k

Moving on with my problem, in the last 3 months I made from an old computer a little home lab (jellyfin, PhotoPrism, and a shared folder to move around devices on my LAN). I installed the casaOS web GUI for an easier experience. Everything went okay for those months until the power went off for 2 hours. Nothing to worry about, the computers were off, and nothing was damaged, but the moment I turned on the server I was unable to connect to the server at all, no web GUI, no jellyfin, and no ssh (keep in mind that I use this only locally). If I ping my computer from the server I get the "Destination host unreachable" message (the same goes if I ping my PC from the server). The thing is that I can ping any other outside website and even the router (192.168.1.1). I assume that this has something to do with my router being off for 2 hours and something changed but I cannot find what, because I didn't make any changes to it anyway, it's just like it was for the past 2 years.

The way I have this set up is like this: 
[LIST]
[*]I have 1 Windows 10 computer that I use every day, where I try to connect to the server (IP: 192.168.1.3); 
[*]1 computer with the Ubuntu server (192.168.1.7); 
[*]and 1 basic fiber optic router (gateway 192.168.1.1) from my internet provider (where both computers are connected). 
[/LIST]

I searched the whole internet for the last couple of days but nothing is working... Hope someone here can help me out :) . 

Due to the Ubuntu servers being on another computer, I cannot really copy and paste my terminal here (maybe I'll take some photos with my phone) but let me know what info is needed to figure this out.

---

