---
title: "Wifi defaults to soft off..."
date: 2016-12-18
forum: Networking &amp; Wireless
---

### Post by jagdtigger on 2016-12-18
Greetings.

I just installed Kubuntu 16.10 on my laptop(Dell Inspiron 7720, wifi card: intel n6230) and i just notice that i do not have wifi(until now it was connected through wire). When i checked with "rfkill list" it showed that its soft blocked. But even if i enabled it the GUI still didnt showed the AP list... I dont know what to do :/ , any ideas where to start?

Thanks in advance for the help :) .

---

### Post by wildmanne39 on 2016-12-18
Please do:
```
sudo modprobe -rv dell-laptop
```
does wifi com on? if so do:
```
echo "blacklist dell-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf

```

---

### Post by jagdtigger on 2016-12-18
Nope, still nothing:
[https://dl.dropboxusercontent.com/u/1201829/Ubuntu_forum/Spectacle.kn1599.png](https://dl.dropboxusercontent.com/u/1201829/Ubuntu_forum/Spectacle.kn1599.png)

---

### Post by ajgreeny on 2016-12-18
Please copy and paste the terminal output you get as it is unreadable in your screenshot.
Also, please do not use large images inline; use the paperclip in the toolbar of the "Reply to Thread" window and navigate to the image on your drive, upload it, and it will appear as a thumbnail in your post.

The easy way to copy/paste is simply to highlight text in terminal with mouse drag, then middle click to paste the buffer; it is one of the Linux tricks that once learned is so incredibly useful you will wonder why other OSs don't do the same.
Or do they now do that?

---

### Post by wildmanne39 on 2016-12-18
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here and please use thumbnails or url's when posting images.
Thanks

---

### Post by jagdtigger on 2016-12-18
Sorry about that, i got used to that the forum is resizing it automatically :D . Here is the script's output:
[https://dl.dropboxusercontent.com/u/1201829/Ubuntu_forum/wireless-info.txt](https://dl.dropboxusercontent.com/u/1201829/Ubuntu_forum/wireless-info.txt)


@ajgreeny
Open it up on a new tab and click on the image, otherwise if you browser window is smaller than the picture it will automatically downscale it ;) . The point of that image was that even though the wifi is enabled i still didnt get the list of AP's...

---

### Post by wildmanne39 on 2016-12-18
If you have not run the second command in post 2 yet go ahead and run it so you can make that change permanent. Then run:
```
sudo dpkg-reconfigure resolvconf
```
```
sudo apt-get update && sudo apt-get upgrade
```
when it is through updating reboot, does that help?

Also check that networking and wireless is enabled in networking manager.

You may also want to make sure wireless is turn on in the bios if you have that option.

Check in the router and make sure that the wireless radio is enabled.

Also your country code is not correct please do:
```
sudo iw reg set HU
sudo sed -i 's/^REG.*=$/&HU/' /etc/default/crda
```
If your country code is not HU please substitute yours, you can find the codes at the following link.
[https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)

---

### Post by wildmanne39 on 2016-12-18
I added more directions to the post above so be sure to read it again.
Thanks

---

### Post by jagdtigger on 2016-12-19
After running the second posts second command and rebooting it still defaults to soft blocked even if i unblock it before reboot. My system is up-to date from the beginning so those comands didnt do anything in this case. Setting the country code didnt had any effect(yes i done a reboot after i run both commands)...

---

### Post by wildmanne39 on 2016-12-19
Please post the output of:
```
cat /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by jagdtigger on 2016-12-19
Here you go:
[https://dl.dropboxusercontent.com/u/1201829/Ubuntu_forum/blacklist-conf.txt](https://dl.dropboxusercontent.com/u/1201829/Ubuntu_forum/blacklist-conf.txt)

---

### Post by wildmanne39 on 2016-12-19
The file shows that the blacklisting of the module stuck.

You say the system remains softblocked but in the wireless file you posted it does not show softblocked so were are you seeing that?
You  can also try:
```
sudo modprobe -rv iwldvm
sudo modprobe -rv iwlwifi
sudo rfkill unblock all
sudo modprobe -v iwldvm
sudo modprobe -v iwlwifi
```
please do not reboot, if it does not come on post another script file.
Thanks

---

### Post by jagdtigger on 2016-12-19
Ok i just run all the commands but no effect:
```
jagdtigger@jagdtigger-Inspiron-7720:~$ rfkill list
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
jagdtigger@jagdtigger-Inspiron-7720:~$ sudo modprobe -rv iwldvm
[sudo] password for jagdtigger: 
rmmod iwldvm
rmmod mac80211
rmmod iwlwifi
rmmod cfg80211
jagdtigger@jagdtigger-Inspiron-7720:~$ sudo modprobe -rv iwlwifi
remove (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) && /sbin/modprobe -r mac80211
rmmod: ERROR: missing module name.
modprobe: FATAL: Error running remove command for iwlwifi
jagdtigger@jagdtigger-Inspiron-7720:~$ sudo rfkill unblock all
jagdtigger@jagdtigger-Inspiron-7720:~$ sudo modprobe -v iwldvm
insmod /lib/modules/4.8.0-30-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.8.0-30-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.8.0-30-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko 
insmod /lib/modules/4.8.0-30-generic/kernel/drivers/net/wireless/intel/iwlwifi/dvm/iwldvm.ko 
jagdtigger@jagdtigger-Inspiron-7720:~$ sudo modprobe -v iwlwifi
jagdtigger@jagdtigger-Inspiron-7720:~$ rfkill list
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
2: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: no

```

---

### Post by wildmanne39 on 2016-12-19
Please do:
```
sudo modprobe -rv dell_wmi
```
does wifi come on?

---

### Post by jagdtigger on 2016-12-19
No, its stays soft blocked, even if i unblock it with rfkill  after running that command its still do not show the list of AP's...

---

### Post by jeremy31 on 2016-12-19
```
sudo sed -i 's/WirelessEnabled=false/WirelessEnabled=true/' /var/lib/NetworkManager/NetworkManager.state
```
Reboot

If it works we can remove the blacklist on dell-laptop
```
sudo sed -i 's/blacklist dell-laptop/#blacklist dell-laptop/' /etc.modprobe.d/blacklist.conf
```

---

### Post by jagdtigger on 2016-12-19
It seems this one solved it, thank you all for the help :) .

---

### Post by wildmanne39 on 2016-12-19
Thanks jeremy31, that was the last piece in the things that needed changed.

---

