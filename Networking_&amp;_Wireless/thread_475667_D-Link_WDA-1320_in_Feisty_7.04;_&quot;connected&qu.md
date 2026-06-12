---
title: "D-Link WDA-1320 in Feisty 7.04; &quot;connected&quot; but no Internet"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by ROCKOQATSI on 2007-06-16
This is a wireless card that many Ubuntu users seem to have good luck with, and what luck, I have one already installed in my system! But, after doing a clean install of Feisty 7.04, and although my card was instantly recognized and sniffed out my home network... I had no Internet. So I ran iwconfig, and it came out with:

lo   no wireless connections

eth0   no wireless connections

wifi0   no wireless connections

ath0   IEEE 802.11g ESSID: " "Nickname" "
          Mode: Managed Frequency: 2.437 GHz Access Point: Not Associated
          Bit Rate: 0kb/s Tx Power: 18 dBm Sensitivity=0/3
          Retry:off RTS thr:off Fragment thr:off Power Management:off
          Link Quality=0/94 Signal level=-95dBm Noise level=-95dBm
          Rx invalid nwid:2342 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Now, I'm a newb, but from here it looks to me like I had to establish an access point. So I set about doing that, with: wlanconfig ath0 create wlandev wifi0 wlanmode ap
And then it said:
The program 'wlanconfig' is currently not installed. You can install it by typing: sudo apt=get install madwifi-tools
Make sure you have the 'universe' component enabled
bash: wlanconfig: command not found

And after... sudo apt-get install madwifi-tools
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package madwifi-tools

And that lead me to believe that Feisty didn't ship with a complete working madwifi, and so I went back to Windows, downloaded the latest madwifi, went back to Feisty, found the folder, tried to compile it, and got a whole bunch of errors the likes of which I don't understand and didn't have the patience to copy! I apologize for being windy but I'm stating as much info as I possibly can because I want to get this f*cker off the motherf*cking ground, and I'm out of ideas.

Please... what am I doing wrong?

---

### Post by bradmayne on 2007-06-20
hey what you need to do is go to the synaptic package manager. Go to System, Administration, synaptic package manager.  then search for madwifi-tools. Then check the program and install from there.  BOOM!!  you got the goods installed from there. OR just plug into with an ethernet connection to someones network and do the same.

---

