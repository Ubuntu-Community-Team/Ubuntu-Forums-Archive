---
title: "Sudden IPW2200 wireless problem on Compaq V2000 laptop"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by gnigamica on 2008-07-29
Any assistance with this would be appreciated.

I have been running 8.04 LTS since upgrading from 7.04 LTS.  Two days ago, wireless networking stopped working.  Rather... stopped coming up automatically.  If I manually run sudo ./networking restart from /etc/init.d, it comes up fine.  At first I thought it might be a hardware problem, but when I boot off the live CD, no problem.

The signal strength meter next to the network applet in the tray has also disappeared, and does not appear even when I manually restart networking.

Any ideas?  It's a bit frustrating, and I'd rather figure this out than do a re-install.

The machine is a Compaq Presario V2000 series laptop using IPW2200 wireless.  Has been running Ubuntu since 7.04 with no problems.

Thanks.

---

### Post by gmoney on 2008-07-29
I also have a Compaq V2000, so I feel your pain on the wireless situation.  I'm not positive, but I think a system update (possibly the kernal, but again, I'm not sure) may have caused issues with the wireless driver.

What kind of wireless card you have on your V2000?  On mine, I have a Broadcom Air Force One.

```
lspci | grep Broadcom
```

Do you see anything about Broadcom after inputting the above command in the terminal?  If so, then this guide should help you (it worked like a charm for my Braodcom card):

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

The title of your post mentions IPW2200.  Is it an Intel Pro Wireless card?  If so, you may want to try this page for documentation:

[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

If you're still stumped, let me know.  I'm certainly no expert when it comes to wireless drivers, but I will do what I can to help you out.

---

### Post by gnigamica on 2008-07-30
My V2000 has the Intel Pro Wireless card.  It has been running Ubuntu for over a year without a hitch, so I'm not sure what happened recently.

My kludge fix has been to add the following line to /etc/rc.local  :


```
/etc/init.d/networking restart
```


Which seems to do the trick... networking is up before I log on.  But I miss the wireless strength meter in the system tray!

There were a number of updates in recent days.  I wonder if one of them has impacted the networking startup routine?

Anyway, thanks for your advice.

---

