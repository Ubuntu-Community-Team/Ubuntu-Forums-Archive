---
title: "BASH script help"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by taylor102387 on 2009-04-01
Ok, I have a script to automate the aircrak-ng prossese and it works so far: 

```
 #!/bin/bash 
clear
read -p "Would you like to run Kismet to find a network? : " kismet
echo ""
if [ $kismet = yes ]
then clear & sudo xterm -e "sudo kismet"  &
else clear & echo "Continuing...
"
fi
read -p "Enter the Wi-Fi Access Points MAC Address : " mac
echo ""
clear
read -p "Enter the Wi-Fi Access Points SSID : " ssid
echo ""
clear
read -p "Enter the Wi-Fi Access Points Channel : " channel
clear
read -p "Enter the Interface you would like to use : " interface
echo ""
clear
echo "Is this correct? : MAC: $mac , SSID: $ssid , Channel: $channel , Interface: $interface"
read -p "yes or no : " start
echo ""
if [ $start = yes ]
then echo "Starting..."
else bash Aircrack-ng.sh
fi
clear
sudo airmon-ng start $interface $channel
clear
sudo xterm -hold -e "sudo airodump-ng -c $channel --bssid $mac -w output mon0"  &
sudo xterm -hold -e "sudo  aireplay-ng -3 -b $mac -h 00:1c:df:1e:55:66 mon0"

```

But if I add a line at the end using & it shuts down! How can you fix this, and if so tell me if you like the script. :P

---

### Post by llamabr on 2009-04-01
Adding & at the end doesn't shut it down, it puts it into the background.  It's still running.

If you ran it manually, you should be able to bring it back to the foreground with

```
fg
```

---

