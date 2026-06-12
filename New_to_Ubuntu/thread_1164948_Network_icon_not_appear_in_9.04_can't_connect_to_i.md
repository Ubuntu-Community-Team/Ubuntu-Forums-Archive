---
title: "Network icon not appear in 9.04 can't connect to internet"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by chamithmalinda on 2009-05-20
I Upgrade my Ubuntu 8.10 to 9.04 but at about 2 or 3 days my net connection is not working(I mean Not appear. But settings are OK ). I have Broad Band connection(E 220 Huwei) . In 8.10 it was working. Also the network icon is not appear on the panel then there is no way to click "Connect". Many of my friends having this problem (Because of Upgrading to 9.04).

---

### Post by billgoldberg on 2009-05-20
> **chamithmalinda said:**
> I Upgrade my Ubuntu 8.10 to 9.04 but at about 2 or 3 days my net connection is not working(I mean Not appear. But settings are OK ). I have Broad Band connection(E 220 Huwei) . In 8.10 it was working. Also the network icon is not appear on the panel then there is no way to click "Connect". Many of my friends having this problem (Because of Upgrading to 9.04).

Are you using wired or wireless?

Post the outcome of 

ifconfig and iwconfig

here.

---

### Post by chamithmalinda on 2009-06-03
I have a wireless connection(HSDPA)

---

### Post by valex on 2009-06-03
I suffered same problem. bt still havent no answer. finally i reamoved ubuntu and installed mandriva.

---

### Post by theozzlives on 2009-06-03
Check if Network Manager is installed.

---

### Post by chamithmalinda on 2009-06-03
Finally I found a way to connect to the Internet Sorry for Valex (Installing Mandriva).

Simple way but this is not the answer that i want(Still there is no network icon on the panel)

GO TO >> [COLOR=Red]**System > Preferences > Network Connections >**[/COLOR]
         
            and double click on your net connection(Properties) then put a tick mark on
            _**connect automatically**_.
            Then every time You boot Ubuntu connection will **automatically established**.

---

### Post by matador1504 on 2009-06-03
Same problem here. I have network manager installed, just the network icon does not show. It's a problem since when I sometimes lose wireless connection i have to log out and log in again. I guess i can use other tools such as wlanassistant etc but would prefer network manager.

Any ideas anyone

---

### Post by matador1504 on 2009-06-03
Actually i think i solved it

If you right click in the GNOME panel and select "Add to panel" and select Notification Area. The icon should now appear...

Hope this helps!

---

### Post by chamithmalinda on 2009-06-08
maxa thankx [matador1504]("http://ubuntuforums.org/member.php?u=353614") and valex,,,,,,,,,,,,,,,,,,,

---

### Post by ledzepjes on 2009-06-21
Wow, thanks, that solved my problems...right clicking panel menu...clicking add to panel...and adding "Notification Area" I was messing with the autohide and transparency settings of the top panel menu before I lost my network manager tray icon, opera tray icon and synce tray icon. Would that have caused it to disapear? I wouldn't think so, but thanks, nm-applet is displayed now and so is my opera and snyce tray icons! :P I couldn't figure this out for the life of me since the nm-applet was running but wasn't displaying, and was I ready to reinstall gnome-desktop, luckily I found this first.

---

