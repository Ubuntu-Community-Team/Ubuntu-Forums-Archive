---
title: "noob needs help with WPA, confusion???"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by kill4killin on 2007-01-06
Ok, well I just got a Dell Inspiron laptop and after doing a lot of research I went with the Intel Proset wireless 3945 chipset for it. To my suprise when I started up 6.10 for the first time, it did exactly the oposite of what I was used to when I try to configure wireless...it WORKED with no configuration. Thats doing your homework I guess lol...

Anyway, now I am back on my college campus and I would like to be able to take advantage of the wireless network available however I need to setup the security for their network. This requres me to use WPA/TKIP settings.

Now, I read the article above on WPA, but now I'm very confused what to do? I already have wpasupplicant but how to do I set up the wireless card for WPA?

Thank you

---

### Post by bernied on 2007-01-06
Try networkmanager - it should be in the repositories (or may even be installed). Let us know if you have joy with that, because it is easier than wpa_supplicant.

---

### Post by kill4killin on 2007-01-06
Ok, well I got network manager gnome and network manager from synaptic but I can't seem to figure out how to use it now...I don't even know where it installed it to...I tried doing a locate networkmanager and a locate network-manager ect, ect but still nothing...suggestions?

---

### Post by bernied on 2007-01-07
I think you just type
```
networkmanager &
```in a terminal (the '&' is so that it runs in the background - you can also do it without).

I am sketchy about this because I use kde, and it is knetworkmanager there.

You should be able to get a list of installed files from synaptic.

---

### Post by kill4killin on 2007-01-07
Ok, well I have Kwlan running right now but, after I am able to configure all of the settings I need including:

SSID: xxxxx
Authentication: wpa-eap
Encryption: TKIP
username: xxxxxx
password: xxxxxxx

then I click Add and it gives me this error.

```
Failed to save the wpa_supplicant configuration.
Is update_config=1 defined in wpa_supplicant.conf?
```

I went and did a locate for wpa_supplicant and came up with the exampel file for wpa_supplicant.conf and took away the # from update_config=1 and moved the conf file to /etc/wpa_supplicant.conf but it still gives me that error...what am I doing wrong?

---

### Post by bernied on 2007-01-07
You have an example file, but not a .conf file. Copy the example file to wpa_supplicant.conf, like this:
```
sudo cp /etc/wpa_supplicant.example /etc/wpa_supplicant.conf
```
EDIT: My apologies, didn't read your post properly, wait a sec...

---

### Post by bernied on 2007-01-07
Again I apologise, I feel now that I should have just helped you with your original request, because doing it the old-fashioned way is what I'm going to suggest now. You can edit your wpa_supplicant.conf file directly. Something like:
```
sudo nano /etc/wpa_supplicant.conf
```
Open another terminal window and type
```
man wpa_supplicant.conf
```
for some example configurations.

I have to go eat - back later...

---

### Post by kill4killin on 2007-01-07
Ok, well it is good to know that I have it in the right place at least. I will play with this a little bit later and see what I can do with it. With any luck I hope I can have this going by tomorrow at the earliest.

Well, here is the problem with editing it manually. The certificate that they use at my college is obtained usually automatically when you log into the network from your computer. However, I do not have this certificate nor the location at which to obtain it from in order to save it to my computer manually and point wpa-supplicant to it. Will the wifi manager automatically do this as it does in windows? ](*,)

---

### Post by bernied on 2007-01-07
I don't know about this EAP stuff (if that's what you're talking about). I only do wireless at home with WPA-PSK (pre-shared key) and TKIP (don't know what that is).

The problem that you're having with the 'failed to save wpa_supplicant configuration' might be just to do with permissions.  There's an option for 'ctrl_interface_group=' in the example wpa_supplicant config file, that you might need to look at. You could simply change the group to your user name, since you are sure to be a member of that group, or maybe choose admin.

To find out what groups you belong to, try:
```
groups
```

I'm going to give you the details of the rest of my setup on my Kubuntu laptop, in case it's useful. The hard part is done (making the thing work) - it worked out of the box for you (mine too - ipw2200).

So my way is totally manual, no fancy graphical stuff. The best things about this are that the network comes up at boot, before the desktop, so all the desktop stuff that needs the network (like music players with libraries on network drives) doesn't panic when it isn't immediately there, you don't have to type in any passwords, and I feel like I know what's going on. The worst bit is that it only works on one network (but I think you can have multiple SSIDs in the  wpa_supplicant.conf file so that it selects the first one on the list that is available).

So the only other file involved is:
/etc/network/interfaces:
```
# I've left out sections on lo (loopback) and eth0 (wired interface) devices
auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Dwext -ieth1 -c /etc/wpa_supplicant.conf -B
pre-up sleep 2  # this line is to make sure that the interface is associated before it sends out the dhcp request
```
but replace 'eth1' with whatever your wireless interface is called. To find out, try ```
iwconfig
```

Then there is wpa_supplicant.conf, mine looks like this:
```
#ctrl_interface=/var/run/wpa_supplicant
#ctrl_interface_group=wheel

network={
        ssid="MySSID"
        scan_ssid=1
        key_mgmt=WPA-PSK
        psk="This is not my key"
}
```
I disabled the ctrl_interface bits because they didn't seem to work for me - I don't know what was missing, but I'm happy to do without. So this is the bit that you're going to have to figure out for your EAP stuff.

Maybe, if you are not provided with a certificate, you could see if you can find the one that your windows install is holding for you. But I don't know how to do that.

---

### Post by bernied on 2007-01-07
One more thing, read the man (manual) pages, like that 'man wpa_supplicant.conf' that I said a couple of posts ago. You can do this with all commands, like:
```
man nano
```will tell you how to use nano, or ```
man interfaces
```will tell you all about the /etc/interfaces file.

