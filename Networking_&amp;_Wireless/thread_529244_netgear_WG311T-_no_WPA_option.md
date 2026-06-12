---
title: "netgear WG311T- no WPA option"
date: 2007-08-19
forum: Networking &amp; Wireless
---

### Post by ajmansell on 2007-08-19
I am attempting to get my WG311T up and running but it doesn't give me a WPA option for security, just a couple of WEP options.
I'm not sure if its relevant but I don't get the "wireless" bars on the top right of the screen that I have seen in my long trawl around the forums/wiki to find the answer.
I currently have 'net connection via wire but need to set up a computer for the kids that we can supervise .
I appear to be right up to date with the network manager and WPAsupplicant but maybe I'm looking in the wrong places for the wrong problem.
I will continue to trawl the web but I'm starting to be tempted to the darkside and switching  the boot disk back to the dog that is win2K.
Any help appreciated but you are dealing with a newbie so instructions/questions need to be real simple.

---

### Post by ajmansell on 2007-08-22
I have now loaded Kubuntu and have got a little further. I am getting to 28% of something when I attempt to connect to the wireless network. It comes up with "Activation stage:Configuring device." and there it stops. This is in the KNetworks Manager. All attempts to get Madwifi have met with doom. The Adept Installer doesn't seem to list it anywhere.
3 Days no replies so far.3 more days with Kubuntu and then its 6.0.6 LTS and after that I'll have to use windows 2000 to keep my kids safe on the internet. Desperation is setting in.
Does anyone have any suggestions?

---

### Post by nickmcg on 2007-08-22
Hi,

I don't know what chipset the wg311t uses, but it could be that the driver doesn't support wpasupplicant (one example of this is the legacy drivers for rt2500, rt61, rt73 which you can configure  using iwpriv or rutilt)

Short of trawling through dmesg output, I don't know of an easy way to find out which network driver you are using.

HTH

Nick

---

### Post by Roswellgrey on 2007-08-22
> **ajmansell said:**
> All attempts to get Madwifi have met with doom. The Adept Installer doesn't seem to list it anywhere....

ajmansell : If your card is Atheros based ( and hence you need the madwifi drivers), there is a fair chance you have them installed already, as they are included in the 
"linux-restricted-modules-2.6.20.16-xxxxxx" package ( assuming you are running Feisty )

Anyways, post the output of "lshw -class network" for starters.

This will ( hopefully) show the device and the driver in use.

Have to ask the obvious - have you got SSID Broadcast *enabled* on the Wireless Access Point  / Wireless Router ?
NetworkManager is not happy with no SSID being broadcast.

And have you tried to connect with all encryption on the Wireless Access Point / Wireless Router temporarily disabled  ? ( just to make sure that the association with the Access Point,  and the DHCP stuff, works in the clear...)

---

### Post by ajmansell on 2007-08-24
OK - most strange.

I checked the operation of the network with SSID broadcast on and encryption off and it picked it up OK.

I left SSID broadcast on and reset the encryption back to on and not a glimmer.

That was yesterday. I had another go (checking lshow as suggested) and then had another crack at it and low and behold it asked me for my WPA password. Once entered it asked me to set another password and magically connected to the internet.

So I can now confirm that the WG311T works (at least with Kubuntu).

Thanks for those that took the time to offer suggestions.

Unfortunately I don't know exactly what made it work but I'll live with that at the moment.

---

### Post by ajmansell on 2007-08-24
Now 20 minute later and one reboot it won't connect again.

The KNetworkManager only shows a Wired Network option.

And the Adept Manager thinks it is still installing something (result of a failed Java install I am guessing).

However I did establish that madwifi isn't installed in the Adept "safe" mode.

Can someone advise on how to close down Adept- rebooting doesn't work so is there a kill command or something.

I can then download madwifi (have established I have an Atheros chipset)

Any thoughts why working one moment and not the next?

---

### Post by Roswellgrey on 2007-08-24
You probably really won't like this suggestion at all, but in case something is a bit wobbly on the install .....

As its a new machine, it **might ** be worth doing a reinstall so that you are starting with a clean, known baseline.  

If it was me, I would install Ubuntu, and let it sort out the Restricted Driver stuff itself when you boot after the instal ... 

If you do this, when you reboot, it should  pop up and ask you if you want to use the Restricted Driver for the Network Card - say yes,  and then at least you know you have a 
solid baseline......

---

### Post by ajmansell on 2007-08-24
Do you suggest Fiesty or 6.0.6 LTS?

---

### Post by Roswellgrey on 2007-08-25
If it was me, I would give Feisty Ubuntu another shot....
Ububtu,  rather than Kubuntu, because **personally**, in the first few days of usage, 
I found Gnome easier to get around than KDE.
Your mileage may vary of course ...
Its very easy, at a later date, to add the KDE Desktop to the Ubuntu install if you wish ...

---

### Post by ajmansell on 2007-08-27
I have reinstalled Fiesty and it recognised the wg311T and picked up the network straight away. It then asked for the WPA password and logged me in.
I can't understand why it didn't do it first time around but will live with that.
It asked for a password for the "keyring"? which I duly invented.
On rebooting it asked for the keyring password and then for the WPA password.
Is there any way around this? The computer is for my 10 year olds for "supervised" browsing so I want it to be automatic.
Thanks for the advice so far.
Alastair

---

### Post by Roswellgrey on 2007-08-28
Firstly, glad you got it working :)

The "keyring" is a basically a password "safe" - in theory, you put in the WPA password once, assign a keyring access password, 
and then it should never ask you for the WPA password again. 
It will, however, ask for the keyring access password every time you reboot.  

There are ways around this - this thread might be worth a read

[_http://ubuntuforums.org/showthread.php?t=187874_]("http://ubuntuforums.org/showthread.php?t=187874")

FYI : There are other ways of achieving the connectivity without using NetworkManager, and as such, the keyring could be made redundant.  

One way is to manually edit a couple of configuration files , disable NetworkManager and then the network will start on boot
with no user intervention ( as per wieman01's sticky thread [_here_]("http://ubuntuforums.org/showthread.php?t=318539") )

The other is to use "wicd" - an alternative to NetworkManager, which I believe doesn't use the keyring at all. 

Food for thought, anyways ....

---

### Post by ajmansell on 2007-09-06
I was having issues with the network manager. It would find the network but couldn't log into it. It would put up the WPA passphrase "window" up every 2-3 minutes and would eventually log into the network. Once in it went fine.

Wifi Radar had a short lived success.

I then tried WICD. There was a script to install it which didn't work but the WCID forum had pretty clear instructions (for a newbie) to install it manually. it uninstalls the Network Manager (which has got rid of the keyring screen at log in).

WCID has options for the wifi driver (atheros/madwifi in my case). Without changing the driver it had difficulty getting an IP address. That may have been the issue with network manager and Wifi radar as certainly the latter reported not being able to get an IP address.

WICD appears to be the way to go for me, and from other threads solves some WPA problems and gets rid of the keyring.

Thanks to all for input and clues.

Alastair

---

