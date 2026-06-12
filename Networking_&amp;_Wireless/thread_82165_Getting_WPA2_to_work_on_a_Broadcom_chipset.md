---
title: "Getting WPA2 to work on a Broadcom chipset"
date: 2005-10-26
forum: Networking &amp; Wireless
---

### Post by sigma2805 on 2005-10-26
Hello Everyone!
First off let me say that I hope i'm not double posting this information.

This forum has helped me out ALOT over the past couple of months getting my laptop setup so i think its about time i contributed something back. I had to get a new router today cause my other one died so i got a new Linksys WRT54G because of linksys GPL'd the source code for this router(reason enough to support them :) ) and several people have made variants to it which i might be interested in. 

BTW: If you are using a WRT54G as well, make sure you upgrade the firmware to 4.20.7 which, as of this writing, is the most current version and  configure it under Wireless->Wireless Security to use WPA2 Personal with the AES algorithm.

Now for the fun part! Broadcom released a new set of drivers in July that supports WPA2. You can find them on compaq's website(i have a compaq so i'm biased :) ) by searching for  SP30379.exe which is a self extracting .exe file. Hopefully you have a windows machine nearby where you can grab the bcmwl5.inf file from the extracted folder.  copy this file to your linux cpu. Anyway once you have that file follow the instructions below to remove and then add the new driver

sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -i /(folder that the file is in)/bcmwl5.inf
now verify that the driver installed correctly by typing 
sudo ndiswrapper -l
you should see > Installed ndis drivers:
bcmwl5  driver present, hardware present


Then you need to edit your wpa_supplicant file to reflect the changes in your network configuration, mine looks like this

> 
ctrl_interface=/var/run/wpa_supplicant

ap_scan=2
network={
scan_ssid=1
ssid="myssid"
proto=WPA2
key_mgmt=WPA-PSK
pairwise=CCMP
group=CCMP
psk="mypsk"
}

The ap_scan=2 part tells your cpu to use wpa_supplicant to scan for hidden ssids as well as non-hidden and the pairwise and groupwise are set to CCMP which is actually AES encryption which according to [WikiPedia]("http://en.wikipedia.org/wiki/WPA2#Linux") is more secure from what i read.

Now reboot and hopefully it works. I will try to answer questions but i can't answer them all so hopefully some of the gurus on this forum can help out.

P.S. One of the more interesting side effects i encountered after loading the new drivers is that the blue wireless light for me now flashes when data is being sent and doesn't stay on consistently so if anyone could help me with configuring the light to stay on, i would appreciate it :)

---

### Post by AlexPJ on 2005-10-30
Hi sigma2805,

I've got a nearly identical setup to you: WRT54G and Broadcom (Buffalo WLI-CB-G54) on a Dell Laptop. I can't get it working; I can get WEP up though.  I feel that I am very close.

Noobs (like me) should note that I found threads 25683 and 31418 really helpful - to fill the bits about the repositories etc

Can you tell me what you put in the WAP security boxes please? Was it the hex?  There is a little detail I have missed somewhere!

Thanks in advance,

Al.

---

### Post by sigma2805 on 2005-10-30
hi. If you are referring to the wpa_supplicant file, then the passphrase i used was the actual passphrase in quotes....Meaning i didn't convert it to hex. wpa_supplicant will do that by itself if its required. can you post your wpa_supplicant file so i can take a look? feel free to change your passphrase and ssid.

---

