---
title: "hostapd+madwifi - need a clear howto"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by andytof47 on 2007-02-05
Hi I have been reading and googling all day about this but I still don't have a working accesspoint....

I have an atheros network card and an 2 other wired cards in my system

1 is pppoe interface and I want the wireless to be able to allow others in the Network to log in or even just associate with and access internet with this setup.........

I have tried installing via synaptic hostapd because everytime I try to compile from source I get an error  hmmmm  something like this 


_madwifi.c
driver_madwifi.c:21:28: warning: include/compat.h: No such file or directory
driver_madwifi.c:22:32: warning: net80211/ieee80211.h: No such file or directory
driver_madwifi.c:28:39: warning: net80211/ieee80211_crypto.h: No such file or directory
driver_madwifi.c:29:38: warning: net80211/ieee80211_ioctl.h: No such file or directory
driver_madwifi.c: In function ‘set80211priv’:
driver_madwifi.c:136: error: ‘IEEE80211_IOCTL_SETPARAM’ undeclared (first use in this function)
driver_madwifi.c:136: error: (Each undeclared identifier is reported only once
driver_madwifi.c:136: error: for each function it appears in.)
driver_madwifi.c:137: error: ‘IEEE80211_IOCTL_CHANLIST’ undeclared (first use in this function)
driver_madwifi.c: In function ‘set80211param’:
driver_madwifi.c:182: error: ‘IEEE80211_IOCTL_SETPARAM’ undeclared (first use in this function)
driver_madwifi.c: In function ‘madwifi_configure_wpa’:
driver_madwifi.c:215: error: ‘IEEE80211_CIPHER_AES_CCM’ undeclared (first use in this function)
driver_madwifi.c:218: error: ‘IEEE80211_CIPHER_TKIP’ undeclared (first use in this function)
driver_madwifi.c:221: error: ‘IEEE80211_CIPHER_WEP’ undeclared (first use in this function)
driver_madwifi.c:227: error: ‘IEEE80211_CIPHER_NONE’ undeclared (first use in this function)
driver_madwifi.c:236: error: ‘IEEE80211_PARAM_MCASTCIPHER’ undeclared (first use in this function)
driver_madwifi.c:243: error: ‘IEEE80211_PARAM_MCASTKEYLEN’ undeclared (first use in this function)
driver_madwifi.c:258: error: ‘IEEE80211_PARAM_UCASTCIPHERS’ undeclared (first use in this function)
driver_madwifi.c:266: error: ‘IEEE80211_PARAM_KEYMGTALGS’ undeclared (first use in this function)
driver_madwifi.c:277: error: ‘IEEE80211_PARAM_RSNCAPS’ undeclared (first use in this function)
driver_madwifi.c:284: error: ‘IEEE80211_PARAM_WPA’ undeclared (first use in this function)
driver_madwifi.c: In function ‘madwifi_set_ieee8021x’:
driver_madwifi.c:347: error: ‘IEEE80211_PARAM_AUTHMODE’ undeclared (first use in this function)
driver_madwifi.c:348: error: ‘IEEE80211_AUTH_AUTO’ undeclared (first use in this function)
driver_madwifi.c:361: error: ‘IEEE80211_AUTH_WPA’ undeclared (first use in this function)
driver_madwifi.c:361: error: ‘IEEE80211_AUTH_8021X’ undeclared (first use in this function)
driver_madwifi.c: In function ‘madwifi_set_privacy’:
driver_madwifi.c:379: error: ‘IEEE80211_PARAM_PRIVACY’ undeclared (first use in this function)
driver_madwifi.c: In function ‘madwifi_set_sta_authorized’:
driver_madwifi.c:387: error: storage size of ‘mlme’ isn’t known
driver_madwifi.c:395: error: ‘IEEE80211_MLME_AUTHORIZE’ undeclared (first use in this function)
driver_madwifi.c:397: error: ‘IEEE80211_MLME_UNAUTHORIZE’ undeclared (first use in this function)
driver_madwifi.c:399: error: ‘IEEE80211_ADDR_LEN’ undeclared (first use in this function)
driver_madwifi.c:400: error: ‘IEEE80211_IOCTL_SETMLME’ undeclared (first use in this function)
driver_madwifi.c:387: warning: unused variable ‘mlme’
driver_madwifi.c: In function ‘madwifi_del_key’:
driver_madwifi.c:426: error: storage size of ‘wk’ isn’t known
driver_madwifi.c:435: error: ‘IEEE80211_ADDR_LEN’ undeclared (first use in this function)
driver_madwifi.c:436: error: ‘IEEE80211_KEYIX_NONE’ undeclared (first use in this function)
driver_madwifi.c:441: error: ‘IEEE80211_IOCTL_DELKEY’ undeclared (first use in this function)
driver_madwifi.c:426: warning: unused variable ‘wk’
driver_madwifi.c: In function ‘madwifi_set_key’:
driver_madwifi.c:457: error: storage size of ‘wk’ isn’t known
driver_madwifi.c:469: error: ‘IEEE80211_CIPHER_WEP’ undeclared (first use in this function)
driver_madwifi.c:471: error: ‘IEEE80211_CIPHER_TKIP’ undeclared (first use in this function)
driver_madwifi.c:473: error: ‘IEEE80211_CIPHER_AES_CCM’ undeclared (first use in this function)
driver_madwifi.c:488: error: ‘IEEE80211_KEY_RECV’ undeclared (first use in this function)
driver_madwifi.c:488: error: ‘IEEE80211_KEY_XMIT’ undeclared (first use in this function)
driver_madwifi.c:490: error: ‘IEEE80211_ADDR_LEN’ undeclared (first use in this function)
driver_madwifi.c:492: error: ‘IEEE80211_KEY_DEFAULT’ undeclared (first use in this function)
driver_madwifi.c:495: error: ‘IEEE80211_KEYIX_NONE’ undeclared (first use in this function)
driver_madwifi.c:500: error: ‘IEEE80211_IOCTL_SETKEY’ undeclared (first use in this function)
driver_madwifi.c:457: warning: unused variable ‘wk’
driver_madwifi.c: In function ‘madwifi_get_seqnum’:
driver_madwifi.c:518: error: storage size of ‘wk’ isn’t known
driver_madwifi.c:525: error: ‘IEEE80211_ADDR_LEN’ undeclared (first use in this function)
driver_madwifi.c:530: error: ‘IEEE80211_IOCTL_GETKEY’ undeclared (first use in this function)
driver_madwifi.c:518: warning: unused variable ‘wk’
driver_madwifi.c: In function ‘madwifi_sta_deauth’:
driver_madwifi.c:697: error: storage size of ‘mlme’ isn’t known
driver_madwifi.c:704: error: ‘IEEE80211_MLME_DEAUTH’ undeclared (first use in this function)
driver_madwifi.c:706: error: ‘IEEE80211_ADDR_LEN’ undeclared (first use in this function)
driver_madwifi.c:707: error: ‘IEEE80211_IOCTL_SETMLME’ undeclared (first use in this function)
driver_madwifi.c:697: warning: unused variable ‘mlme’
driver_madwifi.c: In function ‘madwifi_sta_disassoc’:
driver_madwifi.c:722: error: storage size of ‘mlme’ isn’t known
driver_madwifi.c:729: error: ‘IEEE80211_MLME_DISASSOC’ undeclared (first use in this function)
driver_madwifi.c:731: error: ‘IEEE80211_ADDR_LEN’ undeclared (first use in this function)
driver_madwifi.c:732: error: ‘IEEE80211_IOCTL_SETMLME’ undeclared (first use in this function)
driver_madwifi.c:722: warning: unused variable ‘mlme’
driver_madwifi.c: At top level:
driver_madwifi.c:743: error: ‘IEEE80211_ADDR_LEN’ undeclared here (not in a function)
driver_madwifi.c: In function ‘madwifi_process_wpa_ie’:
driver_madwifi.c:766: error: storage size of ‘ie’ isn’t known
driver_madwifi.c:774: error: ‘IEEE80211_ADDR_LEN’ undeclared (first use in this function)
driver_madwifi.c:775: error: ‘IEEE80211_IOCTL_GETWPAIE’ undeclared (first use in this function)
driver_madwifi.c:766: warning: unused variable ‘ie’
driver_madwifi.c: At top level:
driver_madwifi.c:811: error: ‘IEEE80211_ADDR_LEN’ undeclared here (not in a function)
driver_madwifi.c: In function ‘madwifi_wireless_event_wireless’:
driver_madwifi.c:942: error: type of formal parameter 2 is incomplete
driver_madwifi.c:945: error: type of formal parameter 2 is incomplete
driver_madwifi.c: In function ‘madwifi_set_countermeasures’:
driver_madwifi.c:1340: error: ‘IEEE80211_PARAM_COUNTERMEASURES’ undeclared (first use in this function)
make: *** [driver_madwifi.o] Error 1





