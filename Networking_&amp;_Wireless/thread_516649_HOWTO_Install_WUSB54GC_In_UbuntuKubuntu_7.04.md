---
title: "HOWTO Install WUSB54GC In Ubuntu/Kubuntu 7.04"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by hendricks on 2007-08-03
[COLOR="DarkRed"]EDIT: I'm trying to switch the drivers from ndiswrapper to SerialMonkey. I HIGHLY recommend trying the SerialMonkey drivers. They seem much better, but I haven't done very much testing in other configurations besides my own (Kubuntu Gutsy 64 bit). If you are interested, see the post on page 12 of this thread.[/COLOR]

Hey guys. I've made a script that can do this very easily. It uses ndiswrapper to install for 32bit or 64bt Ubuntu or Kubuntu. If there are any problems, please let me know and I'll fix them immediately.  You can get the script from here: (its about 7 megs now, but let me know if you get an error about libc6, which is what I took out...)

Fresh Fesity Install: [Feisty wusb54gc.tar.gz]("http://www.fileden.com/files/2007/7/27/1301349/Feisty/wusb54gc.tar.gz")
Fresh Gutsy Install: [Gutsy wusb54gc.tar.gz]("http://www.fileden.com/files/2007/7/27/1301349/Gutsy/wusb54gc.tar.gz")

Extract the directory somewhere, then cd into it.

```
cd wusb54gc
```

Then just run the script by typing

```
sudo ./wireless
```

And then the fun begins. It'll install the dependencies, compile ndiswrapper, install the rt73 system files, modprobe ndiswrapper, and blacklist the crappy drivers ubuntu thought would work when we installed. Worked for me.

Reboot.

Now, if you're using KDE (**Kubuntu** users), it will install **Wireless Assistant**, which is the easiest way to get the internet working after you reboot. Just go to KDE->Internet->Wireless Assistant, or type

```
sudo wlassistant
```

Put in your info and you should be good to go. Otherwise, you may need to put in your info manually.

If you're using Gnome (**Ubuntu** users), it has a great thing called **Network Manager**, which is an applet that runs usually when you startup.  Just use that.  Otherwise, you may have to put it in manually.

For those of you who have to put it in manually, here is an example of what mine looks like:
```
dhclient -r wlan0
ifconfig wlan0 up
iwconfig wlan0 mode managed channel 6 key open 3214567890 essid MyNetwork
iwconfig wlan0 ap 00:15:E9:65:E3:F6
dhclient -q wlan0
```

Something like that atleast.  Thats it! Let me know how it goes guys. This will work with default installations of Ubuntu/Kubuntu, or atleast it did for me ;-)

  --Hendricks

---

### Post by wdetmar on 2007-08-04
It works really well.

I've been fighting this for a few days now. I replaced my old PCI card (after getting nowhere with manually configuring ndiswrapper) with the Linksys WUSB54GC and I still couldn't get it to work until I found your script.

You may want to see if your fix can be linked to from this page:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53)

or maybe here....

[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC)

This second link had some detailed instructions but your script made it very easy.

Take care, and thanks :)

---

### Post by sebbouckaert on 2007-08-05
I just wanted to thank you for this script! After 2 days of trying every possible method of installing a wusb54gc card on my wife's desktop without succes your script did it in 5 minutes! wow! :KS

---

### Post by LorisB on 2007-08-06
I am very interested by this script, but before puting my hands on it, can you confirm that this script make the device work with WPA encryption ?

thanks

---

### Post by njdfan1241 on 2007-08-06
I can vouch that this works well :)

---

### Post by hendricks on 2007-08-06
> I am very interested by this script, but before puting my hands on it, can you confirm that this script make the device work with WPA encryption ?

I'm not sure. Does anybody else know how well ndiswrapper works with WPA?
I guess i'll set my router to WPA and give it a shot and let you know how it goes.

--Hendricks

---

### Post by hendricks on 2007-08-06
> 
[QUOTE]I am very interested by this script, but before puting my hands on it, can you confirm that this script make the device work with WPA encryption ?
I'm not sure. Does anybody else know how well ndiswrapper works with WPA?
I guess i'll set my router to WPA and give it a shot and let you know how it goes.[/QUOTE]

Good news Loris, I just booted into 64bit Ubuntu and 32bit Kubuntu and it worked in both. However, if you're using Kubuntu, I could not get it to work with the wireless assistant, but I used KNetworkManager, which is the KDE equivalent to networkmanager in gnome, and it worked there (can't get knetworkmanager to work with wep though for some reason, which is why I suggest you use wireless assistant).

--Hendricks

---

### Post by Hyssar on 2007-08-07
It didn't work for me.
I am using Kubuntu 7.04 64-bit.

Here is the result of sudo ./wireless the second time I ran it. First time, I was sure it would work correctly so I didn't think about saving it...

```
hyssar@hyssar-desktop:~/Desktop/wusb54gc$ sudo ./wireless
Ndiswrapper is up to date. Skipping installation.
Installing wlassistant...
dpkg : erreur de traitement de wlassistant_0.5.5_0ubuntu5_amd64.deb (--install) :
 ne peut pas accéder à l'archive: Aucun fichier ou répertoire de ce type
Des erreurs ont été rencontrées pendant l'exécution :
 wlassistant_0.5.5_0ubuntu5_amd64.deb
RT73 driver already installed with ndiswrapper. Skipping install.
Ndiswrapper already added to modprobe.
Ndiswrapper already added to modules list.
rt2x00lib already blacklisted
rt73usb already blacklisted
Cleaning up files
Done

```

Because my system is using French I must translate a little bit :

erreur de traitement de wlassistant_0.5.5_0ubuntu5_amd64.deb (--install) :
 ne peut pas accéder à l'archive: Aucun fichier ou répertoire de ce type
Des erreurs ont été rencontrées pendant l'exécution :

Means :
Errors in processing wlassistant [...]
can not access the archive : No file or directory of this type
Some errors occured during execution :

Why has it happened ?
lsusb :

```
Bus 005 Device 002: ID 13b1:0020 Linksys
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

Since I installed Kubuntu, my WUSB54GC has always been recognized by KNetworkManager but it is not anymore, now...
Also, it worked once, the day I installed Kubuntu but it crashed after 10 min of use.

I must also specify that the driver rt73.inf was already installed but I didn't succeed in making it work.

Thanks!

---

### Post by hendricks on 2007-08-07
Hyssar,
  It looks like I've made a typo in the script for the 64bit wireless assistant. Sorry about that. You can install it manually by extracting the file "compressed_files.tar.gz", navigating to the folder called 64bit, and installing the file called "wlassistant_0.5.5-0ubuntu5_amd64.deb" (see the hyphen instead of the underscore?? oops :oops:)

However, it doesn't look like this is your only problem. Maybe this is because you tried to install it before? Let me know what you get from these commands:
```
ndiswrapper -v
ndiswrapper -l
modprobe -l | grep ndiswrapper
```

Try removing any drivers installed with ndiswrapper (from "ndiswrapper -l"). Most likely, you'll need to type this:
```
ndiswrapper -r rt73
```

And then re-run the script (ignore the error about wlassistant for now if you still get it).

Anyway, i'll be updating the script now. Also, I think I may remove libc6 from the included deb files since it takes up about 10 megs (total for 32 and 64 bit) as it *should* come installed on your system by default. (i'll verify this later today)

---

### Post by killphil on 2007-08-07
I got my Linksys card to work with by following this.
[http://wiki.archlinux.org/index.php/RT73_Wireless](http://wiki.archlinux.org/index.php/RT73_Wireless)
but I'm using debian on this particular machine.  I also can't get it to run on startup.  I'm actually about to post to see if I can find a solution.  Basically the no roaming setup at the end of the instructions didn't work.  Nice thing is no ndiswrapper.

---

### Post by Hyssar on 2007-08-07
I removed ndiswrapper after the last try then, when I saw your post I reinstalled it

 ndiswrapper -l
nothing appears

 ndiswrapper-v
utils version '1.9' utils version needed by module : '1.9'
filename : /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version : 1.47
vermagic : 2.6.20-16-generic SMP mod_unload

 modprobe -l | grep ndiswrapper
/lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko


When it will work, I will need to repeat the operations every kernel update?
Should I reinstall Kubuntu to have a clean system to restart from the beginning? ( And the WUSB54GC should even work automatically for some time, time to download your application and start using it!)

---

### Post by hendricks on 2007-08-07
Hyssar,
  Did you re-run the script? With the command "ndiswrapper -l", it should be showing that the rt73 driver is installed after you've run the script. Maybe you have an old version of ndiswrapper still installed somewhere that is conflicting? Try running
```
sudo dpkg -r ndiswrapper-utils-1.9
sudo dpkg -r ndiswrapper-common
```
If anything was removed, re-run the script. I've uploaded a new version so please download the new version (link updated in first post).  If you still don't get anything from "ndiswrapper -l", then we've got a problem. You can manually install rt73 driver by doing this after unzipping the "compressed_files.tar.gz" file:

```
cd 64bit
sudo ndiswrapper -i rt73.inf
```

> When it will work, I will need to repeat the operations every kernel update?
As far as I know, you should not, but I am not an expert on ndiswrapper.

> Should I reinstall Kubuntu to have a clean system to restart from the beginning?
I wouldn't reinstall kubuntu just yet. You can if you want. I'm going to do some more testing since it should work for default installations of ubuntu/kubuntu (just tested it out on 64bit ubuntu and 32bit kubuntu a couple of hours ago, and I'm running 64bit kubuntu right now, but I haven't tested it from a clean install of 64 bit kubuntu yet, which I'm about to do later today).

One last thing, try using Wireless Assistant once it is installed. KNetworkManager doesn't always work for me. I usually have better success with wlassistant.

--Hendricks

---

### Post by Hyssar on 2007-08-07
I'm really new to Linux and I dont exactly know how to install .deb packages.

Also, I've been doing some 'manipulations' to understand how the installation of programs work so, my ndiuswrapper, KNetwork and drivers are maybe corrupted. I will reinstall everything tomorrow.
Then, I will restart all the operations from the beginning with your new download.

Thanks a lot,

Hyssar

---

### Post by Hyssar on 2007-08-08
Everything is reinstalled.

Could you please make an other post with a new tutorial for 64-bit users?

Thank you!

---

### Post by Hyssar on 2007-08-08
It worked!

I reinstalled Kubuntu then,

1- I ran wireless
2- Reboot
3- sudo apt-get install wlassistant_0.5.5-0ubuntu5_amd64.deb

It takes some time to Konqueror to realize that it is connected to the Internet

THANKS!!!!!!!!!!!!1 :)

---

### Post by CorneliusBear on 2007-08-15
Hi hendricks,

I'm trying to run your script on Ubuntu 7.04, which was upgraded first from Dapper to Edgy, and then from Edgy to Feisty.  I made no drastic modifications, and am running the provided kernel from Feisty.  But when I try to run ```
sudo ./wireless
```  I get the following output:

(this occurs while the script is attempting to compile the ndiswrapper.  Everything seems to succeed until the lines below:)

```
make -C driver
make[1]: Entering directory `/home/noop/wusb54gc/ndiswrapper-1.47/driver'
Can't find kernel build files in /lib/modules/2.6.20-16-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/noop/wusb54gc/ndiswrapper-1.47/driver'
make: *** [all] Error 2
make -C driver install
make[1]: Entering directory `/home/noop/wusb54gc/ndiswrapper-1.47/driver'
Can't find kernel build files in /lib/modules/2.6.20-16-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/noop/wusb54gc/ndiswrapper-1.47/driver'
make: *** [install] Error 2
./wireless: line 59: ndiswrapper: command not found
./wireless: line 60: ndiswrapper: command not found

