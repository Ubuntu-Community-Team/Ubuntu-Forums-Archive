---
title: "Setting up Ad-Hoc network for iPod Touch"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by XWingz87 on 2007-11-09
I have problem getting my ad-hoc network running for my iPod touch.  I run Kubuntu Fesity Fawn 7.04, and I don't consider myself linux-savvy, so any help would be appreciated.  Thank you.

Here's what I get after I set it up.

xtc@Xiaotian-Linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"xtcipod"
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1782   Missed beacon:0


xtc@Xiaotian-Linux:~$ lspci | grep 3945
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by XWingz87 on 2007-11-26
Come on guys, there's been almost 150 views and no replies?  Is the problem _that_ difficult to solve?

---

### Post by mikecomua on 2007-11-30
What exactly is a "ad-hoc network". If you just want to get into yout iPod's filesystem to get NES ROMs on it or something you have to install FileZilla ```
sudo apt-get install filezilla
```, then specify the user name as root, the password as alpine and port 22. Enter your iPod's IP and you're good to go. After you've done this you can also browse your iPod from Network in Nautilus.
P.S. Do you know any good program to convert videos to the ipod touch?

---

### Post by EddieT on 2007-12-02
For XP I use [MediaCoder]("http://mediacoder.sourceforge.net/") which has plugins for ipods and they work well with my touch.  As for a good Linux tool I haven't found one yet.

---

### Post by nwadams on 2007-12-13
i got the same problem, except i'm just trying to set up an ad-hoc network in general not specifically for the ipod touch but the same principle applies

---

### Post by 3rdtreenz on 2008-01-03
Hi, well this is very late, I came here trying to figure out a different problem, but I'm doing the same thing.  I use debian, but i think its basically the same. This is what I did to get an adhoc network with the ipod touch:

With my broadcom card, ad-hoc networking didn't work at all (cell:invalid) with the kernel native driver, so I had to use NDISwrapper instead for my wireless card.

added the following to /etc/network/interfaces:
"
auto eth0
iface eth0 inet static
wireless_essid itoucher
wireless_mode ad-hoc
wireless_channel 10
address 192.168.1.0
netmask 255.255.255.0
"
(eth0 being my wireless card)


I set my ipod to 192.168.1.1 and the connection works fine, can browse the web etc, and the ipod can ping out.  Unfortunately for some reason I can't ping the ipod though.

---

