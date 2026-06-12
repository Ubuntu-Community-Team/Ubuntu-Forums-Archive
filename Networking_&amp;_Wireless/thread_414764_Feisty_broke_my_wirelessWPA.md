---
title: "Feisty broke my wireless/WPA"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by davisond on 2007-04-20
I've been struggling with this ever since I upgraded from edgy to feisty about 5 weeks before the release date for feisty.  I've refrained from posting much about it until after the release in case something in the runup to the release fixed it.  It didn't.

My laptop roams between a lot of networks (home, 2 work locations, several client sites and a few hotels and conference centres). Home, work and some client sites use WPA most of the rest are open.

Let me start out by making a few things very clear:

[LIST=1]
[*]There is no issue with the networks or AP's I'm associating with.  Guaranteed.  They work for everyone else and...
[*]My setup on this same machine worked PERFECTLY under edgy on the same networks and AP's (I know that's not most people's experience)
[*]Any solution that requires X to be loaded (let alone gnome, or systray applets or anything else) is NO SOLUTION AT ALL.  I often need the network for mutt and slrn from the console and don't login to a gui.  Nor do I want a gui tool to select a network that then tells me to put in my password when it's already encrypted in wpa_supplicant.conf
[*]I use xubuntu, (XFCE rather than Gnome)
[/LIST]

The behaviour I see is just very erratic and the problem is actually getting connected with or without WPA to networks in general, with that being worse for DHCP enabled networks - which is almost all of the ones I use.  Once the machine is associated and gets a DHCP response, things are usually fine.  Getting there is a nightmare and can take up to 30 minutes of manual effort after every reboot or suspend/resume cycle.

In /etc/network/interfaces I have: 
```

iface lo inet loopback

iface eth0 inet dhcp

iface wlan0 inet manual
        wpa-roam /etc/wpa_supplicant.conf

iface default inet dhcp

allow-hotplug eth0 
auto lo
auto wlan0

```

my /etc/wpa_supplicant.conf file is exactly the same as the one that worked under edgy (and under gentoo before it).

Typically after a suspend/reboot, I get messages in syslog about it not being able to get a DHCP response and it falls back to the avahi configured 169.0.0.0 config.  

Any amount of /etc/init.d/networking stop|start|restart makes no difference at all.

Running sudo wpa_cli from the command line and checking status usually shows that it's not associating correctly.  Many times the messages say "associating with xx:xx:xx:xx:xx:xx" followed by "failed to associate with 00:00:00:00:00:00".  Where the first value is the actual AP MAC address and the second is the literal value of all zeros.  Huh??

Sometimes, switching off the wireless hardware on the laptop for a few seconds works, more often it doesn't.  Never had to do this under edgy.

Once associated, the wpa_cli BACKGROUND script never seems to call "wpa_action wlan0 CONNECTED" as I think it is supposed to.  Sometimes running this command manually works, more often not.

Killing all wpa_* processes and dhclient* processes and restarting networking very occasionally works, more often not.

Usually, after many many minutes of trying lots of different things, it will just suddenly work.  And then my wireless is fine until I shutdown or suspend and then I have to go through the whole circus again afterwards.  I've also tried myriad different setups in /etc/network/interfaces (too many to mention or even remember) with all sorts of pre-up and post-up commands in there to try to get more reliable operation.

So far, nothing has worked and I'm getting really frustrated with it now.  The worse thing is that there appears to be no consistent set of symptoms and no consistent set of steps to take to make it work.  I just have to keep trying all kinds of things until one thing works (usually a different thing to the one I tried the previous day).  The most frustrating thing is that almost all of the solutions and help I've seen from people on wireless issues in feisty start out by saying "just click..." which is an instant turn off for the reasons highlighted earlier.

Although I said this was no solution, I have tried tools like wifi-radar and network-admin to see if they had more success so that I could then analyse them under strace to see what they did.  That didn't work either.

If anyone has any advice at all, I'd be really grateful.  Even just advice on what I can do to analyse the underlying behaviour would help.  The interaction between wpa_supplicant, wpa_action and wpa_cli seems intractable from the man pages - I've no real idea what's meant to be doing what.

Many thanks.

---

