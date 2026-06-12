---
title: "connection sharing"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by art_monu on 2011-05-08
I have an android mobile phone and I want to browse the web on it using the wi-fi sharing the connection on my PC using wifi ITI modem. 

When I used windows and tried to connect the android to the wifi, it said "Obtaining IP address.. ". When I clicked on the BSNL connection icon on the taskbar and enabled " Allow other users to connect to this network", my android immediately got connected.

Now I am using Ubuntu 11.04 and when I connect my android, it says "Obtaining IP address..". Please tell me how can I enable the sharing of Internet on Ubuntu.

---

### Post by dineshs on 2011-05-09
How did you connect your PC ? wired(ethernet) or wifi?
Are you using a dialler in PC(modem in bridge mode)?
If your modem is wifi why dont you configure it in PPPoE mode so that 
1)you dont need a dialler,you can directly use your web browser.
2)you can share the connection esily.
To configure modem in PPPoE mode pl see modem/CPE config in
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html)

---

### Post by art_monu on 2011-05-09
I am using a DSL connection and my PC is connected to modem by LAN wire. The modem is a wifi modem. I want to use internet connection on my PC as before but connect my android phone to the net using the wifi modem. Please tell how can I do it?

---

### Post by dineshs on 2011-05-09
Configure your ITI modem in PPPoE mode as given in the link.Is it DNA 211 modem by ITI?
>     Open browser. Type 192.168.1.1 in Address bar. click Go
    Enter both Username and Password as admin. Click OK.
    Wireless Configuration
        Click Advanced setup on the left side.
        Click Wireless on the left side,Ensure that enable wireless is ticked.
        Click Security on the left side. Select WPA-PSK as Authentication type.
        Enter Preshared key (8 character alphanumeric password) as wi-fi secret password.
        Click Save below . 
    WAN Configuration
        Click WAN on the left side.
        Tick Remove at the right end of the line having 0/35 as VPI/VCI values.
        Click Remove below.
        Click Add , A new window will appear. Click Next. Select PPP over Ethernet and click Next.
        Enter PPP Username and PPP Password. click Next. Click Next. Click Save. 
    Click Save/Reboot. Wait till reboot is complete (3 minutes)...If configuration is not saved, DO NOT click Save/Reboot. Stop after previous step.
Now from your PC you can directly access internet (no need of dialler)using web browser
From phone check available wifi networks and proceed.

---

### Post by kaspar_silas on 2011-05-09
O incidentally you can just assign yourself an ip by hand if you are only getting stuck at the obtaining ip stage. 

Right click on the wireless indicator icon on the ubuntu desktop list and record the connection information. Then go into wireless setting in android, then into advanced setting and select static ip. 

Lets say the ubuntu wireless ip was listed at 192.168.2.1 
then you'd use these settings.

IP Address: 192.168.2.X    
set X to any number 1-255 just not the same as above

Gateway: 192.168.2.1
i.e. the Ubuntu computer 

Netmask: 255.255.255.0

For the dns: Just enter the same values as the desktop.

Just remember to untick static ip afterwards or no other wifi will work.

---