```

It seems to be saying that make can't find kernel modules for the kernel I'm running.  The kernel was installed when I performed the dist-upgrade via Adept (KDE equivalent of update-manager).  Any idea what the appropriate build path would be?  Is there some other package I need to install before running the script?  Has anyone else encountered this problem?

Thanks for any help you can provide,

CB

---

### Post by hendricks on 2007-08-15
> It seems to be saying that make can't find kernel modules for the kernel I'm running. The kernel was installed when I performed the dist-upgrade via Adept (KDE equivalent of update-manager). Any idea what the appropriate build path would be? Is there some other package I need to install before running the script? Has anyone else encountered this problem?

In Adept, make sure the kernel headers are installed (search for linux-headers and select the one matching your installed kernel version). I've got **linux-headers-2.6.20-16** and **linux-headers-2.6.20-16-generic** installed, along with **linux-headers-generic**.

Also, it probably wouldn't hurt to have the build-essential package, although its not required.  If you don't have an internet connection on your system, you can download the files to another computer and transfer them to a USB stick from this site:

[**http://packages.ubuntu.com/feisty/devel/**]("http://packages.ubuntu.com/feisty/devel/")

Hopefully that should do it. Ndiswrapper needs the kernel source to install. It looks like the headers didn't get installed when you upgraded your kernel.

--Hendricks

---

### Post by CorneliusBear on 2007-08-15
Hi Hendricks,

I've already got **linux-headers-generic, linux-headers-2.6.20-16-generic** and **linux-headers-2.6.20-16** installed.  However, they all install files underneath /usr/src/linux, which is not where the ndiswrapper makefile is looking for them.  It complains:

```
make -C driver
make[1]: Entering directory `/home/noop/wusb54gc/ndiswrapper-1.47/driver'
Can't find kernel build files in /lib/modules/2.6.20-16-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
```

so if it's looking for the kernel headers (is that the same thing as kernel build files?), then should I add KBUILD=/usr/src/linux to the makefile.  But no one else seems to have had this problem, so I'm super confused :)  Can you think of anything else?

Thanks,

CB.

---

### Post by CorneliusBear on 2007-08-15
Hey Hendricks & All,

It compiles now.  Though I had all three packages you reccomended, I didn't have  **linux-headers-2.6.20-386** installed, which did the trick.  Thanks for all you help!

CB

---

### Post by solarhexagon on 2007-08-15
THIS IS NOT WORKING FOR ME! ](*,)](*,)](*,)](*,)](*,)](*,)](*,):sad: OK sorry, I just need better instructions. What does "cd into it" mean?

---

### Post by hendricks on 2007-08-15
Open up the terminal, and go to the directory where you extracted the files. For instance, if they were extracted to your desktop, you would type:

```
cd ~/Desktop/wusb54gc
```

Then run the code.

--Hendricks

---

### Post by CorneliusBear on 2007-08-16
Hi again Hendricks,

While your script does a good job of installing ndiswrapper, and the module loads fine, I can't connect to my network (WPA encrypted) using KNetworkManager.  In your previous post where you said that you got the card to work with WPA, did you follow the exact steps you took in [https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC?](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC?)

Thanks,

CB

---

### Post by hendricks on 2007-08-16
> While your script does a good job of installing ndiswrapper, and the module loads fine, I can't connect to my network (WPA encrypted) using KNetworkManager. In your previous post where you said that you got the card to work with WPA, did you follow the exact steps you took in [https://help.ubuntu.com/community/Wi...nksysWUSB54GC?](https://help.ubuntu.com/community/Wi...nksysWUSB54GC?)

I actually didn't have to change anything at all. It worked right away. I just had to right click on the knetworkmanager icon, select my network, put in the passcode, and it connected. My guess is that you can follow those instructions in your link to do it manually if its not working for you, or try searching the forums some more from other people using ndiswrapper and wpa.  Sorry I can't be more help. If you get it working, please post how here.

--Hendricks

---

### Post by CorneliusBear on 2007-08-19
Hi again,

O.k, I've managed to get the device working.  I removed NetworkManager, as that didn't seem to be working for me.  Then I followed the advice in this thread: [http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa_supplicant+feisty]("http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa_supplicant+feisty")

specifically in the first post.  My network has ESSID hidded and uses WPA(1).

I installed the ndiswrapper driver via the script by Hendricks (thanks man, it worked really well for me!)  I also have wpasupplicant installed as well as wireless-tools.  Here's the /etc/network/interfaces I'm using:

```
noop@SargentPepper:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid myssid
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk mywpahexkey

```

You can generate a hex key for your network & ssid by following the instructions in the post I quote above.  I also found that the wpasupplicant package did not install a config file (/etc/wpa_supplicant/wpa_supplicant.conf) by default, so I installed the following.  Much of the configuration is the same as in /etc/network/interfaces, and I'm not sure that it's required, but I have one and it seems to work..  Here's the /etc/wpa_supplicant/wpa_supplicant.conf:

```
noop@SargentPepper:~$ cat /etc/wpa_supplicant/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
#ctrl_interface_group=0

#ap_scan=1

network={
        ssid="myssid"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        group=TKIP
        pairwise=TKIP
        psk="myhexkey"
}

```

Hope this helps someone.  Hendricks, thanks again for your support.

CB

---

### Post by pmryan on 2007-08-19
:) Thank you! 
The script worked perfect.
I downloaded to a USB drive. (I had to switch my "save as" to ALL FILES because I also use WinZip)
Uploaded to my pc running Ubuntu Fiesty Fawn 7.04.
Plugged in the WUSB54GC.
Ran the script and then rebooted.
I clicked on the network and was off and running.
Great job!

---

### Post by ZundappBella on 2007-08-19
OK I'm trying to get this to work on a friends laptop and I ran the script, but running wireless asistant it comes up with "no useable wireless devices found. Wireless assistant will now quit"

Rerunning the script gives this

Ndiswrapper is up to date. Skipping installation.
Wlassistant is installed. Skipping installation.
RT73 driver already installed with ndiswrapper. Skipping install.
Ndiswrapper already added to modprobe.
Ndiswrapper already added to modules list.
rt2x00lib already blacklisted
rt73usb already blacklisted
Cleaning up files
Done
 
lsusb gives me

Bus 001 Device 004: ID 0781:5406 SanDisk Corp.
Bus 001 Device 003: ID 13b1:0020 Linksys
Bus 001 Device 001: ID 0000:0000

ndiswrapper -l gives

rt73 : driver installed
device (13B1:0020) present (alternate driver: rt73usb)

modprobe -l | grep ndiswrapper gives

/lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko


 and ndiswrapper -v gives

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-15-generic SMP mod_unload 586


I think I'm close, but just not quite there. Any suggestions?

btw this is a new kubuntu install, never updated or anything installed. All done by a noob (me)

---

### Post by hendricks on 2007-08-20
ZundappBella,

 What do you get from these three commands?

```
iwconfig
ifconfig
cat /etc/iftab
```

--Hendricks

---

### Post by ZundappBella on 2007-08-20
Hi Hendricks,

Thanks for replying, I'll post the replies on Thursday evening sometime, the computer
is at work and I'm off for a couple

