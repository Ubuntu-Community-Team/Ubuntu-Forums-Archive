---
title: "NetworkManager under Fluxbox -- keyring problem?"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by AlucardZero on 2006-11-07
Hi,

I'm trying to use Fluxbox.  After some difficulty I have it almost working satisfactorily.

When I log in (after a reboot), I am not prompted for my keyring password, as I was in Gnome.  NM tries and fails to connect to my wireless network, and asks me for my WEP key every single time (then "connects" but fails to get an IP address.. but it works in Gnome).

Logging into Gnome, everything works fine, and if I then log back into Fluxbox, wireless works.. until it dies again.

From lots of searching and fixing other problems, I have the following in my ~/.fluxbox/startup:
```
GSDPID=`pidof gnome-settings-daemon`
if [  "x$GSDPID" == "x" ]; then
gnome-settings-daemon &
fi

gnome-keyring-daemon &
nm-applet --sm-disable &
gnome-power-manager &
```

However, this has not been enough to fix things.  Ideas?

Alternatively, is there an alternative to network-manager(-gnome) that can do WPA?

---

### Post by kylevan on 2006-11-07
I'm not sure about your problem with the keyring, but I'm pretty certain that NM supports WPA/WPA2 right out of the box.  At least it did on my install.  Is your router configured to use WPA?

---

### Post by AlucardZero on 2006-11-07
NM supports WPA, yes, but that's not the problem.  Under Gnome, wireless works.  After a bootup and login to Fluxbox, wireless does not work.  After a bootup, login to Gnome, logoff and login to Fluxbox, wireless works.

When I log into Gnome after a reboot, I am prompted for my keyring password, and I enter it and wireless works.  When I log into Fluxbox after a reboot, I am not prompted, and wireless does not work, even when I enter the network settings manually.

So since NM works under Gnome but doesn't seem to elsewhere, as I see it my choices are a) find out what the hell else NM need to work or b) use something else.

Edit: Sorry, just remembered -- I'm on a week-old clean install of Edgy.

---

### Post by AlucardZero on 2006-11-09
Well, wpagui and wifi-radar are out. Any other suggestions?

---

### Post by david.hilton.p on 2007-09-15
The fix has been posted elsewhere, but as this is (or was) the first result on google for fluxbox wireless, I'll just post the solution here.

To have access to the gnome keyring manager, you need to have
```
gnome-keyring-daemon &
```
in your .fluxbox/startup file.

---

### Post by AlucardZero on 2007-09-16
if you read my posts, that did not work for me when I tried it.

That said, it may or may not work now, but for me it's a moot point since I am an XFCE convert now.

---

