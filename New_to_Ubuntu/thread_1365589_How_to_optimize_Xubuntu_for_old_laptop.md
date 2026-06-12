---
title: "How to optimize Xubuntu for old laptop ??"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by rfv-370 on 2009-12-27
[LEFT]Hello,

[/LEFT]
        [LEFT]I am looking at how to improve /  optimize / fine-tune Xubuntu 9.10[/LEFT]
        [LEFT]in order to speed it up a bit. I am running it on my old laptop.



My config is:[/LEFT]
        [LEFT]Laptop VAIO PCG-Z600NE[/LEFT]
        [LEFT]Pentium III - 250Mhz - 244Mb HD-32Go[/LEFT]
    [LEFT]Linux: Xubuntu 9.10 - fresh install


                                        Currently (with Firefox, Abiword and a terminal) the memory looks like:
```
[LEFT]rfv@vaio:~$ free -mt[/LEFT]
    [LEFT]             total       used       free     shared    buffers     cached[/LEFT]
    [LEFT]Mem:           244        206         38          0         17         83[/LEFT]
    [LEFT]-/+ buffers/cache:        104        139[/LEFT]
    [LEFT]Swap:          713         65        648[/LEFT]
    [LEFT]Total:         958        271        686[/LEFT]

```                                       I want to use Xubuntu for watching TV (streaming displayed in VLC), listening radio - from internet using MPlayer(.ram format)-, watching movies from usb drive(Mplayer/VLC)  and browsing internet (firefox). And well, time to time, I use abiword ... And that is really all, no programming, no office work.
        [LEFT]I find Xubuntu slow is there anything that I could do to remove processes I do not need to start-up ? And which ones ? How to stop them at start-up?
[/LEFT]
        [LEFT]Any idea would be welcome ?!
(The list of running processes is at the end of my message)

[/LEFT]
        [LEFT]Thanx a lot and Merry Christmas to all developers working on Ubuntu/Xubuntu and also forum members!
 
[/LEFT]
        [LEFT]

Kind Regards,[/LEFT]
        [LEFT]

Robert[/LEFT]
        [LEFT]