So I would really appreciate help with this because it's driving me nuts and there just isn't a complete from begining to end howto regarding this particular setup


Thanks in advance
don't mind the whining

It will help alot of people in the end

---

### Post by BeachBum on 2007-03-21
I seem to have figured out how to get hostapd working, I still get errors but connectivity still works.  

Two things:
1. Hostapd is configured, by default, to compile with support only for the hostap driver, not madwifi (its easy to change though) so installing via synaptic won't do much good.
2. The error you're seeing is the installer telling you it cannot find the madwifi source drivers.  You should be able to get the madwifi drivers from synaptic, but its apart of the linux-restricted-modules package.

If you would like to use WPA/WPA2 etc, first create the virtual access point using the madwifi drivers
> wlanconfig ath0 create wlandev wifi0 wlanmode ap
and verify it works WITHOUT ENCRYPTION FIRST; try to connect from another computer.

Next, we download madwifi source from repos:
> sudo apt-get source linux-restricted-modules-2.6.xxx
where xxx is your kernel version.
Download hostapd source from repos:
>  sudo apt-get build-dep hostapd
and >  sudo apt-get source hostapd

You'll notice this downloads some tar.gz files and some directories.  To setup hostapd for installation:
1. cd into hostapd directory
2. edit defconfig, and uncomment 
> CONFIG_DRIVER_MADWIFI=y
CFLAGS += -I/path/to/linux-restricted-modules/madwifi
the madwifi sources are in the linux-restricted-modules directory we just downloaded.
3. > cp defconfig .config
4. Edit the hostapd.conf file to your needs, but do NOT TURN ON ENCRYPTION, not yet.
5. Run make and make install
7. Run > sudo hostapd -dddd /path/to/hostapds-src/hostapd.conf where -dddd is very verbose (for debugging), and the default spot for the hostapd.conf file is /etc/hostapd/hostapd.conf
Check the output in the terminal for major errors, and attempt to connect from another computer.  

