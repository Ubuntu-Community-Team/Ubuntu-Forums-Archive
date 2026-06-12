---
title: "HP ProBook running 18.04 does not connect to a specific router"
date: 2018-08-27
forum: Networking &amp; Wireless
---

### Post by davidh56 on 2018-08-27
The HP probook on which this is being typed won't connect to the owners router. The behaviour  is that we can see the network SSID but we cannot enter the network password as the "Connect" option is greyed out. Any advice on tracking this down would be much appreciated. I have a wireless-info.txt if that is helpful - where should I post it? (Note that the device connects to a network on a different router). i beleive the router in question is a couple of years old (and yes, its been restarted and other devices can connect to it without issue). At the moment I am suspecting some crazy config issue with the probook, but need pointers on where to start looking

Cheers!

---

### Post by chili555 on 2018-08-28
> I have a wireless-info.txt if that is helpful - where should I post it? [http://paste.ubuntu.com](http://paste.ubuntu.com) Next, post the link and we'll review it. Please be certain that the troublesome SSID (router) is listed in the scan results and tell us which it is.

---

### Post by davidh56 on 2018-08-28
Hi

[Here ]("https://paste.ubuntu.com/p/FqdGWkm8Dd/")is the link to the paste .

The SSID in question is "vodafoneTQ3L".

Just FYI. THis is a rural location - the nearest neighbour is about a kilometer away. This diagnostic was taken about 5 meters away from the router itself. I am aware of at least 4 devices that connect to the router without issue (I own two of them!) 

Thanks for your help!

---

### Post by chili555 on 2018-08-28
> [[/etc/NetworkManager/system-connections/vodafoneTQ3L]] (600 root)
[connection] id=vodafoneTQ3L | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=vodafoneTQ3L
[ipv4] method=[COLOR="#FF0000"]disabled[/COLOR]
[ipv6] method=ignoreHmmmmm...

I think you meant to select Automatic (DHCP).

[IMG]https://i.stack.imgur.com/Lu4y0.png[/IMG]

I suggest a few other changes. Make sure the router is set to a fixed channel; 1, 6 or 11 and not auto channel select.

Also, I recommend that your regulatory domain be set explicitly. Check yours:

  ```
  sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

   ```
 sudo iw reg set NZ
```

Of course, substitute your country code if not New Zealand. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

   ```
 REGDOMAIN=NZ
```

Proofread carefully, save and close the text editor.

Please post back to tell us if there is any improvement.

---

### Post by davidh56 on 2018-08-28
That looks like it - however I assume the dialog you showed is in wifi settings? On this machine that appears to be broken. Is there a command line way of changing that setting?

---

### Post by chili555 on 2018-08-28
The kwik n durty way is to remove the connection information altogether, restart NM (or possibly reboot) and let NM detect it again. From the terminal:

```
sudo rm /etc/NetworkManager/system-connections/vodafoneTQ3L
sudo service network-manager restart

```
If it doesn't see the router and offer to connect, try a reboot.

---

### Post by davidh56 on 2018-08-29
yep - that did the trick.

Now to find out why the menus don't work

Thanks very much for your help - much appreciated!

---