Thanks again,
Bill

---

### Post by hercegnovi on 2007-08-21
The installation script worked for me, but when I reboot the computer, I am not connected to the router any longer. Is it possible for settings to be saved, so I do not have to reconnect to the router each time I reboot the computer?

---

### Post by hendricks on 2007-08-21
> The installation script worked for me, but when I reboot the computer, I am not connected to the router any longer. Is it possible for settings to be saved, so I do not have to reconnect to the router each time I reboot the computer?

Thats a good question. I've been trying to figure this one out for some time. The problem is that you need super user rights to configure the network. These rights are available during bootup of the os (adding scripts to rc.s), but I have never been able to get the network configured that early in the boot processes even if its the last thing to run before loading the window manager. It seems like I always have to wait until after I am logged into KDE, at which point there are no more super user rights available without having to re-type in the password. I'll try and look into it some more. If anybody figures it out, please post.

--Hendricks

---

### Post by ZundappBella on 2007-08-22
> **hendricks said:**
> ZundappBella,

 What do you get from these three commands?

```
iwconfig
ifconfig
cat /etc/iftab
```

--Hendricks


Hey Hendricks, here's what I get

dave@Dave:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
---------------------------------------------------------------------------------------------------------
dave@Dave:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:02:4B:3F:66
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:59040 (57.6 KiB)  TX bytes:59040 (57.6 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:18:F8:2C:6B:99
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

----------------------------------------------------------------------------------------------------------
dave@Dave:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:08:02:4b:3f:66 arp 1

---

### Post by hendricks on 2007-08-23
Dave,

From what you've posted, it looks like your system is missing wlan0 from iftab. First, confirm what your MAC address is for the usb stick, it should say it on the back of it (it looks like yours is 00:18:F8:2C:6B:99 from ifconfig). I'll assume that this is your MAC address. Then type this in the Terminal:

```
sudo bash
echo -e "\nwlan0 mac 00:18:f8:2c:6b:99 arp 1" >> /etc/iftab
```

Reboot

Hopefully thats it. Let me know if its still not working and I'll take a closer look at your output.

--Hendricks

---

### Post by fluteflute on 2007-08-23
Thanks for making the script. My WUSB54GC is working using non ndiswrapper methods anyway but I'll bookmark this page incase I need it!

---

### Post by hendricks on 2007-08-27
> Thanks for making the script. My WUSB54GC is working using non ndiswrapper methods anyway but I'll bookmark this page incase I need it!

Your welcome! I made the script for myself and realized (from all the forum threads about this card) that other people may need it also.

On another note, I've figured out how to automatically connect to your network when you log in. The solution is probably not what most people are looking for though. It involves making your own script (probably be easiest to just use mine and fill in your network connection info) and then making a desktop file in the autorun directory (either for gnome or kde) that runs the script with root privileges using

```
echo "my password" | sudo -S /home/hendricks/directory_to_script/./wireless_startup
```

Something like that at least. Anyway, if anybody wants more detailed instructions, let me know and I'll be happy to post them. But again, the drawback is that you will have to have a script to connect to the internet instead of using NetworkManager (for gnome) or Wireless Assistant (for kde).  If you're running kde, the solution is very easy because you can get the commands from simply running wireless assistant from the command line and making note of what commands it runs to connect to your network.

--Hendricks

---

### Post by grantwfuller on 2007-08-30
I have this problem also but I have installed the rt73 driver using ndiswrapper (the Windows driver came from the installation CD) I have Ubuntu 7.04 newly installed and the iwconfig command gives me the "not associated" result' Here is what I get from ifconfig:

-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:21:D1:16:F8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12928 (12.6 KiB)  TX bytes:12928 (12.6 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:1A:70:3A:59:E2  
          inet6 addr: fe80::21a:70ff:fe3a:59e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:35146 (34.3 KiB)

wlan0:ava Link encap:Ethernet  HWaddr 00:1A:70:3A:59:E2  
          inet addr:169.254.7.119  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-70-3A-59-E2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
[I]
I have blacklisted the native driver[/I] 
Any help would be appreciated

---

### Post by grantwfuller on 2007-08-31
I followed the instructions carefully but still can't get connected. The final attempt when trying
 ```
sudo bash
echo -e "\nwlan0 mac 00:18:f8:2c:6b:99 arp 1" >> /etc/iftab
```
gave me : bash: /etc/iftab: Permission denied
I am signed on as super administrator, why would this be a permission problem? Any help?

---

### Post by grantwfuller on 2007-08-31
I found that the iftab file contains the correct mac number for wlan0
I am assuming that means this was not the problem. (I'm way over my head but I sure would like to get this working)

---

### Post by hendricks on 2007-09-03
Grantwfuller,

Sorry for the late reply. School work is starting to catch up to me and I won't be able to help with these problems for much longer I think.  Anyway, first double check that you have the right mac address in your iftab file (the instructions I gave earlier were for someone else). What is your output from "iwconfig"? Also, I think the reason why you got an error earlier was maybe because you copied and pasted both lines in at the same time? Gotta type a password after running a sudo command so you have to do it separately.  But I think you got the gist of what I was trying to do there anyway.

Hendricks

---

### Post by chas2007 on 2007-09-06
Hendricks,

Thank you so much for creating the script and making it available here.  I used it recently on Klikit ([http://www.klikit.org]("http://www.klikit.org")), which is a Kubuntu derivative, and it worked like a charm.  A blissfully painless experience. :)

Nothing else I tried worked, it was a real relief to find this thread with your solution.  I'm very grateful, thanks for a job well done. =D>

---

### Post by scottsark on 2007-09-09
Thanks for all of your hard work hendricks. Everything has gone swimmingly however i cannot connect to the web even though the network manager says i am connected. When I pull up the network settings screen, the wireless connection is not accessable. Please forgive the extreme naivity as I am only 3 hours old to linux. As a matter of fact I've even managed to screw up the dual boot mode when i installed Ubuntu and erased my whole hard drive! Oh well. I just want internet access so I can use the tutorials and become a productive member of the Ubuntu community. Thanks in advance from a friends pc.

---

### Post by scottsark on 2007-09-09
I guess I just needed another hour. I got it working in the network manager after disabling the roaming and filling in my network info. Sorry for the thread pollution and thanks again to hendricks. The door to   linux is now open for me to trip and fall into.

---

### Post by ukrgdjklzb on 2007-09-26
geez i have a dummer question this is my first day using ubuntu at all, i have that  wireless card so i keep having to reboot to windows to read about it.. so when i extract the script and go to the folder in terminal and type sudo ./wireless i get a command not found message. is there a paticular language i need to install or something ive never used sudo b4 to get root access either

---

### Post by pdripley on 2007-09-27
hendricks - thanks a ton for this script!  worked great and saved me a bunch of time.  

i'm running edubuntu 7.04.  after running the script and rebooting i selected my wireless network from the list, but it wasn't working.  i had to click 'connect to other wireless networks' and enter in the network name and the wep key.  after that it worked great!

---

### Post by keyeser67 on 2007-09-29
Made it to the file O.K. but when input  sudo ./wireless, I get "password:". I tried the password, but nothing comes up as I type. When I hit enter I get "Sorry, try again".

---

### Post by hendricks on 2007-09-30
keyeser67,

When you use the "sudo" command, it will not show what you're typing as you type it. The "Sorry, try again" means that you typed in your password wrong. Make sure you're typing your password in right. its the same password you use to log in.

--hendricks

---

### Post by ukrgdjklzb on 2007-10-01
scratch that last for some reason it worked fine when i extracted the original .tar in linux instead of using winrar from windows

---

### Post by hendricks on 2007-10-16
Hey all,

To those that are wondering, I'm planning on updating this script with the new release of Gutsy in a couple of days if the OS is still installing the driver wrong. I'll keep you guys updated to make everything as easy as possible.

--Hendricks

---

### Post by fishish on 2007-10-19
Worked great on Xubuntu Feisty Fawn 7.04. I should preface my next comment with, I am new to Linux.

Then I upgraded to Xubuntu Gutsy Gibbon 7.10, and now it doesn't work. 

Should I have chosen to not remove obsolete packages at the end of the upgrade?

Before I screw up Gutsy Gibbon, will this script work for this upgrade?

---

### Post by fishish on 2007-10-19
Disregard my last post. I restarted my system a second time after the upgrade, removed then re-attached the USB adapter, and now Gibbon recognizes it. 

Thanks for your time.

-Brian

---

### Post by fishish on 2007-10-19
Thought I had connection problems worked out. Worked temporarily, but disconnects.

Disregard that last disregard.

---

### Post by hendricks on 2007-10-19
fishish,
I haven't tried the script on the new version of ubuntu yet. I'll post as soon as I know more. It should be in the next couple of days.

Hendricks

---

### Post by hendricks on 2007-10-22
Well guys, I've just tried out Ubuntu and Kubuntu 7.10 and it appears that they finally got the drivers installed right for the WUSB54gc. At least for me, wireless was even working in the live cd environment. If there is a justified need to continue this script for the new OS, please post here why. The whole reason I made this script was to get wireless working "out of the box" on fresh installs and it looks like Ubuntu finally pulled it together :-) Let me know how everything goes for you guys.

--Hendricks

---

### Post by fishish on 2007-10-23
Hendricks,

Xubuntu 7.10 connects through the WUSB54GC like a charm. I get a full signal strength, 4 bars, for a few minutes. And then nothing. The signal bars go blank. Firefox will not open a single webpage. I am browsing on my laptop utilizing the very same router, without a glitch. But the Xubuntu machine sitting right next to me ultimately does not maintain a connection. I have tried roaming mode and a manual router connection.

The oddest part is that immediately after the first restart, it worked perfectly. The following morning, and ever since, webpages do not open. I have tried numerous.

Lately, I haven't checked the other posts in the forum regarding this problem. I'll do that now.

---

### Post by hendricks on 2007-10-23
Thanks for the info fishish, I'm pretty busy this week due to classes and interviews, but I'll try to update the script by this weekend for 7.10. I've never actually intended for the script to work in anything except Ubuntu and Kubuntu so we'll see what happens I guess.  It may take me a little longer than this weekend though, depending on how different this new version is from the last. Hang in there! I'll do what i can

--Hendricks

---

### Post by fishish on 2007-10-23
Hendricks,

Back story: Regardless, your script worked in Xubuntu 7.04 last week. Couldn't leave well enough alone, though and installed 7.10. When 7.10 failed to connect, I thought about running it again,  but decided against it, and responded in your thread instead.


Thank you in advance, fishish

---

### Post by hendricks on 2007-10-24
Well I've got some good news and some bad news.

Good News:
[INDENT]It works with Gutsy! I'm using it right now.[/INDENT]

Bad News:

[INDENT]After some updating dependencies and ndiswrapper to the newest version, ndiswrapper seems to always crash if I have my wireless stick plugged in while booting up. I'm going to do some more testing to make sure. I should definitely have the updated script ready by this weekend, but we may just have to live with unplugging the wireless adapter on start up.... we'll see how it goes.[/INDENT]

--Hendricks

---

### Post by fishish on 2007-10-24
Thanks Hendricks! I will wait to try it after the weekend. My WinXP laptop will have to suffice for now.

---

### Post by Insane_Homer on 2007-10-24
Thanks Hendricks! I've just tried the script on a clean install on **7.10** and it worked just great!

Supperb work, thanks again!

---

### Post by hendricks on 2007-10-27
I've updated the links and now there's a separate one for Gutsy, although apparently the old files worked anyway (thanks Insane_Homer).  As far as upgrading (for fishish), I'm about to check it out right now to see what exactly is keeping it from working.

--Hendricks

---

### Post by isTHEr3mOr3 on 2007-10-28
Fantastic! Superb job, works like a charm. I do think this should be supported out of the box. It is a very popular device.

---

### Post by GordonFrohm on 2007-10-28
This doesn't seem to work for me.
I'm using Ubuntu 7.10 by the way
I have a WUSB54G v4 USB Network adapter

Please help. (I've been trying to get this to work for quite a while now...)

---

### Post by hendricks on 2007-10-30
GordonFrohm,

Firstly, type

```
dmesg | grep ndiswrapper
```

and make sure that there are only a few lines printed. If there is a dump of information, then ndiswrapper crashed, so you should reboot and try not having your wireless card plugged in until after you log in. Otherwise, take a look at what you get from typing the following:

```
iwconfig
ifconfig
```

If everything looks normal, it could be that this script is for the WUSB54GC, the compact version of your card. I'm not 100% sure if the script I've made will work for you. That said, you should first try to find the correct drivers. If you're using 32 bit Ubuntu, then you can find them on your install cd that came with your WUSB54G. You need the files that look like rt73.inf, rt73.cat, and rt73.sys. If you are using 64 bit, you may be able to find them on the linksys website or a google search (its how I found the 64 bit drivers for my version).  Put those three files somewhere, and then fire up terminal:

First, cd to the directory where you placed the files. Then type:

```
ndiswrapper -l
```

To just confirm that the rt73 driver is installed. Then type:

```
sudo ndiswrapper -r rt73
sudo ndiswrapper -i rt73.inf
```

The first line removes the old driver for the wusb54gc, and the second line installs the new driver for your card using the 3 files in your current directory (only the inf file needs to be pointed to for it to install the other files).

Thats all I can say for now without more info. Let me know how it goes and good luck!

--Hendricks

P.S. Sorry for anyone waiting to see about upgrade stuff. I haven't had time to look at it yet since I only designed this script for fresh installs.....I'll get around to it soon, i promise

---

### Post by Hyssar on 2007-11-22
> Hendricks : If there is a justified need to continue this script for the new OS, please post here why.

Yes, the default driver with Gutsy is the smallest possible. It doesn't including special and useful options like monitoring and diffusing. The RT73 driver is really nice, that's why i will run your script tonight on my gutsy to upgrade whitout pain.


thanks again for your wonderful job,

Hyssar

---

### Post by Hyssar on 2007-11-22
nice, it works great on Kubuntu 7.10, but the monitor and master modes aren't supported by this driver, sad :(

Nice work, hendricks!

---

### Post by Zoological on 2007-11-23
It didn't work for me..... 

I'm running 7.10 and I have a WUSB54GC usb adapter, but the script thing you provided didn't help. it ran though.

I'm really new, and really stuck, so any help would be appreciated.

I don't think it recognizes my adapter. I've tried plugging it in after I log in, and I've tried everything else I can but it's not working.

---

### Post by hendricks on 2007-11-25
Hey guys, I'm going to be really busy for the next couple of weeks. I'll do what I can to help, but I can't make any promises.

Zoological, is your OS an upgrade or a fresh install? Post what you get from these commands.

```
iwconfig
ndiswrapper -v
ndiswrapper -l
modprobe -l | grep ndiswrapper
```

Do you have any other wireless cards plugged in? Are you running 32bit or 64bit?

--Hendricks

---

### Post by Zoological on 2007-11-25
I'm running a fresh install of 7.10 (my first ever) and I have no cards plugged in except the wusb54gc (in my usb). It's 32 bit I believe.

Heres what I got:

iwocnfig:
lo         no wireless extensions

eth0    no wireless extensions


ndiswrapper -v
Error: no ndiswrapper utils found!

ndiswrapper -l
same^^

modprobe -l | grep ndiswrapper
/lib/modules/2.6.22-14-generic/misc/ndiswrapper.ko

---

### Post by hendricks on 2007-11-26
Zoological,

Try running the script again (make sure your wusb54gc stick is plugged in when you run it).  There may be a bug in the Gutsy script, so try the Feisty script after you've tried the Gutsy script again.

--Hendricks

---

### Post by Zoological on 2007-11-26
Neither worked. Both ran. And I re-booted after each script.

If I have time (and I remember) I'll boot Ubuntu again and execute the commands you gave me yesterday. I intended to, but I forgot.

---

### Post by LinuxLuver29 on 2007-12-02
Thank you so much!  You really helped me!  I have been waiting to get this installed.  Thanks a lot.

---

### Post by johanbach on 2007-12-08
Great job on the script Hendricks!  It worked great for me.

Johan

---

### Post by Merk42 on 2007-12-08
Does this work for WUSB54GSC? If not, I completely give up and am going back to Windows.

---

### Post by Stafke on 2007-12-16
I'm glad to read about this script. I've also got this linksys wusb54gc causing me some headaches in the past, but something strange happened when I tried to install. I'm working on Xubuntu Gutsy, but some others for whom it worked did as well, so this shouldn't be a problem.

Before running  the script, my laptop found the wireless network, but always disconnected after about 10 seconds.
After running the script (which seemed to work allright), I do not get the option 'wireless network' in Networkmanager anymore (which I did get before).
When I go to manual configuration, it takes about ages to load, but then it does find my networks, including the wireless one. Using wifi-radar, I can also see my wireless network (sometimes giving strong signal, sometimes none)

I've tried rerunning the script, but it says everything has already been done. Any advice?
Thanks in advance,

---

### Post by Stafke on 2007-12-16
Perhaps I forgot to mention that it "finds" my wireless network after ages in manual configuration, BUT that I cannot connect. So, it's not just a matter of impatience to wait, it's just not working.

---

### Post by hatevalyum on 2007-12-20
I'm a newb and I've just installed Ubuntu Feisty on a G4 PPC. This script does a bunch of craziness on my machine. Is the powerpc causing the problems? Does ndiswrapper even work on ppc systems?

---

### Post by uhuru_1 on 2007-12-28
I have installed Linux half a dozen times in the last six or eight years. I had not installed it for a couple years lately. When I came into a seven year old PC I decided to install Linux on it. I found out that Linux no longer supports a video card that old. What? Linux, the people's OS doesn't support old stuff? Sounds like the hated Windoze! I managed to get a newer PC and got Linux installed ok. Next I spent the last *three days*reading these forums and trying to make my WUSB54GC wireless card work. This particular thread has  been going for over a year and the driver problem is still not solved (well it works until you reboot). It is the same old same old with Linux. The OS is free or cheap, but periferals don't work. They work if you become an expert at hacking the system to find some arcane file that isn't happy until you stumble on the problem after hours and hours of fiddling. I guess the answer is to buy the enterprise edition with support. Wait! That sounds like buying Windows. Of course you could buy a PC with Linux already istalled, which is fine until something needs to be repleaced, then you are back to the same old driver problem again. I am typing this on a Windows XP machine because stuff just works. Linux will always be tomorrow's OS for the desktop people who don't have a degree in IT and endless time to solve problems that don't exist in Windows. Its been nice. I'm putting my Linux stuff on Craig's List.):P

---

### Post by bartos on 2007-12-31
How do i get monitoring mode now with this as it says ndis wrapper can't monitor?

or how do I remove it all?

---

### Post by ziploc67 on 2007-12-31
> **Merk42 said:**
> Does this work for WUSB54GSC? If not, I completely give up and am going back to Windows.

i agree with this guy, i have the same model, and for some reason, this suggestion did something to my kernel libraries. regardless, does anyone know if this works with the WUSB54GSC model? that would really help out me and merk.


edit: neither of the packages worked, so much for linux.

---

### Post by LastChanceLeeward on 2008-01-02
Hendricks! Bravo!

Thank you, thank you, thank you for starting and delivering on this thread!

I am a linux n00b, and could not proceed without the help of smart and kind humans such as yourself. I have been freaking searching and searching for over 2 months to find a wireless card that will work in Ubuntu Gutsty on a Toshiba laptop. The roadblocks or "challanges" have been many for this n00b on the wireless frontier. First, a Toshiba Satellite L45-S7423 Laptop has an infamous RealTek built-in wireless adapter that is for some reason on the USB bus. It is a RTL 8187b, and I read and read and banged my head on the wall trying to make it work for weeks and never could. The joykill of no wireless internet is a show-stopper for most people (my immediate family and friends) and Linux. However, I am quite stubborn and therefore kept persisting. So, I started reading about linux compatible PCMCIA cards, and there seemed to be at least one that many people wrote about, the D Link WNA-2330. It was less than thirty bucks and compatible at least on paper so I almost bought it last night. Trouble was, being that I'm a linux n00b and a laptop n00b, I decided to look at my laptop one more time before buying a wireless card. *#&@ it! My Toshiba laptop has no freaking PCMCIA slot! WTF, over? It has some new expresscard (trademark) slot that is allegedly many times faster than the old PCMCIA card bus but NOT backwards compatible with PCMCIA. However, the dilemma is that very few cards are currently being sold for it! Even worse, I cannot find RUMOR of one linux compatible expresscard anywhere on the internet. So I was stuck on stupid. That is, until I found your enlightening thread. My logic was that I had no choice but to go USB Wireless. In addition, I have basic terminal typing and pasting abilities, but I do not want to be the first person to land on that moon, or tag that medium ubuntu asteroid (make a particular component work with ubuntu) or whatever. As a result, I need something that either "just works", "works out of the box", or be able to find a guru who likes to write complete instructions on the internet with command line code or a script that actually works. I believe you are it. As a result, I am off now to buy the WUSB54GC for 49.99 at the local box down the road a ways. Wish me luck, cuz I'm gonna be crying for help right here, same bat channel, if it does not place nice with 7.10 64. I'll be celebrating if this freaking works, believe me. Also, I can think of two people that this confirmed by me information can immediately benefit. Otherwise, I will be viciously cursing TOSHIBA's and RealTek's names for not being more Open!  Caveat emptor!

---

### Post by LastChanceLeeward on 2008-01-02
Eureka! IT WORKS!!!!!!!!!!!!!!!!!!!!!!!!!!:)

One shot of Patron Gold Tequilla to you, kind sir.

Wireless Internet via USB on Linux !!!!!!  :guitar:

This worked for me on a 7.10 Gutsy 64 with Gnome.

It was not a fresh install either.

SOLVED.

---

### Post by d00derino on 2008-01-09
Wow, thank you so much! This script was so easy to use.

---

### Post by Ken McCoy on 2008-01-10
Thanks for the script! When nothing else worked, your solution delivered!

---

### Post by Maricaibo on 2008-01-16
The Linksys WUSB54GC works in Gutsy right out of the box!

Using Gutsy 7.10 and after a full day's fooling around with NDISWRAPPER, even loading Fiesty 7.04 a couple of times I saw a post here that said the NIC works right out of the box- just don't have it plugged in until after you log on.

Fresh install of Gutsy, logged in, plugged in the USB dongle, checked Network Admin, which didn't work (duh).

Went to Terminal and downed the wired connection, set my wireless parameters (essid, key, mode) and ran 'sudo dhclient wlan0'. Had to do it twice but it's up and running...couldn't believe my eyes when I saw it get ad IP address!

Patience, Grasshoppah...

---

### Post by golfront on 2008-01-18
I used the Gutsy script but it did not work for my Ubuntu Studio install. The script depends on libc6 version 2.6.1-lubuntu9 while my system uses 2.6.1-lubuntu10.

Is it possible to adapt the script for the current libc6 version?

- Mike

---

### Post by hendricks on 2008-01-20
hey sorry guys for not being around few a while. i got busy with school ending and moving to start a "real" job. i'll have more time and be trying to update the script as much as possible. i'll start by trying to answer questions in the next few days that people have been asking. sorry again for taking so long on this. i'll also try to explain at some point what the script actually does in case i can't maintain this anymore so other people can take it over. and thanks for all the positive feedback people! i'm glad i've helped out so many on this issue!

--hendricks

---

### Post by dcasp3r on 2008-01-26
:KS Thank you!  Worked like a charm on Gutsy 64 using WPA.PSK (I'd suspected the "off-the-shelf" drivers might be the issue and this spared me the time (that I don't really have to give) so much appreciated)

~$ dmesg | grep wlan
[   40.347354] wlan0: ethernet device 00:1c:10:63:f1:b9 using NDIS driver: rt73, version: 0x0, NDIS version: 0x501, vendor: 'IEEE 802.11g Wireless Card.', 13B1:0020.F.conf
[   40.348285] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   43.405297] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.267200] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

---

### Post by vcolo on 2008-01-28
Genius!!!!!!!

I just finhished installing, and for the first time in two months I have the internet running when I turn on the computer.

Thank you for the help.

---

### Post by safjazz on 2008-02-03
After trying to get my Atheros card to work for days, I bought the WUSB54GC and used your script. Thanks for saving me from more frustration!

---

### Post by xaer0knight on 2008-02-04
hello... so many topics/post to things related to WUSB54G here in the forum.

The only questions i have here is:

Does this script work for Xubuntu 7.10?
Will it work for my WUSB54G Version 4 Wireless Adapter?

i'm not new to Ubuntu but i have an old 800Mhz Pentium 3, and im sick of Windows XP!!

i have downloaded NDISWRAPPER to floppy and try that no luck
i've gone as far as turning off my 2Wire Router Firewall and Security features..

---

### Post by samlindemer on 2008-02-10
I've spent 2 days trying to connect to the internet with this crappy little Linksys and this is the only working solution! Thank you, Hendricks! Simple and straightforward for Ubuntu n00bs too!

---

### Post by Bad_Byte on 2008-02-17
> **hendricks said:**
> Hey guys. I've made a script that can do this very easily. 

Thanks!

---

### Post by DreamClown on 2008-02-18
Many thanks for this script! I've been trying for days to get my wireless up and this fixed it in 10 minutes!

Peace,
~DC~

---

### Post by hooankrtz on 2008-02-18
Pardon my ignorance, but can anyone tell me how to Code. What do you open, the terminal? Yes, i downloaded the scrypt sggested by Hendricks, but how do you Code and run it, where? You know, another thing, I'm running Ubuntu and have the 64-bit thing, the pc recognizes the usb adaptor and it shows that is picking up several wireless signals aside from the one I want to connect to, but the the browser doesn't hook up. I appreciate some help. Thanks:)

---

### Post by DreamClown on 2008-02-19
> **hooankrtz said:**
> Pardon my ignorance, but can anyone tell me how to Code. What do you open, the terminal? Yes, i downloaded the scrypt sggested by Hendricks, but how do you Code and run it, where? You know, another thing, I'm running Ubuntu and have the 64-bit thing, the pc recognizes the usb adaptor and it shows that is picking up several wireless signals aside from the one I want to connect to, but the the browser doesn't hook up. I appreciate some help. Thanks:)


