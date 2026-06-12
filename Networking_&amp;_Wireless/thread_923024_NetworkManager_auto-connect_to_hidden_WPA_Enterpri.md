---
title: "NetworkManager auto-connect to hidden WPA Enterprise"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by TBKDan on 2008-09-17
Hi, I have Ubuntu 8.04.1 x64 installed on my Dell XPS M1730 laptop with an Intel 4965AGN card that I just installed today.  Everything works fine, I can connect to both my WPA2-PSK broadcasted network at home and my WPA Enterprise hidden network at school, but the problem lies in auto-connecting to the school network.  Since my home network ssid is broadcasted, nm-applet picks it up and connects right away.  However, even though the school network is saved in nm-applet, it refuses to auto-connect and there is no way to tell nm-applet "try this saved profile"; I have to choose "Connect to other Wireless network" every time and fill out my information... it gets pretty tedious after a bit.  Is there any way to get nm-applet to automatically connect to a hidden WPA Enterprise SSID, or at least connect using the saved profile instead of entering everything manually every time?  I've tried wicd (a couple of weeks ago), and from what I remember it failed the test because it couldn't connect to WPA enterprise (something like that, I can't remember offhand, but end result it couldn't connect at all).

So, bottom line: short of configuring my own script (wpa_supplicant or other), is there any way to get nm-applet to automatically connect to a hidden ssid WPA Enterprise wireless network?  It obviously is possible... XP/Vista/Macs all do it :(

Thanks for any input.

---

### Post by TBKDan on 2008-09-18
Bump... I would try this with Ibex alpha but I don't want to actually install it and this requires a reboot to test =/

---

### Post by secretspicy15 on 2008-09-19
I'm having the same issue. I will let you know if i find anything!

---

### Post by TBKDan on 2008-09-21
Is there any way to install nm-applet 0.7 on Hardy without completely fubar'ing my system?  I just want to test to see if I can expect this to help...

---

### Post by mcmonkeys1 on 2008-10-29
i think this seems to be a widespread problem, i guess hidden networks are just being ignored for some reason?

also, bump!

---

### Post by TBKDan on 2008-10-29
In Ibex it's a little easier to deal with since it actually remembers the settings and you can select that profile to attempt to connect, but it still does not automatically find it and connect if it's hidden :(

---

### Post by scientist434 on 2008-10-29
I have intrepid and it doesn't connect at all to my wpa2 personal network hidden ssid hardy was fine with it if i configred it each time so this still seems to be a problem wpa encrytions in intrepid.

good luck bump

---

### Post by TBKDan on 2008-10-29
I can connect just fine to a WPA enterprise hidden network when I manually tell it to.  Sometimes however I get a weird issue where NetworkManager doesn't properly set the SSID.  Right before you hit connect, try the following:

```
sudo iwconfig wlan0 essid SSID
```
Where wlan0 is your wireless device name and SSID is obviously your SSID.  Click connect and see if it connects.

---

### Post by c011699 on 2008-11-06
<gripe>
Same issue here - Ihave to manually enter the connection settings each time I want to connect to my corporate network (WPA2 Enterprise, hidden SSID).  Running hardy, using nm-applet.  I can see the profile under 'Edit Wireless Networks' but there is no way to actually SELECT that profile.  I can understand the limitations / resource consumption in scanning for an arbitrary number of hidden profiles, but there should be some way to SELECT a saved profile, otherwise what's the point of saving the settings?
</gripe>

---

### Post by TBKDan on 2008-11-06
You can select and activate a profile much easier in Ibex, but it still does not do it automatically if the SSID is hidden (if it is not hidden, it works just fine :)).  But as I mentioned, sometimes for me it would try to associate with an open SSID when nm-applet was trying to connect to the hidden WPA2Ent SSID which obviously did not work; I sometimes have to manually set the SSID while it is trying to activate the profile.

---

### Post by lvleph on 2009-02-17
So tere is no solution to this yet? I suppose a startup script could accomplish this?

---

### Post by mcmonkeys1 on 2009-02-21
well, i installed Intrepid Ibex, and the problem of having to re-enter user/password has dissappeared, because i can no longer connect to these networks whatsoever! another step backwards for me, doh! am having to boot into windoz€(ugh!) in college to connect to network.


on an unrelated note KDE 4.1 is horrible also. reminds me of vista, putrid.

---

### Post by lvleph on 2009-02-21
My universities wireless gives me all sorts of problems. In fact, it is not just linux it is also my friends Macs. You should inform your university of the issue. My solution to my problem was to bring a wireless router to my office and hook that up. lol Now I don't have to worry about blocked ports either on the wireless.

---

### Post by mcmonkeys1 on 2009-02-24
solution: don't use network manager to connect to these networks.
i can't remember all the details, but u have to do it manually basically, includes such things as a wpasupplicant.conf file and 2 other scripts. and probably using windows driver with NDIS wrapper.

couldn't be bothered myself.

---

### Post by TBKDan on 2009-02-24
> **mcmonkeys1 said:**
> solution: don't use network manager to connect to these networks.
i can't remember all the details, but u have to do it manually basically, includes such things as a wpasupplicant.conf file and 2 other scripts. and probably using windows driver with NDIS wrapper.

couldn't be bothered myself.

With Ibex, it *can* connect to these networks if you tell it to manually connect via NetworkManager, it just can't automatically discover *hidden* SSIDs.  Again, NetworkManager can connect, just not automatically.  And luckily with Ibex, it saves the login information so you don't have to re-type it every time you wish to connect.

---

### Post by Hamilton José Brumatto on 2011-11-10
Hi, there is a trick that works fine for me:

at "/etc/rc.local" you include the following line:

iwlist wlan0 scanning essid "HIDDEN_ESSID" 1>/dev/null 2>/dev/null

where wlan0 is youw wireless interface, and "HIDDEN_ESSID" is the essid of your hidden wireless access point.
Optionally you can log out the results.

Hamilton

---

### Post by overdrank on 2011-11-10
Thanks for sharing. Thread closed. Back to sleep little thread. :)

---

