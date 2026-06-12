---
title: "How can i get wpa_supplicant settings in gui to connect to network"
date: 2007-01-02
forum: Networking &amp; Wireless
---

### Post by KenSentMe on 2007-01-02
I have a laptop with an internal (Intel) wireless device and i use it to connect to different wireless networks (at home and at work). Today i got my wireless networking working on Ubuntu at work. I used wpa_supplicant and wpa_supplicant.conf has these settings:

```

network={
        ssid="fontys"
        scan_ssid=1
        key_mgmt=IEEE8021X
        eap=PEAP
        phase2="auth=MSCHAPV2"
        identity="***"
        password="***"
}

```

Then i run sudo wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant/wpa_supplicant.conf and sudo dhclient eth1 to connect to the wireless network.

Because i also use my laptop at home i want to use a gui to be able to connect to both wireless networks. What is the best way to do that in Gnome?

I tried wpa_gui, but it always gives me 'Could not get status of wpa_supplicant' and i haven't figured out how i can get network-manager-gnome to use the wpa_supplicant settings.

Is there anyone who can help me on this?

---

### Post by SugarDaddy on 2007-01-02
I recently figured out how to configure wpa_supplicant.conf to accept multiple APs and put together a little HowTo in the post below. Rather than describe the steps all over again, just click the link below:

[http://ubuntuforums.org/showthread.php?t=326590](http://ubuntuforums.org/showthread.php?t=326590)


Bottomline, it's just a matter of copying your network block and changing the settings for your home router's security settings. Also, you need to make sure that the /etc/network/interfaces eth1 is set for dhcp versus a static IP and that you have the pre-up and post-down commands for wpasupplicant included as well.

Hope this helps! :)

---

### Post by KenSentMe on 2007-01-03
I've already got my configuration from your thread, thanks for that. But i want to bring it to a gui so i can connect to some new networks without having to go to the cli every time.

---

### Post by spd106 on 2007-01-03
I don't know if it will do multiple phase authentication, but have you tried wifi-radar?

---

### Post by SugarDaddy on 2007-01-03
That's a good question. I tried WiFi radar but it doesn't support WPA encryption standards and neither do the Gnome Networking gui or the Network Manager gui. So to my knowledge there isn't a gui that supports WPA. I could be wrong, and hopefully I am! In fact I find it hard to believe as long as WPA has been around that it hasn't been incorporated into one of the existing gui's.

 Anyone else know of one?

---

### Post by KenSentMe on 2007-01-04
Well, network-manager-gnome supports wpa, it's one of the options. I can't get it running here, but it think that's for a problem with the access point. I just wonder if i can put the above settings with network-manager-gnome (or NetworkManager as the official name).

---

### Post by spd106 on 2007-01-04
Have a look on the N-M [mailing list]("http://mail.gnome.org/archives/networkmanager-list/"). Apparently N-M doesn't support phase2 yet (gui issue), though it may if your willing to build from SVN. I haven't found a guide for this yet, but there must be one around somewhere.

---

### Post by SugarDaddy on 2007-01-04
OK, that makes sense because I use WPA2 with AES encryption. Thanks.

---

### Post by sabme on 2007-03-16
Not sure if it's too late to reply on this but I was trying to do exactly the same thing.

The only gui application that worked for me was kwlan not sure if you have to have kde installed for it to run.  Also you have to click File > Start WPA_Supplicant each time you start it.  Still much better than Network Manager or anything else and it does remember multiple access points.  You also have to scan to pick up your access point 1st time around.

---