Yes, you open a terminal to run the code.

First, right click the downloaded file wherever you saved it and choose "extract here"

Then, in the terminal, type:  cd wusb54gc

This changes the directory you are in to the file you just extracted.

Then, in the terminal, type:  sudo ./wireless

This will run the script.

Now just reboot. This worked perfect for me the first time I used it. I hope this helps you.

Peace,
~DC~

---

### Post by ncarty97 on 2008-02-21
OK, I tried this, but am having no luck.

I'm running the 32bit Gutsy version.  I have the USB54GC.  I haven't done anything off the fresh install other than change the background and try to configure the network connection (which worked once) with the default driver.

Here is what I get in the terminal:

> ncarty97@nate-desktop:~$ dir
Desktop    Examples  Music     Public     Videos
Documents  file:     Pictures  Templates  wusb54gc
ncarty97@nate-desktop:~$ cd wusb54gc
ncarty97@nate-desktop:~/wusb54gc$ sudo ./wireless
sudo: unable to execute ./wireless: No such file or directory
ncarty97@nate-desktop:~/wusb54gc$ 
ncarty97@nate-desktop:~/wusb54gc$ 


I'm in the wusb54gc directory, and the "wireless" file is there, but I get "sudo: unable to execute ./wireless: No such file or directory"

I even opened the "wireless" file to make sure the script was in there.

