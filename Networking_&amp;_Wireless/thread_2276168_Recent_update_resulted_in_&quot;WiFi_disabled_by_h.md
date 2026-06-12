---
title: "Recent update resulted in &quot;WiFi disabled by hardware switch&quot; error on Lenovo laptop"
date: 2015-04-30
forum: Networking &amp; Wireless
---

### Post by jacky5 on 2015-04-30
Hi
I had this problem when I first bought the Lenovo-G50-70 laptop & solved it (thanx, guys!) but today's updates have done something else, I think.
```
uname -mr
``` 
returns 
3.13.0-51-lowlatency x86_64

```
lspci -nnk | grep -iA2 net
```
returns 
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
    Subsystem: Lenovo Device [17aa:380a]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

```
rfkill list all
```
returns 
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes

I think the problem is that the update has set the default to the ideapad when it should be phy0.
How do I sort this?
Have attached the wireless-info.txt file in case that helps?

Jacky

---

### Post by cavalligianluca on 2015-04-30
I have a G50-30 (lenovo) and i have this issue too. Every time i do a fresh install i've got the wifi dead. I think you have to blacklist the ideapad_laptop module again. It was released a patch but it fix the problem only for the yoga series.
[http://community.linuxmint.com/hardware/view/21090](http://community.linuxmint.com/hardware/view/21090)

---

### Post by jeremy31 on 2015-04-30
You might be able to fix it without blacklisting ideapad-laptop by following these instructions [http://iseborn.eu/2014/07/21/activating-wifi-in-ubuntu-on-lenovo-yoga-2/](http://iseborn.eu/2014/07/21/activating-wifi-in-ubuntu-on-lenovo-yoga-2/)

But edit the ideapad_laptop.c file so that line 841 to identify your laptop
With the G50-30 just make the line be
```
DMI_MATCH(DMI_PRODUCT_VERSION, "Lenovo G50-30"),
```

Then follow the rest of the instructions to see if it works.  I see in the Makefile that it does create a backup of the existing ideapad_laptop module

---

### Post by cavalligianluca on 2015-05-01
> **jeremy31 said:**
> You might be able to fix it without blacklisting ideapad-laptop by following these instructions [http://iseborn.eu/2014/07/21/activating-wifi-in-ubuntu-on-lenovo-yoga-2/](http://iseborn.eu/2014/07/21/activating-wifi-in-ubuntu-on-lenovo-yoga-2/)

But edit the ideapad_laptop.c file so that line 841 to identify your laptop
With the G50-30 just make the line be
```
DMI_MATCH(DMI_PRODUCT_VERSION, "Lenovo G50-30"),
```

Then follow the rest of the instructions to see if it works.  I see in the Makefile that it does create a backup of the existing ideapad_laptop module

It works indeed :D. Thanks. I'm going to update my post on launchpad with this solution.

---

### Post by www.rzr.online.fr on 2015-05-02
Hi,

I am trying to push it for G40-30 and if it's merged I'll try for others ... keep in touch at :

[https://bugs.launchpad.net/ideapad-laptop/+bug/1450946](https://bugs.launchpad.net/ideapad-laptop/+bug/1450946)

---

### Post by jeremy31 on 2015-05-02
> **jeremy31 said:**
> You might be able to fix it without blacklisting ideapad-laptop by following these instructions [http://iseborn.eu/2014/07/21/activating-wifi-in-ubuntu-on-lenovo-yoga-2/](http://iseborn.eu/2014/07/21/activating-wifi-in-ubuntu-on-lenovo-yoga-2/)

But edit the ideapad_laptop.c file so that line 841 to identify your laptop
With the G50-30 just make the line be
```
DMI_MATCH(DMI_PRODUCT_VERSION, "Lenovo G50-30"),
```

Then follow the rest of the instructions to see if it works.  I see in the Makefile that it does create a backup of the existing ideapad_laptop module

Jackie, you should be able to do similar but make yours

```
DMI_MATCH(DMI_PRODUCT_VERSION, "Lenovo G50-70"),
```

RZR,  The strange thing is that not all laptops in the same version have the hard block issue, just seems to be the ones with Realtek wifi

---

### Post by cavalligianluca on 2015-05-03
> **cavalligianluca said:**
> It works indeed :D. Thanks. I'm going to update my post on launchpad with this solution.

Ok maybe it doesn't work so well. Sometimes the connections suddenly stops and i have to reboot the laptop. I'm back with the blacklist workaround.

---

### Post by jeremy31 on 2015-05-03
> **cavalligianluca said:**
> Ok maybe it doesn't work so well. Sometimes the connections suddenly stops and i have to reboot the laptop. I'm back with the blacklist workaround.

There are other fixes for the dropped connection

```
[COLOR=#111111]echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

[/COLOR]And if that doesn't fix it, the backports from 3.19 or lwfingers driver found [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)

---

### Post by cavalligianluca on 2015-05-04
Oh, i thought that those options weren't needed with the ideapad module on.

---

### Post by jeremy31 on 2015-05-04
The ideapad module causes the hard block unless blacklisted or modified, blacklisting the module may cause issues with FN key combos.  The rtl8723be wifi has issues in other computers

If you happen to update and get a new kernel, you will have to build and install the ideapad_laptop module for the new kernel
```
cd /workspace/ideapad
```
```
make clean
```
```
make
```
```
make install
```

---

### Post by Pilot6 on 2015-05-04
I made a ppa with G50-30 patch. Other models can be added too.

[https://launchpad.net/~hanipouspilot/+archive/ubuntu/ideapad-laptop](https://launchpad.net/~hanipouspilot/+archive/ubuntu/ideapad-laptop)

---

### Post by Pilot6 on 2015-05-04
jeremy31,

As I said before, there is no need to build and install modules for every kernel. DKMS can be used.
There is even no need to build a deb package. Just to crate a dkms.conf file. You can take mine form ppa as an example.
Then put source to /usr/src/ideapad-laptop-<version>
Then run

sudo dkms install -m ideapad-laptop -v <version>

And the module will build automatically for every new kernel.

---

### Post by jeremy31 on 2015-05-04
Pilot6, it might be easier for you to add the G50-70 and G40-30 to your existing PPA and I will send people to your PPA.

  It seems to me that the G series only has hard block issues with the rtl8723be wifi, any one else agree?

---

### Post by Pilot6 on 2015-05-05
No problem. I will add them both today. But still it is better to push it upstream.

---

### Post by Pilot6 on 2015-05-05
I added [COLOR=#000000]G50-70 and G40-30 to the ppa.[/COLOR]

---

