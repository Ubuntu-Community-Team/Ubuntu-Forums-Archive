---
title: "wireless help"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by PeB0 on 2008-06-20
i need help getting wireless to work with my compaq nc6120 

WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:78:e0:6a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off

---

### Post by chili555 on 2008-06-20
> wireless=radio off There is a wireless switch or key combination on your laptop that turns the wireless card on or off. It's off. Please turn it on.

---

### Post by PeB0 on 2008-06-20
there is a switch on the laptop but when i press it nothing it still says the same thing

---

### Post by chili555 on 2008-06-20
I was reading this: [http://www.thinkwiki.org/wiki/Ipw2200](http://www.thinkwiki.org/wiki/Ipw2200)

Let's try, first:```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 disable=0
```Now, when you run *sudo lshw -C network,* does *radio=off* disappear? Can you now connect wirelessly?

If not, please try:```
sudo su
echo 0 > /sys/bus/pci/drivers/ipw2200/*/rf_kill
```Can you now connect?

Whatever works I think we can make permanent.

---

### Post by PeB0 on 2008-06-20
well i tried both of them and none of them seemed to work because it still says
wireless=radio off

---

### Post by chili555 on 2008-06-20
Is there any setting in the computer's BIOS to enable/disable wireless or enable/disable the switch?

---

### Post by PeB0 on 2008-06-20
i have no clue

---

### Post by chili555 on 2008-06-20
Here is something else to try. ```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 led=1
```Now press the wireless switch. Does the LED work and does *sudo lshw -C network* clear up?

Also see this: [http://ubuntuforums.org/archive/index.php/t-191492.html](http://ubuntuforums.org/archive/index.php/t-191492.html) Especially, check this:> I had the same problem in my HP nc6120 laptop. Now it's fixed.

I did install multiple drivers (related to WiFi) from Compaq site on my Windows, after that my wireless key become working even in Linux and after reboot. This key is located on the right side after Power button and "i" button (on this model). Now pressing that key turns on and off a blue LED. Bluetooth become On. But WiFi Kill switch still was ON (even when you this blue LED was lighting).

Now I read that in this laptop we have restricted ethernet controller, that works only with EITHER 100-base-T OR with WiFi, but not simultaneously.

So, to get WiFi working you should pull out your ethernet cable. It seems to be that magic 'Kill Switch'. And also you should press WiFi button (the light is On).

---

### Post by PeB0 on 2008-06-20
well i read tried and nothin but thanx for your anyways friend i guess il just have to switch to windows if i wanna go wireless

---

