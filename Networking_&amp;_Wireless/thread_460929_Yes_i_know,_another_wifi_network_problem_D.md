---
title: "Yes i know, another wifi network problem :D"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by netreg on 2007-06-01
Hi all,

i did a fresh install of Ubuntu 7.04 on my Inspiron 9300 and got wireless working with WPA encryption and i thought Happy Days \\:D/  it all seems to work fine and I am truly on the road to leaving MS Windows, or so i thought. 

Using dhcp, it works.  The little wifi icon appears in the top right, and i can select the wifi network that i want to join. 

However, i want to set a static IP, so following various posts and modifying the interfaces file, i set a static ip, restart the network and bang...  no wireless icon, no connectivity, nada :(

I just cannot get wifi to work with a static IP ](*,)   My cabled connection does work with a static IP.

Is there something I am missing???????

Has anyone come across this type of issue????? 



thanks
Darren

---

### Post by blazercist on 2007-06-01
how bout trying to setup static dhcp on your router, most routers have the option to assign IP's by MAC address, that way you'll always get the same IP for your machine and you don't have to disable DHCP.

---

### Post by Genecks on 2007-06-01
Computer IP correlates to IP given by router. Tell router to send the mail where you live.

---

### Post by netreg on 2007-06-01
> **blazercist said:**
> how bout trying to setup static dhcp on your router, most routers have the option to assign IP's by MAC address, that way you'll always get the same IP for your machine and you don't have to disable DHCP.

I have a linksys WAG354G which doesn't have that ability unfortunately.

but thanks for the advice.

thanks
Darren

---

### Post by MrObvious on 2007-06-01
Go to the network settings, disable roaming mode, choose the network and set it up statically from there by choosing a Static address from the drop down menu. If you want screenshots I can post them. However for me to do so I need to be reminded to check this thread via PM since there are so many of them :D.

Hope this helps!
Paul

---

### Post by netreg on 2007-06-02
> **MrObvious said:**
> Go to the network settings, disable roaming mode, choose the network and set it up statically from there by choosing a Static address from the drop down menu. If you want screenshots I can post them. However for me to do so I need to be reminded to check this thread via PM since there are so many of them :D.

Hope this helps!
Paul

Paul,  thanks but i have tried that and that also stops it from working....

I have been reading and i think there is a potential bug with Network Manager...  I shall keep reading :)

thanks
Darren

---

