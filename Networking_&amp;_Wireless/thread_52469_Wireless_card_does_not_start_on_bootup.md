---
title: "Wireless card does not start on bootup"
date: 2005-07-27
forum: Networking &amp; Wireless
---

### Post by StinkyPinky on 2005-07-27
I installed ndiswrapper and got the rtl8180 Windows drivers working. 
The problem is when I restart my laptop. It loads the ndiswrapper and the light in the card starts flashing. It sits there for about a minute and then continues to boot up.
When I log in to Ubuntu I have no network connectivity. In Network Settings the interface wlan0 shows as active. If I click Deactivate and then Activate I mysteriously have a network connection that works perfectly. 

Please help me to get it configured so that the connection works when I start up the computer. It irks my wife enough that I have a non Windows system. I really don't want to tell her that she has to click a few extra buttons before she can spend money on eBay.

My interfaces file looks like this (of course, I substituted asterisks for the sensitive information):

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface wlan0 inet dhcp
wireless-essid ************
wireless-key ************

auto wlan0

---

### Post by Imgonna on 2005-07-28
I agree re the wife -- the only function that mine made sure was working before we ditched windoze was the networking and auto initalisation.

I have a laptop running a belkin pcmcia card that uses the Realtek chips - same as you.

My interfaces file is similar except I dont have:

mapping hotplug
script grep
map eth0

Or any wireless-key ************ settings as they are not enabled on my home Wlan.

I assume that you made the ndiswrapper persistent with the -l (i seem to remember) switch?

I also remember reading somewhere that there are **issues** with the use of keys / ndiswrapper and this chipset (not sure where and cant find any proof)  -- suggestion -- turn of the keys on you home Wlan and see what happens.

Are you running your WLan in infrastructure with an Access Point or AD-HOC card to card?

Sorry cant help more.

Glen

---

### Post by StinkyPinky on 2005-07-28
I disabled WEP on my network. No more wireless key. It works fine now. I originally turned it on because my wireless router reported that there were more connections to it than the number of computers I have. I will have to keep a close eye on it or those pesky neighbors will start stealing my bandwidth again.

---

### Post by navilon on 2005-07-29
My card wont start after reboot unless i do....

modprobe ndiswrapper
dhcpcd wlan0

how do i get it to see the card when the machine boots?

---

### Post by strikeforce on 2005-07-29
Add the ndiswrapper into /etc/modules.

Find your wlan0 script and make sure the default is setup to dhcpd

---

### Post by navilon on 2005-07-29
[QUOTE=strikeforce]Add the ndiswrapper into /etc/modules.

Find your wlan0 script and make sure the default is setup to dhcpd[/QUOTE]

Ok i added ndiswrapper to /etc/modules and that part works. Thanks!

but where do i find the wlan0 script?

---

### Post by strikeforce on 2005-07-29
do a locate and the file name which is wlan0 or exact command is.
```

sudo updatedb
sudo locate *wlan0*

```

I'm coming from a Fedora background so I haven't found every file yet :(  I will when I get home but in the mean time you can try it that way.

---

### Post by JayCnrs on 2005-07-29
Ubuntu doesn't use dhcpcd, instead they use **dhclient** , so in order to get an IP address run **sudo dhclient wlan0**. 

After you installed the windows driver for the card and found everything was working did you issue the command:

ndiswrapper -m

After you have this done you can go into System-->Administration-->Networking and then configure your Wireless card, you will see wlan0 in the configuration file so highligh this and configure, you can then put in your wep key, essid info and once this is completed you go back to where it shows all your network interfaces, make sure wlan0 is set as the default gateway, then it will auto start when you are booting.

Good luck

---

