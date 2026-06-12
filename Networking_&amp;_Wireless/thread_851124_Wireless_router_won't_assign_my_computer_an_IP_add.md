---
title: "Wireless router won't assign my computer an IP address - please help"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by Oreo Priest on 2008-07-06
My wireless router won't assign my computer an IP address. My computer's wireless has worked on other wireless networks but not this one, and other computers (running windows) work on this wireless network. If I plug in a cable, it still works.

I have tried network-manager and wicd, but neither connects. Signal strength is good, but wicd shows "Obtaining IP address" at the bottom and makes no progress after that. I think it may be because the encryption is WEP, but that is pure speculation.

Please help!

---

### Post by issih on 2008-07-06
Hmmn, has this computer running ubuntu ever actually connected to a wireless network?

I ask as on my machines I have had woreless cards do almost exactly what you are suggesting, in terms of seeming to connect, but never actually getting through to achieving an ip address, and the only thing I could do was to replace the wireless drivers.

Things you could try.

1) try static ip
2) try turning off the encryption in the router as a troubleshooting measure.

---

### Post by Oreo Priest on 2008-07-06
The computer using Ubuntu has connected to other wireless networks.

I'm not exactly a master of Ubuntu, so could you tell me how to do either of those things? If I assign a static IP, what should I choose?

---

### Post by issih on 2008-07-06
First of all I'd try disabling encryption in the router, just to establish if the hardware is functioning at all.

basically log into your router (can't really tell you how that is done, it'll depend on the model) then set encryption on the wireless to none.

If you can connect then, you will know that at least its not a basic hardware fault.

After that choosing a static ip will depend on the dhcp pool being used.

Somewhere in the router configuration there will be a setting to enable dhcp, and it will probably state that it will start from a certain ip address, and use a set number in its pool.

e.g.

router ip = 192.168.0.1

dhcp start address = 192.168.0.50
dhcp pool size = 50

if you ignore the first 3 numbers (the 192.168.0) which must be the same, and concentrate on the last number. This number can range from 0 to 255. and any number in that range not assigned to another networked box is a valid ip on your network.

the dhcp server is claiming all the ip addresses from 50 to 100 for its use, and the router is on 1, so you could use 3-49 and 101 to 255. 

I'd just pick the easiest, so something like 192.168.0.2 in this case.

Then select manual configuration from the networking applet.

unlock the dialog, then select the wireless connection and hit properties.

Now untick roaming mode, enter the details of your wireless network in the obvious places,

in the connection settings select static ip
IP address = your selected ip address
Subnet Mask = 255.255.255.0
Gateway Address = your router's ip address

thats it.

Hope that helps

---

### Post by fballem on 2008-07-06
Other item to check on the router is whether or not MAC filtering is enabled. MAC filtering is designed to allow only specific computers to connect to the router.

This is normally accessible from your router administration. If MAC filtering is enabled, then you will need the hard-coded MAC ID of the wireless ethernet adapter in your computer (not sure how you get this, every computer is different). Once you have the MAC ID, then add the id to the MAC Filter table and save the configuration on your router.

You will then have to reboot your computer. If all goes well, you should be able to connect to the router.

I have MAC filtering setup on my router (for security), and the symptoms you describe sound like what happens to me if I haven't added the MAC ID to the filter table in the router.

Hope this helps.

---

### Post by Oreo Priest on 2008-07-29
So apparently it's not the router's fault - my computer now won't connect to any wireless networks. Where could I find new drivers to install? Which ones should I install?

---

