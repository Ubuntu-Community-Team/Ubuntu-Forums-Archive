---
title: "Ethernet not working Ubuntu 14.04LTS"
date: 2015-01-24
forum: Networking &amp; Wireless
---

### Post by helloworld3 on 2015-01-24
My Ethernet just stopped working after I might have probably messed up with some of the settings.

I have a dual boot windows 8 and Ubuntu. Internet works fine on windows 8, and used for for ubuntu too.
But sometimes it did't.

so I did as instructed here.

[http://askubuntu.com/questions/6129/why-does-my-ethernet-port-sometimes-not-work](http://askubuntu.com/questions/6129/why-does-my-ethernet-port-sometimes-not-work)
 
and a few other links.

I am using a static IP provided by my institute and it's own DNS servers

My bash history is this:
Note: The sudo dhclient eht0 doesn't show anything in my case i had to terminate using ctrl+c everytime.

    sudo service network-manager stop
    sudo ifconfig eth0 up
    sudo dhclient eth0
    ubuntu-bug -p network-manager

    sudo nano /etc/udev/rules.d/70-persistent-net.rules
    sudo modprobe -r r8169 && sudo modprobe r8169
    sudo dhclient eth0
    ubuntu-bug -p linux
    sudo service network-manager start
    
    sudo lshw -C network
    sudo ifup eth0 
    ifconfig -a
    cat /etc/resolv.conf
    
    sudo service network-manager stop 
    sudo ifconfig eth0 up
    sudo dhclient eth0
    sudo service network-manager start


------------------------------------
After sometime I used these commands
------------------------------------


    sudo dhclient eth0
    sudo service network-manager stop
    sudo service network-manager start

    route -n
    nano /etc/resolv.conf
    sudo nano /etc/network/interfaces 
    ifconfig
    lspci |grep Ethernet
    sudo nano /etc/NetworkManager/NetworkManager.conf
    sudo nano /etc/network/interfaces
    lshw -C network
    rfkill list
    sudo ethtool eth0
    lsmod

------------------------------------------------------------------------
After searching everywhere and ethernet stopping now i used the following
-------------------------------------------------------------------------
    sudo modprobe -rfv 8139cp 8139too
    sudo modprobe -v 8139too
    sudo depmod -a 
    sudo update-initramfs -u

I didn't change any of the files I guess.
After I started today using my ethernet, I was 
 being shown two connections for the first time:Wired connection1 and  Auto Ethernet
I never saw Auto Ethernet before.

EDIT: Can anyone atleast suggest a  way to reset all network settings as if ubuntu was fresh installed.

---

### Post by ian77 on 2015-01-24
ubuntu should get its network config from:

/etc/network/interfaces

Can you paste the contents of that file here please?

Cheers

---