### Post by zba78 on 2007-04-20
although I appreciate that you don't want to use any GUI tools is it possible to just try network-manager in XFCE just for the sake of 'elimination process'. If you can connect successfully with network manager each time then at least you would know that feisty's networking tools seems to be working.

I apologise in advance if this is no help to you whatsoever.

---

### Post by davisond on 2007-04-20
not at all, appreciate your response.  As mentioned in the original post, I have tried these tools (and wifi-radar) and have had no more success with them than without.

Regards

---

### Post by davisond on 2007-04-24
update: I've now re-installed feisty from scratch on this laptop and the problem remains.  I have tried using the bcm43xx driver and ndiswrapper - both exhibit the same issue (previously I only used ndiswrapper on edgy).

Seems clear to me that feisty and wpasupplicant just do not work together.  Which is a major shame because the rest of it looks great.  Anyone at all offer any insight here?

---

### Post by hiddensphinx on 2007-04-24
I can get WPA to work on the LIVE CD but not as a install :(

---

### Post by Brucevdk on 2007-04-25
The network at my college uses WPA (EAP-TTLS/PAP), I use wpa_supplicant to connect to it without any problems as far as I can tell. There's probably a better (more automated) way of doing this, but it works and I haven't yet figured out how to do it better (I notice you use wpa-roam and wpa_cli, I'll look into that). 

Perhaps this information can assist you in your problem, did you try manually authenticating using wpa_supplicant directly (see below)?

My wireless card (2200BG) is supported by the ipw2200 drivers and wext and my wireless interface is *eth1*.
```

$ lspci | grep "Network controller"
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

```

*/etc/wpa_supplicant.conf*:
```

# path to UNIX socket control interface and controlled by group users
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

# Miscellaneous settings
eapol_version=1
ap_scan=1
fast_reauth=1

### Haagse Hogeschool
network={
    ssid="HHS-802-1x"
    key_mgmt=IEEE8021X
    eap=TTLS
    identity="<username>"
    password="<password>"
    phase2="auth=PAP"
}

```

I manually authenticate with the network using (-dd = debug mode):
```
sudo wpa_supplicant -dd -D wext -i eth1 -c /etc/wpa_supplicant.conf
```

And I use dhclient to get me an IP:
```
sudo dhclient eth1
```

---

### Post by davisond on 2007-04-25
I've tried similar with varying levels of success, but what you're doing manually is much of what the scripts in feisty attempt to do anyway.  My main problem that I can see is the number of networks I switch between.  It always seems to be worse if I suspend in one location and resume in another - which I do all the time.

What's in your /etc/network/interfaces file?

I commented on an old bug too that seems to be describing similar issues for the madwifi driver: 
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/37697]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/37697")

Cheers,

---

### Post by Brucevdk on 2007-04-25
> **davisond said:**
> What's in your /etc/network/interfaces file?
Nothing much, I haven't even touched it. It lists interfaces I don't even think I have (eth2, ath0, wlan0).

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

Anyways good luck, I'll be keeping an eye out on this thread.

---

### Post by davisond on 2007-04-25
interesting.. no eth1 in your interfaces file.  That will be half the reason you have to do stuff manually I should think.  You might try the following in there if those manual commands always work for you:
```
auto eth1
iface eth1 inet dhcp
    wpa-conf /etc/wpa_supplicant.conf
```

then when you stop/start networking, hopefully your wireless should just connect.  Keep an eye on /var/log/syslog

---

### Post by davisond on 2007-04-27
as always seems to be the way with these things, something stupidly simple appears to have fixed it.  It's even something I advised Brucevdk to do in my last post.

I changed wpa-roam to wpa-conf in my interfaces file.

So far, it's working.  I suspended from work yesterday and resumed at home with no obvious issues.  Immediate connection to the right AP.

GAH!

Hope someone else may find this thread if they come up against the same issues in the future and it saves them all the frustration I've just had :)

---

### Post by bachya on 2007-05-02
Hi all,

Same song and dance on my end - was using ndiswrapper and wpa_supplicant nicely with Edgy, and the upgrade to Feisty broke it.

My /etc/network/interfaces file looks like:


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wpa-conf /etc/wpa_supplicant.conf


Like many other people, the GUI wireless interfaces that come with Feisty show my network, but I cannot connect to it.  Not a gateway problem, as every other computer can connect to it.

Any advice would be greatly appreciated.

---

