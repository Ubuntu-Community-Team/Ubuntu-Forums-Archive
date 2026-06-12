---
title: "Transmission BitTorrent Client not working"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by jonathanfrost on 2009-07-14
I've been trying to get it to work but it just seems to sit there with the torrent I want to download. Any suggestions for an upgrade or is there just something wrong with it?

---

### Post by theozzlives on 2009-07-14
> **jonathanfrost said:**
> I've been trying to get it to work but it just seems to sit there with the torrent I want to download. Any suggestions for an upgrade or is there just something wrong with it?

could be the torrent, I've ran into that.

---

### Post by nhasian on 2009-07-14
the torrent should have at least 1 seed and hopefully they have a slot for you to connect to.  otherwise you'll have to wait for a slot to open up.  try a different torrent.  also if your computer is connected to a router, make sure you hae opened up your port properly so bittorrent can connect to the maximum number of peers.

---

### Post by vinutux on 2009-07-14
Yeh seeder is needed atleast 1

Try **[COLOR="Green"]Deluge[/COLOR]** instead of transmission

.

---

### Post by superprash2003 on 2009-07-14
do you have the correct ports open?

---

### Post by Le canard on 2009-08-24
Hello everyone,
I'm experiencing the same problem. Downloads don't start, no peers connect ("Downloading from 0 of 0 peers"). I've tried different torrents and I could get peers (and start to download) with only one of them. I've also tried using Deluge, but the problem persisted.
I'm using Ubuntu 9.04 (installed it today!) and I'm double-booting with XP. I tried donwloading the exact same torrents that won't work in Ubuntu using BitTorrent in XP and it worked just fine.
I checked the port and it's open. I'm using a router and I have the option "Use UPnP or NAT-PMP port forwaring from my router" checked (if it's unchecked the port closes up).
Any help is appreciated.

---

### Post by tuxxy on 2009-08-24
My solution...Deluge :)

```

sudo apt-get install Deluge
```

---

### Post by Le canard on 2009-08-25
Yesterday I tried using Deluge, but the problem persisted. Today, Transmission still doesn't work, but Deluge is.
Thanks for the advice.

---

### Post by rossjman1 on 2009-08-25
Does anyone know how to fix the transmission problem other than getting a different client? Every torrent I try to download gives the error "Data not fully available." Even though torrents have upwards of 300 to 3000 peers, I cannot download anything. Uploads are working, though.

---

### Post by metalgearac!d on 2009-08-25
I'm having the same problem...

---

### Post by CK84 on 2009-08-26
same problem here....

---

### Post by wcGary83 on 2009-08-27
I also am having the same problem! Could it be from an update? it always worked for me, now its somehow broken...

---

### Post by Cheezespread on 2009-08-27
Were the trackers from pbay ? . Heard many are having issues pbay trackers

---

### Post by CaptainPoopsock on 2009-08-27
This is most certainly a tracker issue. All piratebay trackers seem to be affected. I was able to download from torrents using other trackers.

---

### Post by wcGary83 on 2009-09-02
I thought is was a tracker issue, but deluge works fine... Also transmission can't connect to any tracker!

---

### Post by Z3r0t0l0rEnCe on 2009-09-04
I'm having the same issue were the downloads just won't start. I've tried from several different trackers and still nothing. Checked to make sure ports are open and nothin. I dont feel that a new client needs to be installed just find out the problem and fix it. I even went as far as to install a different distro of linux. Currently using Ultimate Edition 2.3 and still have this issue on another distro. So the problem to me seems to have come from an update.

---

### Post by rahrahmah on 2009-09-04
ETA: I just downloaded and tried Deluge, and it worked. Now, can any one tell me how to make that my default torrent opener?

---

### Post by pawlu89 on 2009-09-12
I think it was due to an update since, in ubuntu i don't have any firewall installed and in windows xp I can (therefore it is not due to an ISP).

Hope this problem can be fixed.

---

### Post by pawlu89 on 2009-09-12
I think I succeded.

The problem in Transmission Bittorrent Client is that it is not the latest version.

I do not like a new distro every 6 months due to several configurations, and therefore I have to update myself the repisitories.

I followed this thread and now works fine 

[http://ubuntuforums.org/showthread.php?t=1057639](http://ubuntuforums.org/showthread.php?t=1057639)

---

### Post by misfitpierce on 2009-09-12
I was having a few of the issues but I got newest version 1.74 from getdeb.net... removed old one then installed the new one and it works fine now. No problems since. Love my Transmission to death.

---

### Post by monkeyKata on 2009-09-15
Hello all,

I'm having the same problem, where downloads don't get going and stay stuck at 0 of 0 peers even if several peers are listed from the download site.  Checking my ports they are closed, even using the latest version (1.74) from the ppa.

Anyone know how to open up the ports?  Things were working fine for me, too, until one day when I think an update may have changed things.

---

### Post by durand on 2009-09-15
To open a port with the default ubuntu firewall, open a terminal (Applications > Accessories > Terminal) and type:
```
sudo ufw allow port_number
```

Replace port_number with your port. You will need to do the same with your router as well. Then just restart ufw.

```
sudo /etc/init.d/ufw restart
```

and it should work.

rahrahmah, right click on a torrent file, go to the last tab (I think) and change the default program.

---

### Post by nhasian on 2009-09-16
wow way to revive an old thread.  you should create a new one next time :)

anyway actually you dont need to mess with the ubuntu firewall.  you need to open the ports in your router.  for more info see [http://portforward.com/](http://portforward.com/)

> **monkeyKata said:**
> Hello all,

I'm having the same problem, where downloads don't get going and stay stuck at 0 of 0 peers even if several peers are listed from the download site.  Checking my ports they are closed, even using the latest version (1.74) from the ppa.

Anyone know how to open up the ports?  Things were working fine for me, too, until one day when I think an update may have changed things.

---

### Post by durand on 2009-09-16
Its hardly old..And yeah, you probably don't need to open ports on your computer but I've found that I needed to, which is why I said that.

---

### Post by SlappyPappy on 2009-09-24
"wow way to revive an old thread. you should create a new one next time"

Hey you're really friendly huh pal? Nice to see that ol' Linux hostility... I mean friendliness popping up now and again. Some things never die I guess.

BTW try Deluge, WAAAAAAAAAAAY more fun and better than Transmission. Install from Synaptic and you're good to go, it's already there for the taking.

---

### Post by comthre3 on 2011-05-03
Let me start by clearing some of the dust from this thread. Well I've upgraded to Natty (unfortunately) many issues with my media server! trying to solve one at a time, however this one seems to be a douzy! I cannot for the life of me get this thing to work! transmissions/vuse/deluge! u name it! torrent clients just wont download! i;ve tried deleting the config files, used different torrents, even experimented with different clients, the router ports are all correct! 
Can someone please look into this! Transmission is my favorite app, the web GUI and the webserver option are amazing! whats the use if its not even downloading tho...

any help would be highly appreciated

---

### Post by durand on 2011-05-03
Look up your ISP online and check if they block bittorrent access. Many do.

---

