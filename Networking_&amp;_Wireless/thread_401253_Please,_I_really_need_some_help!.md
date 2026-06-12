---
title: "Please, I really need some help!"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by cebert on 2007-04-04
I configure my wireless NIC (WMP54G) 

I inputted the settings (ESSID, IP, Subnet Mask, Default Gateway) and then went and had a look in network tools, I am sending and recieving packets, but when I try to browse the web, I get server not found.

So i thought restarting couldn't hurt, when I reloaded, the part where it "configures network interfaces" just hangs, after about 10 minutes, it goes a text based loaded, were I can move the text starter around and type stuff in.

(its the third time I've had to reinstall Ubuntu. *sigh*)

Thanks.

---

### Post by Kobalt on 2007-04-04
Can you please post the result of the following command line : ```
iwconfig
```

---

### Post by pillu on 2007-04-04
I think you are connected to the network if you can send or recieve packets. But you cannot resolve the hostname due to dns error. Could you open the terminal and type the following commands plz
```
ping 209.85.135.99
```
If you get a response then type
```
ping www.google.com
```

See if you get a response to one or both of the commands and post the result here.

pillu

---

