---
title: "Ubuntu 16.04: Laptop Bluetooth laggy/erroneous compared to Windows 10"
date: 2017-09-30
forum: Networking &amp; Wireless
---

### Post by ibd2 on 2017-09-30
Hi all

I am running Ubuntu on my laptop as a separate partition from Windows. I just got the new Logitech MX Ergo mouse which uses Bluetooth. I noticed that the mouse pointer is "sometimes" laggy, even though the mouse is right next to the laptop! When I boot into Windows, the mouse works perfectly smoothly, so it must be a software or driver issue and not an interference or other physical problem. 

By "sometimes laggy", I mean that it works fine for a minute, then it is choppy for a few minutes, fine for a minute again, then choppy, etc.

I had previously noticed that bluetooth reception on this laptop under Ubuntu is rather weak, when I was testing a Bluetooth gamepad. It is a Gigabyte Aero 14 laptop (GTX 1060 version).

What I tried so far to solve the problem, without success:
- Try the solution posted here: [https://askubuntu.com/questions/663500/ubuntu-14-04-bluetooth-mouse-lags-time-by-time](https://askubuntu.com/questions/663500/ubuntu-14-04-bluetooth-mouse-lags-time-by-time), including the "sudo modprobe btusb" commands.
- top / htop show no suspicious CPU activity when the Bluetooth mouse is active.

Any ideas how to fix? Are there some drivers I could try updating?

Best regards
ibd

edit: some diagnostics.
Running "dmesg | grep -i blue": [https://pastebin.com/mQfepwfT](https://pastebin.com/mQfepwfT)
Running "sudo service bluetooth status": [https://pastebin.com/E9wkJChJ](https://pastebin.com/E9wkJChJ)
Running "lspci -knn | grep Net -A2": 03:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)    Subsystem: Intel Corporation Wireless 8260 [8086:1010]
    Kernel driver in use: iwlwifi"
"hciconfig -a": [https://pastebin.com/WLhWva8F](https://pastebin.com/WLhWva8F)

---

### Post by jeremy31 on 2017-09-30
You could try changing the bluetooth coexistence parameter with
```
echo "options iwlwifi bt_coex_active=0" | sudo tee /etc/modprobe.d/iwlopt.conf
```
Reboot

---

### Post by ibd2 on 2017-09-30
Thank you for the suggestion. Already tried that, as I hinted at with "tried the solution posted here". No change. There seem to be a lot of people that have issues with "Intel Corporation Wireless 8260" under Linux. Any other ideas how to improve BT reception?

Another error I get is that the BT mouse just stops working when I wake up the laptop from sleep. I can bring it back to life by doing "sudo modprobe -r btusb", followed by "sudo modprobe btusb". Any other ways to fix this?

---

