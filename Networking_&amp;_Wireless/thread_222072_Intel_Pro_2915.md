---
title: "Intel Pro 2915"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by cmilhaus on 2006-07-24
I have a Dell XPS 140M Laptop with an Inter Pro Wireless 2915 a/b/g card in the unit, and I am having a devil of a time getting Ubuntu to recognize it and connect me to my Belkin G Wireless Router.
Ubuntu sees the wireless card calls it Eth0, but beyond that I am lost at how to make a network or Internet connection. On the plus side, sound works flawlessly

---

### Post by Paerez on 2006-07-24
I have a dell laptop with 2915 and it works perfectly. eth0 is most likely your lan, while it is eth1 that is your wireless. Try using network manager to connect to wireless networks.

---

### Post by cmilhaus on 2006-07-24
I woud really love to follow your suggestion, but for the life of me, I am unable to find "Network Manager" anywhere on my installation of Ubuntu. Is this a special program one downloads perhaps? :rolleyes:

---

### Post by Paerez on 2006-07-24
its in the add/remove programs. Just click "Advanced" to get the full list, and search for:
network-manager-gnome

or simply type this in a terminal:
```
sudo aptitude install network-manager-gnome
```

---

### Post by cmilhaus on 2006-07-27
Sorry, it was realy good advice, alas it does not work. Even with the LIVE CD. the default connection is "lo"
Just not able to connect wirelessly which is a shame since everything else appears to be working perfectly.
:(

---

### Post by Paerez on 2006-07-27
type this in for me and tell me what you get:
```
lsmod | grep ipw
```

---

### Post by cmilhaus on 2006-07-29
ipw2200                      107308       0
ieee80211                      37064      1    1pw2200

This was before I did a direct wired connection to my wireless router  

after is as such

bobm@belking:~$ lsmod | grep ipw
ipw2200               107308  0
ieee80211              37064  1 ipw2200
bobm@belking:~$

---

### Post by Paerez on 2006-07-29
ok so now run this:
```
sudo iwconfig
```

---

### Post by cmilhaus on 2006-07-30
bobm@belking:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"belkin54g"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

bobm@belking:~$

---

### Post by cmilhaus on 2006-07-30
bobm@belking:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"belkin54g"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

bobm@belking:~$

Please ignore the smilies, where they show up that should read "0"

---

### Post by Paerez on 2006-07-30
if you put the output in ```
 tags, then the smilies dont show up. OK so your wireless is good to go, now you need to use one of the wireless managers like network manager or wifi-radar or something to connect. I suggest network manager. Run network manager like this:
[code]nm-applet --sm-disable
```

---

### Post by cmilhaus on 2006-07-30
bobm@belking:~$ nm-applet --sn-disable

Entered this command, and nothing happened <G> Did I do something wrong?

---

### Post by Paerez on 2006-07-30
in your notification area there should be the network manager applet. Mine has bars to indicate the signal level because I am connected. You can then click on it to pick a wireless network. I attached a screenshot.

---

### Post by cmilhaus on 2006-07-30
Nope, I get something that looks like a speaker, now when I do the code, I get a second one...
The Wireless is still not responsive, is the wireless automatically configured by Ubuntu on installation? I have flutzed around with the settings, so now I am unsure of what to do or not to do next
However, when I stick my network cable in, I got Internet Access, but still no wireless

---

### Post by Paerez on 2006-07-30
OK go to system->preferences->sessions. Click the current sessions tab and scroll to the bottom. Check to make sure that the nm-applet command is there. If it is, log out of gnome and log back in. Then you should get the network manager tray icon. Click it, and it will let you connect to both wireless (if detected) and wired (if plugged in) networks.

---

### Post by cmilhaus on 2006-07-31
I am attaching a screen shot to show you what my task bar (at top) looks like I have no little bar icon, and the line is in the preent session
I will be waiting for your reply, as I have said before you are a wonderful sourec of assistance

---

### Post by cmilhaus on 2006-07-31
Praise the Intel Gods, I'm wireless and I am connected and it just works.
I stopped trying to "help" Ubuntu. I have the signal graph, and everything
It was a dedicated short-circuit between the user abd the keyboard
Again, I am MOST grateful to you for all of your patient help

---

