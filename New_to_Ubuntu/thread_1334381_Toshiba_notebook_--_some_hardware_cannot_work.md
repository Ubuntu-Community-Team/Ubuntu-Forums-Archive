---
title: "Toshiba notebook -- some hardware cannot work"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by billyauhk on 2009-11-22
I have installed Ubuntu 9.10 on my Toshiba Satellite L500 and I faced some problems when configuring the hardwares. Pls give me a hand.

1. Cannot install ATI driver.(My graphics card is Mobility Radeon HD 4570)
I have tried System > Administration > Hardware Drivers. I saw the ATI driver is on the list, but it does not activate even when I click the activate button and typed in my password.
I have tried to install fglrx through Synaptic Package Manager instead, but it cannot help.
What would be the cause and how can I fix that?

2. Synaptic Touchpad does not work
I have read [http://help.ubuntu.com/community/SynapticsTouchpad](http://help.ubuntu.com/community/SynapticsTouchpad), get SHMconfig, xserver-xorg-input-synaptics and gsynaptics installed, but the touchpad just does not work. I can see it in xinput list as:
"SynPS/2 Synaptics TouchPad"    id=8    [XExtensionPointer]
    Type is TOUCHPAD
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 1472
        Max_value is 5472
        Resolution is 1
    Axis 1 :
        Min_value is 1408
        Max_value is 4448
        Resolution is 1
Hope this helps.

---

### Post by Woodbadger on 2009-11-22
I have to say that you're one step ahead of me. I can't even get Ubuntu 9.10 to load on my Toshiba Satellite M105. It tries, but it won't load. I don't know if it's the ATI graphics or some other problem. The processor is a Celeron M with 64 bit architecture capability. I've tried installing both 32 and 64 bit versions. I'm open to suggestions. And I'm a newbie, so if you have instructions, make them tediously detailed. Assume I know nothing.

---

### Post by sandyd on 2009-11-22
> **billyauhk said:**
> I have installed Ubuntu 9.10 on my Toshiba Satellite L500 and I faced some problems when configuring the hardwares. Pls give me a hand.

1. Cannot install ATI driver.(My graphics card is Mobility Radeon HD 4570)
I have tried System > Administration > Hardware Drivers. I saw the ATI driver is on the list, but it does not activate even when I click the activate button and typed in my password.
I have tried to install fglrx through Synaptic Package Manager instead, but it cannot help.
What would be the cause and how can I fix that?

2. Synaptic Touchpad does not work
I have read [http://help.ubuntu.com/community/SynapticsTouchpad](http://help.ubuntu.com/community/SynapticsTouchpad), get SHMconfig, xserver-xorg-input-synaptics and gsynaptics installed, but the touchpad just does not work. I can see it in xinput list as:
"SynPS/2 Synaptics TouchPad"    id=8    [XExtensionPointer]
    Type is TOUCHPAD
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 1472
        Max_value is 5472
        Resolution is 1
    Axis 1 :
        Min_value is 1408
        Max_value is 4448
        Resolution is 1
Hope this helps.
1. click on it, restart the computer, then click on it again and take a nap. sometimes it takes a long time to show up.
if it seriously doesnt show up, then run this in the terminal
```

sudo apt-get install envyng-core
sudo envyng -t

```
follow instructions for ATI drivers.


OR

ive found that the latest (catalyst 9.10 drivers) actually work quite well, so you can also do this
```

wget -c https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-11-x86.x86_64.run
chmod 777 *.run
sudo sh ati-driver-installer-9-1-1-x86.x86_64.run

```

---

### Post by billyauhk on 2009-11-23
Thank you. Problem 1 is solved.

---

### Post by lisati on 2009-11-23
> **Woodbadger said:**
> I have to say that you're one step ahead of me. I can't even get Ubuntu 9.10 to load on my Toshiba Satellite M105. It tries, but it won't load. I don't know if it's the ATI graphics or some other problem. The processor is a Celeron M with 64 bit architecture capability. I've tried installing both 32 and 64 bit versions. I'm open to suggestions. And I'm a newbie, so if you have instructions, make them tediously detailed. Assume I know nothing.

I have one of the Toshiba M200 range. I tried loading 9.10 from a USB stick but didn't have any joy with the brief tests I did. 9.04 works fine on this machine.

---

