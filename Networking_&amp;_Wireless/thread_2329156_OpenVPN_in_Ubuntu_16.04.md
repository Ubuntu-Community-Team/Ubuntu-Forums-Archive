---
title: "OpenVPN in Ubuntu 16.04"
date: 2016-06-28
forum: Networking &amp; Wireless
---

### Post by Mads_Unneberg on 2016-06-28
I have used Ubuntu with a OpenVPN connection from Private Internet Access since v.14.04.3 and the installation guide from version Ubuntu 10.10 has always worked. In some cases I have allso used the installation guide for Ubuntu 12.04. Then again these are the only guides PIA has for Linux.
      But this time with v.16.04 it seems totally inposible to get the OpenVPN Connection to work.....
      - So please, anyone, help me with this..
      M.

---

### Post by QDR06VV9 on 2016-06-28
1. What errors do you see?
2. Explain how you tried to install it.

---

### Post by Mads_Unneberg on 2016-06-28
- SORRY...
I just went over-board and lost every thing by Closing/Killing the terminal in anger and frustration......  
Give me some time and I`ll try to get it all up again?
M.

---

### Post by Mads_Unneberg on 2016-07-05
- This took avail....
I didnt answer you **[COLOR=#ff0000]runrickus [/COLOR]**and sorry again about that. 
The problem I had was nothing bigger than entering "gnome" in the end of the command installing network manager openvpn. [COLOR=#ffffff]aa[/COLOR]
[B]
I will show the hole command now:
[/B]                         
[LIST=1]
[*]1.     In **Terminal**, install *openvpn* packages with      
*sudo     apt-get install network-manager-openvpn-gnome*
**2.     ****Then r****un**      
*sudo     wget [https://www.privateinternetaccess.com/openvpn/openvpn.zip](https://www.privateinternetaccess.com/openvpn/openvpn.zip)*          
**3.     ****Extract** the files from the zip with      
*unzip     openvpn.zip*      
**4.     ****Move** *ca.crt* and *crl.pem* to */etc/openvpn*
*mv     ca.crt /etc/openvpn      - and another -           mv crl.pem /etc/openvpn* 
[*][I]
[LIST=1]
[*]**5.****THEN     ****O****PEN** the *Network Manager* from the menu bar.          
Go     to Edit Connection
**6.     ****Choose** *add*     and **select** the *OpenVPN*     connection type, and click **Create**.          
**7.     ****Enter** *Private     Internet Access SSL* for the *Connection Name*.      
**8.     ****Enter**     &#8220; Your choice in PIAs Regional Gateways&#8221;    for the *Gateway*          
**9.     ****Select** *Password*     and **enter** your *login     credentials*.      
**10.     ****Browse** and select the *CA Certificat* we saved in     **Step 3**.      
**11.     ****Choose** *Advanced*     and enable **LZO Compression**.          
**12.     ****Apply** and exit.      
**13.     ****Connect** using the **Network Manager** by clicking on **Private Internet Access SSL**.   
You can also **Edit** your Internet Provider **"Ethernet Network"** to **"Automatically connect to VPN when using this connection**" . 
[/LIST]
  - AND THATS IT !

[I]Regards
Mads.
:D[/I][/I]
      
 SORRY-SORRY-SORRY I`W BEEN TRING TO EDIT THE https: LINK IN POINT 2 TO NOT TO BE A LINK BUT IT WONT CHANGE....  

[*]SO HER YOU GET THE HOLE AND RIGHT COMMAND LINE:  [COLOR=#ff0000]**sudo wget [https://www.privateinternetaccess.com/openvpn/openvpn.zip](https://www.privateinternetaccess.com/openvpn/openvpn.zip)**[/COLOR]
[*] 
[/LIST]

---

