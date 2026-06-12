---
title: "iwconfig works, but not menu"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by wsj-m on 2006-08-03
I was attempting to activate my wireless card on the network-admin gui (from Xubuntu) and did not get anywhere.  I saw the box to enter my essid and key, but activating it did not do anything. ](*,) 

Finding the madwifi HOWTO, I was able to use 
*iwconfig ath0 essid ... key ... *
followed by 
*dhclient ath0*
and the card connected to my lan. :D

I guess I have two questions ...

1. how can I automate this.  I used to speak RedHat, and am unfamilar with how the network scripting / configuration files

2. any ideas why the gui application did not work ?

thanks for any help :-)

---

### Post by cantormath on 2006-08-03
Ideas that work for me.

I use Wifi-radar, Waproamd, and Network Manager, all of which I installed from the add/remove or synaptic....

2nd)
restart the machine, iwconfig the card to see that it is showing up, and 
use dhclient
Open terminal and type:
@cantormath-laptop:~$ sudo dhclient

let it finish, see if it gets you an ip.

_Note:_
try do this with wep off and no mac filtering, if you have that turned on.  Maybe go to a coffee shop with free wireless to test it if you dont want to change your home settings.

Make sure that you activated the card through the gui, and deactivate eth0 if you dont plan to use a lan line.

---

### Post by stormblue on 2006-08-04
Here is what I did:

1. Set up a file called eth2.sh  or whatever you want to call it just make sure it ends in .sh

2. And then modify the following to fit your needs:

```
#/bin/bash
sudo ifconfig ath0 up
sudo iwconfig ath0 essid Thepizzabox
sudo iwconfig ath0 key open ADC8015C8CDC98CA9011CEABA7
sudo dhclient ath0
```

3. to run it put it in your /home/username folder and then open up the terminal and run type:

```

sudo ./eths.sh
```

I never could get a GUI to work, but this way seems to work well for me as I can run different scripts for different cards and locations.

---

### Post by wsj-m on 2006-08-04
Thank you all for your suggestions :D 

wifi-radar does connect me with my network, which is good.  This my be because it uses the madwifi libraires, which do seem to be ok in the commandline.

I attempted to use it as a daemon, which it said that scanning was not available.  It works in win XP, so I am not sure why it is saying that.  I am looking at the wifi-radar pyhton code to see what I can discover (which will be fun because I know more perl and C then python).

Thanks again

---

