---
title: "Wondering if anyone has ideas??"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by bmachia on 2008-11-08
Hi
Since my re-build to Ubuntu 8.10 (Intrepid Ibex), I'm hanging on boot/timing out on "Configuring Network Interfaces".  After doing some research, I found this hang is coming from /etc/network/interfaces.

My interfaces file looks like this;
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
auto wlan0

I believe my problem is that the laptop is looking for a dhcp server at boot.  When it doesn't find it, the script moves on.  But, the hang-time is really too long.

To stay Secure I use WAP2 and I hid my SSID.  This is for reasons of the neighborhood.  So far my out of sight-out of mind concept seems to be working and I'd really like to keep it that way.

Does anyone have suggestions how I can stop the hang, (i.e. delay in boot time)?

Is this something I can comment out of the grub script, without getting into too much trouble?  
Or, are there easier ways to accomplish my goal?

Bill

---

### Post by Steve1961 on 2008-11-08
if you're using network-manager you shouldn't need the wlan entry in /etc/interfaces. Try commenting out it by putting a # in front of each line

---

### Post by bmachia on 2008-11-08
Hi Steve
Thanks for the reply.

Over the years, the automatics of WICD and KNetworkManager have gotten me in trouble.  Consequently, I've become a purest, in that I use Command lines and shell scripts to connect to my networks.  I feel they are more reliable and a-bit faster.

I'm just wandering if there is anyway to edit the GRUB script to comment out the "Configuring Network Interfaces" line\call?

Bill

---

### Post by Steve1961 on 2008-11-08
Hmmm, man grub doesn't seem to offer any real advice.  The only thing I can suggest is to comment out those lines I suggested, and when you want wireless just uncomment them and do a sudo /etc/init.d/networking start.

A bit long-winded I know, and there must be a better way to do it but I can't think of anything off the top of my head.

---

### Post by bmachia on 2008-11-08
Thanks Steve,
We're both thinking the same way.  There has got to be an easier way, but my light bulb is dim at the moment.

If I come up with something, I'll post it here..

Bill

---

### Post by bmachia on 2008-11-08
Well, I found a solution to my problem...

I added the below wireless-essid line to my interfaces file, so it now looks like this in the wireless section:
iface wlan0 inet dhcp
wireless-essid xxxxxxxx   (replace the xxxx's with your own hidden essid)
auto wlan0


With this little change, I no longer need my commands or script file.  
(i.e. 
sudo -S ifconfig wlan0 down
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid "xxxxxx"
sudo iwconfig wlan0 mode Managed
sudo ifconfig wlan0 up
sudo dhclient wlan0
)

Hope this helps someone in the future...

Bill

---

