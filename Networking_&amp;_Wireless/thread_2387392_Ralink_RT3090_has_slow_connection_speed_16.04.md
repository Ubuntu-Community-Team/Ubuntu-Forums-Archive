---
title: "Ralink RT3090 has slow connection speed 16.04"
date: 2018-03-18
forum: Networking &amp; Wireless
---

### Post by matteo35 on 2018-03-18
Hello,
I am new to linux and setting up my lenovo Z575 laptop with Ubuntu 16.04.  Everything seems to be working well, except the wireless network speed is very slow.  My computer is dual boot with Windows 7.  In Windows, I get 30 MB/s download and upload speeds.  In linux, I am getting 0.3 and 1.8 MB/s download and upload speed, respectively.  I've updated and upgraded, disabled IPv6, rebooted router and computer.  I ran the wireless info script and the results can be found here:

[http://paste.ubuntu.com/p/Z6KDrZjmQr/](http://paste.ubuntu.com/p/Z6KDrZjmQr/)

[FONT=arial][SIZE=3]I would appreciate any help you can give me.  Please let me know if there is any other information you need.  Thanks!

Matt
[/SIZE][/FONT]

---

### Post by wildmanne39 on 2018-03-18
Please do:
```
echo "options rt2800pci  nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
Then:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
When you run the first command if you get an error let me know and we will change the number 1 to a y becasue all of the file you posted is not there so I can not be 100 percent sure if it should be a 1 or a y but it will not hurt to run the command.
I think that will help a lot.

---

### Post by matteo35 on 2018-03-18
I tried the code you suggested.  Did not get any errors and I rebooted my computer.  Did not seem to make much of a difference.  Maybe a slight improvement...  I reran the wireless script:

[http://paste.ubuntu.com/p/TYDJVV22HK/](http://paste.ubuntu.com/p/TYDJVV22HK/)

I could try pasting the text, but it is a pretty long file.

---

### Post by wildmanne39 on 2018-03-18
I know it is a long file but very easy to do with copy and paste function to pastebin.

I image since you are on the same channel as another network and its signal is very strong your device is trying to roam between the two but I can not tell since most of the file is missing, I recommend changing the channel to a fixed channel instead of auto, try 11.

I also recommend setting your encryption to just wpa2 and not mixed mode, also go into network manager and change your settings to match the screenshots.

I realize you have already set IPV6 to ignore but do make all the other changes please.

Reboot

---

### Post by matteo35 on 2018-03-18
I manually copied to pastebin so it should have the full file:

[https://pastebin.com/tr8Lc0Fc](https://pastebin.com/tr8Lc0Fc)

For changing the channel, I would do that on the router, correct?  For changing the mixed mode to WPA2, in the network settings there was only an option for WPA and WPA2, not WPA2 only.  I'm guessing this a change on the router also?  Thanks for your help.  It is much appreciated.

---

### Post by wildmanne39 on 2018-03-18
> **matteo35 said:**
> I manually copied to pastebin so it should have the full file:

[https://pastebin.com/tr8Lc0Fc](https://pastebin.com/tr8Lc0Fc)

For changing the channel, I would do that on the router, correct?  For changing the mixed mode to WPA2, in the network settings there was only an option for WPA and WPA2, not WPA2 only.  I'm guessing this a change on the router also?  Thanks for your help.  It is much appreciated.
Yes both settings are in the router and after changing them you have to save the changes before you close the browser window.

Seeing the rest of the file it looks like channel 6 may be the best choice for you network, there is still 4 networks on that channel but there signal strength is very weak so it should not cause issues with your network.

When you make the changes to just WPA2 in your router set it to CCMP also know as AES right now it shows CCMP/TKIP TKIP is slower and I have never seen both together so this may cause an issue.

The driver parameter should have been with a y and not a 1 so lets fix that, please do:
```
sudo rm /etc/modprobe.d/rt2800pci.conf
```
Then:
```
echo "options rt2800pci  nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
after you run all the commands and make the changes in your router reboot and I think you should see some improvement.

You may also want to change your network name, I know linux in general has issues with certain names like with spaces and the like I have never seen one with all numbers before so that may cause an issue.

---

### Post by matteo35 on 2018-03-21
I went through and made the changes you suggested, except that I did not change the router name.  I may test that this evening if I have time, but it seems like a stretch considering I can connect to the router.  When I look at connection information, it doesn't appear to ever try switching to another signal.  However, I do see in the connection speed that it will say 54 MB/s and every so often will drop to 1 MB/s.  Any downloads I have attempted over wifi occur at the very slow speed and I have to connect to a cable to get them to complete.  At work now, so I will paste the connection info later this evening.

Are there specific drivers that I need to install?  When I look at the list of linux drivers, I do not see my ralink driver there.  Doing some searching I found this article:

[https://askubuntu.com/questions/686188/how-to-install-wifi-driver-ralink-corp-rt3090-wireless-802-11n-1t-1r-pcie-i-am?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa](https://askubuntu.com/questions/686188/how-to-install-wifi-driver-ralink-corp-rt3090-wireless-802-11n-1t-1r-pcie-i-am?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)

Could something like this be the problem?  


Here is my updated connection information:
[https://pastebin.com/SMZnTQeQ](https://pastebin.com/SMZnTQeQ)

Thanks for your help!
Matt

---

### Post by matteo35 on 2018-03-31
Just want to bump this thread.  I haven't made much progress on this problem since I've been super busy.  Also I have not seen any other suggestions.  Should I give up and try getting a wireless wifi adapter? :(

Matt

---

### Post by praseodym on 2018-03-31
Can you please show
```

dmesg | grep rt2
```

---

### Post by matteo35 on 2018-04-01
Here it is:

[   21.178849] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3090, rev 3213 detected
[   21.184091] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0005 detected
[   21.683166] rt2800pci 0000:03:00.0 wlp3s0: renamed from wlan0
[   28.759974] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   29.361320] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34

---

### Post by matteo35 on 2018-04-03
Another bump to see if anyone has any ideas.  Thanks.

---

### Post by praseodym on 2018-04-04
Try installing "LinSSID" and search for free channels. Channel 6 is very busy

---

### Post by matteo35 on 2018-04-04
I will do that and take a look.  One thing to consider is that I have no issues when running Windows 7 on that laptop (it's dual boot).  Also, I was going to try and see how it works when connecting to a different router at my in-laws, I just haven't been able to get around to it.  There will be no other interference there...

---

### Post by matteo35 on 2018-04-06
So I installed LinSSID.  It appears channel 1 is the busiest channel and channels 6 and 11 are roughly equivalent.  Right now I have it set back at channel 1, but I will probably change it to 11.  Even on the busiest channel, Windows gets 30 MB/s and Linux gets 0.5 MB/s.  I can try connecting to a different router this evening and at least see if the router might be the issue.

---

### Post by praseodym on 2018-04-06
Try Wicd instead:
```

wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```

---

### Post by matteo35 on 2018-04-09
Ok, I've tried a couple of things.  Before performing the commands you suggest above,  I tried connecting to another wireless router.  This seemed to go much better as I was able to get 17 MB/s download and 3 MB/s upload.  I don't have that connection information but will try it again another day when I have a chance.  After that, I came home and tried the commands above.  I had no issues until I got to the last 3 commands.  After each one I got the following response:

sudo: unable to resolve host z757: Connection timed out

At the end, I had no wireless network connection at all.  I tried rebooting and the wireless network was available again but was very slow.  I tried repeating the commands, but then I lose my network again.  AT this point I opened the WICD network manager and tried connecting through the program.  It says that I connected, but I did not have internet access.  So, after all of that, if I restart the computer, it goes back to being able to connect at the original slow speed.

*edit adding current wireless info:
[http://paste.ubuntu.com/p/y3XByhgHvk/](http://paste.ubuntu.com/p/y3XByhgHvk/)


Matt

---

### Post by matteo35 on 2018-04-13
Just bumping again. I will be able to go try the other wireless router this weekend and get a print out of what goes on when I connect to that one.

---

### Post by praseodym on 2018-04-13
Change the encryption mode to WPA2-AES (CCMP), not mixed mode WPA/WPA2 (without TKIP)

---

### Post by matteo35 on 2018-04-14
I changed my router to WPA2 and I changed in WICD also.  No improvement.  Although, my network manager says WPA/WPA2.

[https://paste.ubuntu.com/p/Zqv9rcPdTd/](https://paste.ubuntu.com/p/Zqv9rcPdTd/)

---

### Post by matteo35 on 2018-04-16
I installed the drivers for a usb wireless adapter.  I was able to get that working, but the slowness issue continued.  So, I think that rules out my wireless card.  I will post my information this evening when I am at home.  Is it possible that there is an incompatibility with my router?  When I go to another house and use a different router, it seems to work ok.  I guess I need to compile statistics for all of these different cases and find out what is different!  If only I had infinite time...  Thanks for all the help so far.  I have really learned a lot and I am very appreciative that you guys are willing to take the time to help new users like myself!

Matt

---