If it works, you can edit /etc/hostapd/hostapd.conf to enable WPA or whatever you choose, just note, make sure the connecting card supports WPA or WPA2 (tkip or ccmp), and also, I was not able to connect with 
> wpa_pairwise=TKIP CCMP, instead I needed to change it to > wpa_pairwise=TKIP, though your mileage may vary.  Best of luck, and be sure to read the comments in hostapd.conf and google when in doubt!

When you are done setting everything up, you can kill the daemon from the terminal, and use the init scripts to start hostapd.

---

### Post by Paris Heng on 2007-07-24
Hi,

Do anybody there know how to install Hostapd ?

Please assist.

---

### Post by BeachBum on 2007-07-24
Please provide more details so we can help.  Are you using madwifi?  How familiar are you with Ubuntu/linux?

---

### Post by Paris Heng on 2007-07-24
> **BeachBum said:**
> Please provide more details so we can help.  Are you using madwifi?  How familiar are you with Ubuntu/linux?

(1) I am a newbie on Ubuntu, Yes, i am using Madwifi with Atheroes Chipset.
I want to build a access point in my home, so how to actually install this **Hostapd** daemon (NOT Hostap driver) ?

(2) After all, do i need to make it to be Master mode in the madwifi driver? If i install the Hostapd daemon? Are the below command is the must although i am installed the Hostapd?

**wlanconfig ath0 create wlandev wifi0 wlanmode ap **

(3) IF to install Hostapd --> But i having problem below (statement taken from READ ME file in Hostapd)

"madwifi driver for cards based on Atheros chip set (ar521x)
([http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/))
Please note that you will need to add the correct path for
madwifi driver root directory in .config (see defconfig file for
an example: CFLAGS += -I<path>)"

