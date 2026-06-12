---
title: "Wireless Functionality in Network Manager Stopped Working"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by SendDerek on 2006-11-03
Alright guys/gals...  I hope you can help.

So, I'm using [this guide]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX") to get beryl and AiGLX working with my Intel 945GM chipset and the installation went bad.  The problem I had was with this line:

```

sudo apt-get install xserver-xorg-air-core linux-dri-modules-common linux-dri-modules-`uname -r`

```

Particularly the "linux-dri-modules-'uname -r'" part.  Everything else installed just fine, that was the only one that it couldn't find. So, I figured I would just skip it and continue with the how-to.

So, I get to the end and it doesn't work properly, so I decided to try and reverse everything that I had done, including removal of the packages in that step I mentioned.

I just recently found that my wireless option on the network manager isn't showing up anymore.  My wireless card is still active in my Network Settings.

I tried this line to see if I could just restart the network manager service (maybe it would clear up any hiccups):

```

sudo /etc/init.d/dbus restart

```

Well, it restarted it, but no resolve.

I then tried to reinstall what I had removed before.  No help.

Anybody have any ideas?  I would appreciate any help.

Thanks.

---

### Post by SendDerek on 2006-11-03
Bump.

---

### Post by SendDerek on 2006-11-05
Okay, so I pretty much gave up in trying and reformatted.  

It was a good idea anyways I guess... I have no idea what I just did to my system by trying to follow that guide. lol.

(Funny thing is, I followed that exact guide about 2 weeks ago and it worked perfectly!)

---

### Post by suchawato on 2007-09-17
I Have the same problem.
All of a sudden, Gone.
No wireless function on my deskbar.
I had installed kde as well, and if I attempt to launch the knetwork manager applet, nothing happens.
As far as I know, knetwork manager is just a kde interface for network manager.
It seems that network manager died.
I can access wireless on an open network only now.
This is similar to what wireless was like in Ubuntu 6.10 Edgey Eft.
I could get on the nehbors open network just fine, but any attempt to access a password protected network (WEP, WPA, etc) and no go.
I am online right now by having set up our wireless network as open.
I am glad to see that someone else has had this problem though, as I was beginning to think  I was going a little nuts.
I am currently accessing the home hetwork using Wifi Radar.
This thing is sketchy about how it will access the network as well.
Sometimes, outa the blue, the internet ceases functioning. The network connection aplet I added to the deskbar will show a signal on atho and the netwok setttings will show I am connected to the home network, WITH an IP address, but I will have no internet function.
The only fix is to disconnect, and reconnect using wifi radar.

F*ck.
I had hopped that these wireless problems had been solved with Fiesty.
Looks like we will have to wait until Gutsy to see whether it is fixed or not.
Good thing it comes out in a couple of weeks.

Good Luck.
If you need wireless, I'd try Wifi Radar in the mean time. you can download it on another computer and transfer it to your problem one.

---

