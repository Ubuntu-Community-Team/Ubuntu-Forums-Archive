---
title: "Configuring 6.10 to do 802.1x Authentication with PEAP over wired connection."
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by dennis.groome on 2007-03-09
Here's the situation: 

I work for the University of New Orleans in a new position. It's my job to make sure that resident students in the dorms can access the 802.1x authenticated network. We use PEAP  and MSCHAPSv2 to authenticate to a RADIUS server. However, this is not wireless, it's all done through our campus-wide LAN. Windows and Mac users have an easy solution. Since I'm the only one in the (small) office that uses Linux, I've been charged with coming up with a solution so that our Linux users can authenticate to our network. If at all possible, it would be nice to have an easy solution, probably using wpa_supplicant because it's easier to configure than xsupplicant from what I've been reading.

I have a completely fresh install to test and work on, so it's pretty much 6.10 out of the box with the updates installed.

Any and all advice is greatly appreciated. If I can get this to work, I'll compile it into a HOWTO for others. I've seen a number of University students post here trying to do the same thing I'm doing.

---

### Post by dennis.groome on 2007-03-09
Here the solution I came up with. It's not the most elegant, and I'm open to suggestions on how to improve it, but it works. Most of this was taken from [http://www.stevens.edu/itwiki/cgi-bin/wiki/index.php?title=802.1x#The_quick_and_dirty](http://www.stevens.edu/itwiki/cgi-bin/wiki/index.php?title=802.1x#The_quick_and_dirty)

But they left out two important things in their HOWTO:

> 
sudo apt-get install wpagui
sudo apt-get install dhcpcd


Everything else worked as advertised.

Now, here's the catch. You'll need to run that script every time you want to authenticate. Any way to get this to run on startup?

---

### Post by dennis.groome on 2007-03-09
One more thing: without an internet connection, we can't run apt-get to install packages. What needs to be done to download and manually install packages, preferably from a CD.

---

### Post by wieman01 on 2007-03-10
Could you post the contents of these files please:
> gedit /etc/network/interfaces
> gedit /etc/wpa_supplicant.conf
Not sure about the second file as I don't use it. May have a different name or so. I'll let you know how to write a script later on.

As for your second question, you can download the Ubuntu Live CD. It has all packages that you would need to get started (including wpa-supplicant).

---

### Post by dennis.groome on 2007-03-11
> **wieman01 said:**
> 
As for your second question, you can download the Ubuntu Live CD. It has all packages that you would need to get started (including wpa-supplicant).

wpa_supplicant is installed by default in 6.10. Does it have dhcpcd? I don't think it has wpagui. Either way, they're both Networking (Universe). That included on the 6.10 cd?

I'll post the contents of my config files when I get back to the office on Monday.

---

### Post by dennis.groome on 2007-03-12
Here's /etc/network/interfaces. I didn't change anything, it's the default from the install.

> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


And here's wpa_supplicant.conf

> 
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
ap_scan=0
network={
        key_mgmt=IEEE8021X
        eap=MD5
        identity="foo"
        password="foo2u"
        eapol_flags=0
}


---

### Post by wieman01 on 2007-03-12
One more question: What is your wireless interface (e.g. ath0) and what chipset are you using (e.g. Atheros)? 

By the way, Network-Manager also supports LEAP... Just in case you prefer a GUI.

---

### Post by dennis.groome on 2007-03-12
I'm not using wireless at all for this, it's only connecting with a wired connection. I'm not sure what chipset it's using, just that it's a Toshiba R15 notebook.

---

### Post by wieman01 on 2007-03-12
Ethernet it is of course... 

Please try this and restart the network:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
wpa-driver [COLOR="Red"]wired[/COLOR]
wpa-eap [COLOR="Red"]MD5[/COLOR]
wpa-key-mgmt [COLOR="Red"]IEEE8021X[/COLOR]
wpa-identity [COLOR="Red"]foo[/COLOR]
wpa-password [COLOR="Red"]foo2u[/COLOR]

#auto wlan0
#iface wlan0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
Restart the network:
> sudo /etc/init.d/networking restart
If this works, then please restart your PC and see if you are connected after startup. If not, take a look at the second post (#2) of [this thread]("http://www.ubuntuforums.org/showthread.php?t=202834").

---

### Post by wieman01 on 2007-03-12
If this does not help, please post the command that you are using to start the authentication process.

---

### Post by dennis.groome on 2007-03-12
Why should I change my configuration? It's working. I followed exactly the instructions here [http://www.stevens.edu/itwiki/cgi-bin/wiki/index.php?title=802.1x#The_quick_and_dirty](http://www.stevens.edu/itwiki/cgi-bin/wiki/index.php?title=802.1x#The_quick_and_dirty)

---

### Post by wieman01 on 2007-03-12
> **dennis.groome said:**
> Why should I change my configuration? It's working. I followed exactly the instructions here [http://www.stevens.edu/itwiki/cgi-bin/wiki/index.php?title=802.1x#The_quick_and_dirty](http://www.stevens.edu/itwiki/cgi-bin/wiki/index.php?title=802.1x#The_quick_and_dirty)
Alright, but you were asking for automatic startup... That would do the trick. Nevertheless, if you don't want to change the configuration, just post your startup line/command and we do it that way.

---

