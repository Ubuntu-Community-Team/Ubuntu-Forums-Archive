---
title: "No DNS with NetworkManager"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by zionlion on 2006-11-08
Hi everybody,

I'm facing a serious issue. I've been searching the forum for many days, but I couldn't find a solution for my problem.

here's the problem:

I'm using the latest Ubuntu 6.10 Edgy
At first I installed NetworkManager following the Howto [here]("http://ubuntuforums.org/showthread.php?t=125150&highlight=howto+networkmanager")
everything went fine except when I tried to install the wpa_supplicant using the code described:```
cd ~/wpa
cvs -d :pserver:anonymous@hostap.epitest.fi:/cvs login
```

at this point I couldn't login and therefore could't install the newest wpa_supplicant. maybe that is already the cause of my problem and perhaps someone can help me fix it.
But I went on, because edgy already has wpa_supplicant included so I tried to go on without that step.
the rest of the installations were succesful.
I rebooted and after making my Router broadcast the ssid NetworkManager succesfully connects to my WLAN-Router, but internet still didn't work.
I looked at the connection status and the DNS field shows 0.0.0.0!
I am using a static ip which is noticed by NetworkManager. Gateway as well.
Only the DNS is always set to the one above.
I tried several suggestions I found in the forum like editing dhclient.conf , resolv.conf, which is always overwritten by NetworkManager. I searched for a named.conf which is mentioned in another advice, but it doesn't exist on my system.
When I connect my laptop via wire with the router I also have to kill NetworkManager, manually edit resolv.conf and restart the network device to get connected.

Anybody who has an idea what's the cause of my problem is very welcome to tell me
.
thx in advance

zionlion

---

### Post by handy on 2006-11-08
I'm out of my depth with wireless stuff.

When you edited **dhclient.conf** did you try the:

**prepend domain-name-servers 208.67.222.222, 208.67.220.220;**

Except with your ISP's DNS addresses in place?

If you haven't here is an easy [how-to]("http://ubuntuforums.org/showthread.php?t=282034"), if you have, I'm sorry I can not help you.

---

### Post by zionlion on 2006-11-08
hi handy,

that's just exactly what I meant with I edited the dhclient.conf. that's what I tried, but with no result.
i thought the file is for dhcp isn't it. or does it effect the resolv.conf even in the case of a static ip?

anybody an idea what's the problem with wpa_supplicant? maybe that could be the cause...

---

### Post by handy on 2006-11-09
Sorry zionlion, my knowledge really quite limited, I don't know about wireless, I try to avoid it (personally), cables are great.

DNS is all the [how-to]("http://ubuntuforums.org/showthread.php?t=282034") deals with.

As I said in my previous post, wireless is beyond me.  

Someone should be able to help you out, Edgy does seem to be better for some, & Dapper better for others?

All the best!

---

### Post by erasmusp on 2006-11-09
I too had a DNS problem when I installed Edgy as a new installation. In version 6.06 you got the choice to pick which of your ETHx is your default with Network Manager. If you upgrade to 6.10 this facility stays in the Network Manager. However, if you do a clean install of 6.10, this facility is not available anymore.

To me this was a show stopper with 6.10 because our network is on a DHCP server which uses a proxy setting to connect to the network. Thus, no matter what I tried, even disabling the wireless card in Network manager, it kept on defaulting to ETH0 (wireless) and do not pick up the proxy settings on ETH1 which I need to connect to the Internet. 

Every time I delete the details it picks up on the wireless network and put in the proxy settings I DO want, if I close Network Manager and open it again, it reverted back to the old settings.

I suppose there is a manual way of editing the config files and change the default ETHx, but why take the facility out of Network Manager in the first place? :( 

Regards,
Phill

---

### Post by zionlion on 2006-11-09
no problem handy, thanks for your efforts.

I installed wpa_supplicant without cvs, but as i thought it has nothing to do with the dns issue.

so my problem still exists: networkmanager overwrites the resolv.conf and because of the fact that I use dhcp the dhclient.conf has no effect on the resolv.conf.
at the moment I manually edit the resolv.conf and restart my wlan card after every boot, but that's not very practible.

does anybody have a solution for this problem?

---

