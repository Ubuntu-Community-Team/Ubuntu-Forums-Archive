---
title: "[SOLVED] Authentication Problem while connecting to internet"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by manishsk on 2008-03-31
Hi

I have ether net card and ADSL router to connect. Somehow I manged Ubuntu 6.06 to detect my ethernet card using below driver. eth0 shows up in my Netwroking utility.

**Driver Used:**
[http://gurukumara.googlepages.com/sc92031-2.6.tar.gz](http://gurukumara.googlepages.com/sc92031-2.6.tar.gz)

I entered all the details regarding DNS servers and default Gateways.

I am able to ping my gateway IP address.  I then went to sudo ppoeconf and configured it with user name and password with all other genral settings.

But whenever I do pon dsl-provider. It shows loaded.
And when I give plog it shows Authentication denied messege.

Due to this I am not able to connect to my internet. The same user name and password works well on windows. (just for info, I am using Tata Indicom wired connection).

What could be wrong out here? Unable to connect :(:(

---

### Post by erginemr on 2008-03-31
What type of modem are you using? Can you please provide its brand / model name?

I suppose it is connected to your ethernet card (as compared to USB modems) and has its own user interface (which can be reached by entering its IP number to your web browser) to input user name and password. Am I correct?

---

### Post by manishsk on 2008-03-31
Silan SC92031 PCI Fast Ethernet Adapter 

This is my ethernet card connected on PCI slot.

Its from Intex.

Proabbaly you are right. I am not at my pc right now. I will check at EOD. But I guess it should work the other way too right? I mean in windows, the conecting from the network place works for me. I mean the common dialer application in windows.

Thanks,
Manish

---

### Post by erginemr on 2008-03-31
No, what I meant was not your ethernet card, but your ADSL modem, if any?

My wrong, I have assumed that you are using an ADSL modem or something of similar nature to connect to the network, but now I began to think that in our networking system, you are connecting to the Internet directly through your ethernet card, with no intermediate router? Is this the case?

---

### Post by manishsk on 2008-03-31
no I am using the ADSL modem. Whenever I type the gateway IP address in browser I am able to a configuration webpage for the modem. Accroding to my windows setting it requires me to select the Bridge mode connection type instead of PPPoE etc options.

ISP: (This comes under Encapsulation section). If I select anything else it doesn't connect in Windows.
   Dynamic IP Address  
   Static IP Address  
   PPPoE/PPPoA  
   Bridge Mode  -- my ISP requires me to select this.

I connect to net directly.

It tried select    PPPoE/PPPoA  in Ubuntu. It showed me some PAD0 timeout.
And failed to complete the PPPoE discovery. How caan I make linux to behave in the same way windows does it, ie. using the Bridge mode.


Thanks,
Manish

---

### Post by erginemr on 2008-03-31
In my case, I only needed to edit the file: **/etc/network/interfaces**
with: 
```
gksudo gedit /etc/network/interfaces
```
such that it read:
```
auto lo
iface lo inet loopback

[B][COLOR="Red"]auto eth0
iface eth0 inet dhcp[/COLOR][/B]
```

Please try the same and reboot. You should be connected to the Internet automatically via your router's own interface this way.

You can also use the following generic commands to confirm that your ethernet card is identified as **eth0**:
[http://ubuntuforums.org/showpost.php?p=4576441&postcount=3](http://ubuntuforums.org/showpost.php?p=4576441&postcount=3)

---

### Post by manishsk on 2008-04-01
Ok will check that. What I did tried yday is that, I selected DHCP from the Networking utility for the my eth0 wired connection. Then on DNS tab I added the DNS servers. After that I tried to connect using pon-dsl-provider. But still no luck.

My router(ADSL modem) address is 192.168.1.254. When I change the connection type to PPPoE from there and give the username and password. I do get connected but I get PAD0 timeout and Unable to complete PPPoE discovery messeges in plog. And then connection gets terminated.

As per my windows settings it should be in Bridge mode. But then it gives me Authentication problem.

I have a internal dialup modem too but its not active. Also is their any situation where the password which stored in the /etc/ppp/pap-secrets is getting encrypted before login? i mean that can be a reason why I get authentication failure?

I tried lot of ways but unable to get online. Something very small thing I am missing but I am not able to findout.

ifconfig shows the eth0. It also shows ppp0 when I do pon. And it removes it when I do poff.

Please help. I will check /etc/network/interfaces today.

Thanks,
Manish

---

### Post by erginemr on 2008-04-01
To back you up with more information, I am currently connected to the Internet via a crappy ADSL USB modem. It shows up as ppp0 upon the command **ifconfig** and I can start and stop the connection with; **pon adslusb & poff** respectively. 

Then, I got my hands on a real modem once, which is connected through the ethernet interface. And all I had to do was to add those two lines to the **/etc/network/interfaces** file. I had messed with Gnome Network Applet first too, which proved to be a mixed bag with random connections at will. So, if you want a persistent connection, I believe Network Applet is not the way to go.

What I'd like to emphasize here is that pon/poff are all related to modems connected with a USB interface. That your system detects **ppp0 **and allows you to use pon/poff might be attributed to the fact that you may also happen to have another PCI modem in your box. 

Hope this will shed some light on your problem...

---

### Post by manishsk on 2008-04-01
Just one question before I test with /etc/network/interfaces.

The entry which you asked me to put ie.
> auto eth0
iface eth0 inet dhcp

Will this make my internet connection to start automatically when boot up my machine? Actually I do not want to start on boot up. I have separate user name and password which I use in Windows to connect. However, it connect to LAN thru the router automatically. When I connect to Internet from windows it connects from the WAN miniport in the ADSL router and then establishes the connection. 

Here are some details:
I have only 2 PCI slots. One holds internal Dial Up modem. Other Holds the ether net adapter card to which I can connect a cable coming from my ADSL router (or modem i can't decide what to say it, it just outside of my box and has a cable coming from my wall to it) 

Just for info: I have another cable coming from wall which is actually my telephone line whcih I can use for the other dial up modem. But Anyways I need to use that modem too but I am not interested in configuring it now. Though lspci shows it detepected with correct drivers.

The network applet shows 2 entries one having the phone picture which is currently inactive. The ohter is eth0 which I made active by making it DHCP and adding DNS servers.

When I run pppoeconf it detect eth0 which it was not when the dirvers for the ethernet card were not installed (see my first post). So I believe it is trying to access the right card.

Now I will try modifying the /etc/network/interfaces today EOD. Do post if you want to ad up some thing to this.

---

### Post by erginemr on 2008-04-01
I can add just a few remarks:

1. Yes, with these settings, your computer should start up as connected to the Internet. But I don't get why you don't want this default behavior. I can understand that you don't want to connect at boot in Windoze, where there are suspicious ports open, God knows who is listening to, beside M$ sniffing around behind our back. On the other hand, in Ubuntu, all ports are closed by default and you are perfectly safe. 

2. > When I connect to Internet from windows it connects from the WAN miniport in the ADSL router and then establishes the connection.
I wish I could comment on this, but don't know anything about "WAN miniports".

3. Probably, your computer refers to the dial-up modem when it refers to ppp0.

4. When I configured the router before, I had edited the file "/etc/network/interfaces" only, but it turns out that this is equivalent to setting wired connection in the network applet to "Automatic DHCP". Kindly see the attachment.

---

### Post by manishsk on 2008-04-01
Hi erginemr

1. My connection is a paid connection. I have some GB download limit per month. So I keep my connection down whenever I do not require.

2. WAN miniport is acually whenever in windows, you try to connect it access this in ADSL router/modem then it establishes the connection with the ISP then the username/password verification happens. And then we get connected to internet. Before that LAN connection happens automatically which obtains IP address (but this one ususally common all the time, actully IP is assigned after connecting to Internet). If you have seen such modem it has LAN led then the ADSL LED. 

Windows is quite good enoguh to do this automatically. I must agree.

This [link]("http://www.broadbandbuyer.co.uk/Shop/MFR/ShopDetail.asp?ProductID=2400") has (kind of) screen shot of my router. Not sure of exact model.

3. Why would it go to dialup modem when in sudo pppoeconf referes to eth0 and makes all the settings in dsl-provider?

4. Thanks for the screenshot! My PC has some similar configuration. 2 entries in the Networking applet.

Anyways thanks a lot buddy for your efforts.

---

### Post by manishsk on 2008-04-01
Yeeeeeeeeeeeeee!!!

Yahooooooooooooooo!!
I am posting from Ubuntu!!!

Got connected....!!

And now below is my stupidity graph:
I was using a correct username but did not aded the @domain part to it. So naturally it was giving me Authentication failure.... :) :D

Well now its working well!!

Thanks all..

---

### Post by manishsk on 2008-04-01
The only problem is I am seeing I always loose my DNS servers entered in the Network applet. Will work on this now. Need to findout why?

---

### Post by erginemr on 2008-04-01
Great! :D Welcome back to the online world!

---

### Post by prshah on 2008-04-01
> **manishsk said:**
> 
Due to this I am not able to connect to my internet. The same user name and password works well on windows. (just for info, I am using Tata Indicom wired connection).



Give the whole email address (eg [email]someone@eth.net[/email] or [email]someone@vsnl.net[/email]) instead of JUST the username ("someone").

---

### Post by manishsk on 2008-04-01
I am marking this as solved! Despite restarting my PC i was able to re-connect to internet so am not bothering about the DNS servers. :biggrin:

Thanks everybody for all the possible help! I hope this will help others whos has got similar problem.

---

