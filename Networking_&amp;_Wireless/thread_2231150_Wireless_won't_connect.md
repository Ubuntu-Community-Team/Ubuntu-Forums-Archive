---
title: "Wireless won't connect"
date: 2014-06-23
forum: Networking &amp; Wireless
---

### Post by kakashi_12 on 2014-06-23
Using Lubuntu 14.04 . Wired connection works just fine. I have another laptop connected to the wireless network fine.

I can see the available wireless network. I click on our wireless network and put in the WPA2 key. Then the dialog box just goes away.
It won't say connected after that. I bring up a browser and it just shows "server can not be found".
I know I am putting in the correct key.

I changed WPA2 to WPA to see if that would work. Same result.

Also, I can seem to use sudo on the laptop. It says authentication failure. Trying to use 'sudo ifdown eth' and 'ifup wlan0'. I HOPE those are the correct commands.
Do I have to unlock root to use it and how?

Also, I changed the user account to an admin. Before it didn't have rights to connect to wired and wireless network, so i clicked that checkbox. But didn't make a difference still.

---

### Post by wildmanne39 on 2014-06-23
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If you do not have ethernet connection then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385).
Thanks

---

### Post by kakashi_12 on 2014-06-23
Connected through Ethernet now to diagnose issue...

---

### Post by wildmanne39 on 2014-06-23
Please do:
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
Then change the channel in your router to 1 or 11 save changes then reboot router and computer.
Thanks

---

### Post by kakashi_12 on 2014-06-23
Thanks for your help, but nevermind.
Fix: manually create the wireless connection (rather than clicking on connection).
Input proper SSID, selected WPA2, input network key, chose MAC Address from dropdown menu, and made sure it was set for DHCP and not Static (IPv4).

---

### Post by kakashi_12 on 2014-06-23
Not sure why I can't just choose the connection, but good enough for me I guess.
I think it's because.... When I went to GNOME Menu, System (or Preferences), Then Network Connections; only Wired Network shows. Wireless doesn't even show. I had to actually create the connection... not just the connection for that particular network (I believe).

---

