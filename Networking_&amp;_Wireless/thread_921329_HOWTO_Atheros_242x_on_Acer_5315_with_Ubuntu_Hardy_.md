---
title: "HOWTO: Atheros 242x on Acer 5315 with Ubuntu Hardy Heron"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by ubuntista on 2008-09-16
First create some temporary directory like:

```
mkdir ~/tmp
cd ~/tmp
```

Download madwifi hal driver:
```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz
```

... and extract it:
```
tar zxvf [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)
```

Go into source directory:
```
cd madwifi-hal-0.10.5.6-r3861-20080903/
```

... and run:
```

make
sudo make install
sudo modprobe ath_pci

```


Enjoy!

---

### Post by gabsik on 2008-09-16
Great! It works on my acer aspire 5520 with 05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01),good !

---

### Post by hontalan on 2008-09-30
worked perfect.

i had to do this first though:
sudo apt-get install build-essential


...and shouldnt tar zxvf [http://snapshots.madwifi.org/madwifi...current.tar.gz](http://snapshots.madwifi.org/madwifi...current.tar.gz) be just without the http? thats how i did it anyway....

---

### Post by Freakshowpb on 2008-10-15
i got this to work for about a week

 now it crapped out on me (the drivers are still there its just the card doesnt pick anything up anymore or wont turn on)

---

### Post by waldoian on 2009-01-31
Because I searched for well over a month on how to do just this, I'll add some updates.

This also works for the Dell Vostro A860 (and probably A840) so hopefully this thread will popup for those searching for something other than Acer.

The URLs in the HOWTO are dead, dead, dead.  Bad admins for the madwifi project, bad, bad admins ;)  It appears they've done some major cleanup and organization on their site(s), but they've left a ton of dead URLs around that don't redirect to the proper places or even at least a page explaining what the heck is going on.

**Updated HOWTO:**
```

mkdir ~/tmp
cd ~/tmp
```

Download madwifi hal driver.  I used the one dated 30-Jan-2009 and it worked great.  Go here to get a current version URL (as they appear to have gotten rid of the "current" build)
[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/), then (using the 30-Jan-2009 file as an example:
```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3938-20090130.tar.gz
```

... and extract it:
```
tar zxvf madwifi-hal-0.10.5.6-r3938-20090130.tar.gz
```

Go into source directory:
```
cd madwifi-hal-0.10.5.6-r3938-20090130/
```

... and run:
```
make
sudo make install
sudo modprobe ath_pci
```

**sudo modprobe ath_pci** didn't seem to do anything for me on the Vostro A860, I had to actually reboot the computer for the wireless to work.  Good news is that the wireless is automatically working on any reboot and you don't have do anything special as I've seen on other HOWTOs.

---

