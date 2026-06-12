---
title: "WPA on Intel Pro/Wireless 3945 ABG not supported?"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by fearpi on 2007-05-06
In Network Settings, I can select only "WEP key (ASCII)" or "WEP key (hex)" for my key, and therefore can't use a WPA-protected network. I'm using an Intel Pro/Wireless 3945ABG on Feisty.

---

### Post by BKK on 2007-05-07
same issue. Funny thing is that before I upgraded from edgy it worked GREAT!  I have a feeling that the new "restricted drivers" may have something to do with the problem. I hope someone can shed some light on this! I have done some searching on how to fix and nothing has worked yet. The wpa_supplicant thing and that is all installed already...

Peace

---

### Post by Josh1 on 2007-05-07
Same issue, I use wired like 0.05% of the time which is annoying.. and now even those won't work for feisty.

---

### Post by chili555 on 2007-05-07
WPA is certainly supported by the card, as:```
sudo iwlist eth1 key
```will confirm. Perhaps this will help: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by fearpi on 2007-05-07
Well, I'll give that a shot. It looks like a lot more effort than really should be required just to do what I want to do.

Also, where in SC are you, chili? I'm in Charleston.

---

### Post by chili555 on 2007-05-07
> where in SC are you, chili?Lake Wylie, up by Charlotte...beautiful here today!

---

### Post by pedroeloy on 2007-05-07
Hi have exactly the same problem with the wireless network (3945abg) and trying to connect with wpa (on Feisty).
I've tried reseting it to roaming mode under networking, then do a manually connect and the option for wpa is now available !!. 
It seems to connect but since i'm using a static ip,  all the setting for gateway, dns, etc are 0.0.0.0 except for the ip that seems correct.

To make things worst the wired connection is not working also (RealTek 8168/8111).

Any suggestions are welcome.

---

### Post by fearpi on 2007-05-07
Thanks for all your contributions. Indeed, I had roaming mode disabled. Enabling roaming mode allowed me to select the network from the notification area icon, and *then* I am prompted for my WPA key. It seems to me, then, that network-admin is outdated: Under the "Password type:" dropdown box, I can only choose WEP (hex) and WEP (ascii).

---

### Post by chili555 on 2007-05-08
> It seems to me, then, that network-admin is outdated:Well, not really. 'Roaming Mode' actually means, approximately, 'hand over control to Network Manager.' That's what the notification area icon is part of. I only roam from the breakfast room to the family room to the porch; I don't want roaming or Network Manager, so I deselect Roaming Mode.

If you need to roam from home to university to coffee shop, you want Network Manager, and you need to set Roaming Mode.

The problem becomes WPA; Network Manager handles it more or less seamlessly, wpa_supplicant without Network Manager is a bit harder.

This begs the question, how can an operating system be all thing to all people at all times and still be secure?

End mini-rant.

---

### Post by fearpi on 2007-05-08
I'm sorry, but I don't see how your reply even addresses my comment - I think there's been a misunderstanding here. I say network-admin is outdated simply because I can't use it to connect to a WPA-encrypted network. I have to use roaming mode to defer to the Network Manager in order to connect to a WPA-encrypted network - even though I'm not actually roaming. network-admin's interface doesn't even give me the option of selecting WPA; I can only choose WEP in it. And as WEP is long since cracked, effectively the problem with network-manager is that it doesn't allow me to connect to a secure network.

---

### Post by chili555 on 2007-05-08
At the risk of inciting some kind of war...> I say network-admin is outdated simply because I can't use it to connect to a WPA-encrypted network.Respectfully, there are lots of people on these forums who run wireless unencrypted or with WEP. Read the titles of the posts. Some, I guess, do so out of a false sense of security out there in the woods with no house or wireless signal visible for 5 miles. Some, I suppose, do so because they don't want to take a chance of messing up what works now. Some just don't have the budget to get new equipment. For them, the networking admin gui works just fine.

I have trouble saying it's 'broken.' I have no trouble saying it's not the right tool for every job. Neither, in my opinion, is Network Manager. I prefer the terminal and manually editing config files with vim.

---

### Post by pedroeloy on 2007-05-09
I'm willing to try the manual configuration for connection with my wireless 3945, static ip,  wpa(tkip) and feisty.

Can you help me out how to do so , ou direct me to some tutorial?

I'm willing to try an learn how to configure it, but the amount of differente configuration files i see is daunting, and most of them look redundant. 

Regards,
PedroEloy

---

### Post by chili555 on 2007-05-09
I haven't done so myself, but this looks like it will do the job. Just take each step one at a time, work carefully and check your work.

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by pedroeloy on 2007-05-10
I was able to configure it manually and only had to edit /etc/network/interface.
There was a eth1(?) interface missing in the interface file

---

### Post by chili555 on 2007-05-10
Excellent! Glad it's working for you. :)

---

### Post by usererror on 2007-05-31
I'm using WPA at home and LEAP at work with my 3945 Intel card and Network-Manager...it does work!  no command line configuring needed. :)

---

