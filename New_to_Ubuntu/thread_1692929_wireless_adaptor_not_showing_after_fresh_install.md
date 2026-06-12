---
title: "wireless adaptor not showing after fresh install"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by alive063 on 2011-02-22
Hi,after a fresh install of ubunustudio (with low latency),my wireless adaptor is not showing and I cant see where to turn it on/update driver.
 output of iwconfig is; lo no wireless, eth0 no wireless, wlan ieee 802.11abg essid:'dovado'(dovado is my router,I put that into network settings) 
output of rfkill list all is; 0: dell-wifi:wireless lan soft blocked no, hard blocked no, 1: bluetooth; yes yes, 2;hy0 wireless lan; no no.
While installing, network did not autodetect and I chose skip for now.
It worked fine before on ubuntu10.10.
Its a fairly new dell latitude e6400xfr.
help a newbie please.

---

### Post by frankduffey on 2011-02-22
> **alive063 said:**
> Hi,after a fresh install of ubunustudio (with low latency),my wireless adaptor is not showing and I cant see where to turn it on/update driver.
 output of iwconfig is; lo no wireless, eth0 no wireless, wlan ieee 802.11abg essid:'dovado'(dovado is my router,I put that into network settings) 
output of rfkill list all is; 0: dell-wifi:wireless lan soft blocked no, hard blocked no, 1: bluetooth; yes yes, 2;hy0 wireless lan; no no.
While installing, network did not autodetect and I chose skip for now.
It worked fine before on ubuntu10.10.
Its a fairly new dell latitude e6400xfr.
help a newbie please.
From the Software center down load and install KNetwork manager I just solved my Wireless network problem Be sure you are using the Broadcomm 43xx driver. I also downloaded RTUtLan Manager so take a look at your configuration if you are running windows go to a cmd prompt type ipconfig/all write down all the info or use the terminal in Ubuntu type ifconfig and write down the DNS servers and your network card address and other info.

---

### Post by frankduffey on 2011-02-22
> **alive063 said:**
> Hi,after a fresh install of ubunustudio (with low latency),my wireless adaptor is not showing and I cant see where to turn it on/update driver.
 output of iwconfig is; lo no wireless, eth0 no wireless, wlan ieee 802.11abg essid:'dovado'(dovado is my router,I put that into network settings) 
output of rfkill list all is; 0: dell-wifi:wireless lan soft blocked no, hard blocked no, 1: bluetooth; yes yes, 2;hy0 wireless lan; no no.
While installing, network did not auto detect and I chose skip for now.
It worked fine before on ubuntu10.10.
Its a fairly new dell latitude e6400xfr.
help a newbie please.

From Frank Duffey
Franks Computers
Gainesville,Fl
From the Software center down load and install KNetwork manager I just  solved my Wireless network problem Be sure you are using the Broadcomm  43xx driver. I also downloaded RTUtLan Manager so take a look at your  configuration if you are running windows go to a cmd prompt type  ipconfig/all write down all the info or use the terminal in Ubuntu type  ifconfig then and write down the DNS servers and your network card address  and other info. I hope this helps be sure you are using the correct Router Settings for the channel Run the configuration program for your router be sure your Ubuntu network shows up That was one of m,y problems after reinstalling Ubuntu 10.10 I Good Luck with this message me if yiou need futher help I am a A+ Certifited Technicain and Norvell network certifited. I had my Own Computer Business for over 10 years with a partner. I still do Computers part time now I am a Disabled Veteran Vietnam Era Veteran. You can add me here as a friend

---

### Post by grahammechanical on 2011-02-22
Am I understanding you correctly? You were using standard Ubuntu 10.10 and now you have installed Ubuntu Studio 10.10? Is that correct? I have both installations and I have just loaded Ubuntu Studio to answer your post.

There is some kind of conflict between the kernel that Audio and Video professionals use and the networking utilities. For this reason networking is not activated during an installation. Network Manager is not installed. There are tools to get networking set up but it is different from Network Manager so it may be confusing. This is what I did. Others have found that it worked for them as well. You can only try.

Ubuntu Studio Internet

1) Something is needed to indicate that an Internet or networking connection has been made. 

Right click the top panel and select Add to Panel. In the list presented by the dialog box select Network Monitor [Monitor network activity]. Click Add.

This action will put an icon of two connected monitors (screens) that will flash when there is network activity.

2) Setting up connections. Click on the Ubuntu Studio icon on the left of the top panel. Go to System>Administration>Network.

Do not go to System>Preferences>Network. It is the wrong type of network.

In the dialog box that appears select the Connections tab. Click the shield icon at the bottom and in the middle of the dialog box. It has "Click to make changes" alongside it.

Enter your login password. A list of available connections will appear. Select either Wireless Connection, Wired connection (eth1) or Wired connection (eth0) and click the Properties button.

For a Wireless connection put a tick mark against the box "Enable this connection". You may have to do this twice to get the tick mark to stick.

Make sure that the network name (ESSID) is the correct one.

Set the password type WPA Personal.

Enter the Network password. This is the wireless key or WPA-PSK key.

Set the configuration to Automatic configuration (DCHP) if that is the correct setting.

Enter if necessary the IP address, Subnet mask, Gateway address.

Click OK.

Click the make changes shield to prevent any further changes.

Click close and then reboot. Cross your fingers.

Connection Properties wlan0

Left or right click the Network Monitor icon.

A dialog will appear that will give the connection name, its status, an activity report (packets and Kilo bits received and sent) and signal strength. There is also a button to Configure the connection. Every time I click this button I get a Interface does not exist message even though there is an active connection.

Regards.

---

### Post by alive063 on 2011-02-22
Hi Graham, I did have ubuntu10.10(all ok) duel booting with windows7(constant bsod when running audio apps). now I have 'studio' on the full disk (I am now on a second netbook which works fine on my network.
I have already put network monitor on the panel,
in network settings I have put in the name of my network, there is no password set,I dont know what to put for IP address, Subnet mask, Gateway address, but on auto configuration they are greyed out.
Are any settings from this netbook relevant to the 'studio' pc? 
rebooted with crossed fingers, nothing.
There is no icon on the panel showing signal strength *)))

---

### Post by grahammechanical on 2011-02-22
The settings required are the settings of the router/modem. If two machines or two operating systems connect to the same modem then they are connecting to the same network and will use the same settings.

Once you have a connection when you click on the network monitor icon a dialog box will appear. The signal strength will show as a bar of colour moving across the dialog box.

The trick I think is to get the tick mark in Enable this connection to  stick. I also found that things work if you only enable the wireless  connection or the wired connection. Not both. It can work but you may  not always get any connection. A reboot is definitely needed, in my opinion.

There is another way. Through the terminal. I think that Ubuntu should be a point and click OS. so, I do not suggest terminal commands from the beginning. I am not familar with these commands anyway.

In a terminal type

rfkill unblock wifi

then

sudo ifconfig wlan0 down

followed by

sudo ifconfig wlan0 up

Reboot.

Regards.

---

### Post by alive063 on 2011-02-23
Did that and still cant find my router, will I try a wired connection (have to move router from optimal position)?
Would a wired connection reduce the possible conflict with my low latency audio settings?
Thanks, Adam.

---

