---
title: "Wireless intermittently dropping out"
date: 2018-12-22
forum: Networking &amp; Wireless
---

### Post by tri++ on 2018-12-22
[ATTACH]282007[/ATTACH]
(Or for more convenience - [https://pastebin.ubuntu.com/p/FjdnGSmwxz/](https://pastebin.ubuntu.com/p/FjdnGSmwxz/))

The gist of the problem is: I constantly have to run "sudo service network-manager restart" in order to reconnect to the internet. 

Basically, I'll be randomly doing internet things, and all of a sudden, the page will seemingly take forever to load. A simple ping to google will hang forever, and dmesg will have a series of lines like this:

[102905.740758] wlp2s0: authenticate with c8:a7:0a:ac:99:0c
[102905.744921] wlp2s0: send auth to c8:a7:0a:ac:99:0c (try 1/3)
[102905.748641] wlp2s0: authenticated
[102905.751362] wlp2s0: associate with c8:a7:0a:ac:99:0c (try 1/3)
[102905.756072] wlp2s0: RX AssocResp from c8:a7:0a:ac:99:0c (capab=0x31 status=0 aid=7)
[102905.764819] wlp2s0: associated
[103306.789926] wlp2s0: deauthenticating from c8:a7:0a:ac:99:0c by local choice (Reason: 3=DEAUTH_LEAVING)
[103306.797975] wlp2s0: failed to remove key (1, ff:ff:ff:ff:ff:ff) from hardware (-22)
 
Power management (a la iwconfig) is already off.

---

### Post by praseodym on 2018-12-23
Lets check

```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi-11n.conf
```
Reboot

---

### Post by tri++ on 2018-12-23
That returned - options iwlwifi 11n_disable=1

And then I rebooted and ran the same thing, and it gave me the same output

EDIT: Wow I'm an idiot, but regardless that didn't work

---

### Post by tri++ on 2018-12-25
Bump

---

### Post by Hadaka on 2018-12-25
Hi, this "may" help..Please copy and paste
one line at a time to avoid error.
*BACKUP the file....
```
sudo cp /etc/default/grub /etc/default/grub.bak
```
*Verify line to modify....11th line of file /etc/default/grub
```
sudo sed -n 11p /etc/default/grub
```
*Output should read....
*  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"  *
*Append to line 11.... of /etc/default/grub
```
sudo sed -i 's/quiet splash/& irqpoll/1' /etc/default/grub
```
*Verify change to /etc/default/grub
```
sudo sed -n 11p /etc/default/grub
```
*Output should read....
* GRUB_CMDLINE_LINUX_DEFAULT="quiet splash irqpoll" *
*Update the file /etc/default/grub
```
sudo update grub
```

***To revert back to original file and configuration..simply over wright..
```
sudo mv /etc/default/grub.bak /etc/default/grub
```
```
sudo update grub
```
Hope that helps

---

### Post by tri++ on 2018-12-25
Now I'm getting roughly the same problem, but with different symptoms. My wireless still drops out, and restarting network manager is a temporary fix, but dmesg looks very different.

[   12.796180] hpet1: lost 54 rtc interrupts
[   17.769346] hpet1: lost 316 rtc interrupts
[   20.843393] hpet1: lost 193 rtc interrupts
[   73.509274] wlp2s0: deauthenticating from c8:a7:0a:ac:99:0c by local choice (Reason: 3=DEAUTH_LEAVING)
[   73.517925] hpet1: lost 3367 rtc interrupts
[   73.532233] wlp2s0: failed to remove key (1, ff:ff:ff:ff:ff:ff) from hardware (-22)
[   73.620518] hpet1: lost 1 rtc interrupts
[   74.317667] hpet1: lost 39 rtc interrupts
[   76.403209] wlp2s0: authenticate with c8:a7:0a:ac:99:0c
[   76.404387] hpet1: lost 126 rtc interrupts
[   76.415482] wlp2s0: send auth to c8:a7:0a:ac:99:0c (try 1/3)
[   76.418680] wlp2s0: authenticated
[   76.420039] wlp2s0: associate with c8:a7:0a:ac:99:0c (try 1/3)
[   76.425263] wlp2s0: RX AssocResp from c8:a7:0a:ac:99:0c (capab=0x31 status=0 aid=7)
[   76.428115] wlp2s0: associated
[   90.721895] hpet1: lost 911 rtc interrupts
[   90.777356] hpet1: lost 3 rtc interrupts
[   90.840934] hpet1: lost 1 rtc interrupts
[   90.934942] hpet1: lost 4 rtc interrupts
[   92.658540] hpet1: lost 109 rtc interrupts
[   92.963690] hpet1: lost 18 rtc interrupts
[   93.121721] hpet1: lost 8 rtc interrupts
[   93.152255] hpet1: lost 1 rtc interrupts
[   93.314789] hpet1: lost 5 rtc interrupts
[   93.516561] hpet1: lost 11 rtc interrupts

---

### Post by praseodym on 2018-12-25
[https://askubuntu.com/questions/967441/17-1-wlp6s0-failed-to-remove-key-1-ffffffffffff-from-hardware-22](https://askubuntu.com/questions/967441/17-1-wlp6s0-failed-to-remove-key-1-ffffffffffff-from-hardware-22)

See here for that error. Check the GUI approach or restart the router

---

### Post by Hadaka on 2018-12-26
Hi  1+ on praseodym's suggestion..
From a working ethernet wired connection.
Please open a terminal, copy and paste...
```
sudo sed -i 's/[COLOR=#000000]quiet splash irqpoll//' /etc/default/grub
[/COLOR]sudo update grub
```
Please also do..one line at a time..
*Helps clean up kernel issues
```
[COLOR=#000000]sudo apt-get autoremove
sudo apt-get autoclean[/COLOR][COLOR=#000000]
sudo apt-get update
[/COLOR][COLOR=#000000]sudo apt-get dist-upgrade[/COLOR]
```
remove wired connection,boot and test wireless
Thanks
*To revert to original [COLOR=#000000]/etc/default/grub code...
[/COLOR]```
[COLOR=#000000]sudo sed -i 's/DEFAULT=""/DEFAULT="quiet splash"/' /etc/default/grub
[/COLOR]sudo update grub
```

---

