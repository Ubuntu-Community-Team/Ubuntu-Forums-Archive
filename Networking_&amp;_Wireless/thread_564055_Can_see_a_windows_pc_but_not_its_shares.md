---
title: "Can see a windows pc but not its shares"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by FarmerJo on 2007-09-30
Hi,

I have been trying some time now to access the shares of a windows xp machine from ubuntu (fiesty). I have modified the smb.conf file to use a workgroup name of MYNET to match that of the windows pc. I am able to browse the network and can see the windows pc but when I click it I can get no further and get the message.

"The folder contents could not be displayed".

The xp machine does have a number of shares and both the windows firewall and norton firewall have been disabled for now. The ubuntu machine is able to ping the xp machine. On the ubuntu machine I have installed the firestarter package but for now have disabled the firewall.

I can access the ubuntu machine shares (I have shared the home directory) from the windows pc but cannot access the windows shares from the ubuntu pc.

I am clean out of ideas why this is happening, has anyone got some suggestions?

Regards
FarmerJo

---

### Post by dmizer on 2007-09-30
see the second link in my sig.

configuring smb.conf does not allow your ubuntu computer to access windows.  it only allows windows to access ubuntu.

---

### Post by FarmerJo on 2007-10-01
Many thanks for the link. I will follow this with great interest.

Regards
FarmerJo

---

