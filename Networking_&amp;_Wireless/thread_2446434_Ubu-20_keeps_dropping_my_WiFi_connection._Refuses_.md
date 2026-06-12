---
title: "Ubu-20 keeps dropping my WiFi connection. Refuses to connect."
date: 2020-06-30
forum: Networking &amp; Wireless
---

### Post by Mugsy323 on 2020-06-30
I have Ubuntu 20.04 LTS installed and use a USB Wifi adapter for my Internet connection.

When I start Ubu, my Internet connection ALWAYS starts disconnected. Clicking "Connect" tries for about 20 seconds then gives up.

I have no idea what's wrong. The WiFi connection worked perfectly when I installed Ubu from a thumb drive, including downloading "third-party" drivers and software, but now that installation is complete, it is extremely difficult to establish/maintain a connection (which I'll always lose a few minutes later.)

I'm typing this from Windows on the same PC using the same Wifi adapter. Any ideas? :mad:

TIA

---

### Post by CelticWarrior on 2020-07-01
Please read [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) and follow instructions. Post the results here.

---

### Post by Mugsy323 on 2020-07-01
Thanks for the reply.

I downloaded the script from Windows to a thumb drive, copied it from the thumb drive to Ubu's Downloads folder, changed the Permissions to "Allow executing file as a program", and as noted at the link:

[COLOR="#FF0000"][NOTE 1: Since Ubuntu 13.04, Text Files open up in text editor even if they are made executable. To change this-
Open any folder > go to Files > **Preferences** > Behavior tab > select "Ask each time" option under "Executable Text Files" section.][/COLOR]

But when I go to "Files" ("Downloads" folder open. Ubu 20.04), "Preferences" does not appear in the menu.

I tried to change "Open With" to "Run Software", but that didn't work either. I might be able to execute it from the Terminal if I knew what command to use.

TIA

---

### Post by Mugsy323 on 2020-07-03
Update: I'm noticing I stay connected for about 15 minutes when I first boot into Ubu. Logging off & Restarting is the fastest way to reconnect.

Very annoying.

---

### Post by praseodym on 2020-07-03
Lets try

```
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

### Post by Mugsy323 on 2020-07-04
Hmm, I executed the commands from the terminal (Copy/Paste. Didn't retype) and it didn't appear to have any effect (I did reboot.)

When Ubu starts, I typically (always?) have a connection, which can last anywhere from 30 seconds to 5 minutes.

(my network is "Virus Central". Everything fine at first.)
[[img]https://i.postimg.cc/4K264qCZ/1-Wi-Fi-connected-at-boot.png[/img]](https://postimg.cc/4K264qCZ)

(Suddenly, connection stops, but visible networks still visible and icon stil says "Connected".)
[[img]https://i.postimg.cc/ykCFN0GJ/2-Wi-Fi-Connected-but-not.png[/img]](https://postimg.cc/ykCFN0GJ)

(A minute later, all visible networks disappear except mine, which is unable to connect... yet still says "Connected" on header [but icon on toolbar now shows broken].)
[[img]https://i.postimg.cc/3WvX7tt5/3-Visible-Networks-disappear.png[/img]](https://postimg.cc/3WvX7tt5)

As I mentioned, this is the same computer & same connection (same USB WiFi adapter) I'm using in Windows to reply.

Big thanks.

---

### Post by kc1di on 2020-07-04
In a terminal what does the following command show for your card info?
```
lshw -C network
```
post back here.
also what is the output of ```
iwconfig
```

---

### Post by Mugsy323 on 2020-07-05
Thanks. Here are my results:
[ATTACH]286400[/ATTACH]
[ATTACH]286401[/ATTACH]

---

### Post by kc1di on 2020-07-05
those outputs look incomplete please rerun them with sudo (as super User) 
Or let us know which wireless card is in the machine.
Also you can run the wireless script in  my signature.

---

### Post by Mugsy323 on 2020-07-07
Sorry for the delay:

Running the commands with Sudo this morning actually produced *less* information. I'm not sure these will be helpful:

Thx.

---

### Post by praseodym on 2020-07-12
Try these module parameters:

```
echo "options r8712u low_power=1 power_mgnt=0 ht_enable=0" | sudo tee /etc/modprobe.d/r8712u.conf
```
Reboot

---

### Post by Mugsy323 on 2020-07-12
> **praseodym said:**
> Try these module parameters:

```
echo "options r8712u low_power=1 power_mgnt=0 ht_enable=0" | sudo tee /etc/modprobe.d/r8712u.conf
```
Reboot

Big thanks for the reply.

"Unfortunately", I couldn't wait any longer to find a solution to the issue. I ended up moving the PC next to the router last night so I could connect the Ethernet cable directly instead of relying on the WiFi. So I can't test your script.

Thanks anyway.

---

### Post by ungaratto93 on 2021-01-21
thanks [COLOR=#E8E6E3] @[/COLOR]**praseodym** , this works for me!

---

### Post by miragecmd on 2021-01-23
Hi all, same problem here.
3/4 days ago DNS stopped to resolve addresses and after one day starts also this tedious problem with wifi (only for my ubuntu 20.10 pc).
Every 5/10 minutes it stops at all and restart after a minute or so. I've noticed that keeping track of the network a continuous ping seems that many packet were lost and when restarts the first one has a huge time in ms! The card during this freeze results UP (ip a) and also i've yet disabled the power manager (wifi.powersafe = 2).
Something that you could double check?

PS. Nothing also disabling the wpa.supplicant and leave the only NetworkManager.. :(

PPS. _With tethering works all fine_ O.O"

---

