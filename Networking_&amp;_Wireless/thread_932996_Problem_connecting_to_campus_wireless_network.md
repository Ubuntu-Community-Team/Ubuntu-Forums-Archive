---
title: "Problem connecting to campus wireless network"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by porterusaf on 2008-09-29
Ok so I've never had any problems connecting with wireless networks before this... Our campus wifi has a very specific policy/encryption scheme (directions to setup are attached below). I followed the directions, but originally I messed up one of the fields. Now every time I try to connect to the network the connection just sits there trying to connect and nothing happens (I'm never assigned an IP address through Network Manger). I tried a few different things to change the settings but the Net Manager keeps reverting to the orginial settings and I can't get connected. I normally wouldn't come for help like this, but I'm really stumped.

Any ideas for clearing the connections history/cache?

Any ideas why these directions may not work on Hardy Heron (which I am using) or my XPS M1530 w/ Intel card?



Instructions:
Ubuntu: Connecting to 'restricted.utexas.edu'

This procedure connects Ubuntu computers to the restricted.utexas.edu wireless network using the Network Manager.

Configuration: Network Manager

Time to complete the procedure: 10 minutes

   1. Download the certificate file. You can obtain this file from the guest.utexas.edu wireless network if necessary.
   2. Click the Network Manager icon and select the restricted.utexas.edu wireless network.
   3. Select the following options in the Wireless Network Key Required dialog box.
          * Wireless Security: WPA2 Enterprise [recommended] or WPA Enterprise.
          * EAP Method: TTLS
          * Key Type: AES [recommended for WPA2] or TKIP
          * Password: [Your UT EID password]
          * CA Certificate File: cacerts.pem

      Keep the default settings for the other fields in the dialog box.

      Note: The WPA2 security protocol is recommended for campus wireless network users; however, the network also supports WPA. Select the AES encryption type for WPA2 and the TKIP type for WPA.
   4. Click the Connect button to complete the configuration and connect to the restricted.utexas.edu network.

---

### Post by cpetercarter on 2008-09-29
Have you tried :

right click on the wireless icon (a screen with a red x if you are not connected to a wireless network) > edit wireless networks > highlight the campus network > remove.

Then start again.

---

### Post by porterusaf on 2008-09-29
Sure have... That's what I don't understand... A couple of times I thought I had the cache cleared, but then the connection would just hang until eventually Netowrk Manager froze and it's proccesor usage started to sky rocket (like 50%+).

---

### Post by jklasdf on 2008-10-02
Try deleting any files in /etc/NetworkManager/system-connections if there are any.

---

### Post by porterusaf on 2008-10-03
I've been able to wipe the old settings, but now I just can't connect to the network.. Not to sure if it's the wifi card driver (bc the wifi card works on dows) or just Ubuntu itself.

---

