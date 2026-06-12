---
title: "Wierd Intel® PRO/Wireless 3945ABG problem"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by momok on 2007-02-02
hi,yal. i need some insight from you all, em, i running into a wierd problem with my Toshiba Satellite M105-S323. it has a built in wireless device from Intel Pro Wireless 3945. well, it works find in finding wifi AP, and connected just find, but when i try to browse to internet it just slow as hell, even if i place my laptop near the AP. other laptop doesn't have this problem, they just works allright. so i figured that the AP is okay. my configuration on this AP is open with 64 bit WEP. em, i try to figure this out either using XP or Linux (i have try, Suse 10.1, Fedora 6, Freespire, Kubuntu 6.06, Mandriva One, and finally Ubuntu 6.06) and i have done install-uninstall thing for almost 4 days now :( ,. could any body just explain it to me what the hell is going on with this **** laptop? (sory my language, i'm just tired of this) pleeeaaasssseee heeeeelp meeeee! :confused:

---

### Post by gillbates on 2007-03-15
sorry I cant help But I can tell you that i have exactly the same problem on my new tosheba satelite m110/l00 

so at least you are not alone out there

in my case i have identified that the reason it is so slow is that it is loseing packets (ping something) but dont know why or how

anyone ?

---

### Post by bgpaglia on 2007-04-25
Hi everybody!

I've the same problem with my toshiba L100... seems to be the processor alimentation (that is not continous...) 

CAN ANYONE HELP US?

Thank you!

---

### Post by chili555 on 2007-04-25
This will be my first triple-play! I will try to help all three of you at once. First, please disable IPv6: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4). Reboot and then post the output of:```
sudo iwconfig
ping -c3 www.google.com
```Please obscure any encryption details. Thanks.> processor alimentation (that is not continous...)Not sure what this means. French? Can you translate a bit better?

---

