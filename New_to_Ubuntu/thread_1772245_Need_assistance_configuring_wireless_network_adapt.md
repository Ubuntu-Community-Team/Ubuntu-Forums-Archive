---
title: "Need assistance configuring wireless network adapter - server 11.04"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by derekmas10 on 2011-05-31
I just installed server 11.04 on a computer at my home - but here's the issue. I live in a remote location and don't have internet other than wireless via tethering my Droid.

How do you go about configuring a wireless NIC so that i can use my phone's data connection to sudo apt-get update?

---

### Post by mishathegoat on 2011-05-31
Just curious why you're using Ubuntu Server?

I'm no professional.. and I usually don't help people on the Ubuntu forums but I'll give it a shot heh heh.

**First:**
Okay. I would first type in:

```
sudo iwconfig
```

to list see if Ubuntu recognizes any of your wireless interfaces. Such as:

```
wlan0
ath0
etc
```

[B]Second:
[/B]

If you see your wireless device, lets say wlan0, then use:

```
sudo ifconfig wlan0 up
```

to initialize the device.
[B]
Third:[/B]

Then use:

```
sudo iwlist wlan0 scan
```

to list the wireless networks around you.

**Fourth:**

To connect to your wireless network:

No encryption:
```
sudo iwconfig wlan0 essid "wireless_name_here"
```
(Yes, include the quotations)

WEP:
```
sudo iwconfig wlan0 essid "wireless_name_here" key hexkeyhere
```

example:

```
sudo iwconfig wlan0 essid "bulldogs" key 0011223344
```

**Finally:**

```
sudo dhcpcd wlan0
```

this will get an IP assigned to you and you'll be ready to go!


~~~~~~~~~


If you didn't see your wireless device before, then make sure your wireless device is supported.

Use

```
sudo lspci
```

or

```
sudo lsusb
```

to find the name and model of your card.

Then check here:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

to see if it's listed and for more instructions.

---

### Post by derekmas10 on 2011-05-31
First off, thanks for the quick reply - I'm using server 'cause I'm a Windows Network guy and want to learn ubuntu. 'Cause I can type of thing.

I will definitely try this when I get home - I know the system recognizes my wireless card 'cause it asked me about it during setup.

---

### Post by derekmas10 on 2011-06-02
So here's the issue - i am using a wireless card from an old laptop attached to a pci adapter. It worked fine in windoze, and the ubuntu system sees it and is using the correct driver, but since it "thinks" it's a pci nic, it's showing as eth1 versus wlanX.

Is there a way to change this? I'll look further in the forums but since this thread's seen 54 views, perhaps someone out there can show me a way.

---

### Post by mishathegoat on 2011-06-07
Regardless of the interface name, it should still work. Are you saying that it's still not working? Or that you'd just like to change [FONT="Courier New"]eth[/FONT] to [FONT="Courier New"]wlan[/FONT]?

---