PS: I know puppy linux may be better but (i) I did not find a way to have it booting on the VAIO - problem due to the PCMCIA CD-Rom drive I think, and I need VLC 0.8 or higher for proper streaming to watch TV from my freebox. So not sure that PuppyLinux would do that.[/LEFT]
    [LEFT]PPS: I tried fluxbuntu - faster to problem with VLC and would not recognize my WIFI PCMCIA card DLink G630)[/LEFT]
    [LEFT]PPPS: I would prefer not to have to reinstall a lighter WM - ie switch to Flubox - as I guess it might be a long story ?[/LEFT]
       
  

                           ```
My running processes:
    [LEFT]Running Processes:[/LEFT]
    [LEFT]UID        PID  PPID  C STIME TTY          TIME CMD[/LEFT]
    [LEFT]root         1     0  0 09:14 ?        00:00:01 /sbin/init[/LEFT]
    [LEFT]root         2     0  0 09:14 ?        00:00:00 [kthreadd][/LEFT]
    [LEFT]root         3     2  0 09:14 ?        00:00:00 [migration/0][/LEFT]
    [LEFT]root         4     2  0 09:14 ?        00:00:00 [ksoftirqd/0][/LEFT]
    [LEFT]root         5     2  0 09:14 ?        00:00:00 [watchdog/0][/LEFT]
    [LEFT]root         6     2  0 09:14 ?        00:00:00 [events/0][/LEFT]
    [LEFT]root         7     2  0 09:14 ?        00:00:00 [cpuset][/LEFT]
    [LEFT]root         8     2  0 09:14 ?        00:00:00 [khelper][/LEFT]
    [LEFT]root         9     2  0 09:14 ?        00:00:00 [netns][/LEFT]
    [LEFT]root        10     2  0 09:14 ?        00:00:00 [async/mgr][/LEFT]
    [LEFT]root        11     2  0 09:14 ?        00:00:00 [kintegrityd/0][/LEFT]
    [LEFT]root        12     2  0 09:14 ?        00:00:00 [kblockd/0][/LEFT]
    [LEFT]root        13     2  0 09:14 ?        00:00:00 [ata/0][/LEFT]
    [LEFT]root        14     2  0 09:14 ?        00:00:00 [ata_aux][/LEFT]
    [LEFT]root        15     2  0 09:14 ?        00:00:00 [ksuspend_usbd][/LEFT]
    [LEFT]root        16     2  0 09:14 ?        00:00:00 [khubd][/LEFT]
    [LEFT]root        17     2  0 09:14 ?        00:00:00 [kseriod][/LEFT]
    [LEFT]root        18     2  0 09:14 ?        00:00:00 [kmmcd][/LEFT]
    [LEFT]root        19     2  0 09:14 ?        00:00:00 [bluetooth][/LEFT]
    [LEFT]root        20     2  0 09:14 ?        00:00:00 [khungtaskd][/LEFT]
    [LEFT]root        21     2  0 09:14 ?        00:00:00 [pdflush][/LEFT]
    [LEFT]root        22     2  0 09:14 ?        00:00:00 [pdflush][/LEFT]
    [LEFT]root        23     2  0 09:14 ?        00:00:01 [kswapd0][/LEFT]
    [LEFT]root        24     2  0 09:14 ?        00:00:00 [aio/0][/LEFT]
    [LEFT]root        25     2  0 09:14 ?        00:00:00 [ecryptfs-kthrea][/LEFT]
    [LEFT]root        26     2  0 09:14 ?        00:00:00 [crypto/0][/LEFT]
    [LEFT]root        31     2  0 09:14 ?        00:00:00 [scsi_eh_0][/LEFT]
    [LEFT]root        32     2  0 09:14 ?        00:00:00 [scsi_eh_1][/LEFT]
    [LEFT]root        34     2  0 09:14 ?        00:00:00 [kstriped][/LEFT]
    [LEFT]root        35     2  0 09:14 ?        00:00:00 [kmpathd/0][/LEFT]
    [LEFT]root        36     2  0 09:14 ?        00:00:00 [kmpath_handlerd][/LEFT]
    [LEFT]root        37     2  0 09:14 ?        00:00:00 [ksnapd][/LEFT]
    [LEFT]root        38     2  0 09:14 ?        00:00:00 [kondemand/0][/LEFT]
    [LEFT]root        39     2  0 09:14 ?        00:00:00 [kconservative/0][/LEFT]
    [LEFT]root        40     2  0 09:14 ?        00:00:00 [krfcommd][/LEFT]
    [LEFT]root       187     2  0 09:14 ?        00:00:00 [khpsbpkt][/LEFT]
    [LEFT]root       188     2  0 09:14 ?        00:00:00 [knodemgrd_0][/LEFT]
    [LEFT]root       261     2  0 09:14 ?        00:00:00 [kjournald2][/LEFT]
    [LEFT]root       317     1  0 09:14 ?        00:00:00 upstart-udev-bridge --daemon[/LEFT]
    [LEFT]root       332     1  0 09:14 ?        00:00:00 udevd --daemon[/LEFT]
    [LEFT]root       460     2  0 09:14 ?        00:00:00 [kpsmoused][/LEFT]
    [LEFT]root       471     1  0 09:14 ?        00:00:00 dd bs=1 if=/proc/kmsg of=/var/ru[/LEFT]
    [LEFT]root       474     2  0 09:14 ?        00:00:00 [pccardd][/LEFT]
    [LEFT]syslog     515     1  0 09:14 ?        00:00:00 rsyslogd -c4[/LEFT]
    [LEFT]root       537     2  0 09:14 ?        00:00:05 [phy0][/LEFT]
    [LEFT]root       562     2  0 09:14 ?        00:00:00 [kgameportd][/LEFT]
    [LEFT]102        602     1  0 09:14 ?        00:00:08 dbus-daemon --system --fork[/LEFT]
    [LEFT]avahi      613     1  0 09:14 ?        00:00:00 avahi-daemon: running [vaio.loca[/LEFT]
    [LEFT]avahi      614   613  0 09:14 ?        00:00:00 avahi-daemon: chroot helper[/LEFT]
    [LEFT]103        619     1  0 09:14 ?        00:00:00 hald --daemon=yes[/LEFT]
    [LEFT]root       640     1  0 09:14 ?        00:00:00 /usr/sbin/console-kit-daemon[/LEFT]
    [LEFT]root       642     1  0 09:14 ?        00:00:00 gdm-binary[/LEFT]
    [LEFT]root       703     1  0 09:14 ?        00:00:07 NetworkManager[/LEFT]
    [LEFT]root       715     1  0 09:14 ?        00:00:00 /usr/sbin/modem-manager[/LEFT]
    [LEFT]root       716   619  0 09:14 ?        00:00:00 hald-runner[/LEFT]
    [LEFT]root       795     1  0 09:14 ?        00:00:00 /sbin/wpa_supplicant -u -s[/LEFT]
    [LEFT]root       867   642  0 09:14 ?        00:00:00 /usr/lib/gdm/gdm-simple-slave --[/LEFT]
    [LEFT]root       880     1  0 09:14 tty4     00:00:00 /sbin/getty -8 38400 tty4[/LEFT]
    [LEFT]root       882     1  0 09:14 tty5     00:00:00 /sbin/getty -8 38400 tty5[/LEFT]
    [LEFT]root       893     1  0 09:14 tty2     00:00:00 /sbin/getty -8 38400 tty2[/LEFT]
    [LEFT]root       894     1  0 09:14 tty3     00:00:00 /sbin/getty -8 38400 tty3[/LEFT]
    [LEFT]root       899     1  0 09:14 tty6     00:00:00 /sbin/getty -8 38400 tty6[/LEFT]
    [LEFT]root       907   867  2 09:14 tty7     00:11:55 /usr/bin/X :0 -br -verbose -auth[/LEFT]
    [LEFT]daemon     916     1  0 09:14 ?        00:00:00 atd[/LEFT]
    [LEFT]root       918     1  0 09:14 ?        00:00:00 cron[/LEFT]
    [LEFT]root      1010   716  0 09:14 ?        00:00:00 /usr/lib/hal/hald-addon-rfkill-k[/LEFT]
    [LEFT]root      1011   716  0 09:14 ?        00:00:00 /usr/lib/hal/hald-addon-leds[/LEFT]
    [LEFT]root      1026     1  0 09:14 ?        00:00:00 /usr/sbin/cupsd -C /etc/cups/cup[/LEFT]
    [LEFT]root      1032   716  0 09:14 ?        00:00:00 hald-addon-input: Listening on /[/LEFT]
    [LEFT]root      1145     1  0 09:14 tty1     00:00:00 /sbin/getty -8 38400 tty1[/LEFT]
    [LEFT]gdm       1175     1  0 09:14 ?        00:00:00 /usr/bin/dbus-launch --exit-with[/LEFT]
    [LEFT]root      1192   867  0 09:14 ?        00:00:00 /usr/lib/gdm/gdm-session-worker[/LEFT]
    [LEFT]rfv       1220     1  0 09:15 ?        00:00:00 /usr/bin/gnome-keyring-daemon --[/LEFT]
    [LEFT]rfv       1235  1192  0 09:15 ?        00:00:00 /bin/sh /etc/xdg/xfce4/xinitrc -[/LEFT]
    [LEFT]rfv       1264  1235  0 09:15 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus[/LEFT]
    [LEFT]rfv       1267     1  0 09:15 ?        00:00:00 /usr/bin/dbus-launch --exit-with[/LEFT]
    [LEFT]rfv       1268     1  0 09:15 ?        00:00:01 /bin/dbus-daemon --fork --print-[/LEFT]
    [LEFT]rfv       1279  1235  0 09:15 ?        00:00:02 /usr/bin/xfce4-session[/LEFT]
    [LEFT]rfv       1281     1  0 09:15 ?        00:00:04 /usr/lib/libgconf2-4/gconfd-2[/LEFT]
    [LEFT]rfv       1283     1  0 09:15 ?        00:00:00 /usr/lib/xfconfd[/LEFT]
    [LEFT]rfv       1288     1  0 09:15 ?        00:00:00 xfsettingsd[/LEFT]
    [LEFT]rfv       1290  1279  0 09:15 ?        00:00:03 xfwm4 --sm-client-id 2cc06221e-0[/LEFT]
    [LEFT]rfv       1291     1  0 09:15 ?        00:00:00 gnome-screensaver[/LEFT]
    [LEFT]rfv       1294  1279  0 09:15 ?        00:00:00 Thunar --sm-client-id 259f85a3d-[/LEFT]
    [LEFT]rfv       1296     1  0 09:15 ?        00:00:00 /usr/lib/gamin/gam_server[/LEFT]
    [LEFT]rfv       1298  1279  0 09:15 ?        00:00:05 xfdesktop --sm-client-id 282b219[/LEFT]
    [LEFT]rfv       1300  1279  0 09:15 ?        00:00:13 xfce4-panel --sm-client-id 27e0a[/LEFT]
    [LEFT]rfv       1301     1  0 09:15 ?        00:00:00 xfce4-power-manager --restart --[/LEFT]
    [LEFT]rfv       1303     1  0 09:15 ?        00:00:01 /usr/lib/notify-osd/notify-osd[/LEFT]
    [LEFT]rfv       1304     1  0 09:15 ?        00:00:00 xfce4-settings-helper --display[/LEFT]
    [LEFT]rfv       1305  1300  0 09:15 ?        00:00:07 /usr/lib/xfce4/panel-plugins/xfc[/LEFT]
    [LEFT]rfv       1306  1300  0 09:15 ?        00:00:01 /usr/lib/xfce4/panel-plugins/xfc[/LEFT]
    [LEFT]rfv       1308     1  0 09:15 ?        00:00:00 /usr/lib/gvfs/gvfsd[/LEFT]
    [LEFT]rfv       1311  1300  0 09:15 ?        00:00:01 /usr/lib/xfce4-mixer/xfce4/panel[/LEFT]
    [LEFT]rfv       1319     1  0 09:15 ?        00:00:08 nm-applet --sm-disable[/LEFT]
    [LEFT]rfv       1323     1  0 09:15 ?        00:00:00 /usr/lib/policykit-1-gnome/polki[/LEFT]
    [LEFT]rfv       1324     1  0 09:15 ?        00:00:00 /usr/bin/xfce4-volumed[/LEFT]
    [LEFT]rfv       1328     1  0 09:15 ?        00:00:01 update-notifier --startup-delay=[/LEFT]
    [LEFT]rfv       1331     1  0 09:15 ?        00:00:02 python /usr/share/system-config-[/LEFT]
    [LEFT]root      1337     1  0 09:15 ?        00:00:00 /usr/lib/policykit-1/polkitd[/LEFT]
    [LEFT]root      1339     1  0 09:15 ?        00:00:07 /usr/lib/devicekit-disks/devkit-[/LEFT]
    [LEFT]root      1341  1339  0 09:15 ?        00:00:00 devkit-disks-daemon: not polling[/LEFT]
    [LEFT]rfv       1413  1300  1 09:15 ?        00:08:14 /usr/lib/firefox-3.5.6/firefox[/LEFT]
    [LEFT]rfv       1480     1  0 09:18 ?        00:00:00 /usr/lib/gvfs/gvfsd-http --spawn[/LEFT]
    [LEFT]rfv       1483     1  0 09:19 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata[/LEFT]
    [LEFT]rfv       1691     1  0 09:43 ?        00:00:00 /usr/lib/gvfs/gvfs-gdu-volume-mo[/LEFT]
    [LEFT]rfv       1693     1  0 09:43 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volum[/LEFT]
    [LEFT]root      1974   703  0 11:55 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/N[/LEFT]
    [LEFT]rfv       2425  1305  1 17:45 ?        00:00:11 abiword[/LEFT]
    [LEFT]root      2510     2  0 17:55 ?        00:00:00 [usbhid_resumer][/LEFT]
    [LEFT]root      2513   332  0 17:55 ?        00:00:00 udevd --daemon[/LEFT]
    [LEFT]root      2514   332  0 17:55 ?        00:00:00 udevd --daemon[/LEFT]
    [LEFT]rfv       2531  1305 14 18:00 ?        00:00:00 xfce4-terminal[/LEFT]
    [LEFT]rfv       2532  2531  0 18:00 ?        00:00:00 gnome-pty-helper[/LEFT]
    
  
```  [/LEFT]

