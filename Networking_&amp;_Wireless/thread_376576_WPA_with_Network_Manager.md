---
title: "WPA with Network Manager"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by spacebetween on 2007-03-05
I am using the latest of everything, and I just recently overcame the entire Broadcom 4318 obstacle.

Now I am much happier that I don't have to switch to Windows to get online. I've been trying to figure out this wpa supplicant deal, though.

The network that I primarily use (a university network) uses WPA. I'm not having problems connecting, but is there a way I can make Network Manager remember the settings? It's kind of annoying to have to locate the certificate on my computer, type in my username/password, etc. I have loaded the settings that my university recommends into the /etc/wpa_supplicant.conf file, but I get a little lost after that. Does that even have anything to do with getting Network Manager to remember settings for this network?

I have looked all over for an answer, but maybe I looked with too broad or too specific of terms. I don't mean to spam.

Thanks!

---

### Post by spacebetween on 2007-03-05
bump

---

### Post by WCentauri on 2007-08-07
I'm running into the same trouble with Network Manager on Feisty.  Does anyone have any tips?

---

### Post by nodows on 2007-08-07
You should be able to store your passsword settings in the keyring manager.

Go to System --> Administration --> Keyring Manager

At least on my fiesty box I have to enter my local keyring password
everytime I log onto a secure network that I've put the key into
the keyring manager, which is mildly inconvenient, but much better
than manually putting all the WPA information in for EVERY 
access point.

For me it now automatically stores all new WPA/WEP keys in there
but if you have to do it manually you shoulud be able to add
"nm-applet" to your keyring and give it some information.  

Not sure if this is a complete answer but it should
point u in the right direction.

---

### Post by EdTheUniqueGeek on 2007-08-08
Try installing and using WICD Network Manager instead of the default Gnome Network Manager install. 

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

---

### Post by WCentauri on 2007-08-08
Hey nodows,

Can you more specific as to how you got the keyring-manager to remember your wpa information?  I looked at the keyring-manager gui and did not see an obvious way to add applications to it.

Thanks.

---

### Post by buntunub on 2007-08-08
> **EdTheUniqueGeek said:**
> Try installing and using WICD Network Manager instead of the default Gnome Network Manager install. 

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

Be very careful about installing wicd because when you do, it will uninstall the nm-applet and trash your wifi settings like it did for me. Additionally, it was crap and did not work for even wired networking!

---

### Post by imdano on 2007-08-08
How long ago did you try to use it?  You're the first person I've heard say they couldn't get wired networking to work.

---

### Post by nodows on 2007-08-21
WCentauri... check out [this post]("http://blog.yumdap.net/archives/56-The-ease-of-WPA-in-Ubuntu-Feisty-Fawn.html")

He seems to have a little writeup about using the keyring manager with wpa passwords.
Hope it helps.

---

### Post by kevdog on 2007-08-21
I really like WICD, and the support is great, however I did use network manager with wpa supplicant for a long time.  If you dont need a static Ip, then these are the instructions that worked for me:

[www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

