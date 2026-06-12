---
title: "Intel 2200BG (rev 05) Wireless Card not working"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by Altay_H on 2008-10-10
I recently installed ubuntu on another computer, and unfortunately the wireless was not working out of the box. I had little worries because it was a Intel 2200BG card, and I was under the impression it had excellent compatibility with Ubuntu (unlike the Broadcom card in my other computer...).

Anyway, I can't seem to figure out the problem with the wireless. When I enter the following command to check for drivers, I get the following output:
```
sudo lsmod | grep ipw2200
ipw2200               146120  0 
ieee80211              35528  1 ipw2200

```

This causes me to believe that the wireless drivers are in fact installed. The wireless card is located at eth1, and I believe it is "up". This is what iwconfig returns:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

An obvious problem is that eth1 is saying "radio off", but I can't seem to resolve that. I tried the following commands suggested by [this post]("http://ubuntuforums.org/showthread.php?t=887960"), but all they did is change my ESSID from "" to off/any.

```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 disable=0 led=1


sudo su
echo 0 > /sys/bus/pci/drivers/ipw2200/*/rf_kill
```

The network manager applet originally showed a greyed out wireless option, but now it displays no wireless option at all. I've searched around the web for quite some time, but have made no progress.


I suspected that perhaps installing a driver for the card would resolve the problem, but I was only able to find the driver as a .tgz, which I could not compile. I don't have much/any experience doing so, but the walkthrough I followed didn't work. If you think that might solve the issue, I'd be willing to give it another try, but right now I'm still just trying to figure out what the problem is.


Finally, the only option I really haven't tried is ndiswrapper. I'd rather not use ndiswrapper unless it's necessary, and I feel that with a wireless card with such good support that I can download linux drivers for it, I shouldn't need windows drivers to use it. Any suggestions are much appreciated.

---

### Post by jheaton5 on 2008-10-11
Try System>Administration>Hardware Drivers

Do you see your driver/card there?

---

### Post by Altay_H on 2008-10-11
> **jheaton5 said:**
> Try System>Administration>Hardware Drivers

Do you see your driver/card there?
No. There're no drivers at all there.

---

### Post by cdrigby on 2008-10-14
I just installed Ubuntu 8.04.1 LTS i386 on a newly-acquired, refurbished Thinkpad T42. Initially I could not connect wireless via the Intel 2200BG to my WRT45G. Ultimately I succeeded using WPA Personal. The 'key" adjustment I had to make was to shorten the length of the WPA shared key from 19 characters down to 10 characters, as specified in the WRT45G Wireless security set up.

Briefly, what I did was:

[LIST=1]
[*]Completely disable security on the WRT54G wireless (05:00 AM in a rural area, ok for testing).
[*]Under System -> Administration -> Network, set the "Wireless connection" to "Roaming mode enabled".
[*]Primary click (left-click for right-handers) on the network icon on the top panel and select my wireless network. Confirm connection to Internet.
[*]Try again, but set the WRT45G to WEP security. Repeat the connection procedure in 3. above and confirm.
[*]Try again, but set the WRT45G to WPA Personal TKIP with a 10-character WPA Shared Key. Repeat the connection procedure in 3. above and confirm.
[/LIST]

At this point, it is working fine under WPA Personal, which is sufficient protection for my current environment. This post was made on the TPad, connected wirelessly.

Regards
CDR

---

### Post by Kevbert on 2008-10-14
Do you have a front panel switch for the wireless ? Try pressing it.  Try the following in terminal
```
ifconfig eth1 up
```
The drivers for the interface are normally stored in /lib/firmware and for your interface will be named ipw????.fw or iwl????.fw

---

### Post by Altay_H on 2008-10-14
> **cdrigby said:**
> Primary click (left-click for right-handers) on the network icon on the top panel and select my wireless network. Confirm connection to Internet.

The problem is that the icon is showing no wireless networks. Right-clicking it doesn't even show an "Enable Wireless" option like it does on my other computer.


> **Kevbert said:**
> Do you have a front panel switch for the wireless ? Try pressing it.  Try the following in terminal
```
ifconfig eth1 up
```
The drivers for the interface are normally stored in /lib/firmware and for your interface will be named ipw????.fw or iwl????.fw

There is a wireless button, but pressing it does not change anything (the light doesn't come on). I've already tried the command you suggested, but it doesn't do anything either, surprisingly.

I ended up installing ndiswrapper and copying over the drivers from the Windows partition. It's not a perfect solution, but it works. I think I might give [this]("http://janpatulinux.blogspot.com/2007/03/intel-prowireless-2200bg-for-debian.html") a try too.

---

### Post by subvertbeats on 2009-08-29
Old post I know, but in case it helps anyone else, try 

```

sudo iwconfig wlan0 txpower on

```

replace wlan0 with whatever the name of the interface you want to power on is...

---

