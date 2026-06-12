---
title: "MadWifi Help needed."
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by Niskyspy on 2007-06-17
I am trying to install MadWifi drivers for my Netgear WG511T card but am stuck on step two.

From MadWifi website (Installation section)
"Assuming that you're inside the MadWifi directory, execute the following scripts to remove the current modules from your system and its memory:"

CODE:
cd scripts
./madwifi-unload.bash
./find-madwifi-modules.sh $(uname -r)
cd ..


How do I do this step. When I try to run the script in the Terminal all I get is the following:
CODE:
niskyspy@Niskylaptop:~$ cd scripts
bash: cd: scripts: No such file or directory
niskyspy@Niskylaptop:~$ su
Password: 
root@Niskylaptop:/home/niskyspy# cd scripts
bash: cd: scripts: No such file or directory
root@Niskylaptop:/home/niskyspy# 

Can someone please either explain what I am doing wrong or link me to an easier to follow instructions.

Thank you very much

---

### Post by PaulFr on 2007-06-17
Maybe you are not in the directory where you extracted the MadWifi software ?

---

### Post by Niskyspy on 2007-06-17
Wow, I am such a noob at this.
Started to read "Linux for noob's" and figured out that problem.

This is how CD works, write CD then show how to get to the directory that you are looking for.

niskyspy@Niskylaptop:~$ cd /home/niskyspy/Desktop/madwifi/scripts
niskyspy@Niskylaptop:~/Desktop/madwifi/scripts$ ./madwifi-unload.bash
FATAL: Module wlan_scan_sta is in use.
FATAL: Module wlan is in use.
niskyspy@Niskylaptop:~/Desktop/madwifi/scripts$ 

Now as u see I have another problem, I have FATAL errors for some unknown reason.
I did ifconfig ath0 down, ifconfig wifi0 down to both of my wireless cards and even disabled the wireless network,  but I still getting this damn error can anyone tell me what i should do.

Thank you

---

### Post by guix on 2007-06-18
Hi,

Are you sure you need to install madwifi by yourself ?
They are included in the restricted linux drivers in Ubuntu.
They may already be installed, please show us the output of :
```
lsmod |grep ath
```

---

### Post by tturrisi on 2007-06-18
2 ways to get rid of (uninstall) the existing madwifi:
- if using restricted-modules madwifi then remove via Synaptic.
- i if you previopusly buily madwifi, use the madwifi removal script
...but PRIOR to doing either of the above, you should bring down the interface & unload the modules by:

ifconfig ath0 down
ifconfig wifi0 down
rmmod wlan_wep ath_rate_sample ath_rate_onoe ath_pci wlan ath_hal ath_rate_amrr 2>/dev/null

...then install the latest madwifi & patch them so works w/ aircrack-ng:
```
apt-get install subversion
cd /usr/src
svn checkout http://svn.madwifi.org/trunk/ madwifi-ng
wget http://patches.aircrack-ng.org/madwifi-ng-r2277.patch
cd madwifi-ng
patch -Np1 -i ../madwifi-ng-r2277.patch
make
make install
depmod -ae
modprobe ath_pci
```

---

