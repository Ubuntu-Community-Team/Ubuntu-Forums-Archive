---
title: "Wireless network... Setup works via CLI, but is there a GUI way?"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by Daniel15 on 2008-02-26
Hi everyone,
 I'm using Ubuntu on my laptop, which I also bring to University. I've got a wireless network at home as well as at University. My home one's working fine, it uses WPA encryption, I just need to enter in the WPA key (I'm using NetworkManager in Gnome for it). My one at Uni seems more complex; it needs some sort of CA certificate as well as my username and password. I've got some config files as well as a *radius.cc.swin.edu.cer* file which I guess is the certificate. When NetworkManager tried to connect to this network. It pops up a box full of stuff that I have no clue what to choose (WPA Enterprise or WPA2 enterprise? What key type? What's "anonymous identity"?

So, I couldn't figure out how to connect to it using the GUI, but here's the commands I'm running:
```

sudo iwconfig eth1 essid eduroam
sudo wpa_supplicant -d -w -i eth1 -c swinwifi.conf -D wext
sudo dhclient eth1
```

And swinwifi.conf looks a bit like:
```

network={
        ssid="swinwifi"
        scan_ssid=1
        key_mgmt=WPA-EAP
        eap=TTLS
        ca_cert="/home/daniel/uni/radius.cc.swin.edu.cer"
        identity="[my username]"
        password="[my password]"
        phase2="auth=PAP"
        }

```

Is there an easy way that I can connect to this network using the GUI (or in a config somewhere), while at the same time having my home network still working? Entering those commands all the time is quite tedious. I tried guessing some of the settings, but it didn't work too well (it appeared to connect, but didn't actually connect)

Thanks

---

### Post by L8erG8er on 2008-02-26
Daniel, do you have the network manager applet in your toolbar (two little computer screens one in front of the other offset)?

If so, left click on it and see if you can set up a new wireless connection.

This thread also contains some info that you might find useful:  [http://ubuntuforums.org/showthread.php?t=698695&highlight=howto+setup+network]("http://ubuntuforums.org/showthread.php?t=698695&highlight=howto+setup+network")

---

### Post by Daniel15 on 2008-02-26
L8erG8er, yeah, I have that applet, it's what I used to connect to my home wireless. If I click on my university''s wireless network when I'm there, I get an overwhelming number of options come up, something like this:
[IMG]http://img442.imageshack.us/img442/2762/screenienc6.png[/IMG]

I have no clue what to choose for most of those options, like whether they're using WPA Enterprise or WPA2 enterprise, whether my certificate is a "Client certificate file" or a "CA Certificate file", or what "anonymous identity" means. I tried a few things, it looks like it's connecting, but it just pops up again a minute or so later (which I guess means that it didn't connect properly).

Is it possible to tell what the options are from that config file? I tried, but I could work much of it out (like what exactly "WPA-EAP" is)

---

### Post by Bubba64 on 2008-02-26
At the university I go to there is an office that can get you set up for computer wireless access I would be amazed if yours doesn't, go to the information people and see if they will send you to the right place. You might get the help you need here but I think the school should be able to set you up or they have a web site that does, at my school all I need is my campus email address and a access code, Good Luck the cool thing about the college I go to is that thy have Linux labs and a mirror.

---

### Post by harrydb on 2008-02-26
There is a way to connect to eduroam using the network manager. I tested this with gutsy (7.10) and hardy (alpa5) at the University of Groningen and a friend of mine did the same at the University of Enschede on Gutsy.

In the end it is simple: the default way of just clicking on the network name *never* works, you need to "Connect to Other Wireless Network" and enter the settings as in the pdf/picture.

I wrote a little document on how to configure the network manager for eduroam. It is gzipped because the pdf size limit was too small. 

I don't know if it will work for feisty/edgy/dapper, maybe someone can try?

Edit: posted new version, some minor typos fixed.
(and sorry for the spam in other threads, just wanted to solve this issue once and for all...)

---

### Post by Daniel15 on 2008-02-26
Thank you harrydb, I'll try that when I'm at Uni tomorrow :D. Every time I tried it, I had Key Type set to "Automatic", which was probably why it wasn't working.

> At the university I go to there is an office that can get you set up for computer wireless access I would be amazed if yours doesn't, go to the information people and see if they will send you to the right place.
My Uni does have some Linux support (as well as some Linux labs), but doesn't offer support for wireless on Linux, unfortunately.

---

### Post by aaron552 on 2008-03-04
I got it working with networkmanager by selecting the following options:
Wireless Security: WPA 2 Enterprise
EAP Method: TTLS
Phase 2 Type: PAP
CA Certificate: [The supplied certificate]
Username: Student ID
Password: Novell Password

That's it. It 'just works' now :D

Only one problem: It seems to drop out a lot
But that could be my stupid poorly-supported Broadcom 4311 Wireless card.

EDIT:
Actually, it seems to have become broken... It used to work, but it doesn't anymore :(

---

### Post by harrydb on 2008-03-07
Using a supplied certificated is known to cause problems (disconnection, problems reconnecting). If you do not use a certificate (as I explain in my pdf) a certificate is automatically negotiated and it works better. I really don't know why.

Btw, most people also need to set "Key Type" to "Dynamic WEP", since automatic mostly fails.

Also the b43 driver that will be in Hardy (I am using testing) is a lot more stable in my experience than bcm43xx that is used in gutsy. (I also have a Broadcom 4311)

Harry

---

### Post by aaron552 on 2008-03-10
harrydb, your method worked just as well as mine. I found that there was no difference whether I used your method or mine. It still dropped out just as much whether using the supplied certificate or not.

Also I'm using kubuntu and, as far as I'm aware, the kde network manager applet does not let you select a key type.

---

