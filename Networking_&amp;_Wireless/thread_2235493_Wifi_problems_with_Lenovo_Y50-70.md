---
title: "Wifi problems with Lenovo Y50-70"
date: 2014-07-21
forum: Networking &amp; Wireless
---

### Post by dmmo on 2014-07-21
The problem I have is similar to this thread: [http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222](http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222)
 
At home wi-fi stops working after several minutes, although the status bar shows excellent connection quality to the router. The problem reproduces when I try to use my cell phone as a hotspot. All other devices at home have no problems with the wireless internet connection. The output of the wireless_script is attached. 

Does anybody have an idea how to cure my laptop?

Best regards,
Dmitry[ATTACH]254883[/ATTACH]

---

### Post by Emil_Gelev on 2014-09-15
Exactly the same problem. I did not find any solution. If someone cane give us an advice I will be thankful.

---

### Post by nils3 on 2014-10-02
Cheers, 
I am having the same issues with the same laptop. This is very bad because I am not able to work with ubuntu anymore, had to switch to win8. Since I am not the only one, and after a few kernel releases since the original post here, I wonder if anyone ist still working on this?
regards

---

### Post by jeremy31 on 2014-10-02
The backports from kernel 3.16 have been working very well for some people with realtek wifi cards

---

### Post by apwb-d on 2015-01-28
Same problem here. Tried 3.16 kernel, but it didn't detect any Wi-Fi card.

---

### Post by jin_2000 on 2015-03-25
Hi, I experience the same problems with my Lenovo Y50. Did anyone fine a solution yet?

---

### Post by slayer114 on 2015-09-27
Pretty sure there is a problem with the wifi on the Lenovo Y50, If you look in the forums a lot of preople are saying the same thing. I have been in contact with Lenovo but they deny that this is an issue and try to fob you off.
I am using a work around. I have a TP-Link wireless extender which you can run an Ethernet cable off. I am using it instead of the laptops own wifi system.

---

### Post by jeremy31 on 2015-09-27
> **slayer114 said:**
> Pretty sure there is a problem with the wifi on the Lenovo Y50, If you look in the forums a lot of preople are saying the same thing. I have been in contact with Lenovo but they deny that this is an issue and try to fob you off.
I am using a work around. I have a TP-Link wireless extender which you can run an Ethernet cable off. I am using it instead of the laptops own wifi system.
What does ```
lspci -nnk | grep -iA2 net
``` tell us about the wifi card

---

