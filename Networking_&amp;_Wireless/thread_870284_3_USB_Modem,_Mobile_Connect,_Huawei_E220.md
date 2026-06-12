---
title: "3 USB Modem, Mobile Connect, Huawei E220"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by TDFlanders on 2008-07-25
Hi,

I apologize for posting a new thread here, but unfortunately I have to state that I am in a really rather tight spot here. I need some medical attention in Belgium ASAP, while I'm trapped in Belfast, UK at the moment. I am on a NHS waiting list, but I have no illusions. Problem is I can not easily get of the island since my wallet was stolen and the embassy is in London. So thanks to Belgian bureaucracy I have to go to Dublin to fix traveling documents in the embassy there. Actually I also lost my drivers license, but hey, I'll just have to become an outlaw there I suppose and drive there anyway. In the mean time windows came crashing down on me and I had to download an ISO image of XP Professional through my Ubuntu partition and managed to max out my house mates bandwidth I suppose, while he is on holiday, and I now could also not book a flight or ferry anymore, or look up the road to or address of the Dublin embassy anymore unfortunately. So luckily I had already installed Virtual Box and installed XP SP2 on it after my wireless died. I went to the shop and bought me a 3 USB Modem with a 25 quid top up which should give me 15 gigs. Unfortunately it did not install properly on Ubuntu 8.04 (2.2.19 I think?), so I called 3 customer support after I followed the offline troubleshooter for 8.04 in the terminal. It could not help me and told me to ask my ISP what the primary and secondary DNS are. I do already have the thing installed, mostly through seriously messing around with wine and stuff and through the command-line installing file by file in /bin/* or something. The end result is that I have a 3 USB Modem Logo and can launch the application but when I press on connect the button is just dead. The guy at the phone for 3 broadband support said he could not help me since they only provide support for Mac and MS Windows. He doesn't know any DNS, since the plug and play modem takes care of that. He just knows the IPN is 3internet. At the waiting length for their service, given I am calling through a Belgian subscription subscription GSM, I don't think I am going to call them back. It is probably a lot cheaper to have my parents spice up my HSBC account, after a three day wait for 'oversea' transfers, and buy a bottom end piece of junk Dell at Tesco and resell it later on at eBay with a power grid adapter. Big business will be happy. I hope they plant a tree on my grave, as long as it is not a catholic, protestant or socialist one. Sorry for the sarcasm, I am just loosing the frail ends of whatever feeble sanity I had still left. It looks like the joke is on me here anyway, I don't find it that funny either. Luckily the black album still works. 

A few things about my configuration:
Acer Aspire 9410-4933
Intel Core Duo T2450
2 GHz, 533 MHz FSB, 2 MB L2 cache
17" WXGA+ Acer CrystalBrite LCD
160GB HDD (dual)
DVD+-RW
2GB DDR2
802.11a/b/g wireless LAN

1 Vista Ultimate partition, legal version, totally dead
1 Ubuntu 8.04 partition with 40 GB spare
1 swab (1GB)
1 3GB eternalized XP SP2 partition (now active)

Varia:
I left my 32-bit Vista upgrade CD at home and the 64 version won't do it I'm afraid. I also have an active One Care License and the install disk. I also have a System restore thing done on a 500 GB Seagate Smart drive, that died on me earlier this month.
I could not get connection on my Virtual Box XP Machine, since the offline man pages didn't quite help me with finding how to set up the right USB port. I have discovered six of them and counting. Now I have connection I can sort that all out. I will also have to restore GRUB with the the Edgy CD I have, or my prerelease DVD-RW image of Hardy. I will figure that one out with sudo gedit /media/.../grub/menu.lst I think.

About 3 USB Modem not working, I think it is a driver issue since $ 'sudo * iwconfig' failed to show a driver. I could not install 'ndisgtk' through synaptic or '$ ap-get install' because I didn't have a connection. I couldn't fetch it from my CD or DVD either with '$ apt-get -m --fix-missing source' or anything else. Maybe I can download this through my XP partition? I just rather ask now before I do anything else here. Also '$ ndiswrapper -i any_inffile.inf does not do the trick since it says: 'Err: could not find ndiswrapper utils'.

It is not the end of the bad news I am afraid, since I have to reboot now, since I had a mandatory security update to install MS Chat 2.5, and I installed XP SP3, and now I have to sit next to the screen to click on 'restart later'. I cannot get on the '#ubuntu' help channel on IRC.net anyway, since the server keeps on booting me. I was a or still am a Ubuntero at some point though. Right now I am about to crash due to sleep deprivation. Whenever I close my eyes I see pop up windows, or $ chmod 777 vboxdrv and stuff. So I will now try to find my own little constructive way to bang my head against the wall to cure the headache after I close down this bloody torture machine. After I copy the settings from my 3 USB Modem terminal, just in case my XP partition won't start up again, so I can still try to paste some of that in my Ubuntu version of the 3 USB Modem console first, before I go to bed. BTW, I also have a 'Mobile Connect.ISO' image on my Ubuntu 8.04 partition. Should all else fail, I could try to upload that as soon as I get back online.

Sad patrol indeed,

Thomas

---

