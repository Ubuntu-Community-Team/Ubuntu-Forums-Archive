---
title: "Netgear WG511 v2 Made in China"
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by crockettoo on 2007-01-15
For anyone struggling with this particular card, I recently went through days of grief trying to make it work on my old Dell laptop running Edgy. Eventually I gave up and sold it, thinking I would send it back to the world of Windows where it obviously belongs. It turns out that  I sold it to genius who uses SuSE linux, and he had it working using ndiswrapper in no time. Now, I don't know how this will go in Ubuntu, but could someone please give it a try, and then we'll know.

So, here is what he did and said:

```
rmmod prism54
rm /lib/modules/2.6.17.5-default/kernel/drivers/net/wireless/prism54/prism54.ko
```
> Somehow the prism54 module on my SuSE believes it is responsible for this card, so it grabs the hardware right after the card has been plugged in - and other drivers, such as ndiswrapper, won't have any chance any more from that point on.

Then I configured the card using the Win INF/drivers, and now it is blinking green searching for a network. 

You will need to check that you use the appropriate path for your kernel, and I believe that rmmod is a primitive equivalent to modprobe -r. I also guess you will need to sudo both these commands.

If this works for you, **or not**, please reply to this thread.... cheers

---

### Post by AAM on 2007-01-15
crocketto,

absolutely correct about SuSE and that card. Had lots of problems, there were fixes posted elsewhere on the 'Net.

But it should have worked on Ubuntu with ndiswrapper for you. There are other posts but in the preparation for the Ubuntu install you need to edit some file:

```
sudo gedit /etc/modules (add '*ndiswrapper*')
sudo gedit /etc/iftab (add '*wlan0 mac MA:C_:NU:MB:ER*')
sudo gedit /etc/modprobe.d/blacklist (add '*blacklist islsm, blacklist islsm_usb, blacklist islsm_pci, blacklist prism2usb*')
```

then install & configure ndiswrapper (cd into the directory with the windows drivers (?ndis5 directory)
```
sudo ndiswrapper -i netwg5111.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

```
then plug the device in, go to networking and add the ESSID/WEP parameters and off you go!


So, did it work?

---

