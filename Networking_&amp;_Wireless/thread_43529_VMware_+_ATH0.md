---
title: "VMware + ATH0"
date: 2005-06-22
forum: Networking &amp; Wireless
---

### Post by cwalshsml on 2005-06-22
Wireless is working using ATH0, ETH0 works....VMware is working but only bridging the eth0 adapter. 

Does anyone know how to make it so VMware will bridge off of the ATH0 adapter?

I truly hate wires.

christopher

---

### Post by Lunde on 2005-06-22
[QUOTE=cwalshsml]Wireless is working using ATH0, ETH0 works....VMware is working but only bridging the eth0 adapter. 

Does anyone know how to make it so VMware will bridge off of the ATH0 adapter?

I truly hate wires.

christopher[/QUOTE]

You can use Firestarter Firewall:

**$ sudo apt-get install firestarter**
**$ killall gnome-panel**

Your new firewall should apper in 

**Applications > System Tools > Firestarter**

After the easy configuration wizard, check:

**Edit > Preference > Firewall > Network Settigns > Enable Internet connection sharing**

and choose the **Detected Device** you want to bridge to in the dropdown list above

This is how I did it, hope it helps

---

### Post by Lunde on 2005-06-22
**Additional note:**
You can also use the NAT networking then it will work without any configuration. 

**Additional note2:**
I prefere to pass it throug a firewall and use the Host only network configuration in VMware. To make this work, I had to set the IP address to static in the Client OS and add the Host as default Gateway. Host only will generate a virtual network card named something like vmnet1 witch you have to bridge to form your firewall to make the wireless network available.

---

### Post by cwalshsml on 2005-06-22
[QUOTE=Lunde]You can use Firestarter Firewall:

**$ sudo apt-get install firestarter**
**$ killall gnome-panel**

Your new firewall should apper in 

**Applications > System Tools > Firestarter**

After the easy configuration wizard, check:

**Edit > Preference > Firewall > Network Settigns > Enable Internet connection sharing**

and choose the **Detected Device** you want to bridge to in the dropdown list above

This is how I did it, hope it helps[/QUOTE]


sorry...I am a very...very newbified....newbie.....who is sick of windows.

---

### Post by cwalshsml on 2005-06-22
WHat does it mean when I get the following everytime I do a sudo apt-get....

root@XENOS:/home/cwalsh # sudo apt-get install firestarter
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package firestarter
root@XENOS:/home/cwalsh #

sorry...I am a very...very newbified....newbie.....who is sick of windows.

I think this option may be best as I go from home to work....and don't wan't to worry about changing a static ip address on the guest XP system everytime I move from location to locatoin...

I would prefer to just use wireless.

---

### Post by Lunde on 2005-06-22
[QUOTE=cwalshsml]WHat does it mean when I get the following everytime I do a sudo apt-get....

root@XENOS:/home/cwalsh # sudo apt-get install firestarter
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package firestarter
root@XENOS:/home/cwalsh #

sorry...I am a very...very newbified....newbie.....who is sick of windows.

I think this option may be best as I go from home to work....and don't wan't to worry about changing a static ip address on the guest XP system everytime I move from location to locatoin...

I would prefer to just use wireless.[/QUOTE]

You need to add some extra repositories.

Have a look at this page:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Also lot of other great stuff on this page for you

Since you are new to Linux / Ubuntu, before messing around to much, it's nice to do a backup of your system. 
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

---

### Post by cwalshsml on 2005-06-22
Got the firestarter running....

Confused on ow to make it do what I want.

I have two interfaces defined on my laptop

1. ATH0 
2. Eth0

I want to only use the ATH0 wireless and bridge it's network connectivity to my vm hosts.

What do I need to do?

I have internet connection sharing through firestarter selected...

Help....almost there!!

---

### Post by Lunde on 2005-06-22
[QUOTE=cwalshsml]Got the firestarter running....

Confused on ow to make it do what I want.

I have two interfaces defined on my laptop

1. ATH0 
2. Eth0

I want to only use the ATH0 wireless and bridge it's network connectivity to my vm hosts.

What do I need to do?

I have internet connection sharing through firestarter selected...

Help....almost there!![/QUOTE]

First of all, have you set up networking in VMware? What type of network configuration did you choose? host only, Nat or Bridged

If you chose Bridged which is set as default in VMware then I guess you just have to do in firestarter is: 
Under Network settings, Internet Connected device = ATH0 and Local Network connected device = Eth0

If you chose host only, there should be a vmnet1 in your Local Network connected device

If you chose NAT, there is no need to anything in Firestarter.

---

