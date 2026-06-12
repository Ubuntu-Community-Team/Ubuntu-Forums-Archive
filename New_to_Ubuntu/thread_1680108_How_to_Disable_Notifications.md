---
title: "How to Disable Notifications"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by rs87424 on 2011-02-02
I am currently using Ubuntu Maverick 10.10 and I can't seem to turn off the notifications, specifically the wireless/lan internet notifications. I unclicked the "enable notifications" box and the notifications still appear. I also heard about turning the notifications off in gconf but if I click on that feature then the other feature will re appear. 

I have no idea why I can't turn the notifications off, it seems simple enough but for some reason 10.10 is not cooperating

---

### Post by taseedorf on 2011-02-02
try removing libnotify via synaptic..

---

### Post by rs87424 on 2011-02-02
well if I remove that... wouldn't that remove too many other important applications?

---

### Post by Frogs Hair on 2011-02-02
If you remove the notification area applet , which includes the internet connection notification you will lose all notifications from that applet.
 
The place to remove this is very hard to see on some themes and may appear as thin line or row  of dots to the left of the wireless / lan indicator.
 
I don't know the path to the Gnome panel applets in the gconf. but Gnome panel would be a place to start.
 
As mentioned the  Synaptic Package Manager will also do the trick , because it is possible to remove some functions while keeping others .

---

### Post by rs87424 on 2011-02-02
well I looked into the Synaptic Package Manager and found "python-notify"

the description: libnotify sends desktop notifications to a notification daemon as defined in the Desktop Notification spec. These notifications can be used to inform the user about an event or display some form of information without getting in the user's way. 

based on the description I think maybe I should remove that one?

---

### Post by oldos2er on 2011-02-02
I usually just remove notify-osd.

---

### Post by rs87424 on 2011-02-02
when I try to remove notify-osd the terminal says that it will remove ubuntu-desktop... I wonder if that will cause any adverse effects?

if I want o remove these packages there is always a bad side effect

---

### Post by KlytusLord on 2011-02-02
I am having the same problem. I want to remove only the evolution mail notifier (I do not use evolution, and I have already uninstalled it, but the notification stayed on the panel.)

I also want to remove Universal Access Preferences, but I want to keep my volume and battery notifications.

From what I have been reading, it seems the notifications are just not very configurable; they have no options that I can find.

Like the original poster, when I use the package manager to try and remove what seems to be relevant, I get warnings about all sorts of other things that will also be removed, and since I am not that well-versed in Linux/Ubuntu, and I have no idea how much damage I will do :)

---

### Post by rs87424 on 2011-02-02
Right^

I am not removing anything until I know its tried and true. With Ubuntu, if you start removing things then other things don't work properly.

---

### Post by uRock on 2011-02-02
Do NOT remove libnotify.

---

### Post by uRock on 2011-02-02
> **KlytusLord said:**
> I am having the same problem. I want to remove only the evolution mail notifier (I do not use evolution, and I have already uninstalled it, but the notification stayed on the panel.)
That little package is used by Pidgin as well. I just highlightedthe packages for both and neither wanted to remove anything else. See the screenshot.

> I also want to remove Universal Access Preferences, but I want to keep my volume and battery notifications.Fix this here. [http://ubuntuforums.org/showthread.php?t=1680401](http://ubuntuforums.org/showthread.php?t=1680401)

---

### Post by rs87424 on 2011-02-02
I removed evolution-indicator and no changes happened after I rebooted. I wonder if its absolutely impossible to stop these notifications from happening.

---

### Post by uRock on 2011-02-02
> **rs87424 said:**
> I removed evolution-indicator and no changes happened after I rebooted. I wonder if its absolutely impossible to stop these notifications from happening.
I use Pidgin, the only time the envelope icon appears is when I have an unread message.
The only constants in the notification area, for me, is the one for Parcellite and Network Manager in 10.10.

---

### Post by rs87424 on 2011-02-02
Well.. the only thing I am trying to remove is the notifications for Wireless/LAN network discovery. The pop up bubbles are extremely annoying as they linger for too long on my desktop.

If there is anyway to remove that I would appreciate it immensely.

---

### Post by uRock on 2011-02-02
> **rs87424 said:**
> Well.. the only thing I am trying to remove is the notifications for Wireless/LAN network discovery. The pop up bubbles are extremely annoying as they linger for too long on my desktop.

If there is anyway to remove that I would appreciate it immensely.
I think I may have found something for this. I opened **gconf-editor** via terminal. 

Go to Apps> nm-applet and there are the options shown in the screenshot.

---

### Post by rs87424 on 2011-02-02
you know.. I tried that already. I unchecked those boxes and for some reason the notification box that enables notifications under the wireless/lan icon is checked. So there is something strange going on between the icon on the desktop and nm-applet, I can't seem to find a work around

---

### Post by oldos2er on 2011-02-03
> **rs87424 said:**
> when I try to remove notify-osd the terminal says that it will remove ubuntu-desktop... I wonder if that will cause any adverse effects?


No. ubuntu-desktop is a metapackage; the only time you would need it is when upgrading to a newer version of Ubuntu.

---

### Post by TechWiz2100 on 2011-02-03
You gotta love how people overlook the simplest things...

Start Evolution
Edit > Preferences > Mail Preferences > General Tab
First 4 settings are about notifications for Evolution

Wifi
Right click the wifi icon and uncheck notifications

---

### Post by rs87424 on 2011-02-04
> **oldos2er said:**
> No. ubuntu-desktop is a metapackage; the only time you would need it is when upgrading to a newer version of Ubuntu.

Oh ok.. I was just worried that it would interfere with something

^
I don't even use Evolution... and apparently that option is not there in Evolution...I have already looked

---

### Post by Paqman on 2011-02-04
> **oldos2er said:**
> No. ubuntu-desktop is a metapackage; the only time you would need it is when upgrading to a newer version of Ubuntu.

Generally i'd assume so, but it's not inconceivable that a SRU could be pushed out using ubuntu-desktop, so it could cause you to miss out on an important update even when you aren't upgrading.

But in general the idea is that removing ubuntu-desktop won't break anything, but it might stop you from getting new packages at some point.

---

### Post by TechWiz2100 on 2011-02-04
> **rs87424 said:**
> Oh ok.. I was just worried that it would interfere with something

^
I don't even use Evolution... and apparently that option is not there in Evolution...I have already looked

Dunno what version you are using but the latest most definitely has this option in there

Also if you don't use Evolution, how can it be displaying any notifications when it would not have any accounts linked nor would it even be running.

I think you are confusing Evolution with something else. Or theres another program that is called Evolution

---