Help!  Thanks

---

### Post by ncarty97 on 2008-02-23
Any ideas guys?

---

### Post by PGScooter on 2008-03-02
another success story for gutsy! Thanks a lot!

just as easy as you said

---

### Post by EmoDx on 2008-03-02
This so didn't work for me. Infact, it might have broke the system. Here why I say this:
[LIST=1]
[*]In the network module, the OS doesn't recognize my wireless adapter.
[*]The "Ubuntu Update" icon appeared at the top next to the networking icon. It states, "This usually means that your installed packages have unmet dependencies.
[*]So thinking that the OS needs to download something extra to make the script work, I click it. I get this error while trying to update, "It is impossible to install or remove any software. Please us the pakage manager "Synaptic" or run sudo apt-get install -f" in a terminal to fix this issue first.[/LIST]

So, I am off to try and fix Ubuntu once again. On a side not, I am so F'in tired of trying to get wireless to work I am about to ditch Ubuntu all together.

-E

---

### Post by EmoDx on 2008-03-02
> **EmoDx said:**
> This so didn't work for me. Infact, it might have broke the system. Here why I say this:
[LIST=1]
[*]In the network module, the OS doesn't recognize my wireless adapter.
[*]The "Ubuntu Update" icon appeared at the top next to the networking icon. It states, "This usually means that your installed packages have unmet dependencies.
[*]So thinking that the OS needs to download something extra to make the script work, I click it. I get this error while trying to update, "It is impossible to install or remove any software. Please us the pakage manager "Synaptic" or run sudo apt-get install -f" in a terminal to fix this issue first.[/LIST]

