---
title: "internet configuration"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by leomyster on 2009-08-07
Hello there,

I am a total newbie. I recently removed installed ubuntu. I wanted to access internet. I have the _static configuration_ for windows XP. Since i only know the values that the hold and not their meanings, i am finding it impossible to configure my wired connection in ubuntu 9.04. I have Ip addr., subnet mask, default gateway, preferred dns server and alternate dns server values. As i said, since i dont understand their meanings, i am not able to put these values for the corresponding configuration in ubuntu 9.04. (also there is some additional MAC addr and MTU values which i dont know at all).  Please help me out guys... Can I know where these values need to go in Ubuntu (the XP values to Ubuntu)... 

P.S.: I agree that the answer would almost be like spoonfeeding.... but, there you go - i am a total n00b...

---

### Post by leomyster on 2009-08-07
*i removed xp and installed ubuntu.... forgive my english.. its not my native language...:KS

---

### Post by ibizatunes on 2009-08-07
How are you posting on these fourms? Are you on another pc on your own network, or going somewhere else? Is it XP or Ubuntu the pc your posting from?

---

### Post by cjv8888 on 2009-08-07
> **leomyster said:**
> Hello there,

I am a total newbie. I recently removed installed ubuntu. I wanted to access internet. I have the _static configuration_ for windows XP. Since i only know the values that the hold and not their meanings, i am finding it impossible to configure my wired connection in ubuntu 9.04. I have Ip addr., subnet mask, default gateway, preferred dns server and alternate dns server values. As i said, since i dont understand their meanings, i am not able to put these values for the corresponding configuration in ubuntu 9.04. (also there is some additional MAC addr and MTU values which i dont know at all).  Please help me out guys... Can I know where these values need to go in Ubuntu (the XP values to Ubuntu)... 

P.S.: I agree that the answer would almost be like spoonfeeding.... but, there you go - i am a total n00b...

Just click on the network icon, then unclick the roaming mode, select static ip address under configuration and filled in all the values of your preferred LAN ip, subnet mask and gateway address and there you have it.  DNS servers are already under the DNS tab so you do not need to change those.

---

### Post by alphacrucis2 on 2009-08-07
> **leomyster said:**
> Hello there,

I am a total newbie. I recently removed installed ubuntu. I wanted to access internet. I have the _static configuration_ for windows XP. Since i only know the values that the hold and not their meanings, i am finding it impossible to configure my wired connection in ubuntu 9.04. I have Ip addr., subnet mask, default gateway, preferred dns server and alternate dns server values. As i said, since i dont understand their meanings, i am not able to put these values for the corresponding configuration in ubuntu 9.04. (also there is some additional MAC addr and MTU values which i dont know at all).  Please help me out guys... Can I know where these values need to go in Ubuntu (the XP values to Ubuntu)... 

P.S.: I agree that the answer would almost be like spoonfeeding.... but, there you go - i am a total n00b...

You enter those in Network Manager. The icon for it is over to the right hand side of the top status bar. You shouldn't normally need to enter MTU or MAC address. MAC address is the manufacture assigned layer 2 address of your network card (it is possible to change it from the manufacturers setting but shouldn't normally be required). MTU is the max size of the packets transmitted including headers. The default should be fine but may need tweaking down for VPN's. 

Right click on the Network Manager icon and select Edit Connections. You should be able to figure the rest out from there but ask if you get stuck.

---

### Post by superprash2003 on 2009-08-07
here's a gui guide for that [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

### Post by leomyster on 2009-08-09
thank you superprash.... that link worked for me... my nets working fine now...
as for ibizatunes query... i installed ubuntu on my laptop... and posted this thread from my desktop....

---

