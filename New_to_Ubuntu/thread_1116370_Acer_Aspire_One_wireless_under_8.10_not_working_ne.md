---
title: "Acer Aspire One wireless under 8.10 not working need simple instruction"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by gabel305 on 2009-04-04
I'm trying Linux for the first time on a dual boot aspire one I just purchased yesterday. I'm a longtime Mac user and have always been intrigued by Linux. I heard Ubuntu was the easiest to use, so I installed it last night. 
Unfortunately, I've followed a bunch of documentation /threads across the web, and can't figure out how to get the wireless card working under ubuntu. I'm not a programmer but have managed to get some edits on certain .conf files done only to find out that I couldn't save them. Most of the instructions out there presuppose a certain minimal understanding of linux. 
I've spent 12 hours on this and am totally burnt out and disappointed. Should I just give up on Linux? It seems to be a programmer's OS and probably doesn't have room under its tent for folks like me who just need stuff to work.
I'd appreciate any help. Thanks in advance.

---

### Post by Rumtscho on 2009-04-04
It isn't a programmer's OS, but it does have some probs and wireless is one of them. I used a guide in German for my wireless, if you speak that, try at [www.ubuntuusers.de/WLAN](www.ubuntuusers.de/WLAN). If not, tell us following information: 

- does your Linux recognize the wireless card out of the box? 
Type iwconfig in a terminal. Most lines will say no wireless extensions. If one says "IEEE 802.11bg" and lists ESSID, Mode, Frequency, Access  Point and some others, your wireless card is installed. If not, you should install drivers for it. 

- If the wireless card is not installed, you should tell us manufacturer and model. There are lists on the Internet which tell you if a card needs drivers. 

- If you don't know maniufacturer and model, you'll know at least if it is a USB dongle, or a built-in PCI card. Type lsusb or lspci (depending on the type) and you'll get a list of the hardware connected to the USB (or PCI) ports. If you don't know which one is your card, post here the whole output. 

- Another thing you should know is the type of connection you try to build. Modems usually come with a pre-set type which you can check in the modem manual. Once your wireless card drivers work, you can probe the available networks using the command line sudo iwlist scanning. 

- If your drivers already work, and your modem offers the today usual type of a wpa encrypted network, and you are running Ubuntu 8.10 try the following. 
1. Type sudo gedit /etc/network/interfaces. This opens a configuration file with all your network cards. Add following lines to the file: 

iface wlan0 inet dhcp 
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf 

Save the file and exit. 
Here (and at all places I use the placeholder wlan0) you have to replace wlan0 with the name of your wireless card. This is the entry under lspci (or lsusb) that wants an Access Point (see above). 
2.Type 

sudo touch /etc/wpa_supplicant/wpa_supplicant.conf
sudo gedit /etc/wpa_supplicant/wpa_supplicant.conf 
In this file, type the lines 

ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1
network={
ssid="NETWORKNAME"
psk="NETWORKKEY"
}

save and exit. 
Here, you have to replace NETWORKNAME with the name of your own network, and NETWORKKEY with your own password. They are typically printed on the modem, if not, contact your network provider and ask where to get them. 
3. Type sudo wpa_supplicant -i wlan0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf 
4. After connection, send the wpa job to the background, or start a new terminal. Type ifconfig. If your wireless card has an IP associated, it is connected. Congratulations. 
5. After you got the connection working manually, open again the file /etc/network/interfaces and add the line auto wlan0. Next time you boot your PC, the connection should be there. 

If the above method didn't work, or you don't meet the prerequisitions I listed, please post here the information I requested and we will see further.

---

### Post by JK3mp on 2009-04-04
Yeah... generally advice from multiple forums leads to multiple BS that causes multiple PROBLEMS. But i'll try to help you and NOT be one of the people who have no idea what there talking about, lol. Now can you go to your terminal and give us the output of "lspci" please. :) . This will show if its reading your wireless card and what kind it is. I know ubuntu 8.10 reads alot of them and comes with madwifi drivers etc installed, so if your not using 8.10 u might just try that. Also the reason you can't configure some of the conf files its probably cause you need root privelages.(but thats ok, cause usually if you try to mess with them you jack em up beyond all imagination) So just start off with that output above and hopefully we can help. :D

---

### Post by linuxuser21 on 2009-04-04
> **Rumtscho said:**
> I used a guide in German for my wireless, if you speak that, try at [www.ubuntuusers.de/WLAN](www.ubuntuusers.de/WLAN).

