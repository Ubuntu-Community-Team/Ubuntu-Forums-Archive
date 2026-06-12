---
title: "No Wired Internet"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by gdn1947 on 2009-03-30
Ubuntu 8.10. Just re-installed 8.10 to an old(ish) IBM Laptop R40e. Network Manager appears to be working and shows Auto eth0. Internet access is through a 4 port router which is working correctly but I cannot access the internet from the laptop! All advice is that there should be an automatic connection but there isnt. Any advice appreciated. Thank you

---

### Post by thewolfman on 2009-03-30
Good morning,

try this:

2.1.1.&#8195;DHCP Connections

Most routers use DHCP to allocate IP addresses.

   1. Click the NetworkManager icon in the system notification area.
   2. Under Wired Network click the Radio Button 
      				next to the network you want to connect to.

2.1.2.&#8195;Static Connections

If you don't use DHCP then you can configure a static connection.

   1. Right click the NetworkManager icon in the system notification area.
   2. Click Edit Connections.
   3. Click the Wired tab.
   4. Select the connection and click Edit.
   5. Click the IPv4 tab.
   6. Choose Manual from the Method drop down.
   7. Enter your details and click OK.
   8. Click Close.

This is taken directly from the help menu above where you see the "Life saving thingy" on the top taskbar.

If that doesn't help you, try this:

# Right click the NetworkManager icon and click Edit connections...
# Click DSL.
# Click Add.

I have had trouble with the network manager myself using wireless so I installed "wicd" which works perfectly.

I hope this helps.

---

### Post by gdn1947 on 2009-03-30
Thanks for your advice. Will try it but its so annoying that a wired connection doesnt work straight away. Wireless is an even worse nightmare! 

I have searched the helpfile for wicd but nothing come up. Could you provide some more info please

Thanks again

---

### Post by linux_tech on 2009-03-30
what is output of ```
ifconfig
sudo cat /etc/resolv.conf
```

---

