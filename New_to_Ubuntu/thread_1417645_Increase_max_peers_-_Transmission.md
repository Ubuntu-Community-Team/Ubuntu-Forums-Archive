---
title: "Increase max peers - Transmission"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by toaksie on 2010-02-27
The maximum number of peers that I can connect to per torrent is 300 which I would like to increase but it won't allow it.  I navigated to /home/USER/.config/transmission and tried to change the setting as follows when the program was closed:

    > "open-file-limit": 32, 
    "peer-limit-global": 2000, 
    [COLOR="SeaGreen"]"peer-limit-per-torrent": 1000,[/COLOR] #changed from 300 to 1000
    "peer-port": 51413, 
    "peer-port-random-high": 65535, 
    "peer-port-random-low": 49152, 
    "peer-port-random-on-start": false, 

However on saving and then restarting transmission the peer limit per torrent remained at 300.  Any suggestions to achieve my desired 1000 peers per torrent much appreciated.

---

### Post by MechaMechanism on 2010-03-19
> **toaksie said:**
> The maximum number of peers that I can connect to per torrent is 300 which I would like to increase but it won't allow it.  I navigated to /home/USER/.config/transmission and tried to change the setting as follows when the program was closed:

    

However on saving and then restarting transmission the peer limit per torrent remained at 300.  Any suggestions to achieve my desired 1000 peers per torrent much appreciated.Whoaaaa there!  Unless you have a powerful computer and dedicated symmetric gigabit connection 1000 peers is waaaaaay tooo much!

Try this calculator here to get sane parameters.  This will work for any bittorrent client.
[http://infinite-source.de/az/az-calc.html](http://infinite-source.de/az/az-calc.html)


Also try this one as well:
[http://forum.utorrent.com/viewtopic.php?id=58404](http://forum.utorrent.com/viewtopic.php?id=58404)

---

