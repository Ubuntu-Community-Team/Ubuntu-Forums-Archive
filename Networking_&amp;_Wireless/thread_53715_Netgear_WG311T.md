---
title: "Netgear WG311T"
date: 2005-08-01
forum: Networking &amp; Wireless
---

### Post by CsmcDem on 2005-08-01
Hello,
I don't have much knowledge on Linux. I have just recently installed Ubuntu 5.0.4. During installation, one step was to enter your network information, i tried putting in the SSID (S: ) and putting in the code. Neither of them worked. I was very frustrated ](*,) , and could not take it anymore so i decided to skip that part of the installation. Everything is fine, but my internet connection wont work (im using XP to post this) i'd rather use ubuntu all the time, but now i can only go on for things that don't require the internet. If you have the same desktop card and have solved this problem please respond, or email me at [email]CsmcDem@gmail.com[/email] (please only email me for this  forum)

thanks
classified user  :smile:

---

### Post by amohanty on 2005-08-01
Why not connect via an ethernet cable for the install and setup your wireless card later?

AM

---

### Post by andhraandroid on 2005-09-05
I am experiencing the same problem. I'm not just new to linux I'm pretty ignorant about computers in general especially  the networking stuff. I tried searching online but found nothing that helped me i couldnt get the madwifi drivers to work either. Could someone please help me i like the feel of ubuntu and dont want to switch back to windows. Thanks

---

### Post by tehwa on 2005-09-06
Hi Guys,

I am using a WG311T under ubuntu, I can help you get this card working.

Can you please run ```
lspci
``` in the terminal, and post the ouput. Thanks.

---

### Post by escuchamezz on 2005-09-06
fcgb

---

### Post by tehwa on 2005-09-07
[QUOTE=escuchamezz]can't get this to work either, even under installing a newer version of madwifi, i guess i'll wait for breezy  :neutral:[/QUOTE]
I don't understand you, I just said it works under Hoary. Believe it or not it is supported out of the box, and I have also got it working with ndiswrapper1.2.

---

### Post by acostanza on 2005-09-18
Hello Tehwa and others who know what they are doing,

I just installed breezy badger 5.10 and I'm having difficulty getting my WG311T running.  I believe I am setting it up correctly within the graphical network settings dialogue because under wireless conection (ath0) it picks up my wireless ID (ESSID) and I turned off WEP and am trying to set up the DHCP.  

However, I still can't get online. I can run "lspci" but I don't understand the output.  Any ideas on how to proceed?  

Thanks,
-Adam

---

### Post by tehwa on 2005-09-19
[QUOTE=acostanza]Hello Tehwa and others who know what they are doing,

I just installed breezy badger 5.10 and I'm having difficulty getting my WG311T running.  I believe I am setting it up correctly within the graphical network settings dialogue because under wireless conection (ath0) it picks up my wireless ID (ESSID) and I turned off WEP and am trying to set up the DHCP.  

However, I still can't get online. I can run "lspci" but I don't understand the output.  Any ideas on how to proceed?  

Thanks,
-Adam[/QUOTE]
When I do a fresh install with this card, it occasionally does this to me too. Often, running ```
sudo ifdown ath0
``` then ```
sudo ifup ath0
``` helps it along. I have no idea why  :? .

If that doesn't help it, please post the output.

---

### Post by acostanza on 2005-09-19
I tried those instructions, but it didn't kick my problem.  It tried to do a bunch of DHCDISCOVER on port 67 at different intervals after the 'sudo ifup ath0' instruction.

Maybe this will help, it's the output from the instruction 'lscpi' on my machine:

> everythink@everythink-server:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440GX - 82443GX Host bridge
0000:00:01.0 PCI bridge: Intel Corp. 440GX - 82443GX AGP bridge
0000:00:0c.0 SCSI storage controller: Adaptec AIC-7896U2/7897U2
0000:00:0c.1 SCSI storage controller: Adaptec AIC-7896U2/7897U2
0000:00:0e.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev08)
0000:00:12.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:12.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev01)
0000:00:12.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev01)
0000:00:12.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:14.0 VGA compatible controller: Cirrus Logic GD 5480 (rev 23)
0000:01:0f.0 PCI bridge: Digital Equipment Corporation DECchip 21150 (rev06)
0000:02:04.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

Thank you for the help, I admit I'm just getting into all this and I'm quite paralyzed without internet access :)
-Adam

---

### Post by tehwa on 2005-09-20
[QUOTE=acostanza]I tried those instructions, but it didn't kick my problem.  It tried to do a bunch of DHCDISCOVER on port 67 at different intervals after the 'sudo ifup ath0' instruction.

Maybe this will help, it's the output from the instruction 'lscpi' on my machine:



Thank you for the help, I admit I'm just getting into all this and I'm quite paralyzed without internet access :)
-Adam[/QUOTE]
what was the output of ifup ath0?

---

### Post by tehwa on 2005-09-20
Sorry, I might clarify that last post. If you can paste the output of ifup ath0, it will have some clues as to why the DHCP server can't give your card an address. lspci says the card is OK on the hardware side.

I have gotten this card working many ways under Hoary, Breezy is another story.

---

### Post by [pl]ice on 2005-09-20
WG311T got a newer model out, which doens't work on prism 2 chip, thus it's not the wiki describes :/
   i sold mine WG  :D , but there are people that made it working, ( i didn't bother got another wlan card)
links :  ;)
[http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972)
[http://ubuntuforums.org/showthread.php?t=39073&highlight=WG311T](http://ubuntuforums.org/showthread.php?t=39073&highlight=WG311T)
[http://ubuntuforums.org/showthread.php?t=53715&highlight=WG311T](http://ubuntuforums.org/showthread.php?t=53715&highlight=WG311T)
[http://ubuntuforums.org/showthread.php?t=27268&highlight=WG311T](http://ubuntuforums.org/showthread.php?t=27268&highlight=WG311T)
[http://ubuntuforums.org/showthread.php?t=25534&highlight=WG311T](http://ubuntuforums.org/showthread.php?t=25534&highlight=WG311T)
h

---

