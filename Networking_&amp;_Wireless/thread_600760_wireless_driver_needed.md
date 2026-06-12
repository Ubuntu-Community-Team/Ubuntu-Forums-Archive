---
title: "wireless driver needed"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by xtremer on 2007-11-02
i just installed ubuntu 7.10 on a toshiba m105 with Intel PRO/Wireless 3945
, does anybody know where can i get its driver ????

---

### Post by georges023 on 2007-11-02
If someone could confirm(or correct ;)) what will follow would be nice, thanks.


I think that your Wi-Fi card is of type bcm43xx (broadcom) then you will need :
1.NDISwrapper 1.8 + ndiswrapper-utils for feisty, NDISwrapper 1.9 + ndiswrapper-utils for gutsy (Download them from an internet enabled computer or with an alternate connection.)
2.The drivers files from windows or the toshiba web site. (.INF, .SYS, .CAT) (see above)

Then follow those instructions:
> echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i /home/dave/Desktop/bcmwl5.inf
sudo ndiswrapper -m
sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper/bcmwl5/*.conf
sudo modprobe ndiswrapper

Thanks again to Minuk for pointing me out to the whole bcm43xx issue and the other aforementioned sites.

NOTE: Be sure to uninstall bcm43xx-fwcutter if you installed it already. Also, make sure to get the correct bcmwl5.inf and bcmwl5.sys files from Dell or whoever.


P.S: Instructions aren't from me but i folllowed them for my Dell Inspiron B130 on both Feisty Fawn and Gutsy Gibbon ;)
P.S2: Be sure to adapt the instructions to your case, it's more of a pointer then a How To.

Hope that helped :)

---

### Post by grEnAlEins on 2007-11-02
If it uses the BCM driver mentioned above, all you need to do is enable all of your repositories and you can download a restricted driver that will solve your problem.  I did this with my broadcom card.  I do not know if this will work for you though.

---

### Post by georges023 on 2007-11-03
> **grEnAlEins said:**
> If it uses the BCM driver mentioned above, all you need to do is enable all of your repositories and you can download a restricted driver that will solve your problem.  I did this with my broadcom card.  I do not know if this will work for you though.
I tried downloading the driver for my Wireless card (Dell Inspiron B130) and it didn't work so i followed the instructions above, like i did before in Feisty Fawn.

---