So, I am off to try and fix Ubuntu once again. On a side not, I am so F'in tired of trying to get wireless to work I am about to ditch Ubuntu all together.

-E

Ok, so rule out #3. I fixed that part. Back to not having a wireless adapter recognized Plese tell me how to fix this. Thanks,

-E

---

### Post by hendricks on 2008-03-02
Ok, I finally bought a wireless router so I'm back in business with fixing this thing up. First off, has anyone had any issues with their connection dropping out and only being able to resolve it by restarting their computer? I think there may be a problem with ndiswrapper. If other people are experiencing this problem, then I'll have to completely re-do the script to use a different program. And as a side note, if you have any issues with using the script, please post as much useful info as possible, such as which version of ubuntu you're running, 32/64 bit, if its an upgrade from a previous version, if you had the wireless card plugged in when you installed the os, etc. This info will be very helpful, along with any error messages.

--Hendricks

Edit: Sorry EmoDx, your last post got posted while I was typing up this one. Try typing lsusb in terminal and see if your card comes up. Do you have other wireless cards attached to your comp? Did you have this one (wusb54gc) attached when you installed ubuntu? Can you give some more info on your setup?

---

### Post by EmoDx on 2008-03-02
> **hendricks said:**
> 
--Hendricks

Edit: Sorry EmoDx, your last post got posted while I was typing up this one. Try typing lsusb in terminal and see if your card comes up. Do you have other wireless cards attached to your comp? Did you have this one (wusb54gc) attached when you installed ubuntu? Can you give some more info on your setup?

+ The output of lsusb is:
[B]Bus 001 Device 002: ID 13b1:0020 Linksys 
Bus 001 Device 001: ID 0000:0000  
[/B]

+ When I System>Administration>Network, the console does not show a wireless adapter where it did before the script.

+ When I System>Preference>Hardware Information my wusb54gc appears under the SCSI Device Adapter as a CD-232E

+ I indeed had the adapter plugged in while running the script

+ The activity/power light doesn't come on when I plug the adapter in.

What irks me about the Ubuntu wireless problem is that the adapter worked great when I first installed it. About 48 hours straight until my first reboot. After my first reboot it stopped working. Well, it showed networks and would connect to my secured network, only to drop the connection inside 1 minute.

So how do I de-install the adapter as a storage device?

-Emo

---

### Post by EmoDx on 2008-03-05
> **EmoDx said:**
> + The output of lsusb is:
[B]Bus 001 Device 002: ID 13b1:0020 Linksys 
Bus 001 Device 001: ID 0000:0000  
[/B]

+ When I System>Administration>Network, the console does not show a wireless adapter where it did before the script.

+ When I System>Preference>Hardware Information my wusb54gc appears under the SCSI Device Adapter as a CD-232E

+ I indeed had the adapter plugged in while running the script

+ The activity/power light doesn't come on when I plug the adapter in.

What irks me about the Ubuntu wireless problem is that the adapter worked great when I first installed it. About 48 hours straight until my first reboot. After my first reboot it stopped working. Well, it showed networks and would connect to my secured network, only to drop the connection inside 1 minute.

So how do I de-install the adapter as a storage device?

-Emo

^^ BUMP ^^

Can anyone help me with this one?

---

### Post by hendricks on 2008-03-06
Emo,

 I can't think of any reason why its thinking its a storage device. I'll try to figure out what happened and how to fix it, but I don't know off the top of my head. The script is very basic and just installs some packages and the drivers to ndiswrapper so I can't see how it could have done that.  Please tell me what version of ubuntu you are using and if its Ubuntu or Kubuntu. Can you think of anything else? Try the ifconfig and iwconfig commands and see if they put out any kind of useful information. I need to re-install ubuntu because my upgrade from feisty got messed up so I'll need a few days. Did you upgrade from a previous version of ubuntu?

-Hendricks

---

### Post by wolfwatcher51 on 2008-03-06
Hendricks, You are truly gifted and giving person. I have been reading this thread and you really "hang in there" for the community.

This is similar, but off topic, so please forgive me. I am desperate, and apparently not alone :)
I am trying to install SME server on an older computer. The install went ok until I had to give an ip addy for the box and the gateway. Many tries later, still no connection, so no further loading of program.

So, why you? I have a linksys wrt54g wireless router/access point and hughes satellite modem. The two xp boxes on the router work, but I cannot get the server to see the internet. Would you have any information from your linksys model that I might apply to my problem?

Thanks for reading my post and I hope you are ok with it. Any help would be greatly appreciated. Thanks in advance, Chris.

---