Uh.... Or you don't have to learn German and just read it in english.  Try [this]("http://translate.google.com/translate?hl=en&sl=de&u=http://wiki.ubuntuusers.de/WLAN&ei=iBLYSbHeD4usMv36wYMP&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3D%2522http://www.ubuntuusers.de/WLAN/%2522%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:unofficial%26hs%3Dv5H%26sa%3DG") if you want to read it.

---

### Post by 3rdalbum on 2009-04-04
Wireless on the Aspire One is a solved problem.

First, you need to plug an Ethernet cable into your Aspire One and router so you can have a wired connection.

Then, go to System > Administration > Software Sources and enable the "Backports" repository. Close the program and it will ask you if you want to reload the package list; click Reload.

Then go into Synaptic Package Manager and install the "linux-backports-modules-intrepid" package that contains the good wireless driver.

Once that's done, you need to edit some configuration files. Don't worry, it's easy-peasy-lemon-squeezy. Press Alt-F2 and copy and paste this bit in:

```
gksudo gedit /etc/modules
```

A text editor will open. At the end of the file, on a new line, type "ath5k" without the quotes. Save and close.

Hit Alt-F2 again and paste this in:

```
gksudo gedit /etc/modprobe.d/blacklist
```

At the end of the file, on a new line, type "blacklist ath_pci". Save and close. Take out the Ethernet cable, reboot, and you'll have wireless.

The reason why your previous edits to configuration files couldn't be saved is because you were trying to edit them as your regular user account. For safety and security, **all system-wide files** can only be modified by the root user. The "gksudo" part of the command I gave you, runs the rest of the command as the root user. The "gedit" bit runs a text-editor program called Gedit, and the /etc/modules and /etc/modprobe.d/blacklist are the locations of configuration files that you needed to edit.

The reason why us Aspire One users need to go through this procedure on Ubuntu 8.10 is because Atheros, who makes the wireless card in the Aspire One, are in the process of open-sourcing and improving their wireless driver. They haven't added support for all models of wireless card yet, so sometimes it's necessary to use this different driver. The situation should be resolved in Ubuntu 9.04, where the correct wireless driver will be loaded automatically.

---

### Post by gabel305 on 2009-04-05
Hey guys thanks for the help. I have indeed received a ton of suggestions but am pretty confused at this point. Here is the output from a lspci query in terminal:
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
I also followed the instructions listed here:
[http://www.stchman.com/aspire_one_intrepid.html]("http://www.stchman.com/aspire_one_intrepid.html")
Also did iwconfig:
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

i also followed the instructions to enable windows drivers, which did nothing as far as i can tell.
I'll try some of the other hints listed in this thread and see if they work i guess.

---

### Post by gabel305 on 2009-04-05
3rdalbum - thanks for the help. Although i check the backports box in software sources, when i went back into the package manager I couldn't find the driver you mentioned in the list. I went ahead and did the rest of your instructions on the bet that I had installed it already, alas, no wireless.

---

### Post by gabel305 on 2009-04-05
I have a sickening hunch that all the attempts I've made to fix this problem have created a conflicting mess..Looks like I'm going to have to reinstall Ubuntu after a drive format..I'll give this another hour (for a total of 19) and then resign myself to not using Linux I guess.

---

### Post by 3rdalbum on 2009-04-05
Have you tried clicking the "Reload" button in Synaptic?

If you are running 8.10, then the package should be there. You could try switching mirror in case your local Ubuntu mirror doesn't have the backports packages, although I don't know why it wouldn't.

You're definitely not using 8.04?

If you're already going to be reinstalling Ubuntu, I'd suggest installing the Jaunty (9.04) beta and blacklisting the "acer_wmi" module... or hopefully the latest updates to Jaunty have fixed that little problem. I have Jaunty on my Aspire One right now and it's working very well.

---

### Post by gabel305 on 2009-04-05
I've now reinstalled 8.10 and went through the first part of the fix, loading the new drivers from synaptic list. Unfortunately, when the GRUB list comes up, I now have 8.10.7 or 8.10.11 to choose from. 8.10.7 shows no sign of the new wireless drivers but connects via ethernet. 8.10.11 shows wireless as active, but is not seeing any networks, and ethernet no longer works. I really just want to get up and running and not have to spend another 10 hours trying to fix one thing after another.

---

### Post by gabel305 on 2009-04-05
FINALLY got it running!! Thanks to 3rdalbum and the rest of you for your help and support.
Now I get to explore..yay!

---