---

### Post by ugm6hr on 2009-12-27
The fact that you use VLC (qt libs) and Mplayer (gnome libs) means optimization will be pretty difficult.

There are a handful of things that you could probably just stop from auto-launching in the XFCE Settings and Startup e.g. Printing, Bluetooth, Update Manager.

If you really wanted to optimize, you could also remove Network Manager (and manually configure networking) and gdm (and maybe use Slim).

---

### Post by gradinaruvasile on 2009-12-27
Xubuntu is based on Gtk like Gnome so most Gnome (Gtk) apps will run without additional overhead. The exceptions are the Gnome core apps like totem, nautilus, evolution, empathy etc.

Preinstalled programs with high memory usage are: 
Firefox & Thunderbird - both use a virtual machine like something called Xulrunner - you can compare it to java apps.
Open Office - uses something similar to Firefox's Xulrunner and its slow even on faster hardware.

Light programs are Gtk apps in general - Gnumeric, Abiword, Pidgin, Midori, etc.

I recommend: 
Browser:
Chromium - It is Gtk based and has a damn fast rendering engine. For slower hardware, i recommend using the flashblock extension - yes, Chromium has it too.
I use it on a Dell D630 P4/512MB RAM laptop - it was the fastest browser that could open as much as 30 tabs and remain stable - and those tabs had everything - flash, scripts etc. Firefox lagged as hell even with a few tabs open. Keep Firefox around for the few pages that wont work with Chromium though.
Office apps:
Abiword & Gnumeric - both are fast, Gnumeric supports the .xls/.ods formats really well, Abiword on the other hand is better used with its own format, has poor support for .doc/.odt. Also, keep OpenOffice for compatibility. 