### Post by Kasbell4 on 2008-03-06
ok, in your first thread, Hendrix (which by the way, thanks for all the help as i have NO idea what i'm doing) you said to:

download that file for gusty and extract it- DONE (on desktop)

then you said to cd into it by typing: cd wusb54gc into terminal

when i did this i got this message from terminal:

kevin@kevin-desktop:~$ cd wusb54gc
bash: cd: wusb54gc: No such file or directory


i know its me, what am i doing wrong?

Kevin

---

### Post by lunarmelody on 2008-03-07
> **Kasbell4 said:**
> ok, in your first thread, Hendrix (which by the way, thanks for all the help as i have NO idea what i'm doing) you said to:

download that file for gusty and extract it- DONE (on desktop)

then you said to cd into it by typing: cd wusb54gc into terminal

when i did this i got this message from terminal:

kevin@kevin-desktop:~$ cd wusb54gc
bash: cd: wusb54gc: No such file or directory


i know its me, what am i doing wrong?

Kevin

Kevin,
If the file is located on the desktop, you'll have to cd to the desktop before you can cd in to that directory.  Open a terminal, and type
```
cd Desktop/wusb54gc
```
at the prompt.  Then follow the rest of the instructions.


I have a question as well.  My wireless card works nicely with the network-manager, except during high traffic.  When I try to load a webpage with a lot of content (images, etc.), my wireless connection will crash, and I have to restart my computer to get my connection back.  I think this is an issue with driver stability.  Does anyone know how to fix this?  Thanks!

---

### Post by hendricks on 2008-03-08
> So, why you? I have a linksys wrt54g wireless router/access point and hughes satellite modem. The two xp boxes on the router work, but I cannot get the server to see the internet. Would you have any information from your linksys model that I might apply to my problem?

Sorry Chris, I don't have a clue how to help you. My wireless adapter is completely different than your router, even tho they have a similar model name. Is your server wired to the router? If you're not using a wusb54gc wireless adapter, you may just need to start a new thread and ask our question to other people with that same router.

> I have a question as well. My wireless card works nicely with the network-manager, except during high traffic. When I try to load a webpage with a lot of content (images, etc.), my wireless connection will crash, and I have to restart my computer to get my connection back. I think this is an issue with driver stability. Does anyone know how to fix this? Thanks!

Lunarmeloday, I have also had some problems with the driver crashing. I'm investigating whether its a problem with the ndiswrapper program.  Whats happening for me atleast is ndiswrapper crashes and there is no way to "restart" the program. The computer has to be restarted. It seems other people are having this problem too. I will see what i can do (new ndiswrapper version maybe, or another method all together). 

Anyone that has a similar problem, please post here so I can decide what needs to be done. Thanks!

--Hendricks

---

### Post by ericdrayer on 2008-03-10
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/26553](https://answers.launchpad.net/ubuntu/+question/26553) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I just ran the script and it seems to have worked on the linksys WUSB54G V4 
BUT Gutsy is warning me about a broken dev lib (the script installed an older version than what is available ...I looked it up in the synaptic manager.I am ignoring this while I test other things however I would like to know If by installing the newer version of the lib I might cause a problem as I will undoubtedly be installing updates in the future.
thanks.
EricD 
PS the router is an older netgear CG814W using WEP passphrase 128bit

---

### Post by ericdrayer on 2008-03-10
The script worked but after moving the computer to another room I was unable to get onto the internet.
I seemed to have connection (73%) in the other room even though I could not get on the internet.
I put the computer back so that I could place the adapter on top of the netgear router and tried to test it.
I get the screen to type my pass phrase but I get no connection...0%
I have tried a few options in the router for the frequency but no go.

---

### Post by blobule on 2008-03-16
I just got a WUSB54GC that was almost working with the drivers of Gutsy. It was disconnecting be itself after a short time for no apparent reason.

Your script fixed everyhting perfectly.

Thanks,

---

### Post by Anacranom on 2008-03-16
2 Questions please, 1) does this work with the WUSB54G**_S_**C? And 2) I just fresh installed on a brand-new hard drive yesterday, do I need to have ndiswrapper or does the script get it for me?, please help I'm a real n00b at these things, but i'm trying

---

### Post by Anacranom on 2008-03-16
Please help, I ran the script, no errors, had to reboot, came back up in low graphics mode, now i can't get out of 640x480, and all of the windows are way too big to manipulate thru to get to the config, so dont know if it worked or not,,, please help and tell me what i did wrong and how to fix it, thank you.

---

### Post by smittycity on 2008-03-21
First of all, i skipped pages 2-10 if this thread, I just wanted to say that with a fresh 7.10 install I ran the script and w/ given instructions and it works perfectly. 7.10 will run the wusb54gc, but not well, /w script it works perfectly, no fallouts under stress good stuff. I'm very thankful, I took me a while to find this and I think it need to be made more visible on the forum.

---

### Post by SubCool on 2008-03-25
Hey, i was looking for some help with geting my linksys wusb54g v4 installed. I have tried a few, .. well more then a few different methods (*,)to install it. And it i just cant get it installed. (*,)[-o<I have done an lsusb, and it is seen. It is also seen in my device information. But, i cant get Network Magic to indicated WLAN possibilities. lil help? [-o<Iwhat do you need to know?

---

### Post by penguin5 on 2008-03-26
is there a way to uninstall what this script did? It made my 76% connection into a 56% connection and did  not solve my linksys wusb54gc recognition problem. I just whant to start from the beginning the way it was before i used the script. 

Thanks in advance.

---

### Post by NetworkGuy on 2008-03-26
While this script worked for me out of the box and brought my system to life, I do have an issue and was wondering if anybody ran into this.    

My machine comes up on the network great as long as I allow Network Manager (7.10)  to work with DHCP.  If I try to manually setup everything and use a static IP address, the wusb54gc doesn't associate with the router without me doing a set of ifdown/ifup on wlan0.  I really would like to use a static IP address for other things this machine is going to be doing and I don't want to give sudo access to anyone else that will be using this computer.    Thanks,

---

### Post by hendricks on 2008-03-29
-All
I'm working on an uninstall script, and am testing out another method using serialmonkey instead of ndiswrapper, as ndiswrapper seems too buggy to use anymore. If anyone would want to try out the scripts before I post them to the thread, please send me a message.  I'm using serialmonkey right now and it has so far been working fine for me. No crashes, no abnormal behavior.

--Hendricks

---

### Post by hendricks on 2008-04-06
UPDATE:

Hey guys, I've been working on this and I think I've come up with a better solution. Let me say before I forget that I've only tested this on GUTSY 7.10 KUBUNTU! And while I think it will work on other versions out there (there aren't any apparent dependencies due to the script compiling the drivers), I make no guarantees.  What I need is for people to try out the script and post success or failures.  I'm fairly confident that there won't be any problems, but if there are, thats what I've included the uninstaller for the new drivers.

I've been using the serialmonkey drivers for a while and haven't experienced any problems (the script currently uses ndiswrapper to use windows drivers). I've made some new install files and uninstall files. I'm going to post the links in this post and will update the first post when I'm sure this is a better solution.

First of all, I finally experienced the graphics issues Anacranom had. I can't figure out what the root cause was, but I think it has something to do with ndiswrapper. Uninstalling ndiswrapper doesn't fix it either. I only had the problem AFTER I installed my video drivers (NVIDIA). Therefore, I'd recommend placing your video driver setup file in your home directory so if it happens to you, you can easily log in and re-install them (no GUI of course, but they're easy enough to set up in most cases). Then just type "startx" if everything went fine.

**DOWNLOAD FILES:**
[Old Drivers Uninstall (ndiswrapper)]("http://www.fileden.com/files/2007/7/27/1301349/Gutsy/uninstall_ndis.tar.gz")
[New Drivers Uninstall (SerialMonkey)]("http://www.fileden.com/files/2007/7/27/1301349/Gutsy/uninstall_sm_v0.1.tar.gz")
[New Drivers Install (SerialMonkey) - 32 Bit]("http://www.fileden.com/files/2007/7/27/1301349/Gutsy/sm_v0.1_32bit.tar.gz")
[New Drivers Install (SerialMonkey) - 64 Bit]("http://www.fileden.com/files/2007/7/27/1301349/Gutsy/sm_v0.1_64bit.tar.gz")
[New Drivers Install (SerialMonkey) - Universal]("http://www.fileden.com/files/2007/7/27/1301349/Gutsy/sm_v0.2_universal.tar.gz")

OK, back to the new drivers. First, if you've installed the previous drivers that use ndiswrapper, you'll need to uninstall them. Download the ndiswrapper uninstall, unzip the files, and cd into the directory they were extract to. From the terminal window, type
```
sudo ./uninstall_ndis
```
And follow the instructions.

To install the new drivers, select **one** of the three zip files listed above, depending on your system. If you don't know or don't care about file size (870 KB vs 1.4 MB), then you can pick the universal packages.  Regardless of the package you pick, extract its contents and navigate to the extracted directory with your favorite terminal.  Then type
```
sudo ./install
```

If all goes well, it will install the drivers and they'll be ready to use immediately without restarting. If you're using KDE, the wireless assistant app should pop up and let you connect to your network.

Thats it! You should now be surfing the net.

To uninstall the new drivers, do the same thing you did for the old ndiswrapper drivers, except download the new drivers uninstall file from above and type
```
sudo ./uninstall_sm
```
after navigating to the directory where the files were extracted.

Please post any problems or successes. These drivers are seem much better than ndiswrapper. Good luck and please help me out by posting whether it worked for your setup (Ubuntu/Kubuntu Feisty/Gutsy/Hardy). Thanks!

--Hendricks

PS I'm considering making a GUI for this, for those not experienced with using the terminal. Is this something you all would want?

---

### Post by DJSpazz on 2008-04-07
The Serial monkey did *not* work for
Dual Boot Vista/Gutsy (Vista First) 32bit.
WUSB5**S**4GC

---

### Post by hendricks on 2008-04-07
DJSpazz,

From what I've read on the internet, your wusb54g**s**c uses a Broadcom chipset, not Ralink with the wusb54gc. Your best bet is to use ndiswrapper. If you want, you can use the previous installers I have posted in the first post of this thread, but you'll need to remove the rt73 driver it installs.

First, you'll need to locate the windows driver files for your adapter. They are probably somewhere on the install CD you got, and they have the extension *.cat, *.inf, and *.sys. You can also try to search for them on google (its how I found the 64 bit drivers for the rt73 in the previous scripts).  Copy all three of these files somewhere when you're in Ubuntu. Open up a terminal and navigate to that directory.

First type the following to remove the rt73 drivers (you may need to do sudo in front of them, not sure, but you'll find out if it tells you you can't run the command):
```
ndiswrapper -r rt73
```

Then type the following to install YOUR drivers (replace * with whatever the driver file name is, or you can try to leave it)
```
ndiswrapper -i *.inf
```

Restart your computer. That should be it, but its impossible for me to tell since I don't have this card, although I've been considering buying one because there seems to be lots of questions about it here. Good luck.

--Hendricks

---

### Post by DJSpazz on 2008-04-07
Thanks so much for trying to help me. :DDD
I got the drivers off the internet and did what you told me. Although I have no idea if they are the newest/latest/updated/whatever.
Strangely enough, when I tried to delete the file you told me, terminal told me no such file existed.
Also, when trying to install the drivers, terminal told me they were already installed.
Alas, after rebooting nothing was different.

I was curious, and I checked the hardware manager and its finding and identifying the adapter... But on the actual hardware the light is not blinking and you cannot even scan for networks. ANDD lastly there were only .inf and .cat files, no .sys. Dunno if that helps.

---

### Post by Virta on 2008-04-07
Ok so I installed your script and restarted after it ran thats when i ran into trouble.  I didn't have a manager pop up or anything.  Here are my results (BTW I'm a total linux noob, but i know basic folder..."accessing?" such as the cd command...)

```
pid 134519120
nate@Ezekiel:~$ dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
nate@Ezekiel:~$ ifconfig wlan0 up
SIOCSIFFLAGS: Permission denied
nate@Ezekiel:~$ iwconfig wlan0 mode managed channel 6 key open 3214567890 essid revello
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not permitted.
nate@Ezekiel:~$ iwconfig wlan0 ap 00:15:E9:65:E3:F6      <----mac address im guessing?
Error for wireless request "Set AP Address" (8B14) :
    SET failed on device wlan0 ; Operation not permitted.
nate@Ezekiel:~$ dhclient -q wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
drop_privileges: could not set group id: Operation not permitted
nate@Ezekiel:~$ 



```
What is the number "3214567890," is that required?


I have a WUSB54GC on 7.10 32bit :/

Thanks in advance.

Edit: I overlooked the new installer, ill try that now.

---

### Post by Virta on 2008-04-08
I ran the new installer (after i ran the uninstaller for ndiswrapper) after that i ran the installer. Here is what i got.

```

Unpacking driver files...
Running make...
2.7M rt73.ko
Installing driver files...
FATAL: Module rt2570 not found.
Blacklisting rt73usb...
Blacklisting rt2570...
Blacklisting rt2500usb...
Blacklisting rt2x00lib...
KDE core libraries not installed.  Skipping installation of wireless assistant.
Done

```

