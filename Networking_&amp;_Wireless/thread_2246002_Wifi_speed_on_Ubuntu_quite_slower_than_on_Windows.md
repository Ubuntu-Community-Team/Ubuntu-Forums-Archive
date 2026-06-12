---
title: "Wifi speed on Ubuntu quite slower than on Windows"
date: 2014-09-27
forum: Networking &amp; Wireless
---

### Post by SilentSib on 2014-09-27
Good evening!

I'm using a Windows 7/Ubuntu 14.04 dual boot system.

My download speed on Ubuntu is about the following:

[[IMG]http://www.speedtest.net/result/3792167360.png[/IMG]]("http://www.speedtest.net/my-result/3792167360")

And my download speed on Windows 7 is... well, add about 20 more Mb/s, which is about 46/47 Mb/s total.
It's been like that for as long as I can remember and I just don't understand where that crappy speed is coming from on linux (crappy wireless card, crappy driver, etc. - I wish I knew!)

Anyway, I don't usually post on forums unless I really haven't found any solution that worked before, and I looked quite a while and tried a few solutions posted here and there too, without success.

Here's the log that got created when I used the Wireless Script of user **varunendra** : [click here]("http://pastebin.ubuntu.com/8442599/")

I do admit that my skills in network are a bit limited, but I'm ready to try pretty much anything to get that speed increased here, because switching to Windows just to download something is...not very convenient.

Thanks in advance!

Edit: Alright, in the meantime I've gained about 15Mb/s by following [this]("http://askubuntu.com/questions/363126/slow-wifi-after-with-centrino-wireless-n-1030-rainbow-peak") and just copying what was in the screenshots. Not quite there but I'm definitely getting closer to my Windows download speed.

---

### Post by varunendra on 2014-09-29
Hello SilentSib! Welcome to the forums :)

In the newer versions of the iwlwifi driver, the "11n_disable" parameter has more than two values - 0 or 1. I recommend you try value '8', which enables Tx aggregation, enabling the interface to push larger packets per second, thus possibly gaining better speeds.

If you have added the "11n_disable=1" parameter to the '/etc/modprobe.d/iwlwifi.conf' file, this command will change the value '1' to '8' -
```
sudo sed -i 's/11n_disable=1/11n_disable=8/' /etc/modprobe.d/iwlwifi.conf
```

If you haven't yet added that option, you can add it now with -
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Of course try any one of the above as applicable, not both.

Apart from this, you are using WPA/WPA2 mixed mode encryption with TKIP in the router/access-point you are connected to in the report. If you have admin access to this AP/router, it is highly recommended to change that to pure WPA2-PSK with AES (CCMP). Reboot the router after saving the change.

If this doesn't solve the speed issue, please post back a fresh wireless_script report with the above changes applied.

---

### Post by SilentSib on 2014-09-29
Hi,

Thanks for answering and trying to help!

So, I changed the parameter of "11n_disable" to 8 as you suggested and also changed the encryption of the connection to AES. No change really.

Here's the [new log]("http://pastebin.ubuntu.com/8459801/").

I usually test the speed with speedtest.net, my own dedicated server and also an image I'm downloading from ubuntu.com. The speed varies between 2.5MB/s and 3MB/s in any case but rarely goes over that. And if it does, it doesn't stay like that too long.

---

### Post by varunendra on 2014-09-29
The report doesn't show "11n_disable=8" applied, although the conf file seems to be okay. Please reboot, and check again -
```
grep [[:alnum:]] /sys/module/iwlwifi/parameters
```
Does it show the value of "11n_disable" to be '8'? Currently it is the default '0'.

---

### Post by SilentSib on 2014-09-29
Yep, I rebooted in the meantime and it does show 8.
Plus, the speedtest I'm doing with an image downloaded from ubuntu.com shows that now the download speed is pretty much the same as the one in Windows.

There's just one thing I don't understand but that might not be related to the wifi settings anymore... I'm downloading the same file as a test from my dedicated server from Windows and Ubuntu, and on windows it uses the whole bandwidth but it still doesn't on Linux. Oh well, at least it seems that the speed is normal as far as other sources are concerned.

Thanks a lot for your help :)

Edit: Nevermind that, it seems the speed is OK now too for files downloaded from my server. Oh well!

---

### Post by varunendra on 2014-10-01
You're welcome! So nice to hear another confirmation. :)

---

