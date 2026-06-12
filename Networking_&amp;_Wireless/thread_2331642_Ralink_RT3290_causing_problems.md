---
title: "Ralink RT3290 causing problems"
date: 2016-07-24
forum: Networking &amp; Wireless
---

### Post by spambot3 on 2016-07-24
Okay, I hope there are people who like to solve these kind of problems online. :)

I have CQ58-250SM compaq hp laptop, and it's... no good.

It suddenly restarts in windows, fails, blablabla... So I gave linux a shot, because I need only couple of things:  Wifi support, browser, videos, music, simple word processor.

I tried Lubuntu, machine keeps restarting, then I tried RAM only systems, Linux Puppy, which works great, and Porteus, also great, but my wifi is not supported anywhere (as well in lubuntu, really buggy)



My question is - can you explain a complete linux noob how to install wifi drivers without active internet connection (I can download files on my desktop and transfer them to laptop) so I can use my wireless adapter in any distro?
I'm downloading Xubuntu atm and will try it, but I think I will have same problem as with Lubuntu - device not ready or I could not find module at all like on puppy.

Thanks in advance!

---

### Post by chili555 on 2016-07-24
If I may take a bit of license, I think your question is not, 'how to install wifi drivers without active internet connection', but, instead, 'how to install better wifi drivers than the buggy rt2800pci that my RT3290 uses but without active internet connection'.

I am going to talk a bit about the subject as a whole and then your specific issue.

If you Google 'RT3290 buggy', you will see many posts and few answers. You will see those who complain that they installed a driver from Ralink's website and it doesn't compile at all, much less work. In fact, most of the drivers at Mediatek's site are old, many for kernel version 2.6.something. The current default kernel in Ubuntu 16.04 is not 2.6.something or 3.anything but 4.4.0-xx! You can't ever compile an* older *driver and expect a *better* result.

As for your 3290 specifically, the pickings are slim. You can try to tweak the settings in your router and computer and try to get rt2800pci to work better. You can try a different, maybe better, maybe not driver, and, finally, you can get a different device.

I would love to report to you, and the searchers who I hope will read this, that every device ever made works perfectly in Linux, Windows and Mac, but it isn't true.

First, let's see what we can do with what you have now. First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these changes do not help, please try:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
```If it helps, make it permanent:```
sudo -i
echo "options rt2800pci nohwcrypt=Y"  >>  /etc/modprobe.d/rt2800pci.conf
exit
```

Now, if these changes are ineffective, let's try the maybe driver. Please download this file on some other computer and transfer it on a USB key or similar to the desktop of the subject computer: [https://drive.google.com/file/d/0Bw6He1mvtZ9GSHRMYjhSeVhUMWc/view](https://drive.google.com/file/d/0Bw6He1mvtZ9GSHRMYjhSeVhUMWc/view)

Now open the terminal and do:```
cd ~/Desktop
sudo tar -xvf rt3290sta-2.6.0.0.dkms.tar -C /usr/src
```One of the prerequisites for this process is dkms. If you have the Ubuntu install DVD or USB, drill down to pool > main > d > dkms and drag dkms to you desktop. Then install:

```
cd ~/Desktop
sudo dpkg -i dkms*.deb
```If not, find the package here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) Be sure to select your Ubuntu version; find yours with:```
lsb_release -c
```And also your architecture; either 32- or 64-bit:```
arch
```Again, get it on some other computer, transfer it on a USB, etc.

Once dkms is installed, proceed.```
sudo dkms install -m rt3290sta -v 2.6.0.0 --force
```Reboot and let us hear the result.

---

### Post by spambot3 on 2016-07-24
Sorry, I had some unexpected guests over so I couldn't be active on forum.

I just plugged bootable usb Xubuntu, and everything works smooth, including wireless (maybe because I did not run apt-get update yet, wireless also worked fine on Lubuntu before I did that, so... Maybe just don't touch anything?

As I mentioned, I need this pc only for word processor, browser, music and video. Or should I try updating, is it worth it, what do I get from that anyway?

---

### Post by chili555 on 2016-07-24
You get bug fixes, security patches and improvements in drivers, some of which may or may not include rt2800pci.

If one of the updates is a newer linux-image; essentially a kernel version, and you don't like it, you can always select an older version at the GRUB menu and revert to the older kernel.

In this admittedly old image, you can see how you could select from among several versions, in the example case, -15, -16 or -18. If, for example, -18 was just installed and didn't work for you, select -15 or -16 and boot up.

[http://www.howtogeek.com/wp-content/uploads/2007/09/640x275ximage55.png.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.f8T7JOrYIe.png](http://www.howtogeek.com/wp-content/uploads/2007/09/640x275ximage55.png.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.f8T7JOrYIe.png)

---

### Post by spambot3 on 2016-07-24
Mhm... Thank you a lot!
Do you maybe know how to exclude wireless adapter card when updating whole os?

---

### Post by chili555 on 2016-07-24
> **spambot3 said:**
> Mhm... Thank you a lot!
Do you maybe know how to exclude wireless adapter card when updating whole os?There is no way I know of; sorry.

---