im guessing that fatal error isnt a good thing.  Also i ended up with another failure. >.<  So if anybody has an idea what to do next please tell me

---

### Post by hendricks on 2008-04-09
DJSpazz,

You should not be deleting any files. Try typing

```
ndiswrapper -v
```

To see what version of ndiswrapper is installed. If it says no version is installed, try running the script again. Anyway, after you've verified that ndiswrapper is installed, type 

```
ndiswrapper -l
```
To list the installed drivers. You should see rt73 if you've just run the script. Thats the old driver you're removing, which you remove by typing ndiswrapper -r rt73. Then you install your new driver by typing ndiswrapper -i whatever.inf where whatever is the name of the inf file in the directory you are in (you can type ls at the terminal to list out the files in the current directory to make sure you navigated to the correct location). Also, make sure those 3 files have the same prefix, like whatever.cat, whatever.inf, and whatever.sys.

Virta,

From your first post, I described how to setup WEP protection. Is your wireless set up for WEP or WPA? All of those commands need to be run with "sudo" privileges, so you can either type sudo in front of all of them, or type "sudo bash" before them to temporarily become a super user (type exit to return to normal). The 3214567890 number was an example of a WEP password. If you use WEP, change it to whatever it needs to be. If you're running GNOME, you can just try using the network manager to connect instead of manually typing that info. If you're using KDE, you can try out the wireless assistant program that gets installed, although I'm guessing from your 2nd post that you're running GNOME.

As for the new script, the FATAL error you see doesn't matter. It was just blindly trying to stop a module that wasn't loaded, so thats ok. What set up do you have so I can test it out? Ubuntu 7.10 32 bit? I was really hoping that the new script would work on these different versions without much tweaking :(

--Hendricks

---

### Post by hendricks on 2008-04-10
OK,

I just realized that NetworkManager won't work in Ubuntu (GNOME) with these new SerialMonkey drivers (thats probably your problem Virta). You can still set up your network manually as listed in the first post (there's lots of other posts on Ubuntu forums for different setups like WPA and such). However, I found a program called GTKWifi that works quite well for me at least. I use WEP, so I haven't gotten to try it on anything else, but I've updated the "universal" installer to include it now for version 0.2 of the script. You'll need to reboot most likely after running the script. For those of you using Kubuntu, nothing has changed FYI.

You can download the new file (sm_v0.2_universal.tar.gz) [HERE]("http://www.fileden.com/files/2007/7/27/1301349/Gutsy/sm_v0.2_universal.tar.gz").

I've gotten it to work successfully on Ubuntu 7.10 64 bit from a fresh install, so that means that this script is working for Ubuntu and Kubuntu 7.10 64 bit, but I haven't tried any 32 bit installs yet.

--Hendricks

---

### Post by zer0knowhow on 2008-04-14
Okay, so just to be clear, if I'm using the WUSB54G**S**C, then I'll need to use the first script you made with ndiswrapper?  

Does the one you made with Serial Monkey not work for it?

I'm very n00bish.

---

### Post by hendricks on 2008-04-15
zer0knowhow,

Thats right, if you're using WUSB54G**S**C, you'll need to use ndiswrapper. I'm not sure if it will work, but you have a better chance than using the SerialMonkey drivers. I know for a fact that the SerialMonkey drivers WILL NOT work because they are for a different chipset. Even though your usb adapter is similar in both appearance and name, it uses a different chipset. Basically, its completely different than the one I've made this script for.

But, you can still try and use ndiswrapper. Ndiswrapper can use any wireless driver that windows uses (not Vista drivers), whereas SerialMonkey is made specifically for the Ralink chipsets, such as on the WUSB54GC. The chipset for the WUSB54G**S**C are made by Broadcom.

That said, I have no idea if the way I described will actually work with your adapter. I don't own one, but I've had success using ndiswrapper with some other adapters. I hope this clears things up.  Here is what the ndiswrapper page says about your adapter:

>    1.
      Card: Linksys WUSB54GSC, 802.11b/g, USB 2.0

    *
      Chipset: Broadcom
    *
      USBID: Vendor=13b1 ProdID=0026 (13b1:0026)
    *
      Driver: Downloaded driver [http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1154470123093&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1154470123093&pagename=Linksys%2FCommon%2FVisitorWrapper) here and install. Copied the win files (usb8023.sys and rndismp.sys) from the F5D7051.exe [http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1](http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1) download to the /etc/ndiswrapper/wusb54gsc/ folder. Lastly, use the script detailed [http://www.ubuntuforums.org/showthread.php?t=225206](http://www.ubuntuforums.org/showthread.php?t=225206) here , modidifed with the correct USB ProdID (0026), to get the power working. It’s in the section ‘Getting WUSB54GS to Work in Edgy and Feisty’ Also check out the thread [http://www.linuxquestions.org/questions/showthread.php?p=2559643](http://www.linuxquestions.org/questions/showthread.php?p=2559643) here for why the script is needed and works.
    *
      Other: With 2.6.16 and later kernels, RNDIS devices are not initialized (when device is plugged in, nothing happens). To get it going, you need to set the variable bConfigurationValue in sysfs. An easy way to do this is to add this: BUS==”usb”, SYSFS{idProduct}==”0026”, SYSFS{idVendor}==”13b1”, PROGRAM=”/bin/sh -c ‘echo 1 > /sys/%p/device/bConfigurationValue’” to /etc/udev/rules.d/<ruleFilename> file and restart udev. For FC6 <ruleFilename> is 50-udev.rules.


I know it sounds complicated and probably overwhelming for a n00b. I'll try and get around to getting one off of ebay, but I wouldn't expect this to happen anytime in the near future. Good luck.

--Hendricks

---

### Post by sofasurfer on 2008-04-21
I ran the script at the beginning of this thread for WUSB54GC on Gutsy. No adaptero worko so I am going to reinstall gutsy just to be sure its clean and then try again. I hope that someone responds to this post with some advice. I know this is an old thread. I hope its still being watched.

---

### Post by sofasurfer on 2008-04-22
I've read this entire thread now and there seems to be a bit of non-clarity from my point of view.

Has the script on the first post of this thread been updated and still the one I should be using?

Is the whole proceedure to start with the adapter plugged in and then run the script and accompanying instructions and then reboot and it should work?

What is this recently mentioned link (sm_v0.2_universal.tar.gz)? Is it a replacement for the script on post #1 or where does it come into play?

I don't know if I have v4 of WUSB54GC. How do I tell?

---

### Post by Igtenio on 2008-04-24
I figure this's nothing, but I'd ask just to make sure.

I can safely assume that upgrading to Hardy doesn't do anything adverse to NDISWrapper or this setup, right?

---

### Post by dkerlee on 2008-04-24
I had the wusb54gc, recently moved from XP to Ubuntu Gutsy. Annoying thing was, my wusb54gc kinda worked. The range sucked, and it would drop connection all the time. I'm just posting to say that you're script/driver package worked like a charm - exactly like you said it would. Thank you very much! My connection is as good now as it was in XP. aloha!
drew

---

### Post by chas2007 on 2008-05-02
Hi,
I just want to report here, that I've tried the Gutsy WUSB54GC driver in Hardy, and it works!  I'm using it in HH 8.04 with Gnome Desktop.

The script showed an error, indicated that wlassistant didn't install.  But when it was finished, I was able to configure my connection to the wireless network via the pull down menu, System/Administration/Network.

Everything is groovy now.  :guitar:

THANK YOU once again, for creating this wonderful install script! \\:D/=D>:-D

---

### Post by GrammaToad on 2008-05-06
i dont understand.

i dont have an internet connection to my ubuntu 7.10 or do i have any means of connecting because i cant move my computer into the office.


what do i do if my only internet connection is in windows?

and when you say run a code you mean in terminal right?

im new to new operating systems so give me a break.


i would like to use ndiswrapper but i dont know how if i cant even download it to my ubuntu.

i need to get my internet working because i need to update to 8.04. but if i can update via live Cd then ill do that.

but still i need some help, thanks

---

### Post by GrammaToad on 2008-05-06
also, 7.10 wont even make the green light on my adapter light up. so does this mean it doesnt even see its there?

---

### Post by GrammaToad on 2008-05-07
ok i found out that the green light does light up but just barely, so i know its plugged in and its working

and i also noticed my card is a WUSB54G**_S_**C

can anyone help please i need to update from gutsy to hardy

---

### Post by Milardo on 2008-05-13
Default installation of the adapter still doesn't work, do you have a new script for latest ubuntu? Thanks in advance.

---

### Post by ogiso_akpolokpolo on 2008-05-16
Thanks for this Hendricks!! I recently switched from Ubuntu Hardy (32-bit) to 64-bit hardy. The default drivers that were installed with Hardy were very unstable with the link dropping all the time. I tried you install script for the SerialMonkey drivers and they're working like a charm!
I really appreciate the effort you put into making it easy to install/uninstall.
Thanks again!

---

### Post by Pedro_Pdr on 2008-06-12
Hi guys.
Ive bougth this WUSB54GC too and i have formated my Laptop with Ubuntu 7.10 and with Wireless pen conected at same time i was formating. After Ubuntu installed i enter in Ubuntu and he recognized Wireless conections. So i didnt need to install nothing. But in my mom Laptop with XP we recongnized about 7 wireless conetion and mine in Ubuntu only 2.
But works:)

---

