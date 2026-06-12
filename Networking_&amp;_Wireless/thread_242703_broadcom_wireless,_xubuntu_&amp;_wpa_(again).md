---
title: "broadcom wireless, xubuntu &amp; wpa (again)"
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by loopyzort on 2006-08-24
Hello all, I've scoured all the forums stuff extensively, it seems there are so many people with problems getting WPA working that it's getting harder to find current, relevant walkthroughs on the many approaches available for Ubuntu wireless. Anyhow, I did this once before, so I know it's possible, but it was under Ubuntu not Xubuntu.

My setup:
 - Dell Dimension 9100
 - Xubuntu (running fine)
 - Broadcom wireless card (BCM4306)
 - Apple Airport using WPA

I've seen this article, which was helpful in getting my system to recognize my card: [http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

However, there seems to be open debate about whether fwcutter is better than ndiswrapper. There is also news that the broadcom drivers are native in the latest Linux Kernel, which may break everything I do between now and when Xubuntu pushes out a kernel upgrade.

Anyway, after using fwcutter to get my wireless card recognized, I try to run wpa_supplicant from a command line:
sudo wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant.conf -dd

I repeatedly get a loop where it says it authenticated but association failed (or something like that, I'm typing this from my XP box). Anyhow, I'm using Xubuntu, so I don't want to throw the Network-manager gnome applet in there, is there a clean way to do this? Should I just run out and buy a $70 non-broadcom card and call it a day? Why is wireless & WPA so difficult in Ubuntu (even when I used Network-manager it took several hours to get everything rolling).

Thank you, sorry if this is redundant but googling specific strings from my wpa_supplicant output produced suprisingly few results.

---

### Post by loopyzort on 2006-08-26
Okay, after about 6 hours I figured all of this out and would like to share with anyone else who may be feeling my pain. I am now running ndiswrapper for my wireless card driver and wpa_supplicant (on boot) for WPA network connection.

My setup:
- Dell Dimension 9100
- Xubuntu - fantastic, clean distro
- Broadcom wireless card (BCM4306 ver 03), aka Linksys WMP54G
- Apple Airport AP using WPA

My steps:
- Start with a brandy spanking new install of xubuntu to ensure no stale settings interfere with my setup
- Install ndiswrapper through Synaptic (using wired connection)
- Copy the bcm inf & sys files off my Linksys wireless card cd into a directory on my machine
- Run 'sudo ndiswrapper -i /location_of_your_wireless_driver/your_driver.inf'
- Run 'sudo ndiswrapper -l' to confirm it was installed
- Run 'sudo vi /etc/modprobe.d/blacklist', add ‘bcm43xx’ to the end
- Run 'sudo modprobe ndiswrapper'
- Run 'sudo ndiswrapper -m', then change the file it specifies (/etc/modprobe.d/ndiswrapper) to point to ‘eth1’, rather than 'wlan0', as that's where my machine thinks the wireless card should be
- Run 'sudo vi /etc/modules' and add 'ndiswrapper' to the end of the file
- Open Network Administrator and activate eth1 if it's not already active
- Reboot
- Now Network Administrator recognizes eth1 as active!
- Run wpa_supplicant in a terminal using conf file (see below) and the ndiswrapper driver: 'sudo wpa_supplicant -ieth1 -Dndiswrapper -c/etc/wpa_supplicant.conf -dd' - If you have trouble here, scour the net/boards, as there's a wealth of debug info on troubleshooting wpa_supplicant
- To get wpa_supplicant to connect via '/etc/init.d/networking', I had to do a few more things:
- Read the docs at/usr/share/doc/wpasupplicant/README.modes and implement accordingly, which involved editing my /etc/network/interfaces file to have:
'iface eth1 inet dhcp
wpa-driver ndiswrapper
wpa-conf /etc/wpa_supplicant.conf
auto eth1'
- Reboot, viola!
- I'm connecting to an Apple Airport using WPA, so here's my /etc/wpa_supplicant.conf (for those who are interested). I 'chmod 600' this thing to keep keys hidden from common folk:

"ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

network={
        ssid="my network"
        scan_ssid=1
        key_mgmt=WPA-PSK
        proto=WPA
        group=CCMP TKIP
        psk=my hex key
}
"

BTW, I posted this from Xubuntu over wireless, so all is well for me. I sympathize with all those who've gone through similar pains to get WPA working in Xubuntu. I suppose my setup is a bit atypical, and most people will use Network-Manager w/o a Broadcom card, but if you don't want to pull Gnome stuff into Xubuntu, this should do the job.

Cheers,
lz

---

### Post by anansi on 2006-10-15
what if your network doesn't have a hex key, but a ascii key?
referring the this line from the wpa_supplicant.conf file
 psk=my hex key
what do you replace psk with to provide "my ascii key"?

---

### Post by anansi on 2006-10-17
ok, figured that out
in terminal:
 wpa_passphrase "your network ssid" [passphrase]

where passphrase is the ascii key.

this displays the hex form of ur key that you can cut and paste into your /etc/wpa_supplicant.conf file

btw nice work loopyzort!

---

### Post by kcrouth on 2007-08-03
Wow, your post helped me to finally get my WPA working!
I'm on a Dell D-600 w/ Broadcom card. I had the first part 
working (for WEP) but your WPA help took me the rest of the 
way.

Question.. what do I do when I want to connect to another WPA 
access point? Is there any GUI or do I just repeat the steps to 
generate the key for the /etc/wpa_supplicant.conf?

THANK YOU so much for taking the time to help us!!!

kevin

---

### Post by ugm6hr on 2007-08-04
> **kcrouth said:**
> 
Question.. what do I do when I want to connect to another WPA 
access point? Is there any GUI or do I just repeat the steps to 
generate the key for the /etc/wpa_supplicant.conf?


If you want a GUI - I would recommend Wicd.  If not - manual config is the only way in Xubuntu.

Wicd is lighter than Network-Manager, and is not Gnome dependent - so is a better fit for Xubuntu.

See the link in my signature.

---

### Post by Sp|ke on 2007-09-14
> **ugm6hr said:**
> If you want a GUI - I would recommend Wicd.  If not - manual config is the only way in Xubuntu.

Wicd is lighter than Network-Manager, and is not Gnome dependent - so is a better fit for Xubuntu.

See the link in my signature.

ugm6hr you are a diamond!

It took me 10 mins to set up NDISWRAPPER (Linksys WPC11 ver 4 :( ) I then spent the best part of 2 days faffing around trying to get wpa_supplicant to work with no success at all.

It took all of 2 mins with Wicd

Thank you!

S.

---

