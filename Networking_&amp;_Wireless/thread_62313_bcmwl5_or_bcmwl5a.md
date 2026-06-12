---
title: "bcmwl5 or bcmwl5a"
date: 2005-09-04
forum: Networking &amp; Wireless
---

### Post by KurtB on 2005-09-04
Hi,

I've tried about everything to get my wireless up and running without any luck :(
* howto's
* ndiswtrapper, linuxant, gtkwifi...

I just need to know some things to figure out where it's going wrong:

- I've a Belkin54G PCMCIA Wireless NIC, on the CD that came with it there are 2 files:
* bcmwl5 (large file)
* bcmwl5a (about 40kbytes)

-> on the NIC: model F5D7011 VER1000df

->  which one must I use??? with ndiswrapper -following the howto- and bcmwl5 I get "invalid driver" when I "sudo ndiswrapper -l", with bcmwl5a I get "hardware present, driver installed"

-> power led is ON after reboot, wlan0 is active in:
 system -> admin -> network (and closes quite fast, so I assume it doesn't hang)

using the howto, this parts partially fails (access denied)
```
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
``` 

-> "sudo iwlist wlan0 scan"  doesn't show my wireless anymore

So my questions:
* must I use bcmwl5 even though I get "invalid driver" warning?
* how must I enter my 64bit wep? I tried s:xxxxxxxxxx, xxxxxxxxxx & xxxx-xxxx-xx
* My router is set as AP & the SSID i hidden -> is this supported by ndiswrapper?

-> I'm using ubuntu hoary

any help please...because my ubuntu is quite useless without my wireless   :???:

---

### Post by transactionlogfiller on 2005-09-04
I was using the belkin F5d7000uk card and the drivers that were on the CD only seemed to support speeds up to 11mbps. Then I found the 5a driver on the web and was able to crank it up to 54mbps, but it was a bit lossy - so in the end I went back to wired networking (I found the signal to be crap even under Windows with that card)

I also hid my SSID no problem.

I find the easiest place to set your WEP key is in /etc/networking/interfaces - cos there you can see what you are typing.

---

### Post by KurtB on 2005-09-04
Ok,

but I'd like to give it a try using wireless with my WIFINIC...

F5D7011 ver1000df
broadcom chipset 94306

which is the correct inf driver?
(I've used the one on the CD, and through another link I got to download "R81433.exe". How do I get the inf out of that *.exe under ubuntu?)

then there's the radiostate issue
when installing the driver it says forcing radiostate|0 to |1 -> but I've seen it's better to set it to '0' using :

```
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
``` 

but this fails, also using gedit: nok, can't change radiostate. And when I use a rootterminal, I mess up the entire *.conf file...

---

### Post by mlomker on 2005-09-04
*How do I get the inf out of that *.exe under ubuntu?*

You can't, unless you count installing VMware on Ubuntu.   :-P 

*when installing the driver it says forcing radiostate|0 to |1 -> but I've seen it's better to set it to '0' using *

That's only necessary with on-board nics, not PCMCIA cards...isn't yours a card?

I'd recommend that you disable wep and everything else until you are sure your card is working and then add complexity as you go.  I'd recommend buying a card that has linux drivers.  Even after you get ndiswrapper to work it'll still be slow.  There are some dirt-cheap cards with native drivers.

---

### Post by KurtB on 2005-09-04
thx for the reply :)

yes, it's a pc card,...and I only manage to get both lights on (that is POWER ON and Network blinking)

the gtkwifi applet then sees the SSID, but when trying to connect DHCP always fails

I've sort of stopped trying now :(

wired everything works fine, but I can't stay hooked on my short UTP forever.

Following several howto's, tutorials, installing and uninstalling drivers, setting radiostates on and off, performing dark voodoo rituals and sacrificing chickens didn't help...

Too bad because I kind of like this distribution, but without a decent wifi support it's like having a Porsche without fuel.

ubuntu might be linux for the people, sadly windows still brings wifi to the people.
:(:(:(

nevertheless I'll be lookin' forward to new tools/drivers/releases that support wifi in a better way (especially when you see that this bcmwl5/a i quite common). But now I've tried enough to see wifi doesn't work with my card & ubuntu

---

