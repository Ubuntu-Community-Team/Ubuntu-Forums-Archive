---
title: "No wireless internet detected on live CD"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by tegnoto89 on 2009-12-16
I'm running a new HP mini laptop, and running the live cd via unetbootin, and for some reason I'm not being able to detect any wireless internet connections?

---

### Post by cariboo on 2009-12-16
Id your wireless device being detected and  the driver loaded? To find out, open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network > wireless.txt
```

The above command creates a text file called wireless.txt. Could you paste that into your next post.

---

### Post by tegnoto89 on 2009-12-16
After putting the following into the terminal:

sudo lshw -C network > wireless.txt

I just got "PCI" for a couple of seconds, and then it went away.


Also, upon looking at my hardware drivers, I saw two Broadcom wireless card drivers that had not been activated, but obviously I was unable to fetch them because I don't have any internet connection.

---

### Post by 3rdalbum on 2009-12-16
Is it wireless internet, or a wireless network?

Wireless Internet/Mobile Broadband works from mobile phone towers. Wireless networking is where you have a wireless modem/router plugged into your phone or cable line.

You can set up mobile broadband through the Network Manager applet on your top panel; right-click it and go to Edit Connections, and then click on the Mobile Broadband tab and click Add. Follow the prompts and it will set up.

If you're talking about wireless networking, you should left-click on the Network Manager applet and see if the networks have been detected. If they haven't, then you may need to connect your machine via Ethernet to your modem/router, reload the package list by hitting the Reload button in Synaptic Package Manager, and then look in the Hardware Drivers program.

---

### Post by tegnoto89 on 2009-12-16
> Is it wireless internet, or a wireless network?

Wireless Internet/Mobile Broadband works from mobile phone towers. Wireless networking is where you have a wireless modem/router plugged into your phone or cable line.

You can set up mobile broadband through the Network Manager applet on your top panel; right-click it and go to Edit Connections, and then click on the Mobile Broadband tab and click Add. Follow the prompts and it will set up.

If you're talking about wireless networking, you should left-click on the Network Manager applet and see if the networks have been detected. If they haven't, then you may need to connect your machine via Ethernet to your modem/router, reload the package list by hitting the Reload button in Synaptic Package Manager, and then look in the Hardware Drivers program.


I'm talking about wireless networking- I have a wireless router in my house.  Sorry for the confusion.

The network manager isn't seeing any wireless networks.  I'll connect my computer to my router, try to get the drivers, and let you know how it works.

---