What is the meaning of the above statement? 

Problem: 
--> I don't know the way to install **Hostapd Daemon**

Please assist, HELP!! Thanx :confused:

---

### Post by Paris Heng on 2007-07-25
Hi Beach BUM, 

What u mean by 

**If it works, then copy the madwifi drivers to the hostapd directory** ---> previous post of your

How to locate the Madwifi driver? What u mean by it? It is **Madwifi-source**?

The **installed** Madwifi driver or the **not install** Madwifi driver?

---

### Post by Paris Heng on 2007-07-25
Anyway,

Can you show me the **complete guide to install the Hostapd**, because what you shown before on your post is abit confusing.

Thousand Thank!!!

---

### Post by BeachBum on 2007-07-25
I've updated my post above, please take a look and post any issues/ successes you have.

---

### Post by Paris Heng on 2007-07-26
HOW-TO] Master Mode + Madwifi + Bridging
Dear all,

I have installed Madwifi + Atheroes Wifi in the **laptop A**, and it work well.

I have made the Wifi card into Master Mode (access Point)**(laptop A**).
My another **laptop B** use to connect to it, but cannot!! It just able to scan and detect the availability of the access point where i created in **laptop A**.

Problems:

How I to enable **laptop B** to connect to **laptop A**? What i miss?

(1) Routing ?
(2) NAT ?
(3) DHCP ?
(4) Port Fowarding ?
(5) WPA ?


Please assist.

---

### Post by BeachBum on 2007-07-26
Easiest way is to use Firestarter on laptop A
>  sudo apt-get install firestarter
Run it from System -> Admin -> Firestarter (if in gnome, if in KDE just type kdesu firestarter) Once running, select preferences, and network settings, and set your LAN device (the one connecting to other computers, the wifi device), and enable internet sharing and DHCP.  This will do pretty much everything for you.  Definatly leave firestarter open when you try to connect from laptop B, as you can see if a connection is being made.  Otherwise, it is NOT necessary to have firestarter running all the time, as its only an interface to the ipchains kernel module, which saves firestarter's settings and runs automatically.  For more debugging, you can run hostapd from the command line > sudo hostapd -dddd /path/to/hostapds-src/hostapd.conf  and watch for errors, and you can either google them (best way, you learn yourself) or post them here. 

Otherwise, you can install dhcp3-server, though it will require tweaking some configuration files to get it working right.

Then from laptop B, use network manager (sudo apt-get install network-manager network-manager-gnome).  Once installed, from the run dialog box (alt+f2) type nm-applet.  In the nifty applet, click on it and locate laptop A, and connect.  If running wpa correctly on Laptop A, it should ask for the passphrase, and you should be good to go.

---

### Post by Paris Heng on 2007-07-29
> **BeachBum said:**
> Easiest way is to use Firestarter on laptop A

Run it from System -> Admin -> Firestarter (if in gnome, if in KDE just type kdesu firestarter) Once running, select preferences, and network settings, and set your LAN device (the one connecting to other computers, the wifi device), and enable internet sharing and DHCP.  This will do pretty much everything for you.  Definatly leave firestarter open when you try to connect from laptop B, as you can see if a connection is being made.  Otherwise, it is NOT necessary to have firestarter running all the time, as its only an interface to the ipchains kernel module, which saves firestarter's settings and runs automatically.  For more debugging, you can run hostapd from the command line  and watch for errors, and you can either google them (best way, you learn yourself) or post them here. 

Otherwise, you can install dhcp3-server, though it will require tweaking some configuration files to get it working right.

Then from laptop B, use network manager (sudo apt-get install network-manager network-manager-gnome).  Once installed, from the run dialog box (alt+f2) type nm-applet.  In the nifty applet, click on it and locate laptop A, and connect.  If running wpa correctly on Laptop A, it should ask for the passphrase, and you should be good to go.


Hi, Firestarter is for firewall purposes, how i can use it here? Thanx

---

