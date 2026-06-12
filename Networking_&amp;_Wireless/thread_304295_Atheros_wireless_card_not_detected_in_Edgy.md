---
title: "Atheros wireless card not detected in Edgy"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by OrganicPanda on 2006-11-21
Hey All, I've seen a few threads with lots of info about the current Edgy/Athoros problems but I thought I would post anyway to see if there's any hope for me.

Anyway during edgy install it sees my 3 network interfaces (eth, wifi0 and ath0) but it can't configure or connect to the network, anyway after finishing the install and booting up for the first time I do a 'iwconfig' and there is no sign of wifi0 or ath0, a 'lspci' shows that I have:

```
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

The network card worked (not as good as in windows but still worked) in dapper (with madwifi) so I just assumed it would work in edgy. Is there anything I can do or will I need to downgrade to Dapper?

Thanks,
Panda

---

### Post by FrodoB on 2006-11-21
Unless you are installing from the Alternative CD is should just work out of the box.

---

### Post by trubblemaker on 2006-11-21
yeah I had similar issue with my server.  you didn't pick aethos as your primary interface did you?  So I guess the default is to not add that module to boot on startup.  If you've already been on threads than you can probably **figure out what the kernel module atheros** is and **modprobe it **and then see if it magically appears.  if that works **add it to "/etc/modules", **also make sure that there is a **entry for it in your /etc/network/interfaces** file so that it automatically "comes up"/get's ip on boot.

---

### Post by OrganicPanda on 2006-11-21
I had to install from the alternate cd in text mode because the live cd installer kept crashing my laptop, I take it this is a problem?

@trubblemaker: I chose ath0 as my default interface during install but it failed to connect to my wireless network so I chose the "configure networking after install" (or the option that skips setting up the network, I can't remember the exact text). I have read other threads but I still have no idea what you are asking me to do with "figure out what the kernel module atheros is"

thanks for the replies so far :)

---

### Post by FrodoB on 2006-11-21
If you can get this machine temporarily on the net then it should be easy:

You need the linux-restricted-modules for your kernel. These are not installed in the alternative CD install, but they are available through apt-get if you are on the internet.

Here is the apt-get command: (just cut and paste the commands if desired)
$ sudo apt-get update
$ sudo apt-get install linux-restricted-modules-`uname -r`

After installing these and a reboot ath0 should appear.

---

### Post by trubblemaker on 2006-11-21
I dialed into my server with ath0 and it in my source directory as I installed from[ source ]("http://madwifi.org/wiki/Releases") which is a good next step if this doesn't work.  you can try 
```
 modprobe ath
 modprobe ath_hal
 modprobe ath_rate

```
then see if wireless comes up... ie do the other stuff in the post below.  I didn't do it this way but hey it might work for you!

---

### Post by FrodoB on 2006-11-21
If you can get this machine temporarily on the net then it should be easy:

You need the linux-restricted-modules for your kernel. These are not installed in the alternative CD install, but they are available through apt-get if you are on the internet.

Edit the /etc/apt/sources.list file and uncomment these lines:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

Use this command to edit the file:

$ sudo gedit /etc/apt/sources.list

Save the file.

Here is the apt-get command: (just cut and paste the commands if desired)
$ sudo apt-get update
$ sudo apt-get install linux-restricted-modules-`uname -r`

After installing these and a reboot ath0 should appear.

---

### Post by OrganicPanda on 2006-11-21
Thanks for the replies guys, I'm having to do a reinstall because I cocked something up and now it wont boot but I will try these suggestions as soon as and get back to you.

On an unrelated note, It's pretty annoying that my laptop with 256mb of memory can't handle the regular GUI installer for edgy, ahh well, thanks again.

EDIT: @FrodoB - Did you mean to post that twice? lol

---

### Post by FrodoB on 2006-11-21
Yes, I forget to add the part about modifying sources.list, so I just posted the whole thing together.

---

### Post by trubblemaker on 2006-11-21
wait, don't re-install most days it can be fixed with dsl-live-cd and some work..... if you need to keep your data.  but if you don't hell freshinstalls rule, and I have run egdy with 256MB of ram so don't worry.  You might not want to use beryl but it's all good.

---

### Post by OrganicPanda on 2006-11-21
Right the reinstall is done (I had no data to save anyway).

I added those entries to my sources.list, did an update, installed the restricted modules and sure enough under iwconfig there was an entry for ath0:

```

panda@panda-buntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

But when I go into System-Administration-Networking and enable the device it does nothing, it just completely ignores me and as soon as I press 'ok' it sets itself back to not configured.

I also tried the other instructions with limited success, look:

```

panda@panda-buntu:~$ modprobe ath
FATAL: Module ath not found.
panda@panda-buntu:~$ modprobe ath_hal
panda@panda-buntu:~$ modprobe ath_rate
FATAL: Module ath_rate not found.
panda@panda-buntu:~$ 

```

Any Ideas?

---

### Post by FrodoB on 2006-11-21
For starters just put your access point on WEP with open authentication and put something like this in your /etc/network/interfaces file:

iface ath0 inet dhcp
wireless-essid My_ESSID
wireless-key xxxxxxxxxxxxxxxxxxxxxxx
auto ath0

This example uses 128 bit wep. Fix the key and ESSID name to match yours. For 128bit wep the key would look like this:

s:xxxxxxxxxxxxx

rather than just 26 Xs. 

Then try:

sudo ifdown ath0

sudo ifup ath0

report what you get.

---

### Post by OrganicPanda on 2006-11-21
Wow it worked, thank you so much for your time and knowledge :) :) 

1 question, will it work on startup?

---

### Post by FrodoB on 2006-11-21
With Atheros the answer is usually yes. 

You may need to select the device in System -> Administration -> Networking.

---

### Post by trubblemaker on 2006-11-22
nice work FrodoB

---

### Post by FrodoB on 2006-11-22
Here is the procedure for installing the restricted modules withoout an internet connection:


1) Have the Alternate CD ready for use.

2) Open a terminal command prompt and type the following:

$ sudo apt-get install linux-restricted-modules-`uname -r`

The system should present a prompt asking you to insert the install CD, put it in the CD driver that you used for installation and then press enter. Apt will find the .deb archives and install them for you. A reboot should result in a system that now sees the cards that worked during the install.

---

### Post by OrganicPanda on 2006-11-23
Cool, thank you for all of your help, I'll remember this for next time :)

---

