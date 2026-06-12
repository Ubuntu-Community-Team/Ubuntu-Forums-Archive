---
title: "sky wireless and ubuntu"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by mbzn on 2009-02-03
Hi,
I lately moved in with friends. they use a sky wireless router
I have the "ssid" and the "key", only info i find on the router. I cant seem to set it up on my notebook
I have a intel pro 2100 built in and a orinoco silver pcmcia card
is there a guide i could read as i dont know much about wireless

thanx in advance

---

### Post by jimmy the saint on 2009-02-03
what problem are you having exactly?  Does the network show up under the available wireless networks?  Are you prompted for the passkey?  Does it simply fail to connect after you enter the passkey?

also, open a terminal and give us the output of
```
lspci -v | less
```

---

### Post by mbzn on 2009-02-04
hi

sorry, i'm on a windose pc now so it's kind of difficult posting the output, My wireless cards are detected fine and it picks up the router fine with a good signal.
When i connect to it, it asks me for a key (WEP 40/128-bit key; WEP passphrase; LEAP; Dynamic WEP) - Tried them all...
The key on the router is '8-letters A-Z' if thats any help. it also asks me for Authentication: (Shared key / Open system)..
it then fails to connect and the key i entered changes to a 26-didgit hex key

When i try with WiFi Radar - configure-wifi options-mode-auto;channel-auto;key-xxxxxxxx;security-(tried open&ristricted)
it tells me "could not get ip address"

What am i doing wrong?

---

### Post by jimmy the saint on 2009-02-04
the best thing to do would be to look at the routers security settings and see what kind of security it has.  I am not familiar with sky routers, but usually consumer routers have pretty straightforward firmware.  It will probably be under a section called wireless security or something similar.

---

### Post by mbzn on 2009-02-04
How do i check this as there is no pc conected to the router? and i dont know if there is a manual for it.

---

### Post by jimmy the saint on 2009-02-04
just type the ip address of the router in your webbrowser.  you will likely be prompted to log in to the router.  If the defaults haven't been changed, just look at the router to get the model number, then either go the the manufacturers website, or do a google search for "sky router <model number> default login" or something to that effect.  If your roommate did change the defaults, you will need to get the password from them.

---

### Post by mbzn on 2009-02-04
Thanx alot, sorry as i dont know much about routers, but i think i'll figure it out from here...

Thanx again

---

### Post by Kevbert on 2009-02-04
The Sky wireless router is probably set for WPA-PSK (WPA-Personal) as opposed to WEP. I'm using a Sky branded Netgear DG834GT Router.  
Do you have an ethernet/lan cable that you can connect between the router and PC ? If so, you can temporarily turn off all encryption and make sure that wireless works OK.  With the PC connected open a web browser and enter [http://192.168.0.1](http://192.168.0.1) The router will now ask for a user name - admin and password - sky  From there you want to select Wireless settings and Select Disable under Security Options (to temporarily turn off ALL encryption). Now select Apply and Logout. Close the browser and remove the cable. Now you can try to connect the wireless so remove the cable.  Now go to the two screen icon (top righthand corner of display and right-click it and check wireless is enabled. Left click the icon and select your wireless router (SKYxxxxx) and you should be able to connect.
You can now go back and turn on wireless Encryption (open web browser, enter [http://192](http://192)......)
You need to change the admin password at some point to something other than 'sky' as anyone who can see your router can take over control of the router with the admin and sky (default) passwords.
You can get a manual from the Netgear [[COLOR="Red"]Website[/COLOR]]("http://www.netgear.co.uk/product_support.php").

---

### Post by mbzn on 2009-02-04
thanx alot again... got it working.
now i know a litle someting extra, guess we never stop learning.

---

