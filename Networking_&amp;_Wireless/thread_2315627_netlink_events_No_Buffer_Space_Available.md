---
title: "netlink events: No Buffer Space Available"
date: 2016-03-01
forum: Networking &amp; Wireless
---

### Post by valereguerin on 2016-03-01
LTS.....14.04.....

```
Ksystemlog :

   NetworkManager[1508]    <warn> Couldn't disconnect supplicant interface: This interface is not connected.
   NetworkManager[1508]    <warn> error monitoring device for netlink events: No buffer space available
  CRON[7692]    (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
  CRON[7696]    (buildd) CMD (  /usr/bin/buildd-uploader)
   kernel    [50682.161073] UDP: short packet: From 83.134.218.140:21022 59537/28 to 192.168.0.17:62191
   CRON[10207]    (buildd) CMD (  /usr/bin/buildd-watcher)
   CRON[11463]    (buildd) CMD (  /usr/bin/buildd-uploader)
   CRON[12729]    (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
   NetworkManager[1508]    message repeated 11 times: [ <warn> error monitoring device for netlink events: Aucun espace tampon disponible]
  CRON[14130]    (buildd) CMD (  /usr/bin/buildd-watcher)
  NetworkManager[1508]    <info> (wlan0): device state change: disconnected -> unavailable (reason 'none') [30 20 0]
  NetworkManager[1508]    <info> (wlan0): deactivating device (reason 'none') [0]
  NetworkManager[1508]    <info> (wlan0): taking down device.
  NetworkManager[1508]    <info> WiFi hardware radio set disabled
  NetworkManager[1508]    <info> WiFi now disabled by radio killswitch
  NetworkManager[1508]    <warn> error monitoring device for netlink events: Aucun espace tampon disponible
```

8 giga + 10 gigaSWAPP ? : No buffer space available  ???:lolflag:



```
freeman@freeman-Sniper:~$ inxi -b
System:    Host: freeman-Sniper Kernel: 3.13.0-80-generic x86_64 (64 bit) Desktop: Gnome 3.10.4 Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: G1.Sniper Bios: Award version: F1 date: 01/17/2011
CPU:       Quad core Intel Core i7 CPU 930 (-HT-MCP-) clocked at 2860.314 MHz 
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280] 
           X.Org: 1.15.1 drivers: ati,fglrx (unloaded: fbdev,vesa,radeon) Resolution: 1920x1080@60.0hz 
           GLX Renderer: AMD Radeon HD 7900 Series GLX Version: 4.5.13399 - CPC 15.20.1013
Network:   Card-1: D-Link System DGE-528T Gigabit Ethernet Adapter driver: r8169 
           Card-2: Realtek RTL8187 Wireless Adapter driver: rtl8187 
Drives:    HDD Total Size: 5815.3GB (32.5% used)
Info:      Processes: 315 Uptime: 14:41 Memory: 3296.3/7982.7MB Client: Shell (bash) inxi: 1.9.17
```

01/03/2016 11:04:09    freeman-Sniper    NetworkManager[1508]    message repeated 11 times: [ <warn> error monitoring device for netlink events: No Buffer Space Available/Aucun espace tampon disponible]

HDD Total Size: 5815.3GB (32.5% used)
Info:      Processes: 315 Uptime: 14:41 Memory: 3296.3/7982.7MB 

8 giga + 10 de SWAPP ? : No Buffer Space Available  ???

sudo apt-get update / sudo apt-get upgrade /sudo apt-get dist-upgrade /sudo install -f /sudo install -y /sudo apt-get autoclean/sudo apt-get clean/sudo apt-get autoremove/ 

purge dpkg config :   	 	 	 	   
sudo dpkg -P `dpkg -l | grep "^rc" | tr -s ' ' | cut -d ' ' -f 2`


 / reboot...

and

and

the same thing......:guitar:

---

### Post by The Cog on 2016-03-01
Google translate says that message means "No buffer space available".

---

### Post by valereguerin on 2016-03-01
[                                                      [IMG]http://ubuntuforums.org/customavatars/avatar437760_41.gif[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=437760")                                                                                     [**[COLOR=#DD4814][B]The Cog**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=437760")      
                         [IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG]
\\:D/\\:D/\\:D/:mrgreen:=d>:-k

My wi-fi  engine  works perfectly  with all my : ubuntu/Cubuntu/Kubuntu/Mint/..... Gnome/Unity/Cinnamon....(and more.....) since six years........

```
freeman@freeman-Sniper:~$ lspci | grep -i ethernet
08:00.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)
```

just shoot Proposed repository and downgrade,  **[https://askubuntu.com/questions/59443/how-can-i-revert-back-from-an-upgrade-to-the-proposed-repository](https://askubuntu.com/questions/59443/how-can-i-revert-back-from-an-upgrade-to-the-proposed-repository)**  ;  problem disappear and after recompile  come again ! HARGGGG
I open aptitude : aptitude say libssl:i386(stay not configured) (installed by ia32-lib dependency for....google earth....) conflict with openSSL !

All  the time Google Earth cause problem ! ....i investigate and come back,** i  look at this**  "[U][https://stackoverflow.com/questions/23182765/how-to-install-ia32-libs-in-ubuntu-14-04-lts-trusty-tahr](https://stackoverflow.com/questions/23182765/how-to-install-ia32-libs-in-ubuntu-14-04-lts-trusty-tahr)
[/U]
for reinstall ia32-lib with no problem dependency, i will see after compile....

and this : [URL="https://wiki.ubuntu.com/MultiarchCross"]https://wiki.ubuntu.com/MultiarchCross 

W:Failed to fetch file:/var/cache/apt-build/repository/dists/apt-build/main/binary-i386/Packages  File not found
  [/URL]

This  morning i shoot libssl:i386 and my connection works fine (for the  moment....) but now i reinstall ia32-lib (for My Google Earth !) with the "Stackoverflow link....  Libssl:i386 come back (dependency ia32-lib) ...i wait re-compilation for see (3,3giga in RAM...)

What do you think about MultiArchcross ?

[FONT=Franklin Gothic Medium][I][B][COLOR=Orange][U]~~~Open-source Software and Patience go hand in hand~~~

At the Beginning i hate aptitude today i love it !
[/U][/COLOR][/B][/I][/FONT]

---

### Post by slickymaster on 2016-03-01
@valereguerin
This is an English spoken forum so please write your posts in English unless you are participating in a Loco Forum. We have many users from many different countries, and English is the common language of these forums.

If you prefer, or you find it difficult to do it in English, you can always address your queries at [https://forum.ubuntu-fr.org/](https://forum.ubuntu-fr.org/)

---

