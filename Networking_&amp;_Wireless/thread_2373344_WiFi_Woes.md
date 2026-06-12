---
title: "WiFi Woes"
date: 2017-10-05
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2017-10-05
Folks,

I ran Ubuntu 12:04 for a few years using wifi with no problem.

Due to laptop failure I upgraded to 14:04 and subsequently to 16:04 BUT have been unable to use wifi successfully on my Toshiba Satellite.

I see there appear to be issues with many over this, have tried some of the tips but all to no avail. Fortunately Ethernet is fairly easy but I really would like to resolve this.

I have access to two different APs on my network, one normal 2.4GHz and a 5GHz - both connect then seem to drop.

```
sudo lshw -C network
[sudo] password for geoff: 

  *-network DISABLED
       description: Wireless interface
       product: RTL8821AE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 00
       serial: 80:a5:89:81:0c:3d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8821ae driverversion=4.4.0-93-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 ioport:2000(size=256) memory:f0c00000-f0c03fff


```

It appears to be using the correct driver so I have no idea where to go from here.

Any hints to resolve this would be greatly appreciated.

Geffers

---

### Post by ajgreeny on 2017-10-05
See Wireless-Info in my signature and run the script then report back here the output you get.  It may help our wifi gurus more than the info you've given so far.

---

### Post by Geoff_Lane on 2017-10-05
> **ajgreeny said:**
> See Wireless-Info in my signature and run the script then report back here the output you get.  It may help our wifi gurus more than the info you've given so far.

I think the tar.gz file is attached.

Geffers

---

### Post by QIII on 2017-10-05
Hello!

Rather than attaching an encrypted file for others to uncompress at a very real risk that a malicious payload may be included, we would prefer that you use something like paste.ubuntu.com and provide the url to the plain-text output.

Thanks!

---

### Post by Geoff_Lane on 2017-10-05
> **QIII said:**
> Hello!

Rather than attaching an encrypted file for others to uncompress at a very real risk that a malicious payload may be included, we would prefer that you use something like paste.ubuntu.com and provide the url to the plain-text output.

Thanks!

D'you know, I had never heard of paste.ubuntu.com :eek:

Here is the link;

[http://paste.ubuntu.com/25680685/](http://paste.ubuntu.com/25680685/)

Geffers

---

### Post by Geoff_Lane on 2017-10-05
> **QIII said:**
> Hello!

Rather than attaching an encrypted file for others to uncompress at a very real risk that a malicious payload may be included, we would prefer that you use something like paste.ubuntu.com and provide the url to the plain-text output.

Thanks!

Apologies re the zipped file. The script output gave a message about the text file being too big for an attachment and created the zip too.

Geffers

---

### Post by vasa1 on 2017-10-05
> **Geoff_Lane said:**
> D'you know, I had never heard of paste.ubuntu.com :eek:
...
It's mentioned in the sticky available here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108). From there:> If the issues persist, it is recommended that you install pastebinit, by running:
```
sudo apt install pastebinit
```
This will enable the wireless script to, upon your approval, upload the obtained data to pastebin, creating at the same time a link to it in your terminal, permitting you to paste it to a forum thread.

Once that's done, download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. You can run it using this command:
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz". If you prefer, you can post the file directly to [pastebin]("http://pastebin.com/") yourself. Sensitive information like MAC addresses and WPA/WEP keys are masked automatically.



---

### Post by Geoff_Lane on 2017-10-05
Thank you.

Geffers

---

### Post by QIII on 2017-10-05
> **Geoff_Lane said:**
> Apologies re the zipped file. The script output gave a message about the text file being too big for an attachment and created the zip too.

Geffers


No apologies needed.  :)

Cheers!

---

### Post by jeremy31 on 2017-10-06
The script results show wireless is soft blocked try
```
rfkill unblock wifi
```

---

### Post by Geoff_Lane on 2017-10-07
> **jeremy31 said:**
> The script results show wireless is soft blocked try
```
rfkill unblock wifi
```

