---
title: "Internet on Live CD"
date: 2005-10-29
forum: Networking &amp; Wireless
---

### Post by Kulluminatii on 2005-10-29
I finally got the live cd(version 5.04) to work on my pc thanks to a lot of help from people on these forums. Now I would like to try to go on the internet with the live cd but I have had a few problems. When i first tried to go on the internet I looked around in the live cd and found this network connection thing, I provided my username, password, dialing # and clicked ok, and activated it. When I activated it I opened up firefox and when I typed in a different address It couldnt be found. I searched around on google and found a command I could use to configure the internet. I opened the terminal from the live cd and typed in 'sudo pppconfig'. Everything seemed like it was working and when I finished configuring I didnt kno where I could locate the file I just made. So how can I go about configuring dial-up on this live cd. 

Also how can I use the live cd to the fullest to make sure its the right os for me to install?

---

### Post by adwait on 2005-10-29
I guess you might have gppp installed on the LiveCD (I think), if so you can run that using
```
sudo gppp
```
If not, after you have setup the connection using pppconfig, you can connect using
```
sudo pon
```
and disconnect using
```
sudo poff
```

---

### Post by Kulluminatii on 2005-10-29
Thank you, I'll try that:D

---

