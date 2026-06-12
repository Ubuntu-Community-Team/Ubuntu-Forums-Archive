---
title: "3Com 3CRSHPW-196"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by Johan76 on 2007-07-28
Hi,

I've recently installed Ubuntu 7.04 (Feisty Fawn) on my ACER laptop and everything seems to function, except my wirless network.
I've surfed the net and found several posts on 3Com wireless problems (although most about usb-dongles and/or previous versions of Ubuntu), but still haven't managed to get it working.
I hope someone on this forum might get me on my way ...

As mentioned earlier, my laptop is an ACER (PIV 2,4GHz - 512 MB RAM), without a swith to (de)activate wireless radio. WIFI wasn't built in at the time, so I'm using a 3Com PCMCIA-card (3CRSHPW-196) to connect to a 3Com AP.
As far as I can see, this card should work 'out of the box' when using Feisty Fawn, but in my case, it doesn't. 

I'm not able to connect, neither via Network Manager, nor via Networking. I enter my ESSID, a hexadecimal WEP-key (26 chars - 128 bit encryption) and opt for DHCP.
I was told to install the atmelwlandriver-source via Synaptic, but I'm not able to find it there (I do find atmelwlandriver-tools, but I think this isn't quite the same).
I've downloaded two files from the net - atmelwlandriver-source 2.1.1-3.4_all.deb and atmelwlandriver-source 2.1.1-4_all.deb. However, I don't now a)  if this would be an answer to my problem, b)which version to use and c)how to install them (not having them in Synaptic).

I don't see 'eth1' under etc/network/interfaces in this list, which is my wireless card according to the info when executing iwconfig. I'm on channel 13, but quality and signal only are reported 16/10.

Finally, ifconfig -a mentions an inet-adress 169.254.9.162. This address seems strange to me, as my AP has 192.168.1.1 as an address; I woudl presume other addresses given by the DHCP to be in the same range. Subnetmask in Windows is 255.255.255.0

When connecting via a wired connection (via the same AP), there are now problems.

Anyone know how to fix this ?

Thanks in advance!

---

### Post by GB_Joe on 2008-06-19
Hello!

I'm a total Linux newb I'm afraid, attempting to cross over from the dark side, so all my experience is Windows and DOS. Sorry...

I know this is an old post, but it's exactly the same bit of hardware that I'm struggling with and nothing else showed up on the forum for this.

I've just installed a new Xubuntu Hardy 8.04 on my old IBM T23 laptop, all working except for this 3COM 3CRSHPW-196 wireless PC card.

I read here [HTML]https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCards3com[/HTML] "Get the atmel wireless drivers from synaptic (atmelwlandriver-source) if you are having problems ... Edit: seems to work fine with Edgy, even VPN (Cisco 3000) and WPA (wpa_supplicant) seem to be no Problem"

So, firstly I'm surprised that it doesn't work "out of the box" as suggested, but then I'm afraid I just don't know how acquire and install the Atmel driver. It doesn't show up in Synaptic and I can't find it anywhere to download. I basically don't know what I'm doing, folks, so any help would be greatly appreciated. Please remember that I'm used to Googling for drivers, and just running the saved file - I've got a lot of learning to do!

Cheers,
Joe

---