Regretfully that did nothing. Occasionally I'll get a page up but incredibly slow then appears to halt.

Have to reconnect to Ethernet to get network back.

Geffers

---

### Post by Geoff_Lane on 2017-10-08
> **jeremy31 said:**
> The script results show wireless is soft blocked try
```
rfkill unblock wifi
```

Unfortunately that appeared to do nothing.

Am wondering whether to go along the ndis wrapper route - haven't tried it bur I don't want to use Windows but currently have a laptop that is not portable :(

Geffers

---

### Post by jeremy31 on 2017-10-08
I would try a different parameter
```
echo "options rtl8821ae ips=N" | sudo tee /etc/modprobe.d/rtl8821ae.conf
```
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

To even try ndiswrapper you need a Win XP driver for the wireless

---

### Post by Geoff_Lane on 2017-10-08
> **jeremy31 said:**
> I would try a different parameter
```
echo "options rtl8821ae ips=N" | sudo tee /etc/modprobe.d/rtl8821ae.conf
```
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

To even try ndiswrapper you need a Win XP driver for the wireless

Annoyingly, no change. Promising, connects but then halts almost immediately.

This is a very strange issue, if it wasn't for the fact it worked under Windows I'd be suspecting the WiFi chip.

I did try ndis but used a Win10 64 bit driver - again, thought it looked promising but then just stops :mad:

Lucky I do have access to ethernet, a homeplug gives me a wee bit of portability ;)

Geffers

---

### Post by Geoff_Lane on 2017-10-12
May have accidentally found a remedy.

I have a Raspberry-Pi on my network and I pinged it from this laptop with the dodgy wifi.

Seems whilst the ping is working my wifi works. Just downloaded a 125GB file from a relative with no problems.

Shall have to experiment to see if ping has to be initiated quickly before wifi appears to fail.

Geffers

---

### Post by jeremy31 on 2017-10-12
Can you try the Ubuntu 16.04 ISO, try without installing and see if the issue exists?
I found [https://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git/commit/drivers/net/wireless/realtek?id=b8b8b16352cd90c6083033fd4487f04fae935c18](https://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git/commit/drivers/net/wireless/realtek?id=b8b8b16352cd90c6083033fd4487f04fae935c18)
The kernel on the ISO is from before this condition unless the alignment issue was a problem that led to above commit.  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1622293/comments/18](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1622293/comments/18) seems to confirm my idea

---

### Post by Geoff_Lane on 2017-10-12
Jeremy,

Thank you for quick reply, I will try that ISO later today but just a point.

There was no wpa_supplicant.conf so set one up, that didn't work but strangely got an error of 'unsupported driver' when I issued the following;

> sudo wpa_supplicant -Drtl8821ae -iwlp2s0 -c/etc/wpa_supplicant/wpa_supplicant.conf
Successfully initialized wpa_supplicant
wlp2s0: Unsupported driver 'rtl8821ae'



That is the driver that is supposed to be used.

Geffers

---

### Post by Geoff_Lane on 2017-10-12
> **jeremy31 said:**
> Can you try the Ubuntu 16.04 ISO, try without installing and see if the issue exists?
I found [https://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git/commit/drivers/net/wireless/realtek?id=b8b8b16352cd90c6083033fd4487f04fae935c18](https://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git/commit/drivers/net/wireless/realtek?id=b8b8b16352cd90c6083033fd4487f04fae935c18)
The kernel on the ISO is from before this condition unless the alignment issue was a problem that led to above commit.  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1622293/comments/18](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1622293/comments/18) seems to confirm my idea

Am on the Live-ISO now.

Had to switch to Ethernet as wifi grinds to a halt very quickly. Tried changing WiFi access points (Got three operating in my home) and still no joy.

Seems to be an ongoing issue with Realtek devices.

Geffers

---

### Post by Geoff_Lane on 2017-12-24
Fixed the IP addess and now working fine - two days so far.

:D:D

Geffers

---

