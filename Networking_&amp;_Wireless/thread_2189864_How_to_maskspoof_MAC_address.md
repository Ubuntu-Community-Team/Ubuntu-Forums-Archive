---
title: "How to mask/spoof MAC address?"
date: 2013-11-24
forum: Networking &amp; Wireless
---

### Post by emptycoder on 2013-11-24
Hi everyone, I'm using a wifi connection, the Cloned MAC Address option on Network settings not working and it refuses to connect until I delete the fake address.
So I want to use Macchanger to spoof my MAC, so how to do it with (Wifi Connection) and (Temporarily) not permanently.
And most importantly, how to know if it worked? I tried to use Macchanger-gtk but it doesn't seem to work.
Thanks!

---

### Post by bashiergui on 2013-11-24
Simple to change with a few commands [http://www.upubuntu.com/2013/05/change-mac-address-using.html](http://www.upubuntu.com/2013/05/change-mac-address-using.html)
I guess you know if it worked if you don't time out on the free wi-fi ;)

---

### Post by emptycoder on 2013-11-25
Thanks for your reply, but the link you provided contains a tutorial for Ethernet Wired Connection not Wireless, so changing eth0 to wlan0 would do the trick or do I need another command?

---

### Post by pbrane on 2013-11-25
You should be able to change the interface name from eth0 the wlan0 and accomplish the same thing. Here is a script I wrote that will change the MAC address of any interface and use your original OUI. You can change it if you want. The remainder of the MAC is random.

```

#!/bin/bash

MINPARAMS=1
if [ $# -lt "$MINPARAMS" ]
then
  echo
  echo "usage: sudo $0 <interface>"
  exit
fi

if (($UID > 0)); then
   echo 'This script can be run only by the system administrator'
   exit
fi

# grab the interface
interface=$1
oldMAC=$(ifconfig $interface | grep HWaddr | awk '{print $5}')
# get the OUI
#OUI=$(ifconfig $interface | grep HWaddr | awk '{print $5}' | cut -b 1-8)
echo "old MAC: $oldMAC"

# get the OUI from a list of legit OUIs
OUI_ARRAY=(
	00:1c:bf # intel
	00:12:f0 # intel
	00:1b:e9 # broadcom
	18:c0:86 # broadcom
	d4:ae:52 # dell
	d4:be:d9 # dell
	00:1d:09 # dell
	d4:c9:ef # hp
	d8:9d:67 # hp
	d8:9e:3f # apple
	d8:a2:5e # apple
)
RANGE=12
idx=$RANDOM
let "idx %= $RANGE"
OUI=${OUI_ARRAY[idx]}

# generate a new NIC specific identifier
NIC=$(date | md5sum | sed 's/../&:/g' | cut -b 9-17)
newMAC="$OUI$NIC"
echo "new MAC: $newMAC"

# assign the new MAC to the interface
echo "Do you wish to assign $newMAC to $interface?"
select yn in "Yes" "No"; do
	case $yn in
		Yes ) ifconfig $interface down;
			  sleep 2 # allow interface to go down
			  ifconfig $interface hw ether $newMAC;
			  sleep 2 # allow time to assign MAC to interface 
			  ifconfig $interface up;
			  # display the new MAC
			  ifconfig $interface | grep HWaddr;
			  break;;
		No ) exit;;
	esac
done

```

---

### Post by emptycoder on 2013-11-26
Thanks a lot, but I forgot to tell you that I'm still newbie!:(
I don't know how to use that script, could you please teach me how?
And please keep in mind that I want to change it temporarily not permanently.
Many thanks.:P

---

### Post by bashiergui on 2013-11-26
You don't need the script. Write down your existing MAC address. Then change it using the commands I linked. Change the interface to be the one you need. Then change the MAC address to something different.

When you wantto switch back do the same thing but use your original MAC address.

---

### Post by emptycoder on 2013-11-27
Is this the right command?

sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether  08:00:25:de:40:df
sudo  ifconfig wlan0 up

and when I shutdown my computer and then turn it on, would my MAC turns back to default address?
I'm sorry for being a pain but I'm new to this networking thing.

Please could you provide an example so I can understand, lets say my MAC Address is 09:00:99:00:99:09 what are the commands to spoof it & then restore it back?
Thanks and sorry for not catching on fast!:confused:

---

### Post by oldos2er on 2013-11-27
Moved to Networking & Wireless.

---

### Post by vivek.pr.mi on 2013-11-27
The commands you are using are correct and yes when you will restart it will restore your original mac address. You can check your mac address using ifconfig command. 

To change your mac address type: 

sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether  08:00:25:de:40:df
sudo  ifconfig wlan0 up


And to restore it to original:

sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether 09:00:99:00:99:09
sudo  ifconfig wlan0 up

---

### Post by pbrane on 2013-11-27
The MAC address is hardcoded in the ethernet controller. You can only change it temporarily. The only advantage to using the script is that you get a valid OUI and random address. Having an invalid OUI is a red flag and some layer 2 devices can detect this.

also running the script is only one command. 

sudo newmac.sh eth0

---

### Post by jonobr on 2013-11-27
Hello


I work in telecom and I would be absolutely lost without macchanger. If I go to a location which has a device where the mac is recorded by the provider, I need to mimic the mac to make sure the backhaul is good or see what the device sees.

---

### Post by emptycoder on 2013-11-29
I tried out those commands and the wireless network refused to connect, it keep asking me for the password until I change back MAC address to default, the same problem when I tried Cloned MAC Address option on Network settings.
I'm really confused! What's causing it?

---

### Post by bashiergui on 2013-11-29
As previously stated> **pbrane said:**
> Having an invalid OUI is a red flag and some layer 2 devices can detect this.Also some wireless networks filter MAC addresses and only allow certain MACs to join. Ask your network administrator for those details.

Do you have the password? What happened when you entered your password? 
What's your goal? To join the wireless network using a MAC address not your own?

---

### Post by emptycoder on 2013-12-01
I'm sorry for my late reply!
After spoofing, it keeps asking for my password like forever, it doesn't show any error login message or something.
I'm trying to mask my MAC because I want to protect my privacy, there's only a one ISP on the area where I live and it's snooping on all users activates.
I'm already using VPN but I wanted to mask my MAC for extra protection, that's it.

---

### Post by pbrane on 2013-12-01
I don't think spoofing your MAC is going to give you any more privacy. Layer 2 has to know your MAC to switch the packets to the appropriate port. changing it just means more ARP requests. Your ISP is probably logging layer 3 and 4 traffic. Chances are the only MAC they see is your router WAN port. Not much you can do about that. You're on their network and you probably agreed to their TOS.

---

### Post by emptycoder on 2013-12-02
I think you're right (sigh) well, thanks everyone for helping me! :p

---

### Post by mmweber on 2014-01-06
Kinda had the same problem. Also Network Manager didn't update the cloned-mac field, and used the hardcoded one.  I wrote a little bash script that need macchanger and root access. Here's the link: [http://cyberandspace.wordpress.com/2013/12/30/macbot-0-1-an-interactive-commandline-script-for-macchanger/](http://cyberandspace.wordpress.com/2013/12/30/macbot-0-1-an-interactive-commandline-script-for-macchanger/)  Hope this helps.  Cheers,  Manuel

---