Also, there is an office suite that is not free, but its fast and has Writer,Spreadsheet and Presentation, but until 31 December there is a 
free activation key giveaway for Linux And Windows:

[http://www.softmaker.com/english/](http://www.softmaker.com/english/)
I tried it and its fast and lightweight. Supports the Windows xls/doc/ppt formats well.
Try it and see for yourself.

Mailer:
Sylpheed - very fast mail client and low on resource usage. Its stable, the only thing it lacks is html rendering.

Movie player:
Mplayer or Xine - both are light in memory, i feel Mplayer a bit more stable, but maybe thats because of the more familiar interface.
For music, i would say Audacious - it is lightweight and fast.

Messenger:
Pidgin is more than enough here.

---

### Post by Chris Edgell on 2009-12-27
ugm6hr, forgive me for asking THIS question, tell me where I've gone wrong here.
but I know I've seen in someone's signature, "Never remove Network Manager, you can never get it back."  Is there any truth to that statement?  I feel sure that you know what you're doing, a lot more than I do...that's why I'm asking for point of clarification

---

### Post by bodhi.zazen on 2009-12-27
> **Chris Edgell said:**
> ugm6hr, forgive me for asking THIS question, tell me where I've gone wrong here.
but I know I've seen in someone's signature, "Never remove Network Manager, you can never get it back."  Is there any truth to that statement?  I feel sure that you know what you're doing, a lot more than I do...that's why I'm asking for point of clarification

No, you can remove and re-install network manager very easily.

The only potential problems you would have, where are you going to get the network manager .deb from ? and how are you going to configure your network.

The first is fairly easy, the deb will be in /var/cache/apt/archives and you can simply re-install it with apt-get

If you cleaned your cache (apt-get clean) you will have to down load the .deb =)

