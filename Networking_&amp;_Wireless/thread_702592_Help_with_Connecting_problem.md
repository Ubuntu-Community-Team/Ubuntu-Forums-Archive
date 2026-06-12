---
title: "Help with Connecting problem"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by Anime_Wars on 2008-02-20
Recently, I have installed a wireless driver (madwifi for AR5007EG ) and have had fits of figuring out of why it didn't work.  I had followed tutorials many times over, googled the problem, and had finally given up before having discovered that in actuality it DOES work, just that every time I want to connect I have to go through the Network Settings, remove the encryption key for my network that I put in there, and then re-type it in.  Is there any way around this?  Why does this happen?  

As you can tell, I'm a linux and network newbie, so please excuse any ignorance.  Any insight or input is appreciated.

---

### Post by bsharp on 2008-02-20
I have the same card....are you using 64-bit?  The madwifi does not work with 64-bit yet, you will have to go to ndiswrapper. 

If you are using 32-bit, then you need to download the version of madwifi that is patched for the ar5007eg chipset and install it as normal.

[snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz](snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz) edited, sorry wrong link

EDIT: When I said install it like normal I meant to compile and install it, not through Synaptic.  

```
tar xvf mad*
pushd mad*
make
sudo make install

```
reboot and it should work.

---

### Post by Anime_Wars on 2008-02-20
I'm Not sure if I explained my problem clearly.

What I'm trying to say is that every time I boot up Ubuntu and open up Firefox to browse the web, it becomes clear that I am not connected online.  Then, if I go into Network Settings and re-type my Network Password, I am pretty much set, everything works fine, and I can go online.

My wifi works, I'm just looking for a reason why I have to retype my network password every time in order to go online.

---

