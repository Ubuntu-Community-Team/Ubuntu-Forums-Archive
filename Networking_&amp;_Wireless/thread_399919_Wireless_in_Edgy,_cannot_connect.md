---
title: "Wireless in Edgy, cannot connect"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by hoopsta1423 on 2007-04-02
Hey guys, there has got to be a quick answer for my question.
I just install Edgy on my Presario V2000 with a Broadcom 4318 wireless card
I Installed ndiswrapper with the bcmwl5a.inf and the wireless card can scan and the light is on, telling me that the card is enabled.

One problem though, i cannot connect to any network, and cannot even ping my router using wireless. It is a very weird situation as the card can scan for any available networks but will not connect. I tried editing the /etc/network/interface to put an essid in there, but no luck with that. I have tried three different wifi managers and still no luck

Let me know what you guys need from me, and if you can help me thatd be awesome.

---

### Post by Floppyjoe on 2007-04-02
> **hoopsta1423 said:**
> Hey guys, there has got to be a quick answer for my question.
I just install Edgy on my Presario V2000 with a Broadcom 4318 wireless card
I Installed ndiswrapper with the bcmwl5a.inf and the wireless card can scan and the light is on, telling me that the card is enabled.

One problem though, i cannot connect to any network, and cannot even ping my router using wireless. It is a very weird situation as the card can scan for any available networks but will not connect. I tried editing the /etc/network/interface to put an essid in there, but no luck with that. I have tried three different wifi managers and still no luck

Let me know what you guys need from me, and if you can help me thatd be awesome.

Maybe you are using the wrong driver.
You might try the bcmwl5.inf and bcmwl5.sys instead

---

### Post by hoopsta1423 on 2007-04-02
Tried both of those, bcmwl5.sys does not work, and bcmwl5.inf shows the same results.

When i do iwlist eth1 scan, all the networks show 0/100 quality

ANybody ever have this problem before. My card can see the networks, but will not connect to any of them

---

### Post by mrund on 2007-04-03
I have the same problem. wsconfig sees everyhting just fine, but I can't connect.

---

### Post by leamphil on 2007-04-03
And ditto - see [http://kubuntuforums.net/forums/index.php?topic=3081374.0](http://kubuntuforums.net/forums/index.php?topic=3081374.0) for more details of what I've done/tried/looked at ... any suggestions on what else to look at to diagnose this gratefully received.:confused: 

I've also tried various other incantations that seemed to work for others (eg. wlassistant, knetworkmanager, various & numerous commands).

Is there a trace (tcpdump ??) that I could run to see what is going out ?

---

### Post by John Thomas on 2007-04-03
> **mrund said:**
> I have the same problem. wsconfig sees everyhting just fine, but I can't connect.

Same here.  iwlist sees the available connections, but I was able to connect only once, in a Panera sandwich shop on Palm Sunday.  My signal is strong 100/100, 93/100, 60/100, etc.  The one time the connection worked, I think I got it to go by repeatedly clicking Firefox's Try Again button on the window that reported the Can't find (or 'connect to,' I forget now which it said exectly) the server error.

---

### Post by hoopsta1423 on 2007-04-03
bump, no ideas?

---

### Post by leamphil on 2007-04-03
Found a way to get mine to connect :)  ... possibly only WEP related ?

1) Take out all the fancy stuff in /etc/network/interfaces so there is just things like
    [I]auto wlan0
    iface wlan0 inet dhcp[/I]

2) Use KNetworkManager to start the wireless connection (I understand step #1 is required for the wireless connections to be visible to KNM).
    Without doing anything else, this fails for me, getting to 57% done & then re-asking for my WEP security key

3) SO .. try to connect to the wireless n/w with KNM and while it is trying, enter
    [I]sudo iwconfig wlan0 key s:<your WEP key>
[/I]
Strangely this works for me :)

What I saw happening while KNM was trying to connect (& failing) was a weird WEP key as shown from
   *sudo iwlist wlan0 enc*       ... nothing like what I had given KNM

---

### Post by hoopsta1423 on 2007-04-03
no luck with that last comment

bump
:(

---

### Post by John Thomas on 2007-04-05
> **leamphil said:**
> Found a way to get mine to connect :)  ... possibly only WEP related ?

1) Take out all the fancy stuff in /etc/network/interfaces so there is just things like
    [I]auto wlan0
    iface wlan0 inet dhcp[/I]

2) Use KNetworkManager to start the wireless connection (I understand step #1 is required for the wireless connections to be visible to KNM).
    Without doing anything else, this fails for me, getting to 57% done & then re-asking for my WEP security key

3) SO .. try to connect to the wireless n/w with KNM and while it is trying, enter
    [I]sudo iwconfig wlan0 key s:<your WEP key>
[/I]
Strangely this works for me :)

What I saw happening while KNM was trying to connect (& failing) was a weird WEP key as shown from
   *sudo iwlist wlan0 enc*       ... nothing like what I had given KNM

Stupid question??: Why are you using KNetworkManager?  Are you in the KDE desktop?  Using Kubuntu?  Will NetworkManager act the same for me in gnome-interface ubuntu?

---

### Post by stchman on 2007-04-05
> **hoopsta1423 said:**
> Hey guys, there has got to be a quick answer for my question.
I just install Edgy on my Presario V2000 with a Broadcom 4318 wireless card
I Installed ndiswrapper with the bcmwl5a.inf and the wireless card can scan and the light is on, telling me that the card is enabled.

One problem though, i cannot connect to any network, and cannot even ping my router using wireless. It is a very weird situation as the card can scan for any available networks but will not connect. I tried editing the /etc/network/interface to put an essid in there, but no luck with that. I have tried three different wifi managers and still no luck

Let me know what you guys need from me, and if you can help me thatd be awesome.

A buddy of mine had a Broadcom 43XX wireless card on his machine.  I used the following:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)

and it worked like a charm.  I then followed the procedure listed on my website

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html) (skip the portion about Atheros driver installation)

This got the the WEP, WPA, and WPA2 portion working.  This involved installing network-manager and editing a couple of text files.  The network manager also has a drop down menu that will show you all available networks.

This worked for him and it should work for you.

---

