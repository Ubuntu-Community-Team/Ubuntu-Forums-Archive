---
title: "Coredy WA-AC610 Wifi Adapter not working"
date: 2017-03-27
forum: Networking &amp; Wireless
---

### Post by adventure man on 2017-03-27
Bought this adapter hoping to use the 5ghz speed from my internet.  I'm dual boot with Win7; worked flawlessly on that OS.  I have installed the 3.x/4.x drivers from Coredy's website on Ubuntu 16.04 kernel 4.4.0 and everything seems to go well except that after driver install it doesn't show any networks, just a hollowed out wifi picture up top.  The product page says it's compatible but I also tried this on another computer with Ubuntu 14.04 and the same exact problem.  One last thing, the first time I installed the drivers on my Ubuntu 16 setup, it did connect to my network for about 30 second but then disconnected and kept trying to reconnect. Upon restarting the computer it didn't work at all, no light on the adapter, no networks and that's how it has been since.  

Wireless Script:
[http://pastebin.ubuntu.com/24262393/](http://pastebin.ubuntu.com/24262393/)

Newegg Product Page:
[https://www.newegg.com/Product/Product.aspx?Item=9SIA8BG4M62961](https://www.newegg.com/Product/Product.aspx?Item=9SIA8BG4M62961)

Coredy Product Page:
[http://www.coredytech.com/goods-95-Coredy+AC610+Nano+Dual+Band+USB+Wi-Fi+Adapter.html](http://www.coredytech.com/goods-95-Coredy+AC610+Nano+Dual+Band+USB+Wi-Fi+Adapter.html)

Thanks for any help!

---

### Post by chili555 on 2017-03-27
It has been a long time since I wrote a term paper about one single wireless device, but let's get busy!

I am troubled by this:

> ##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET

I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

   ```
 gksudo gedit /etc/default/crda
```

Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

I am also troubled by this:

> [/etc/modprobe.d/r8712u.conf]
options r8712u low_power=1 power_mgnt=0 ht_enable=0

Yours is clearly an mt7601u device, so let's remove the needless file:

```
sudo rm /etc/modprobe.d/r8712u.conf

```
Likewise this:

```
sudo rm /etc/modprobe.d/ath9k.conf
```

I am also troubled by this:

> [/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

Again, yours is an mt7601u device and this declaration is not useful. Let's remove it:

```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```

Remove the second part so that the file now reads:

```
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

```
Proofread carefully, save and close the text editor.

Next, let's address the driver itself. The driver is included by default in Ubuntu 16.10; that is, kernel version 4.8.0-xx and later. We could install a 4.8 kernel on your system and get rid of the most likely outdated driver from Coredy. Otherwise, we could build a newer driver that we suspect will work much better. Which approach do you prefer?

If the first, then:

```
sudo apt-get install linux-generic-hwe-16.04
```

Reboot and you should be all set.

---

### Post by gogmilk on 2017-03-28
I was posting about this exact same problem last week, I got it working but I have to restart the network manager after login and I'm getting system hangs on shutdown/reboot.

There might be some useful info on the thread here...

[https://ubuntuforums.org/showthread.php?t=2356172](https://ubuntuforums.org/showthread.php?t=2356172)

Interested to hear if you have the same issues after going through chili555s process, at the moment I've got it working so I'm reluctant to make changes until I know it will work. If anyone has any ideas on fixing the hangs and manual network manager reboots it would be great to hear them.

---

### Post by adventure man on 2017-03-30
@gogmilk: thanks for that link, looks like we may have a similar issue, gonna review that once I have a chance!
@chili555: I followed everything you wrote but it ended up not resolving the problem.  Here is the new wireless script: [http://pastebin.ubuntu.com/24282082/](http://pastebin.ubuntu.com/24282082/)

Again thanks for help and advice guys, I really appreciate it

---

### Post by chili555 on 2017-03-30
My sincerest apologies for my following mis-steps:

> Yours is clearly an mt7601u device

Wrong.

> The driver is included by default in Ubuntu 16.10; that is, kernel version 4.8.0-xx and later.

Also wrong.

I regret that I made a mistake. I answer a lot of posts and, like many humans, make an occasional mistake.

In fact, yours is an mt7610u device, not mt7601u. There is a difference as you've seen.

I propose the following; from the terminal:

```
sudo apt update
sudo apt install git
git clone https://github.com/ulli-kroll/mt7610u.git
cd mt7610u
make
sudo insmod mt7610u

```Make should produce lots of warnings but no errors. Your wireless should be working. Post back and let us know. I will have additional steps and comments.

---

### Post by adventure man on 2017-03-30
No doesn't work, when I input the final command to terminal I get this response:

sudo insmod mt7610u

insmod: ERROR: could not insert module mt7610u: No such device


Here is the new wireless script: [http://pastebin.ubuntu.com/24283383/](http://pastebin.ubuntu.com/24283383/)

---

### Post by chili555 on 2017-03-30
Please try:```
sudo insmod mt7610u[COLOR="#FF0000"].ko[/COLOR]
```Please be certain to run the command from the location where you ran 'make.' That is:```
cd mt7610u
sudo make installfw
sudo insmod mt7610u.ko
```...or similar.

EDIT: I added another step from the README.

---

### Post by adventure man on 2017-03-30
Ok, so I followed your new steps and after inputting the final "sudo insmod mt7610u.ko", I get this:

insmod: ERROR: could not insert module mt7610u.ko: File exists

---

### Post by chili555 on 2017-03-31
> insmod: ERROR: could not insert module mt7610u.ko: File existsThat typically means that the module is already loaded and needn't be reloaded. Is it?```
lsmod | grep mt7
```Are there any clues in the log?```
dmesg | grep mt7
```

---

### Post by adventure man on 2017-03-31
I put those codes in and got nothing back...am I doing something wrong?  Kinda confused.

---

