---
title: "Network (LAN/WLAN/WIFI) On-Off script (like after Suspend)"
date: 2023-08-08
forum: Networking &amp; Wireless
---

### Post by xinuzi on 2023-08-08
Just a script to activate network list if it seems impossible for some reason.

```
#!/bin/bash

clear

TITLE="NETWORK ON or OFF"
echo -en "\033]0;$TITLE\a" # Window title

echo "$TITLE"

echo

sel (){ 

select CHOICE in "On" "Off"
do
echo "Your Choice: $REPLY"
if [[ $REPLY > $CHOICE ]] # Error handling
then
echo "Wrong choice!"
elif [[ $CHOICE == "On" ]] 
then
sleep 2
nmcli networking on # alternative: nmcli radio wifi on
echo
echo "Network = On."
elif [[ $CHOICE == "Off" ]]
then
sleep 2
nmcli networking off # alternative: nmcli radio wifi off
echo
echo "Network = Off."
fi
break
done
}

sel

echo

echo "Enter = Restart"
echo "Ctrl+c or window X = Close"

read

exec bash "$0" "$@" # restart script
```

---

