---
title: "Setting up a DWL-520+ card"
date: 2005-10-19
forum: Networking &amp; Wireless
---

### Post by daller on 2005-10-19
Hi There,

Will I have any problems installing this card???:

D-link DWL-520+

The reason why I'm asking, is that I never installed networking hardware in a computer that was already set up!

It is a wireless LAN card! (PCI)

I just ordered it, and I will have no time to test it on my own machine! (And it would be quite embarracing to show up with a solution that doesn't work!)

ANY help is greatly appreciated!!!

---

### Post by f-bomb on 2005-10-19
I've got the same card and set it up successfully under 5.04 hoary.  I outlined what I did to make it work in this thread --> [http://ubuntuforums.org/showthread.php?t=78418](http://ubuntuforums.org/showthread.php?t=78418)

my upgrade to breezy (5.10) caused my card not to work but I found a workaround for it, although it may not worl for you if you did a fresh install of breezy.  YMMV

good luck!

---

### Post by daller on 2005-10-19
The machine that I install it in has Hoary installed!

This is what I have to do:

sudo ln -s /lib/hotplug/firmware/RADIO11.BIN-2.6.10-5-386 /lib/hotplug/firmware/RADIO11.BIN

sudo ln -s /lib/hotplug/firmware/WLANGEN.BIN-2.6.10-5-386 /lib/hotplug/firmware/WLANGEN.BIN

???

Will the system detect the card automatically when I plug it in? (No configuration needed, right?)

The thing that it works in hoary, but not breezy must be a bug! - Have you reported it?

---

### Post by f-bomb on 2005-10-19
IIRC, that's all I had to do....the hardware detection at boot works well enough that I didn't have to do anything other than create those symlinks to the modules pick up the firmware.  Make sure you check out the output from dmesg after you install the card.  ONce you're logged in, use the networking config tool to setup the card.  check the output of iwconfig to make sure your card is getting a signal, etc.

---

### Post by daller on 2005-10-19
[QUOTE=f-bomb]IIRC, that's all I had to do....the hardware detection at boot works well enough that I didn't have to do anything other than create those symlinks to the modules pick up the firmware.  Make sure you check out the output from dmesg after you install the card.  ONce you're logged in, use the networking config tool to setup the card.  check the output of iwconfig to make sure your card is getting a signal, etc.[/QUOTE]

What networking config tool?

I use /etc/network/interfaces - Is that what you mean by a config tool?

---

### Post by william_nbg on 2005-10-19
I have the same card, 'g520+' with the acx111 chip. It worked fine under hoary without out any changes, although, no wep. In breezy It wasn't recognized in the install, but I simply copied by '/etc/network/interfaces' file over from Hoary and it works fine in Breezy. But sometimes when I boot-up it doesn't come on so I run a small script I made and it always comes on.

Script:

sudo /etc/init.d/networking stop
sudo modprobe -r acx_pci
sudo modprobe acx_pci
sudo /etc/init.d/networking start

paste the script in a text file and name it 'net_start.sh'
and then run 'sudo sh net_start.sh' in comand line.

Hope they work out this bug soon, because the rest of Breezy is running just fantistic on my box.

If not, think I'll get a card with a prism chip.

---

### Post by f-bomb on 2005-10-19
[QUOTE=daller]What networking config tool?

I use /etc/network/interfaces - Is that what you mean by a config tool?[/QUOTE]

in the K menu its under System->Networking
in Gnome its under System->Administration->Networking

your card should show up as wlan0 if the driver loaded correctly.  Yo can then edit its properties to enter your ESSID, WEP key, etc

if you're a command line guy, you can use iwconfig to change the configuration

---

### Post by Antal on 2005-10-27
[QUOTE=f-bomb]in the K menu its under System->Networking
in Gnome its under System->Administration->Networking

your card should show up as wlan0 if the driver loaded correctly.  Yo can then edit its properties to enter your ESSID, WEP key, etc

if you're a command line guy, you can use iwconfig to change the configuration[/QUOTE]

Using the new Ubuntu(with GNOME) as well with a European 520 Wireless PCI card and am having issues getting it to work as well.

Card is recognised as wlan0 and when I use the System->Administration-> Networking it still wont work.

I can change settings etc to DHCP, static IP, whatever I want but when I then press "apply/save (whatever it was called)" it seems to crash.

I am not a command line guy (only started playing with linux last week) but if you guys got a little script, do let me know!!

Appreciated!!!

Antal

---

### Post by daller on 2005-10-27
Antal>

Do this:

open a console...

type:

sudo vi /etc/network/interfaces, and press enter

Type in your pass, and press enter

Go to the last line of the file, press "i" (--INSERT--), "end", make som newlines (enter, enter :)) and type in:

iface wlan0 inet dhcp 
wireless-essid NETWORKNAME
wireless-key KEY

Then press "esc", type in ":wq" and press enter... (:wq = Save and exit)

Now the card is configured...

Type in "sudo ifup wlan0", press enter, and maybe type in your password, and press enter again.

What is the output?

(And do you have inet/network-access now?)

---

### Post by janne5011 on 2005-10-27
I have the same card (acx_pci) theres no need make any changes to 5.10.
here is  my "interfacesfile"

# The loopback network interface
auto lo
iface lo inet loopback


# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0

iface wlan0 inet dhcp

wireless-essid janne
wireless-key open xxxxxxxxxx
wireless-mode managed

auto wlan0

---

### Post by Antal on 2005-10-28
Funny thing happened after I installed a new harddrive and did a clean install on it.

Recognises the card straight away now! Coming up as Texas Instruments chip.

Works a treat!

Thanks for all the input guys!

---

