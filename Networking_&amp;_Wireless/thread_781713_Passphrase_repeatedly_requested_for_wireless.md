---
title: "Passphrase repeatedly requested for wireless"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by koma77 on 2008-05-04
I just updated from 7.10 to 8.04 and now there is a problem with my wireless connection.

When I log in I get to enter the passphrase for my WPA. I do that and that blue circle in the network icon starts spinning.
After a while I get to enter the passphrase again, and again and again...

Once in perhaps 20 tries it will work and connects ok for that session!

My signal strength is good and network manager correctly displays available networks, so the card is ok.

As said, it worked in 7.10 and still works in XP. I really don't want to switch back to XP, but without an internet connection...

I suspected that the keyring was to blame since there was no keyring named "default". I created a keyring with that name and rebooted, but no success.

Please, any ideas?

---

### Post by ew16301 on 2008-05-04
You could try to right click on your network manager and then edit wireless networks and remove any of the ones you see there. Also maybe try deleting your keyring.

---

### Post by koma77 on 2008-05-04
I tried removing the network from the network manager, but that didn't do anything.

Which keyring should I delete?

The one I created or the one that was already there? The one that was already there is named "login". If I delete that will it be created again automatically or will I have a bigger mess? :)

---

### Post by koma77 on 2008-05-04
I created a brand new user and tried to login to the network with this user.

I didn't work either... So I guess the keyring is not the culprit here.

Any ideas on what I can try?

---

### Post by pro003 on 2008-05-04
try this, it may help you:

[WICD]("http://wicd.sourceforge.net/")  


[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by pro003 on 2008-05-04
open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line: 

 ```
   deb http://apt.wicd.net gutsy extras 
```

now close and click RELOAD button. Then do the search: wicd

that should help you solve the problem, hopefully:)

---

### Post by koma77 on 2008-05-05
I tried using wicd (which seems to be a very nice application by the way) but it didn't solve my problem.

But, when trying to install wicd I noticed one, perhaps interesting, thing:

I had to connect the wired network in order to install wicd and expected network manager to detect my eth0. It didn't: it just said that there was no connection to the wired network.

But, ifconfig reported an ip-address. And I could access the internet.

So, I installed wicd and set it up to use my wireless, always connect it and set the correct WPA key. Wicd tries to connect but always tries "obtaining an IP address" forever.

Maybe this is related to the configuration of network interfaces or DHCP.

Any ideas or opinions?

---

### Post by pro003 on 2008-05-05
Did you check out with your ISP? maybe they have experiencing some problems, maybe it's up to them, not you... at least that's how it looks to me...maybe am wrong, but just saying that you need to eliminate things and get to the solution.. 

P.S. Do you have same problem in Windows perhaps?

---

### Post by koma77 on 2008-05-05
It still works fine in XP, and it worked nicely in 7.10. 

It stopped working when I upgraded to 8.04.

It seems like there are more people on this forum with the same problem, but I haven't found a solution yet.

It's almost as if network-manager is not getting the right picture on what's going on with the network devices. Dbus?

---

### Post by pro003 on 2008-05-05
i've noticed that many people who have upgraded have various issues in 8.04, it's just am saying that maybe you should try clean install, backup your home folders and give it a try, it's worth of it...:popcorn:

---

### Post by koma77 on 2008-05-05
But still, there must be a reason why it fails, and finding the real cause of the problem will increase the quality (or restore in this case) of Ubuntu.

I think this is Launchpad bug #225599. I want to kill this bug, but I'm running out of ideas. :)

And returning to XP is not a nice idea.

---

### Post by quebecois on 2008-05-06
I got the same problem after upgrade to 8.04. ([http://ubuntuforums.org/showthread.php?p=4807977]("http://ubuntuforums.org/showthread.php?p=4807977"))

My router was configured WPA-PSK TKIP. It was working well with 7.10..

I changed router configuration to use WPA-PSK AES instead of TKIP.  It works!

How you router is configured? Try AES, if available...

---