I hope this helps.

---

### Post by kill4killin on 2007-01-07
Great post, that was pretty much exactly what I was looking for! I will try to configure it how you say when I get back on campus tonight and I will see if I can get a hold of a friends laptop or talk to to the network guys and see if I can't steal the cert for the network. As for the TKIP, that isn't anything important, its just the method of encryption they use over the network, nothing more, its just a setting I know I need to use.

I will try this later and let you know how it goes, again thank you very much for you help!

---

### Post by wieman01 on 2007-01-08
I don't want to hijack this thread, but a comment: WPA-EAP uses a authentication server which you don't since this is not meant for home but enterprise use. WPA-PSK would be the correct choice as highlighted Bernied. 

Another thing: If everything else fails, please try the HOWTO in my signature. It has worked for a number of people and should get you up and running in no time. If you want to use WPA/TKIP, please take a look at the sample configurations given in the HOWTO. 

If you need a graphical tool, either choose "gnome-network-manager" or "wifi-radar".

---

### Post by kill4killin on 2007-01-08
You are not highjacking by anymeans. However, please note that I have no say in what security measures are used in this situation.

I am trying to set this up to run off my colleges wireless network and the security setting that they have in place is WPA-EAS not PSK. I sort of have to just get what they have in place to work, if I had a choice I would have picked PSK however, for the purpose it is serving it is highly insecure compared to how they have it setup with the certificate as you can only obtain the certificate by registering your laptop and proving that you are a student or faculty member of the school.

That post was the first thing I read before posting this question up and though it was a good article, it just wasn't quite what I needed to answer my question.

and bernied: yes, you are correct, you can setup multiple SSID's in wpa_supplicant.conf and have it pick the first one in the list that is available. I found that while scanning the net and man pages for info. I will need to do this as I connect to multiple different networks depending where I am, home, school, cafe, ect.

---

### Post by wieman01 on 2007-01-08
WPA-EAP will be different story then. I suggest that you gain as much information as possible from you network administrator. The thing is that there are so many WPA-EAP protocols out there (e.g. LEAP, PEAP, to name a few) that you need to find out about the particulars of your wireless network.

Can you get more information? Perhaps we can come up with the right scripts afterwards. Would like to give it a try.

---

### Post by kill4killin on 2007-01-08
Here is what I have about the network:

WPA-EAS
TKIP
Username:xxxx
password:xxxx
client_cert:
ca_cert:

So I have set my wpa_supplicant.conf to look like so:
```

network={
ssid="myssid"
scan_ssid=1
key_mgmt= WPA-EAP
group= TKIP
eap=TTLS
identity= myusername
password=mypassword
ca_cert="/etc/cert/ca_cert.cer"
client_cert="etc/cert/client_cert.cer"
}

```

I managed to get the installation CD for the SecureW2 client that we install on the Windows machines and in the installation folder were the two .cer files that I needed, the only thing is that I do not know which one is the ca_cert and which is the client_cert so I guessed and if I was wrong I figured I just flip flop them. If that doesn't work the technician who knows a good bit about linux and setting it up on the network will be in tomorrow and could probably tell me which is which, or if there is something else that I do not have.

::EDIT::
just called the network admin and she said that we use the following settings on the network, one of which I had forgotten about

WPA-EAS
TKIP
PAP
TTLS

how would I put them into my wpa_supplicant.conf file, I think I have it setup right when I have it in like this:
```

network={
ssid="ssid"
scan_ssid=1
key_mgmt=WPA-EAS
pairwise=TKIP
group=TKIP
eap=TTLS
identiy=myident
password=mypass
ca_cert=ca_cert
client_cert=client_cert

```

I get this error if I type in sudo ifup eth1

```

Line 5: unknown EAP method 'TKIP'
You may need to add support for this EAP method during wpa_supplicant
build time configuration.
See README for more information.
Line 5: failed to parse eap 'TKIP'.
Line 10: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to bring up eth1.

```

So obviously having TKIP in the EAP area is not correct...is this where the PAP should go?

---

### Post by kill4killin on 2007-01-08
Ok, I got rid of the errors by removing an old config that was invalid and setting the rest up like this:

```
network={
	ssid="ssid"
	scan_ssid=1
	key_mgmt=WPA-EAP
	pairwise=TKIP
	group=TKIP
	eap=TTLS
	identity="identity"
	password="password"
	ca_cert="/etc/cert/ca_cert.cer"
	client_cert="/etc/cert/client_cert.cer"
}
```

Now I just need to go to a building that has wifi access and test my settings I will come back here if it works.

::EDIT::

I just tested that and it did not work, I tried flip flopping the certs but that still didnt work.

when I do a sudo ifup eth1 I get the following message:

```

Listening on LPF/eth1/00:18:de:9c:2c:05
Sending on   LPF/eth1/00:18:de:9c:2c:05
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by wieman01 on 2007-01-09
TTLS is the right authentication protocol and TKIP the correct encryption method?

---

### Post by kill4killin on 2007-01-09
Ok, well where did my eth1 connection go? I can't seem to get it to connect to even unsecured networks now...what happened???? eth1 isn't in the gnome connection properties anymore just eth0 and lo....

---

### Post by wieman01 on 2007-01-09
Post the contents of this file and we'll see:
> sudo gedit /etc/network/interfaces

---

### Post by springnuts on 2007-11-16
Re 'failed to save wpa_supplicant configuration' ... the command to open gedit has to be run with the prefix sudo, or you will not have the permission.  At least that was why I could not save it.

---

