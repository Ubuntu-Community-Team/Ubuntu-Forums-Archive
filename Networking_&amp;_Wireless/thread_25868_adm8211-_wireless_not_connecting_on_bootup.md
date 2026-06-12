---
title: "adm8211- wireless not connecting on bootup"
date: 2005-04-11
forum: Networking &amp; Wireless
---

### Post by Johanc on 2005-04-11
Hey

I just installed Ubuntu Hoary yesterday on my laptop, and I must say I am pretty impressed. But I have a problem. My laptop is using the internet through a wireless card. This card was found and installed by Ubuntu (very impressing, because before I had to compile the driver to the kernel, thumbs up), but it won't connect on bootup. I must write these to commands before I can connect to the internet: 

iwconfig eth0 essid default
dhclient eth0

And I, as you have probably already guessed, want it to connect automatically to the internet when I boot my laptop. 

Johan Clasen

---

### Post by accuser on 2005-04-11
It sounds like you need to configure you wireless settings properly. The easiest way to do this is from the desktop (assuming you have GNOME here). Select from the menu System -> Administration -> Networking. In the network settings dialog, select your wireless connection and click Properties. You will now be able to configure your network settings.

If you want to do it by hand, you will need to add the following to /etc/network/interfaces. I am assuming that your wireless interface is wlan0, but it may be eth0 or eth1, so change it as necessary.

```

auto wlan0
iface wlan0 inet dhcp
    wireless_essid MyESSID

```

If you need a fixed IP address, use the following:

```

auto wlan0
iface wlan0 inet dhcp
    address 192.168.0.1
    netmask 255.255.255.0
    gateway 192.168.0.254
    wireless_essid MyESSID

```

Remeber to replace the address, netmask, and gateway ip addresses with the ones that you would normally use.

Enjoy!

---

### Post by lao_V on 2005-04-11
you will need to edit your /etc/network/interfaces file

---

### Post by Johanc on 2005-04-11
It still dosen't work, my /etc/network/interfaces look like this:

[I]# Used by ifup(8) and ifdown(8). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.

iface lo inet loopback

auto eth0
iface eth0 inet dhcp
        wireless_essid default
[/I]

does somebody know how I can solve this problem?

Also because I connect to more than one network...

---

### Post by lao_V on 2005-04-11
You will need to add this to your interfaces file:

auto wlan0
iface wlan0 inet dhcp
    wireless_essid MyESSID
    wireless_key X
    wireless_mode managed

I've had some problems using eth0 and wlan0 both at the same time

---

### Post by Johanc on 2005-04-11
should I just put that in the file, or should I also uncomment some of the other lines?

---

### Post by lao_V on 2005-04-11
you can put that in the file replacing the values for essid and key.

---

### Post by Johanc on 2005-04-11
I'm sorry, but I still just can't get it to work.... I'm very thankful for your help...

---

### Post by jonny on 2005-04-11
Remember to prefix your key with s:  It should look like this:

auto wlan0
iface wlan0 inet dhcp
wireless_essid MyESSID
wireless_key s:MyKey
wireless_mode managed

But why not use the System -> Administration -> Networking tool.  That sets up /etc/networking for you without going near a command line - but you have to remember the s: trick there, too.

---

### Post by lao_V on 2005-04-11
[QUOTE=jonny]Remember to prefix your key with s:  It should look like this:

auto wlan0
iface wlan0 inet dhcp
wireless_essid MyESSID
wireless_key s:MyKey
wireless_mode managed

But why not use the System -> Administration -> Networking tool. That sets up /etc/networking for you without going near a command line - but you have to remember the s: trick there, too.[/QUOTE]

"s" should only be added if your key is in string/hexadecimal format. If its numerical then you don't need s

---

### Post by Johanc on 2005-04-11
in the networking settings/interface properties, should I just write an s in the WEP key window?

---

### Post by jonny on 2005-04-11
[QUOTE=Johanc]in the networking settings/interface properties, should I just write an s in the WEP key window?[/QUOTE]If your key is a 5 or 13 character string, you need to prefix it with s:

If your key is any other length, or if you know it's in hex format, you don't need s:

For example, your WEP key is jonny.  You enter s:jonny

At least, that worked for me.  It's actually a bug that's been logged with the upstream gnome team, and it took me much head scratching and digging to find it.

---

### Post by Johanc on 2005-04-13
I reinstalled, and after a while it seems to work.. at least on my own net. Don't know why, but thank you very much for your help...

Johan Clasen

---

