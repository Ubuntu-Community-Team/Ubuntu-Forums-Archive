---
title: "Connecting to wireless at school"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by kingleer on 2007-01-08
First of all, my wireless card is working perfectly in ubuntu. I have a wireless network at home and use it all the time. I'm having trouble connecting to the wireless network at my school library however. 

They have handouts on how to connect to the wireless network here for windows and osx users however. 

For Windows: 

1. From the 'start' button, go to 'Connect to' and click 'wireless Network Connection' 

2. From the left menu bar, click 'Set up a wireless network for a ome or small office', then click 'Next' 

3. In the Network Name (SSID) box, type UTORwin 

4. Select 'Manually assign a network key', then click 'Next' 

5. Uncheck the 'Hide characters as I type' box 

6. In both boxes (Network & Confirm network key), I type UToronto1home 

7. Click 'Next' 

8. Select 'Set up a network manually', then click 'Next' 

9. Click 'Finish' 

10. From the left menu bar, click 'Refresh network list'. UTORwin should appear in the main window. 

>If UTORwin does not appear, check that the laptop's wireless is turned on (normally a switch or button on the laptop) 

To register the laptop's MAc address, start Internet Explorer. You will see a welcome message. etc


I have wlanassistant installed and it picks up several wireless connections (all with the name UTORwin with varying signal strengths - all encrypted - which again confirms my wireless is working- but I think they're just other laptops connected to the wireless network). 

I'm thinking of installing internet explorer, but I don't think its a problem with my browser.  
I just can't connect to the wireless network here. 

I go to configure my wireless network, I enter in the network name UTORwin and the password UToronto1home (as both hexadecimal and ascii) using DHCP, but I still can't connect. 

AGAIN MY WIRELESS CARD IS WORKING FINE. 

Also any cool wireless applications for linux you can recommand would be great. I already have wlanassisstant.

---

### Post by meng on 2007-01-08
Try this at the command line (assuming your wireless interface is wlan0, it may be named something else, e.g. ath0, ath1, eth0, eth1):

sudo iwconfig wlan0 essid UTORwin key restricted s:UToronto1home
sudo ifconfig wlan0 up
sudo dhclient wlan0

If this works, we can move onto the next step which is making these the default boot settings.

---

### Post by teaker1s on 2007-01-08
I don't use the packages you use,but your problem is you are seeing clients not access points try looking through settings
or installing and using
[COLOR="Red"]network-manager-gnome[/COLOR]

---

### Post by kingleer on 2007-01-08
Everything works fine right up until "sudo dhclient wlan0" 

I get the error 

No DHCPOFFERS received 
No working leases in persistent database - sleeping.

---

### Post by kingleer on 2007-01-08
"network-manager-gnome" 

I'll check it out. I'm also gonna try wifi radar. Thanks.

---

### Post by meng on 2007-01-08
> **kingleer said:**
> Everything works fine right up until "sudo dhclient wlan0" 

I get the error 

No DHCPOFFERS received 
No working leases in persistent database - sleeping.

After the first two commands, you could look at:
sudo iwconfig
(and see if you're picking up a signal)

---

### Post by kingleer on 2007-01-09
It WORKS! I'm connected right now. 

I followed your instructions 

sudo iwconfig wlan0 essid UTORwin key restricted s:UToronto1home 
sudo ifconfig wlan0 up 
iwconfig 

And I'm connected. Buts its not very stable. I keep getting kicked off. Any other suggestions?

---

### Post by meng on 2007-01-09
sudo iwconfig
should tell you about your signal strength vs noise. Granted, that seems unlikely to be the reason for getting kicked off, but it's worth looking into anyway. You're using edgy on this notebook right? I found I had similar problems losing the connection with Dapper, but Edgy was better for some reason.

---

### Post by kingleer on 2007-01-09
Edgy it is. 

Its strange, in one part of the campus I'm able to get online easily. In another (one where I know there is wifi and others can get online) this is not the case. 

Can anyone recommand any other wireless progs?

---

### Post by HoMie_G on 2007-10-23
Having the same exact problem. I used the first method (dhclient) it worked for a bit then got disconnected. I tried to do it again, it did not work. using 7.10.  has anyone solved this problem permenantly? also just in case i manage to connect again. is there anything i can do to save the settings and make utorwin my default wireless network?

Thanks,
HoMie_G

---

