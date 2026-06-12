---
title: "Internet Connection"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by orthodoc on 2007-02-25
I have installed ubuntu 6.10 amd 64 version. Its set to a dual boot with win xp.

I have a connexant based usb modem for the adsl connection provided by airtel. I am able to connect to the internet through win xp wich means the connection is fine. After logging into Ubuntu i find that the modem ligh blinks for about 10-15 seconds and then stays on. The message log shows that the modem is working fine and the upload/download rates are displayed. 

How do i make dial up work now? I know the server on their side needs log in for the connection to establish. I made changes to he provider file in /etc/ppp/peers folder. I also created the config file / resolv.confg  / and made the appropriate changes in pap-secrets and chap-secrets files.

Can someone help me out in this??? If ther is anyone with an airtel broadband connection who got through in ubuntu ...please let me know how.

orthodoc

---

### Post by koenn on 2007-02-25
> I also created the config file / resolv.confg / 
that should be **/etc/resolv.conf**, and you don't need to create it - it should be there by default. Whether or not you have to add anything to it depends on your ISP's network config. Most ISP's handle it dynamically so you don't have to touch it.

Other than that, I don't have experience with usb modems so i can't help any further.

---

### Post by orthodoc on 2007-02-25
Well! Actually sorry for the confusion. I meant i created both the config and the resolv.confg files. However the way it was before i made changes was:
```
/etc/resolv
```

and there was no resolv.confg file either in /etc or in the above folder. So I created one at both the places. It doesn't work anyway.

Thanks for the attempt, though!

orthodoc

---

### Post by orthodoc on 2007-02-26
Anybody can help me on this please. 

Am trying to jump the post. Somebody ...anybody, please help!!

Orthodoc

---

