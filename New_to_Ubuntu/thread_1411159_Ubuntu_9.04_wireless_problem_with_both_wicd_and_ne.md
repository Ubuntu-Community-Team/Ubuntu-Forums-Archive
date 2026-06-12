---
title: "Ubuntu 9.04 wireless problem with both wicd and network manager"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by dlteach2 on 2010-02-19
Ubuntu 9.04 on a  3 year old Presario Compaq laptop.  Am newbie and have posted this question before without resolution. I probably wasn't as clear as I hope this message is.  

 A friend installed wicd to access my son's wireless router and connection. It worked but only for that connection.  

So, two days ago, he uninstalled wicd and reinstalled Network manager. We could access the store network and see other networks, but when I returned home, I could no longer connect to the internet through my son's router.  The connection is visible, but when I put in his password and click, a message comes up requesting  a password for keyring to unlock. Says  Network Manager applet wants access.  I have put in both his and my passwords without success. Is there a different type of password that needs to be put in? If so, where do I find it? What happens if I go to another location and can't access anything again?

I have read other posts on the forum about similar problems but never one about problems with both wicd and Network manager. 

Is this problem with my particular type of computer? Thank you so much for any suggestions.

---

### Post by cariboo on 2010-02-20
Right-click the Network-Manager Icon in the top panel, and select edit connection. Click the Wireless tab and select your wireless device, then click the edit button. Make sure Available to all users is enabled, ypu will find in in the lower left corner of the window. Click apply and enter your user password. You may have to reboot to enable the changes.

---

### Post by brij on 2010-02-20
[http://ubuntuforums.org/showthread.php?p=8854161#post8854161](http://ubuntuforums.org/showthread.php?p=8854161#post8854161)

---

### Post by dlteach2 on 2010-02-20
Thank you for responding. With your directions in hand, I just checked my apps and Network Manager is not listed anywhere. The person who changed everything yesterday must have used a different program or may not have listed it again so I could see. I thought he was going back to network manager - my apologies.  
What is new on the list when I click on internet is Transmission BitTorrent Client. I have no idea what that is.

---

### Post by bkratz on 2010-02-20
> **dlteach2 said:**
> Thank you for responding. With your directions in hand, I just checked my apps and Network Manager is not listed anywhere. The person who changed everything yesterday must have used a different program or may not have listed it again so I could see. I thought he was going back to network manager - my apologies.  
What is new on the list when I click on internet is Transmission BitTorrent Client. I have no idea what that is.

He was referring to the network icon at the top of the screen, in 9.04 it looks sorta like two monitors next to each other if using a wired connection (probably next to the speaker). Network manager does not show in the menus you looked at. You can do the same thing he was asking by going to system>>preferences>>network connections and selecting and editing the wireless tab.

Transmission Bittorrent is just what it says---used for download/uploading torrents, not what you are looking for.

---

### Post by dlteach2 on 2010-02-22
thank you. I feel so dumb...but I'm trying.

---

### Post by dlteach2 on 2010-02-24
Well, now the scenario is changed. I'm not even getting to the message about the keyringws. Here is what is I am doing:

Following your instructions I have :

right clicked on Network Manager
Clicked on Edit Connections
Highlighted my preferred wireless connection which I ptyped in somewhere)
Clicked on Edit
Put in SSID name
The Mode says Infrastructure (other choice is ad hoc)
BSSID - I don't what what this is or where to get the information. Please advise
Click on Allow all Users
Click Apply

And the screen comes right back to me. So is it the missing BSSID information? 

Thank you.

---

