---
title: "How to establish internet connection using User Id, Password and Service Name"
date: 2013-12-01
forum: Networking &amp; Wireless
---

### Post by amolravatale2 on 2013-12-01
Dear All,

I am new to Linux. I have installed Ubuntu 12.04.3 LTS on HP laptop (model: dm4-1165dx). Currently Windows 7 and Ubuntu have been installed in dual boot mode.


I use PPPoE method 
Tto create connection (WAN miniport PPPoE) -> once the connection is created, right click on connection & select 'Properties' menu -> In 'General' tab I enter Service Name provided by ISP.
Once connection is established, the shortcut of the connection is created on desktop. This is one time activity.

Now when ever I want to surf internet click on desk top icon , it will ask user id, password and click 'Connect'. 

Can you please tell me how I can set up internet connection in Ubuntu 12.04.3 LTS if ISP has given User Id, password & Service Name

Regards,
Amol Ravatale

---

### Post by varunendra on 2013-12-03
Welcome to the forums Amol!

In Ubuntu :
click on the Network Manager icon (nm-applet) at the top right corner of the screen > Edit Connections > go to "DSL" tab > click "Add" button > under "DSL" tab, enter your desired Service name, ID, Password > Save > Close the settings.

Optionally, you can also tick the "Connect Automatically" checkbox in the DSL settings box to make it connect automatically whenever a cable connection is detected.

---

