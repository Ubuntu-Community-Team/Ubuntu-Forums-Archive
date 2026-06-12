---
title: "BT broadband ADSL2MUE &amp; Ubuntu Dapper Linux setup instructions"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by QBU on 2006-10-18
I have finally got this setup working after pulling my hair out for weeks, thanks to a helpful post from mips on this forum.

Here is a [COLOR="Red"]walkthrough[/COLOR] and the settings I used should anyone else needs them, they may also apply at least in part to other routing modems. This version has been written with newbies in mind, I will try and post a shortened version below if I have time this evening:


(My setup is Ubuntu Dapper with integrated Kubuntu from Linux Format coverdisk, HP PAvillion dv1000 laptop, Linksys ADSL2 Modem connecting to BT broadband basic option 1).

[COLOR="Sienna"][SIZE="4"]_Disclaimer_[/SIZE][/COLOR] This is written by a newbie and may be a case of the blind leading the blind. There may be a neater way of doing this or one that simply works better. I am only sharing what has worked for me finally after a long time tearing my hair out and banging my head against the wall!](*,) Please don't hold me responsible if this doesn't work for you or causes problems on your system! Please also feel free to revise it and improve on it. I have tried to clearly indicate where settings have not been explored fully during my trial and error phase.

 


[COLOR="DarkRed"][SIZE="5"]
1. Ethernet card settings[/SIZE][/COLOR]

With it all plugged in and switched on...;) 

In Ubuntu desktop Go to System/Administration/Networking
Select ethernet connection on which the modem is connected [COLOR="Indigo"](easily identified with the nice image of a network card)[/COLOR]

Click "Properties"

make sure the tick box is ticked to make connection active.

Set Configuration to DCHP.

Click Okay twice to close both the windows.



[COLOR="DarkRed"][SIZE="5"]2. Modem configuration[/SIZE][/COLOR]

Open a web browser window & Type in the modems IP address. 
This should be in the modems documentation. 
For the Linksys ADSL2MUE it is set at the factory to 192.168.1.1 (although you can change this later) 

hit enter.

You should now see the modem setup login screen. Enter the username and password. (again: see your modem documentation) 
For the ADSL2MUE it is set as default to admin/admin.

On the basic [COLOR="Sienna"]setup[/COLOR] screen you should set the following [COLOR="Sienna"]for connecting to BTbroadband:
[/COLOR]

Encapsulation: RFC 2364 PPPoA

Virtual Circuit ID:  VPI = 0
                     VCI = 38

Multiplexing:  VC 
(BT don't specify this but it seems to work & I haven't tried the other option of LLC and have no idea what it means)

User Name: [email]username@btbroadband.com[/email] (substitute this with your username)

Password: (not required for BT) I just put "BT"

Keep Alive on, redial period 1 min.

Click on Save settings.

You should now see the modem LED on the right light up green over the word internet and on the basic setup page it should say connected at the bottom.

You are all set now except for one key thing...



[COLOR="DarkRed"][SIZE="5"]3. Configure DNS[/SIZE][/COLOR]

For some reason Linux/Ubuntu doesn't play ball with this modem when it comes to auto DNS config and passthrough. I have found that I needed to manually configure the DNS IP addresses in the network settings to point them at BT's DNS servers. Here's how:


In Ubuntu desktop again Go to System/Administration/Networking

This time select the DNS tab.

You may find that there is [COLOR="Sienna"]one DNS listed - your modems IP.[/COLOR] (192.168.1.1 for the linksys ADSL2MUE)

[COLOR="Sienna"]I found it extremely important to delete this.[/COLOR] (at first I didn't and just added the BT DNS addresses, the internet worked but it took up to 8 minutes to resolve the addresses before downloading each page)

Click add.

enter 194.72.6.51

click add

enter 194.72.9.38

Click Okay twice to save and activate the settings.

You should now be able to use the internet.


[COLOR="Sienna"]_[SIZE="4"]Note.[/SIZE]_[/COLOR] I chose those two DNS addresses from a list of pairs I found searching the internet for BTbroadband DNS addresses. I can not guarantee that they are guinely BT's as they don't seem to like to disclose them/don't even know them themselves -as many frustrated users who have requested them have found out.

Here is the full list of ones I found to try if you have problems: (listed in pairs primary/secondary)

194.74.65.65/194.72.9.38

194.73.73.94/194.73.73.95 (BTI#1&#2 nband apparently)

194.72.6.51/194.72.6.52 (ns0.bt.net/ns1.bt.net)

---

### Post by Geebird on 2006-11-29
This also works when connecting to Tiscali

Replace the BT DNS addresses with the Tiscali ones

Primary DNS Server 212.74.112.66
Secondary DNS Server 212.74.112.67

---

### Post by dazzler1 on 2007-11-03
If I follow your method and succeed in making an internet connection will I still be able to use the internet through the same USB port running  Xp on a different drive or will I have to reconfigure every time? Also I have installed Ubuntu 7.1. Do you know whether your method will work for this version? Lastly I haven't been able to locate the IP address for my Voyager 105 modem. Any ideas?  Thanks.:confused:

---

