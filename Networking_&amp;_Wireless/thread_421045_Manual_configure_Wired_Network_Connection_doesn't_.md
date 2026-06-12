---
title: "Manual configure Wired Network Connection doesn't work in Feisty Fawn"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by dirken on 2007-04-24
Hey everyone,
I was wanting to connect to the wired network at school but therefor i have to manual configure eth0 (my wired network card). So in edgy I go to Networking and double click the wired icon and i can begin to configure. Afterwards my internet works fine trough the wired connection.
Now I am on Feisty Fawn and wanted to do the same but when trying to do so I have to disable the roaming mode function and i choose for static IP and configure but then the wired connection dissappears from my  list in the panel (the default networkmanager applet in Feisty Fawn) and the IP etc i configured are not applied.
I really need this wired connection so can anyone plz help?

Greetz..
Dirken

---

### Post by lassegs on 2007-04-24
When you disable roaming mode, network-manager stop handling the connection. Then you configure it through System -> Administration -> Networking. Hope that helps.

---

### Post by starbase1 on 2007-04-24
What is "roaming mode"? (For a non techie!)

---

### Post by Alekc on 2007-04-24
I suppose that roaming mode is than you are going around with your notebook, so nm-applet tries to connect to best network which he can find (for example from work to home network changes). But if you are using it at home with only one network you can safely turn it off and input manual params.

---

### Post by PartisanEntity on 2007-04-24
> **Alekc said:**
> I suppose that roaming mode is than you are going around with your notebook, so nm-applet tries to connect to best network which he can find (for example from work to home network changes). But if you are using it at home with only one network you can safely turn it off and input manual params.

If you turn it off you can only connect to WEP or am I wrong?

---

### Post by Alekc on 2007-04-25
For some strange reason... yes :(
Nm-applet can use wpa, network manager no :(((((

---

### Post by starbase1 on 2007-04-25
> **Alekc said:**
> I suppose that roaming mode is than you are going around with your notebook, so nm-applet tries to connect to best network which he can find (for example from work to home network changes). But if you are using it at home with only one network you can safely turn it off and input manual params.

Then it sounds like setting 'Roaming Mode' to On is the best way to get started quickly when you try it for the first time?

Nick

---

### Post by Gujs on 2007-04-25
I have just wired network adapter and when i disable roaming mode and configure static ip, i lose vpn connection in nm-applet. It would be realy great if I could manage vpn through nm-applet.

---

### Post by dirken on 2007-04-26
> **lassegs said:**
> When you disable roaming mode, network-manager stop handling the connection. Then you configure it through System -> Administration -> Networking. Hope that helps.

Thanks for the reacting everyone but lassegs this doesnt work. I can configure it manually but when i run ifconfig i haven't got any ip altough i've set it up myself!
Last thing i tried is right clicking the network manager applet on the panel and disable wireless, then i go to networking by navigate to system -> administration. I now opened the wired connection and disabled roaming mode and set up the ip etc. Now i see that my wireless device is down but my wired device still hasn't got an ip!
Any more help?

Greetz..
Dirken

---