### Post by BeachBum on 2007-07-30
Please read this: [http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

---

### Post by nickswift on 2007-08-04
Great set of instructions.

I get to step 6 and the dpkg barfs with an error I'm not sure about.

dpkg-buildpackage: source package is hostapd
dpkg-buildpackage: source version is 1:0.5.5-3.1
dpkg-buildpackage: source changed by Matt Brown <mattb@debian.org>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 0.5.5-3.1
 sudo debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
/usr/bin/make clean
make[1]: Entering directory `/home/nick/Desktop/hostapd-0.5.5'
rm -f core *~ *.o hostapd hostapd_cli nt_password_hash hlr_auc_gw
rm -f *.d driver_conf.c
make[1]: Leaving directory `/home/nick/Desktop/hostapd-0.5.5'
dh_clean
dpatch  deapply-all  
22_madwifi_plaintext not applied to ./ .
21_madwifi_includes not applied to ./ .
20_madwifi_headers not applied to ./ .
12_conf_etc_hostapd not applied to ./ .
10_config not applied to ./ .
rm -rf patch-stamp patch-stampT debian/patched
 debian/rules build
test -d debian/patched || install -d debian/patched
install: cannot create directory `debian/patched': Permission denied
make: *** [patch-stamp] Error 1
nick@www:~/Desktop/hostapd-0.5.5$ sudo dpkg-buildpackage -rsudo -uc -b
dpkg-buildpackage: source package is hostapd
dpkg-buildpackage: source version is 1:0.5.5-3.1
dpkg-buildpackage: source changed by Matt Brown <mattb@debian.org>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 0.5.5-3.1
 sudo debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
/usr/bin/make clean
make[1]: Entering directory `/home/nick/Desktop/hostapd-0.5.5'
rm -f core *~ *.o hostapd hostapd_cli nt_password_hash hlr_auc_gw
rm -f *.d driver_conf.c
make[1]: Leaving directory `/home/nick/Desktop/hostapd-0.5.5'
dh_clean
dpatch  deapply-all  
22_madwifi_plaintext not applied to ./ .
21_madwifi_includes not applied to ./ .
20_madwifi_headers not applied to ./ .
12_conf_etc_hostapd not applied to ./ .
10_config not applied to ./ .
rm -rf patch-stamp patch-stampT debian/patched
 debian/rules build
test -d debian/patched || install -d debian/patched
dpatch  apply-all  
applying patch 10_config to ./ ... failed.
make: *** [patch-stamp] Error 1

This might be related to the copying of the patch files (and everything else from the madwifi directory. Should have I only have copied some of the compiled output?

Nick

---

### Post by Paris Heng on 2008-01-30
Dear again,

I have the Madwifi running well and able to act as AP, client can connect and use the Internet. I just installed the hostapd from synaptic.

You did mentioned in step 5:

> 5. copy everything in the madwifi directory to the hostapd directory (when it asks you if you want to overwrite files, say no

Where is the madwifi directory located? and where is the hostapd direcotry located? 

Can you let me know the full PATH name? Quite tension with the hostapd now..

Please assist again. Thanx.

---

### Post by BeachBum on 2008-02-01
I haven't dealt with hostapd in quite some time since I got it working, (if it isn't broken then don't fix it), excuse me if I'm rusty.

The reason you're having issues with Hostapd is because it is packaged, by default, NOT to support madwifi.  This means that the hostapd deb does NOT come with the actual madwifi driver (so it can build support) and it means that a config file must be edited to build support for madwifi.

To enable support, download the madwifi sources as outlined in my original post, but you don't have to install them, just keep them downloaded.  Since you need to compile hostapd from sources, download the sources.  Following my guide, copy all the files from the madwifi source directory and say NO to overwriting anything, since you don't want to overwrite the hostapd ones.  Doing this copies all the files necessary for hostapd to build support for madwifi, and then some.  

Next, as my original post states, edit the .config file to enable madwifi support, and continue with my guide.

---

### Post by Paris Heng on 2008-02-02
Dear BeachBum,

I hope you can really help me out this time, I will show you what problems I am facing step by step, hope you will really assist me. Thank in advance. Below is so far what I am done and I stuck half ways in the middle. Basically I have perform 2 ways in installing the **hostapd**:

[COLOR="Red"]**1st way (I follow you posted instructions)[/COLOR]**

1. I have a working Madwifi acts as an AP, so I skipped the steps no. 1 to 6.

2. Step: > sudo apt-get build-dep hostapd

3. Step: > sudo apt-get source hostapd

4. The hostapd source is hostapd-0.5.5 and it  in downloaded into **/etc/hostapd-0.5.5**. Other downloaded files in /etc are:

> hostapd_0.5.5-3.1.diff.gz, hostapd_0.5.5-3.1.dsc, hostapd_0.5.5.orig.tar.gz 

5. Then, I cd into hostapd-0.5.5 and edit the file **.defconfig**:

> CONFIG_DRIVER_MADWIFI=y
CFLAGS += -I**[COLOR="Red"]/usr/src/madwifi-0.9.3.1[/COLOR]** # change to reflect local setup; directory for madwifi src

**/usr/src/madwifi-0.9.3.1** is where I make my madwifi driver.

6. I configured the **hostapd.conf **for my own needs.

> ######################### hostapd configuration file ##########################
#Experiemnt for WPA-PSK

interface=ath0
driver=madwifi
logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2
debug=4
dump_file=/tmp/hostapd.dump
ctrl_interface=/var/run/hostapd
ctrl_interface_group=0
ssid=heng_AP
macaddr_acl=0
accept_mac_file=/etc/hostapd.allow
auth_algs=1
wpa=1
wpa_passphrase=aaaaabbbbbcccccdddddeeeee
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP


7. Step: cp defconfig .config 

8. Copy everything in the madwifi directory to the hostapd directory (no overwrite):

> cp -R /usr/src/madwifi-0.9.3.1 /etc/hostapd-0.5.5

9. [COLOR="Red"]**Problems starting here:**[/COLOR]

> heng@heng:/usr/src$ dpkg-buildpackage -rfakeroot -uc -b
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is


What wrong here? The **-rfakeroot**, it is wrong when you type this?

> heng@heng:/usr/src$ sudo hostapd -dddd /path/to/hostapds-src/hostapd.conf
sudo: *[COLOR="Red"]hostapd: command not found[/COLOR]*


One major problems, actually hostapd command can't execute in terminal! How? This mean hostapd not yet installed, did i need to run? **[COLOR="Blue"]"make clean, make, make install"[/COLOR]** ?

> sudo /etc/init.d/hostapd restart

> heng@heng:/etc/init.d$ /etc/init.d/hostapd start
bash: /etc/init.d/hostapd: No such file or directory


I don't have hostapd file in /etc/init.d, how my going to start the hostapd? The daemon is not there.

10. I ignored your old post. It is ok? 


[COLOR="Red"]**2nd way (I installed from synatic the hostapd)[/COLOR]**

1. There are /etc/hostapd, but inside nothing, only one file >> **hostapd.conf**, even the defconfig and .config file did not have.

2. But, something different here is, it do have **/etc/init.d/hostapd**, I can start, stop and restart.

** Overall, what likely is my problem? Please help me, BeachBum, this all thing drive me insane. I hope you can really help me to figure out. :)

---

### Post by BeachBum on 2008-02-02
You cannot use the hostapd from repos cause it does not support madwifi, so uninstall it completely (dpkg --purge hostapd)

You need to run dpkg-buildpackage from the hostapd sources directory, I see here **heng@heng:/usr/src$** you are in the directory /usr/src, when to build the package, you must be in the hostapd source directory, so cd to /etc/hostapd-0.5.5, then try it again.

---

### Post by Paris Heng on 2008-02-02
> **BeachBum said:**
> You cannot use the hostapd from repos cause it does not support madwifi, so uninstall it completely (dpkg --purge hostapd)

You need to run dpkg-buildpackage from the hostapd sources directory, I see here **heng@heng:/usr/src$** you are in the directory /usr/src, when to build the package, you must be in the hostapd source directory, so cd to /etc/hostapd-0.5.5, then try it again.

Thank again. Did i need to run [COLOR="Blue"]"make clean, make, make install"[/COLOR]  in the /etc/hostapd-0.5.5? Going for meeting now, I try it later. Thank a lot. Any problem i will post again.

---

### Post by BeachBum on 2008-02-02
> **Paris Heng said:**
> Thank again. Did i need to run [COLOR="Blue"]"make clean, make, make install"[/COLOR]  in the /etc/hostapd-0.5.5? Going for meeting now, I try it later. Thank a lot. Any problem i will post again.

Nope, when you run dpkg-buildpackage, it creates a .deb package, which you should put somewhere safe because its basically an installer for hostapd.  Once the package is built, install the package with something like: 
> sudo dpkg -i hostpad...deb
where hostapd....deb is the filename of the .deb package, then reboot and that should be it.

---

### Post by Paris Heng on 2008-02-02
Dear BeachBum,

I stuck here again. 

***[COLOR="Blue"]Problems:[/COLOR] Error, same problems as [I]nickswift's* post.[/I]**

> root@heng:/etc/hostapd-0.5.5# dpkg-buildpackage -rfakeroot -uc -b
dpkg-buildpackage: source package is hostapd
dpkg-buildpackage: source version is 1:0.5.5-3.1
dpkg-buildpackage: source changed by Matt Brown <mattb@debian.org>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 0.5.5-3.1
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
/usr/bin/make clean
make[1]: Entering directory `/etc/hostapd-0.5.5'
rm -f core *~ *.o hostapd hostapd_cli nt_password_hash hlr_auc_gw
rm -f *.d driver_conf.c
make[1]: Leaving directory `/etc/hostapd-0.5.5'
dh_clean
dpatch  deapply-all  
22_madwifi_plaintext not applied to ./ .
21_madwifi_includes not applied to ./ .
20_madwifi_headers not applied to ./ .
12_conf_etc_hostapd not applied to ./ .
attempting to revert failed patch 10_config from ./:
  md5sums match, proceeding ... done (neither success nor failure guaranteed)
rm -rf patch-stamp patch-stampT debian/patched
 debian/rules build
test -d debian/patched || install -d debian/patched
dpatch  apply-all  
applying patch 10_config to ./ ... failed.
make: *** [patch-stamp] Error 1




What should I do later are,

1.
> root@heng:/etc/hostapd-0.5.5#sudo hostapd -dddd /path/to/hostapds-src/hostapd.co

***[COLOR="Blue"]Problems:[/COLOR] /path/to/hostapds-src --------> It is correct path***?

2. 
> sudo dpkg -i hostpad-0.5.5deb

***[COLOR="Blue"]Problems:[/COLOR] Where the .deb will be created? in /usr/bin? or /my current directory***?

3. 
> sudo /etc/init.d/hostapd restart

Please help me, I just left this few steps.

---

### Post by kevdog on 2008-02-03
Paris -- Seems like a great guide

When would I need to follow this guide?

---

### Post by Paris Heng on 2008-02-03
> **kevdog said:**
> Paris -- Seems like a great guide

When would I need to follow this guide?

Hi, this guide for building access point with madwifi + hostapd and it not complete and success yet. I actually building access point using Ubuntu, so now I want to make my access point able to provide WPA-PSK, WPA-EAP (Radius Server). This possible using hostapd. 

I stuck somewhere in the middle for building the hostapd package. I waiting for Mr.BeachBum to reply my previous post. He is very helpful.

---

### Post by kevdog on 2008-02-03
Got it -- basically adds various authentication capabilities to the underlying access point capabilities present with madwifi.  I'll keep my eye on the thread for possible solutions.

---

### Post by BeachBum on 2008-02-03
Instead of making a deb package, try to install hostapd the regular way, .configure, make, make install.

---

### Post by Paris Heng on 2008-02-04
> **BeachBum said:**
> Instead of making a deb package, try to install hostapd the regular way, .configure, make, make install.

Dear BeachBum,

I have issued the [COLOR="Blue"]make[/COLOR] and [COLOR="Blue"]make install[/COLOR] command. The ./configure is not there.

Success with the [COLOR="Blue"]***make***[/COLOR],

> root@heng:/etc/hostapd-0.5.5# make
.
.
.
.
.


Success with the ***[COLOR="Blue"]make install[/COLOR]***

> root@heng:/etc/hostapd-0.5.5# make install
for i in hostapd hostapd_cli; do cp $i /usr/local/bin/$i; done


Success to run the command [COLOR="Blue"]***hostapd***[/COLOR]

> root@heng:/etc/hostapd-0.5.5# hostapd
hostapd v0.5.5
User space daemon for IEEE 802.11 AP management,
IEEE 802.1X/WPA/WPA2/EAP/RADIUS Authenticator
Copyright (c) 2002-2006, Jouni Malinen <jkmaline@cc.hut.fi> and contributors

usage: hostapd [-hdBKtv] [-P <PID file>] <configuration file(s)>

options:
   -h   show this usage
   -d   show more debug messages (-dd for even more)
   -B   run daemon in the background
   -P   PID file
   -K   include key data in debug messages
   -t   include timestamps in some debug messages
   -v   show hostapd version


***[COLOR="Red"]Problems:[/COLOR] I can't find hostapd in /etc/init.d. I can't invoke the following command. How I going to know the hostapd in status? Anyway?***

> sudo /etc/init.d/hostapd restart

***[COLOR="Red"]Problems:[/COLOR] Sorry to ask about this. Which of the following configuration in [B].config** is correct? The (1) or (2)?*[/B]

> (1) CFLAGS += -I[COLOR="Red"]**/usr/src/madwifi-0.9.3.1**[/COLOR]
(2) CFLAGS += -I[COLOR="Red"]**../usr/src/madwifi-0.9.3.1**[/COLOR]


Thank for your help so far. This my last problems. How to start the ***hostapd***? :)

---

### Post by Paris Heng on 2008-02-04
Hi,

Hope to see your post Mr. BeachBum, I am having one week holiday for Chinese New Year. See you at the end of weekend.

---

### Post by Paris Heng on 2008-03-07
Finally, the problems of hostapd with madwifi solved. I able to have my WPA-PSK with hostapd!! I am going to have my WPA-EAP with Radius server later.
Thank you for your all valuable assistance, especially Mr. BeachBum.  I will post all the things in the end of May, I am leaving the country for national service training. Bravo!

---

### Post by Paris Heng on 2008-05-04
[B][I][Solved]
[/I][/B]
This is the tested complete How-to on Hostapd (You can configure both WPA-PSK and RADIUS):

WEP can be easily cracked with some sniffing software. In order to have more secured access point, it is a need of some advance encryption techniques like WPA, WPA2 and RADIUS server authentication. The task is very easy to accomplish with Hostapd. Hostapd is an access point daemon.  Download and compile the latest version of Hostapd and copy hostapd.conf to the preferred location.

To configure the AP with the Hostapd authenticator, the following are the instructions:

1. Make sure the wireless NIC card is in Master Mode. 

2. Download the Hostapd daemon from the website, [http://hostap.epitest.fi/hostapd/](http://hostap.epitest.fi/hostapd/), the release version used for installation is hostapd-0.5.10.tar.gz. Alternative way to get the source package is: 

> #wget [http://hostap.epitest.fi/releases/hostapd-0.5.10.tar.gz](http://hostap.epitest.fi/releases/hostapd-0.5.10.tar.gz) 

3. Compile and untar the package and then change directory into hostapd-0.5.10 directory:

> # tar xzvf hostapd-0.5.10.tar.gz
   # cd hostapd-0.5.10


4. As the driver used is MadWifi, edit the file defconfig in Hostapd directory and uncomment it (Read the Requirements under README). The path for the MadWifi driver is /usr/src/madwifi-0.9.3.1. 

> # CONFIG_DRIVER_MADWIFI=y
   # CFLAGS += -I /usr/src/madwifi-0.9.3.1


5. Create a new file .config and copy the contents of defconfig into it:

> # cp defconfig .config

6. Install the Hostapd:

>   # make clean
   # make
   # make install


7. Edit the hostapd.conf configuration file to specify the exact functionality of the Linux-based AP. The hostapd.conf must configure correctly in order for the authenticator to run without error. More option on the configuration, visit:  [http://www.devicescape.com/docs/uwp/package_guide/pkg_hostapd.php#wp135299](http://www.devicescape.com/docs/uwp/package_guide/pkg_hostapd.php#wp135299)

8. Finally, to run this without error, the wireless card must be in the AP mode. Start up the access point by running (Refer hostapd man page for more options):

> # hostapd -dd -K -t /etc/hostapd-0.5.10/hostapd.conf

Regards :guitar:

-----------------------------
[Paris Heng @ Wifi-Linux]("http://parisheng.110mb.com/")

---

