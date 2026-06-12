---
title: "IPX in ubuntu starcraft problem"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by xokmillzo on 2007-04-23
Hello. I am relatively new to ubuntu and am an avid starcraft player. I installed starcraft through wine and got everything working except for local area networking support. I know that I somehow have to enable a primary ipx interface but I don't know how that is done. I used the information on this website
[http://koti.mbnet.fi/~hoppq/sc-howto.html#ipxnotes](http://koti.mbnet.fi/~hoppq/sc-howto.html#ipxnotes)
however it did not work. Any advice on how to get this working would be great thanks a bunch in advance

---

### Post by xokmillzo on 2007-04-23
ok update. I downloaded the newest starcraft patch and not have udp support
have been using that but now cannot see anyone's games and noone can see mine Help anyone?

---

### Post by timken240 on 2008-06-30
Install PlayOnLinux

```
sudo wget http://playonlinux.botux.net/playonlinux_hardy.list -O /etc/apt/sources.list.d/playonlinux.list
wget -q http://playonlinux.botux.net/pol.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install playonlinux
```
(code from [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html))

Then install starcraft with the PlayOnLinux wizard(requires cd), broodwar with the wizard(requires cd) and the patch 1.15 with the wizard(you don't need to download the patch it does it for you ).

Now use the new option UDP to play the game, 
Good MultiPlayer game =)

---

