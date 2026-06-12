---
title: "Cisco 350 wireless card with WEP (airo driver) solved"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by dpasirst on 2006-09-11
I have seen many threads with people posting about problems with their Cisco 350 wireless card not working (typically with WEP) while the wiki indicates it should work out of the box.

In my case, I knew the card should function properly in ubuntu because it worked on other networks but for some reason, I could not get it to work with my dd-wrt wireless router.

After many searchs and nothing turning up but other people with the same symptoms, I found a configuration mis-match in that my router was set to a long preamble while the wireless card was defaulting to a short preamble.  Fixing that solved it for me, but I bet many of the problems people may have with this card could be fixed very similarly.  Check out the /proc/driver/aironet/*/Config for a listing of possible configuration options.


Here is my fix (I placed this script in /etc/network/if-pre-up.d):
```

#!/bin/sh
#
# This script takes care of configuring cisco wireless
# cards using the airo driver such as 340 and 350 cards.
# It is run by ifup.

AIROPROC=/proc/driver/aironet
CONFIG=Config
SLEEP=2

#some sanity checks
if [ ! -d $AIROPROC ] ; then
        exit 0
fi

for i in $AIROPROC/* ; do
   if [ -w "$i/$CONFIG" ] ; then
       echo "Preamble: long" > "$i/$CONFIG"
   fi
done
sleep $SLEEP
exit 0

```

Don't forget to make it executable...

For convience I have also attached a copy of the script, you will probably want to rename it from .txt to .sh.

---

### Post by mitticus on 2007-03-19
Thank you! 

I was looking for a solution to this for ages.

Works great on my IBM Thinkpad x30 with a cisco airo wireless adaptor on ubuntu edgy.

Hopefully this reply boosts google for anyone else.

Ubuntu airo aironet cisco wireless wep not connecting

---

### Post by 9000 on 2007-04-22
thank you sooo much, Ive been trying to get this to work for ages!!!

---

### Post by tp21 on 2007-07-19
hi,
where can i find the airo driver configurations, under /proc/driver there is no airo.
i am hoping to find the config and to see what i can change, because the script unfortunatly did not work for me.
thanks

---

### Post by subulaz on 2007-08-04
Has anyone noticed the issue returning in Feisty? I have an old ThinkPad A22p with an Aironet PCM-352. It loads airo & airo_cs just fine (in fact, so well that even after I ifconfig eth1 down and remove the card, I still can't rmmod airo), but it will not get an address from DHCP and will not connect to an AP even if I specify a valid address/network/subnet.

I applied the shell script but the Config still shows Preamble: short, and kwifimanager will show a solid green connection but not fill in the AccessPoint value despite the fact iwconfig has correct values for AP, ESSID, etc.

Any ideas, pointers, similar headaches? This is on Feisty 7.04 and kernel 2.6.20-15 & 16 (tried both for the heckuvit)

&laz;

---

### Post by subulaz on 2007-08-12
Update: this is working with a bit of command-line tweaking. After KDE inits all the way, I do the following:

1 - remove the Aironet card
2 - rmmod yenta_socket
(to clear the way for...)
3 - rmmod pcmcia_core

Then, when lsmod shows no trace of pcmcia or airo (which is stubborn when it comes to rmmod), I just add it all back:

4 - insert the Aironet card (the activity light glows bright orange since pcmcia is not up)
5 - modprobe pcmcia_core
6 - modprobe yenta_socket

When all is said and done, everything is active:

```

root@fender:~# lsmod | grep pcmcia
pcmcia           38316  1 airo_cs
pcmcia_core      39696  4 airo_cs,pcmcia,yenta_socket,rsrc_nonstatic

```

The card immediately gets an IP from the router (WRT54GSv2) and is happily active on the network. No clue at all as to why this is happening, though the relationship to pcmcia reminds me of trying to get something working with an old Orinoco card on SuSE 8 & 9, back when it was pcmcia-cs and you had to futz with /etc/pcmcia/config to get the chipset to talk with the wireless tools.

Does this behavior ring any bells with anyone? Is there something mangled in my pcmcia install or some kernel option I should investigate? I'm well and solidly stumped on this one...

&laz;

---

