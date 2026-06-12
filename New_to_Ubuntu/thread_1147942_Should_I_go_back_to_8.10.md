---
title: "Should I go back to 8.10?"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by bgast1 on 2009-05-03
I just downloaded and installed Januty. I'm confused. In 8.10 I needed restricted video drivers and had to install a whole bunch of stuff which I retrieved from one of my previous post to watch encrypted DVD's. I just tried to do that with Jaunty and it didn't work. I tried to play a DVD and it didn't work either.

---

### Post by clhsharky on 2009-05-03
Install  VLC multimedia player  in Synaptic package manager and your DVDs will play. Going back to 8.10 may depend on your hardware.

---

### Post by mgranet on 2009-05-03
Run the following commands:
```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
then
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
You may be asked to accept this package even though it cannot be authenticated. This is normal; typing "Yes" means you trust Medibuntu.

---

### Post by Garrovick on 2009-05-04
It might have something to do with libdvdread3 becoming libdvdread4. I went back to 8.10 earlier today. 9.04 seemed to make my machine not as good as with 8.10. No specifics, just a perception.

---

### Post by bgast1 on 2009-05-04
It worked for one of my DVD's but another one when I chose VLC it closed up. I am attempting to use an external DVD burner/player for this. I suspect it might be because of permissions, but not sure. VLC just starts to open up and just as quickly closes. Totem won't open the DVD either. It happens with both my external and internal drive.

---

### Post by bgast1 on 2009-05-04
> **Garrovick said:**
> It might have something to do with libdvdread3 becoming libdvdread4. I went back to 8.10 earlier today. 9.04 seemed to make my machine not as good as with 8.10. No specifics, just a perception.

As a matter of fact, the packages that I went to install didn't because I got an error stating that it couldn't find libdvdread3.

It looks like I just had to install libdvdcss2. Apparently one of my DVD's was not encrypted and the other was.

---

