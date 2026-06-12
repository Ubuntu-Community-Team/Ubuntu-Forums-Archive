---
title: "how do i get rid of old SSID?"
date: 2005-10-07
forum: Networking &amp; Wireless
---

### Post by mit on 2005-10-07
Hi,

Changed the name of the SSID on my router. The problem is when i boot it keeps saying the name of the old one in the GUI. I can change and it finds the new one straight away.
Just annoying!

---

### Post by Zelut on 2005-10-07
take a look at your /etc/network/interfaces file.  That generally will show your network interfaces and any default SSIDs.  You should be able to change it there.

---

### Post by mlomker on 2005-10-07
Have you looked in the /etc/network/interfaces file?

```

gksudo gedit /etc/network/interfaces

```

---

### Post by mit on 2005-10-08
Hi,

I can open the file which as you say has my old ssid. The problem is that it is read only. I am right in saying that if i can change and save this file my problem is solved?

Thanks
"Edit"

I can open and change the file when using the root terminal. Now all i need to do is get the WEP key to work.

---

### Post by Zelut on 2005-10-08
Yeah, it would be read-only.  You'll need to open it with sudo priveledges (ie; sudo gedit /etc/network/interfaces from the terminal).  If you change the SSID in that file you should auto-connect to your new SSID, yes.

---

### Post by mlomker on 2005-10-08
> I can open and change the file when using the root terminal. Now all i need to do is get the WEP key to work.

That goes on the [wireless-key]("http://www.ubuntuforums.org/showthread.php?p=374072#post374072") line in the same file.

---

### Post by mit on 2005-10-08
Thanks for all your help, guys.
There seems to be a two sided problem. Yes, when i changed the /etc/network/interfaces file to my new ssid it worked :) 

The problem seems to be with getting the Network settings to 1) keep etho as the default- it disappers after the initial time of putting it in! 2) although it configures the WEP key, it shows the 3 arrows for signal, signal strength 100%, it can't ping the router and oviously get out to the net. :(

---

### Post by mlomker on 2005-10-08
> The problem seems to be with getting the Network settings to 1) keep etho as the default- it disappers after the initial time of putting it in! 2) although it configures the WEP key, it shows the 3 arrows for signal, signal strength 100%, it can't ping the router and oviously get out to the net. :(

I'm not following you, partly because I don't use gnome and partly because I do everything at the command-line.

What do you mean by keeping eth0 as the default?  I thought you were using wireless.

Perhaps you should post the contents of that /etc/network/interfaces file.

---

### Post by mit on 2005-10-08
[QUOTE=mlomker]
What do you mean by keeping eth0 as the default?  I thought you were using wireless.

[COLOR="Red"]Yes, i am. Under Network settings there is a drop down field to choose your default ethernet adapter. It appears that when you try and use WEP it doesn't stay on eth0?[/COLOR]

Perhaps you should post the contents of that /etc/network/interfaces file.

[COLOR="Red"]Here goes[/COLOR]

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid mitsnetwork


[/QUOTE]

Please show me where to add the WEP key. God, is this WEP really worth it? :???:

---

### Post by Zelut on 2005-10-08
I don't use WEP myself but I also don't broadcast my SSID and use MAC filtering.  That does a pretty good job of keeping my network private.  I'm sure someone could probably intercept packets but I don't do anything THAT private anyway.. probably just up to you

---

### Post by mit on 2005-10-08
[QUOTE=kuyaedz]I don't use WEP myself but I also don't broadcast my SSID and use MAC filtering.[/QUOTE]

[COLOR="Red"]Interesting. I use MAC filtering and I could disable SSID broadcast. With these 2 settings it would make it pretty hard for someone to connect to my gateway wouldn't it?

The only thing i don't understand about Disabling SSID is if your laptop can see it why can't anyone elses? How do i go about it? I mean, do i have the laptop all set up and then just turn the SSID broadcast off? Then when i re-boot the laptop it will still find the gateway? [/COLOR]

---

### Post by mlomker on 2005-10-08
> Please show me where to add the WEP key. God, is this WEP really worth it? :???:

Something is wrong here.  Your wired ethernet is eth0, I assume.  Is your wireless eth1, wlan0, or ath0?

```

auto lo
iface lo inet loopback

mapping hotplug
  script grep
  map eth0

iface eth0 inet dhcp

iface wlan0 inet dhcp
  wireless-mode managed
  wireless-essid mitsnetwork
  **wireless-key XXXXXXX**

```

I actually use MAC filtering like kuyaedz does, but I broadcast the essid because it makes life easier when I have people over.

---

### Post by Zelut on 2005-10-08
disabling the SSID just makes it so the router doesn't broadcast that its there.  If you name your SSID, for example, purple-dinosaur then you would have to know the name of that SSID to be able to connect.  As long as you type in the name of your SSID your computer will know to connect, same with anyone who comes over--or people you invite to use your wireless.

---

### Post by mlomker on 2005-10-08
> SSID your computer will know to connect, same with anyone who comes over--or people you invite to use your wireless.

That hasn't been my experience.  A variety of cards/operating systems/handheld devices are unable to connect to a hidden essid.

Then again, I'm a network admin so I probably see a wider variety of gear than most.

---

### Post by mit on 2005-10-08
Hi,

No, wireless is etho. I assume it is because i used wireless when i first installed Ubuntu, instead of a wired connection?

Right, it works perfectly with MAC filtering and SSID broadcast disabled. :) 
Should i try and add the lines to the /etc/network/interfaces file to see if i can get wep to work?

---

### Post by mlomker on 2005-10-08
> Should i try and add the lines to the /etc/network/interfaces file to see if i can get wep to work?

If you want WEP, adding that line should work.

```

iface eth0 inet dhcp
 wireless-mode managed
 wireless-essid mitsnetwork
 **wireless-key XXXXXXX**

```

---

### Post by mit on 2005-10-08
Ok, I entered the key as described and re-started for good measure. 
During the text based start up it didn't sync with the clock but when in the GUI it is showing the three arrows to say i have 100% connectivity to my gateway.
It also shows the right SSID in network settings and the WEP key is hashed out.
The problem is i can't connect to it! :o

---

### Post by mlomker on 2005-10-08
> It also shows the right SSID in network settings and the WEP key is hashed out.
The problem is i can't connect to it! :o

Then don't fat-finger the key!  ;)

Seriously, those are the right settings so you'll have to double check your key and maybe try a different one.

---

### Post by mit on 2005-10-08
HI,

LOL :)  the key was definately entered correctly. It just doesn't want to play ball. I also got an error saying to contact the network admin as the device doesn't exist after a red warning sign came over the ethernet sign! 

I would like to thank you and kuyaedz for all your help, but i think i will stick with MAC filtering and SSID disabled- it works every time hassle free. Thanks again!

---

### Post by mlomker on 2005-10-08
Does your router give you the key in hex or ASCII format?  If it's something like this: 0x555555 then try entering it on the key line like: s:555555

I've heard of people having trouble getting hex keys to take.

---

### Post by mit on 2005-10-08
hex :) 

Thanks for all your help

---

