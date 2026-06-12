---
title: "Cannot change MAC address of wifi"
date: 2015-07-05
forum: Networking &amp; Wireless
---

### Post by Daniyal_Javani on 2015-07-05
Hello
I want to change mac address to specific MAC address. I run this command:

```
sudo macchanger --mac=xx:xx:xx:xx:xx:xx  wlan0
```
  My mac changed successfully (check with ifconfig), but still I can't connect to a router that have white list filtering,  also after a try to connecting, mac address automatically change back to  default.

     

I've also try with this command, but still same issue
```
ifconfig wlan0 down
ifconfig wlan0 hw ether xx:xx:xx:xx:xx:xx
ifconfig wlan0 up
```
  What should I do? Is it possible that this problem related to driver or my wifi modem does not support changing mac address? because I can't change mac address in Windows too.
Thanks for your help

---

### Post by NoWayWin8 on 2015-07-05
> **Daniyal_Javani said:**
> Hello
I want to change mac address to specific MAC address. I run this command:

```
sudo macchanger --mac=xx:xx:xx:xx:xx:xx  wlan0
```

The problem is most likely the MAC address you are trying to use. The first 3 bytes are the OUID should be left alone.

Maybe if you make only the last 3 bytes different from the real MAC it will work?

---

### Post by NoWayWin8 on 2015-07-06
> **NoWayWin8 said:**
> Maybe if you make only the last 3 bytes different from the real MAC it will work?

More details from [http://superuser.com/a/823558](http://superuser.com/a/823558)
> 
It is worth mentioning that in a MAC address the least significant bit of the first octet is a multicast flag (multicast addresses have it set to 1), so the adapter's address should normally have it set to 0. This means that valid values of the first octet must end with 0, 2, 4, 6, 8, A, C or E.

Moreover, the second-least-significant bit of the first octet is used to distinguish between globally and locally administered addresses (if it is 1, the address is locally administered), and certain adapters (e.g. Intel Wireless) may enforce this by not allowing to change the address to another "globally unique" one. Hence, the value of the first octet must end with 2, 6, A or E.

(if info from SU is correct, you just have to make sure the 2nd digit is a **2**, **6**, **A**, or **E**)

---

### Post by Daniyal_Javani on 2015-07-07
Thanks, but I want to change to <snip>, so I can't do that?

---

### Post by steven53 on 2015-10-21
This script will do random mac for you, stop wlan, wifi and restart wlan and wifi:

    sudo ifconfig wlan0 down
    sleep 5
    #add chars to the mac
    this+=$(echo "obase=16; $(shuf -i 0-15 -n 1) " | bc ) 
    this+=$(echo "obase=16; $(shuf -i 0-15 -n 1) " | bc )
    this+=":"
    this+=$(echo "obase=16; $(shuf -i 0-15 -n 1) " | bc ) 
    this+=$(echo "obase=16; $(shuf -i 0-15 -n 1) " | bc )
    this+=":"
    this+=$(echo "obase=16; $(shuf -i 0-15 -n 1) " | bc ) 
    this+=$(echo "obase=16; $(shuf -i 0-15 -n 1) " | bc )
    this+=":"
    this+=$(echo "obase=16; $(shuf -i 0-15 -n 1) " | bc ) 
    this+=$(echo "obase=16; $(shuf -i 0-15 -n 1) " | bc )
    this+=":"
    this+=$(echo "obase=16; $(shuf -i 0-15 -n 1) " | bc ) 
    this+=$(echo "obase=16; $(shuf -i 0-15 -n 1) " | bc )
    this+=":"
    this+=$(echo "obase=16; $(shuf -i 0-15 -n 1) " | bc ) 
    this+=$(echo "obase=16; $(shuf -i 0-15 -n 1) " | bc )

    sudo ifconfig wlan0 hw ether $this
    sudo ifconfig wlan0 up
    sleep 3
    nmcli nm wifi off
    sleep 3
    nmcli nm wifi on

---

