---
title: "HOWTO: RTL-8185 With Native Drivers &amp; WPA"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by ubuntme on 2008-04-28
Disclaimer: This how to is somewhat in progress.  I'm writing it because I spent some time getting this working on various distros, and finally succeeded some time ago.  A recent apt-get upgrade broke it, and I couldn't find any decent information to get it back up and running. It seems many have problems with this card which works perfectly well with native drivers and WPA.  Apologies if this isn't very noob friendly or complete, I just wanted the record the steps before I forget again!

So feel free to add comments and let me know if I have missed anything!

First, to know you have this device, the output of lspci should contain:
```
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```

1) Get the drivers:

I recommend getting the drivers from the realtek site:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")

There are also drivers available here:

[http://rtl-wifi.sourceforge.net/wiki/Main_Page]("http://rtl-wifi.sourceforge.net/wiki/Main_Page")

However, the realtek drivers are based on the rtl-wifi drivers anyway, and is IMO an easier option for several reasons; no need to play with subversion comes with useful instructions and scripts, and a version of wpa_supplicant that works with the drivers.

2) decompress the drivers.

Your version number might be different, mine looked like:

```
tar -zxvf rtl8185_linux_26\[1\].1027.0823.2007.tar.gz
```

Note to linux newbies, you rarely have to type the whole file name, if you type a few letters and press tab bash will figure the rest out for you, if it does, tabbing a couple of times will give the options of what it thinks the file names will be and you might need a few more letters.


3) compile the drivers 

Enter the directory you just extracted the file into.

```
 cd rtl8185_linux_26.1027.0823.2007/
```

Now follow the instructions contained in the readme file.  To view the file, open it in a text editor if that is easier for you, or:
```
cat readme 
```

Is a useful way to view files from a terminal, 

Following these instructions should get your card working.

Note, if the command 'make' can't be found, you will probably need to do:
```
 sudo apt-get install build-essential
```

4) Optional, For WPA users only: compile a version of wpa_supplicant specifically for this card

If you already have a version of WPA supplicant installed you  probably should remove it before compiling the version that comes with the code.  

```
 sudo apt-get remove wpasupplicant 
```

The standard version of wpa_suppliant doesn't seem to work, the commands inside the read me include a patch of sorts to get wpa_supplicant working with this card.

5) Automate the process to start on boot.

The scripts that come with the realtek drivers should get the card up and running but that isn't very convenient.

I used some of the instructions from this page:
[http://rtl-wifi.sourceforge.net/wiki/Installing]("http://rtl-wifi.sourceforge.net/wiki/Installing")

First I followed the "Removing mainline ieee80211 Stack". I would also do the same for any existing r8180.ko module if you have one.

e.g.
```
find /lib/modules/`uname -r` -name r8180.ko
```

Will find the above file, Then either delete that file using rm (or move it elsewhere with mv).

```
rm /path/to/file/r8180.ko 
```

Next, I used a modified version of the installing permanently section:

```
mkdir  /lib/modules/`uname -r`/kernel/net/ieee80211
cp ieee80211/*.ko  /lib/modules/`uname -r`/kernel/net/ieee80211
cp rtl8185/*.ko  /lib/modules/`uname -r`/kernel/net
depmod -ae

```

And finally, open /etc/network/interfaces with your favorite editor (e.g. nano):

```
sudo nano /etc/network/interfaces
```

And your wlan0 section should look something like this (note the version number may change for wpa-supplicant, its location is wherever you put it, same with the wpa_supplicant.conf file)

```
auto wlan0
iface wlan0 inet dhcp
pre-up /home/user/wpa_supplicant-0.4.9/wpa_supplicant -Bw -Dipw -i wlan0 -c /etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

A reboot here is probably the easiest way to get things working....

Then hopefully you should have a working wireless connection :-)

If something is not working, check to see if the following modules were loaded, using lsmod.

ieee80211_crypt-rtl
ieee80211_crypt_wep-rtl
ieee80211_crypt_tkip-rtl
ieee80211_crypt_ccmp-rtl
ieee80211-rtl
r8180

If any are missing, you could try modprobing them and restarting networking.

e.g. in my case, ieee80211_crypt_tkip-rtl was not loaded at boot, and is needed for my WPA connection.

so I fixed this by:
```
sudo modprobe ieee80211_crypt_tkip-rtl
sudo /etc/init.d/networking restart
```

as root.  Then to fix this permanently I added ieee80211_crypt_tkip-rtl to /etc/modules

```
sudo echo "ieee80211_crypt_tkip-rtl" >> /etc/modules
```

(this command simply appends the line "ieee80211_crypt_tkip-rtl" to the said file, you can also do this with an editor.)

And that worked for me.

Hope this helps somebody, and apologies for not being noob friendly I will fix it up later if I have the time and inclination....

---

### Post by Reg777 on 2008-04-28
if anyone is having problems with compiling the driver, you can try a patched driver by will daniels: [http://www.willdaniels.co.uk/blog/tech-stuff/1-tech-stuff/1-rtl8185-problems](http://www.willdaniels.co.uk/blog/tech-stuff/1-tech-stuff/1-rtl8185-problems)

and if your using the patched driver above and your getting "patch: unknown command" error during ./makedrv when following the readme manual, you may want to search for patch in synaptic package manager and install it

i had the same problem with rtl8185, ndiswrapper solutions did not work on my pc, but the patched driver worked and havent had any problems ever since :)

---

### Post by Master_Z on 2008-04-30
Can you simplify for me? I am a linux noob apparently. I downloaded the drivers, and then I dragged it out to the desktop. Now what?

---

### Post by amk29j on 2008-05-04
So I'm following the above directions but the directions in the README file for the drivers isn't perfectly clear on some things, especially getting WPA to work.  I understand that you have yet to write it in a clearer how-to, but anyway you can now?  It's been about a week since you posted this.

Thanks!

---

### Post by GonzalitoUY on 2008-05-13
I'm a rookie...how do you remove previous version od wpa suplliant?

---

### Post by ubuntme on 2008-05-18
> **amk29j said:**
> So I'm following the above directions but the directions in the README file for the drivers isn't perfectly clear on some things, especially getting WPA to work.  I understand that you have yet to write it in a clearer how-to, but anyway you can now?  It's been about a week since you posted this.


Sorry, I have been *very* busy.  If you are still interested, can you give me some details on what you were having problems with?

---