The second part is easy, if you know how to manually configure your network.

[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

---

### Post by bodhi.zazen on 2009-12-27
> **rfv-370 said:**
> I am looking at how to improve /  optimize / fine-tune Xubuntu 9.10        [LEFT]in order to speed it up a bit. I am running it on my old laptop.
[/LEFT]
 
IMO it is far easier to do a minimal install and add only what you need rather then start with xubuntu and try to remove stuff.

You can use Crunchbang, Lubuntu, or Zenix if you do not want to start from scratch.

[http://zenix-os.net/index.php?nav=features](http://zenix-os.net/index.php?nav=features)

---

### Post by gsmanners on 2009-12-27
I would strongly suggest staying away from Lubuntu right now. I tried that out in a VM, and it practically installs a full Gnome desktop.

And it may be ugly, but I would suggest using xdm rather than gdm (at least until there's a stable version of lxdm).

---

### Post by Sir Jasper on 2009-12-27
Hi gradinaruvasile,

Thank you for the Softmaker recommendation. I have given it a brief try and I am impressed.

Hi rfv-370,

I am sorry that I can contribute nothing to assist your cause, but I shall be most interested to learn how smoothly your TV experience goes; so I hope you will be so kind as to update us sometime.

My regards

---

### Post by solitaire on 2009-12-27
If you don't mind learning a load of key commands you could use "cvlc" (comand line version of vlc with no frontend) to play / stream video. it's a lot easier on ram and CPU than totem (in my opinion) I can easily playback 720p using cvlc using only about 70% of the CPU. Where as totem gives me a heck of a lot of tearing and sync issues with the CPU hiting 100% for most of the playback.

cvlc also lets me playback 1080p at a push (if i shut down every other program and service not required! lol!) on my 2Ghz Celeron Laptop (with Intel GM965 graphics!!)

---

### Post by ugm6hr on 2009-12-27
> **Chris Edgell said:**
> "Never remove Network Manager, you can never get it back."  Is there any truth to that statement? 

As per bodhi's reply to this - if you are concerned about the possibility of being unable to manually configure networking, then have the network manager .debs already downloaded before you remove it.

You can ensure you have them in /var/cache/apt/archives by:
```
sudo apt-get install --reinstall -d network-manager-gnome network-manager
```

That way, it is easy to reinstall (if necessary).

If you used wired internet, it is unlikely manually configuring the network will be a major problem.  Wifi is slightly tricker.

---

### Post by kerry_s on 2009-12-27
use Debian stable, the older programs are much faster.
I had the vaio pcg-f430, you can run the full gnome with debian.
[http://cdimage.debian.org/debian-cd/5.0.3/i386/iso-cd/debian-503-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/5.0.3/i386/iso-cd/debian-503-i386-businesscard.iso)

---

### Post by snowpine on 2009-12-29
> **rfv-370 said:**
> My config is:[/LEFT]
        [LEFT]Laptop VAIO PCG-Z600NE[/LEFT]
        [LEFT]Pentium III - 250Mhz - 244Mb HD-32Go[/LEFT]
    [LEFT]Linux: Xubuntu 9.10 - fresh install


Your computer does not meet the minimum requirements for Xubuntu, so I would not recommend it if fast performance is a goal: 

> Xubuntu Recommended minimum requirements

    * 700 MHz processor
    * 256 MB of system memory (RAM)
    * 6 GB of disk space
    * Graphics card capable of 800x600 resolution 

An inexpensive "nettop" computer (like the Revo or Dell Zino) would be a much better choice for multimedia in my opinion.

---

### Post by sandy8925 on 2009-12-29
Yeah if what you wrote is correct then 250 Mhz is way too slow ! One thing you could try is compiling the kernel (on another much faster machine) and installing the new kernel. It might speed up. You should also try using some lightweight window manager. I've personally used Fluxbox which is small,simple,lightweight,bare. I've also heard that LXDE is lightweight too.

On the other hand better to use some small lightweight distros like PuppyLinux,DSL(for general use) and Geexbox (for playing media).

Or if you're more adventurous you could try building Linux from scratch. Which would take a loooong time. But you can get exactly what you want and it will probably be fast.

---

### Post by peyre on 2011-03-10
> **snowpine said:**
> Your computer does not meet the minimum requirements for Xubuntu, so I would not recommend it if fast performance is a goal: 
 Xubuntu Recommended minimum requirements
 * 700 MHz processor
 * 256 MB of system memory (RAM)
 * 6 GB of disk space
 * Graphics card capable of 800x600 resolution 

An inexpensive "nettop" computer (like the Revo or Dell Zino) would be a much better choice for multimedia in my opinion.

I hate to jump in after more than a year, but just in case anyone else goes looking this kind of thing up (as I just did), I'd take bodhi.zazen's advice and try out Lubuntu.  Its minimum requirements are a much better match for your old machine:
 * Pentium II or Celeron equivalent
 * 128MB RAM 
 [SIZE="1"]([https://wiki.ubuntu.com/Lubuntu#System%20requirements]("https://wiki.ubuntu.com/Lubuntu#System%20requirements"))[/SIZE]

I have an old Toshiba Tecra 8100; it's a PIII 600MHz [SIZE="1"](IIRC)[/SIZE] with 512MB RAM, and it runs Lubuntu very well, though of course a bit slowly.  The only issue I had was that Lubuntu 10.10 wouldn't run properly, so I fell back on the LTS (10.04), and it's rock-solid.  It's not as polished as my favorite flavor, Xubuntu, but it's just fine for a machine I use like a netbook.

Also, I've found some ideas for optimizing *buntu that might be helpful:

You can have the system mount /tmp in RAM rather than on your hard drive. 
Open /etc/fstab, and add the following line:
tmpfs /tmp tmpfs noexec,nosuid 0 0

You can do the same with your log files, but that has the drawback that log files won't be saved to the hard drive, so good luck diagnosing problems--so I didn't implement that one.  But you can find instructions how to do it, as well as some other pointers, at the following address:
[http://blog.bodhizazen.net/linux/netbook-optimization/]("http://blog.bodhizazen.net/linux/netbook-optimization/")

---

