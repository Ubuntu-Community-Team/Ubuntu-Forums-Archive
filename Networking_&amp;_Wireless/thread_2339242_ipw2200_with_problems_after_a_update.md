---
title: "ipw2200 with problems after a update"
date: 2016-10-06
forum: Networking &amp; Wireless
---

### Post by leozinho29_eu on 2016-10-06
Hello

Some time ago, I had a issue which cause my notebook to reach over 90°C due to a wireless error. It was caused because there was no adequate module loaded. The old issue: [https://ubuntuforums.org/showthread.php?t=2333925](https://ubuntuforums.org/showthread.php?t=2333925)

Since last week, this issue is back again. However, instead of the module ipw2200 not being loaded, it is loaded but stops working. A dmesg message about ASSOCIATE command being already sent is shown, and then the wireless stops working, CPU reaches 100% usage. To restore the wireless, suspending and returning makes go it back to the normal state. With the module, the wireless would work flawlessly for over 48 hours. Now it may stop after boot, after 3 hours, after 12 hours. I've found no pattern.

When this error happens, exactly the same error messages as if the module was not loaded appears. What I noticed this time is that the ASSOCIATE message is the first one that appears.

```
[COLOR=#000000][FONT=&amp][ 8326.112600] ipw2200: Failed to send ASSOCIATE: Already sending a command.[/FONT][/COLOR]
```

When suspending:

```
[COLOR=#000000][FONT=&amp][10129.517088] wlp1s5: Going into suspend...
[/FONT][/COLOR][10129.536344] ipw2200: Firmware error detected.  Restarting.
[10129.567125] ipw2200: Unable to load ucode: -22
[10129.567133] ipw2200: Unable to load firmware: -22
[10129.567133] ipw2200: Failed to up device
```
I am not sure, but my suspect this update caused the issues: 
```
Commit Log for Thu Sep 29 20:54:38 2016



Atualizados os seguintes pacotes:
bind9-host (1:9.10.3.dfsg.P4-8ubuntu1) to 1:9.10.3.dfsg.P4-8ubuntu1.1
dnsutils (1:9.10.3.dfsg.P4-8ubuntu1) to 1:9.10.3.dfsg.P4-8ubuntu1.1
isc-dhcp-client (4.3.3-5ubuntu12.1) to 4.3.3-5ubuntu12.3
isc-dhcp-common (4.3.3-5ubuntu12.1) to 4.3.3-5ubuntu12.3
libbind9-140 (1:9.10.3.dfsg.P4-8ubuntu1) to 1:9.10.3.dfsg.P4-8ubuntu1.1
libdns-export162 (1:9.10.3.dfsg.P4-8ubuntu1) to 1:9.10.3.dfsg.P4-8ubuntu1.1
libdns162 (1:9.10.3.dfsg.P4-8ubuntu1) to 1:9.10.3.dfsg.P4-8ubuntu1.1
libisc-export160 (1:9.10.3.dfsg.P4-8ubuntu1) to 1:9.10.3.dfsg.P4-8ubuntu1.1
libisc160 (1:9.10.3.dfsg.P4-8ubuntu1) to 1:9.10.3.dfsg.P4-8ubuntu1.1
libisccc140 (1:9.10.3.dfsg.P4-8ubuntu1) to 1:9.10.3.dfsg.P4-8ubuntu1.1
libisccfg140 (1:9.10.3.dfsg.P4-8ubuntu1) to 1:9.10.3.dfsg.P4-8ubuntu1.1
liblwres141 (1:9.10.3.dfsg.P4-8ubuntu1) to 1:9.10.3.dfsg.P4-8ubuntu1.1
libnm0 (1.2.0-0ubuntu0.16.04.3) to 1.2.2-0ubuntu0.16.04.1
libsmbclient (2:4.3.9+dfsg-0ubuntu0.16.04.3) to 2:4.3.11+dfsg-0ubuntu0.16.04.1
libwbclient0 (2:4.3.9+dfsg-0ubuntu0.16.04.3) to 2:4.3.11+dfsg-0ubuntu0.16.04.1
network-manager (1.2.0-0ubuntu0.16.04.3) to 1.2.2-0ubuntu0.16.04.1
samba-libs (2:4.3.9+dfsg-0ubuntu0.16.04.3) to 2:4.3.11+dfsg-0ubuntu0.16.04.1


Instalados os seguintes pacotes:
python3-xdg (0.25-4)
redshift (1.10-5ubuntu1)
redshift-gtk (1.10-5ubuntu1)
```

I don't know how to be sure, but I believe that this update broke ipw2200. Is there a way to test with the older version of the packages listed to be sure?

Thank you.

---

### Post by leozinho29_eu on 2016-10-20
Hello

From what I have seen [here]("https://www.vivaolinux.com.br/topico/Rede-Wireless/wifi-cai-e-nao-reconecta-sem-reiniciar-a-maquina") (the page is in Portuguese), the Intel wireless drivers for the older cards (2100, 2200 and 3945) were broken recently. I suppose that this particular update is the responsible, because some old commands/variables (I don't understand the patch notes very well, yet) were removed and then the older wireless cards became problematic. 

I have found a way to make the disconnection become at least less common. I had not enough time to test, but it kept working for more than 10 hours straight and downloading Fedora and Endless OS (this one is huge). The Fedora download ended successfully, but the Endless not due to HDD limitations (I forgot to set the correct partition to save). The internet became nice with new options, but the errors that happened in past, which can be seen [here]("https://ubuntuforums.org/showthread.php?t=2333925&p=13535087#post13535087"), are happening again. Only without the connection loss.

I can't grant this will work all the time, but I added some options to the ipw2200 module, so it became (way) more stable.

1) I have created a new file at /etc/modprobe.d called ipw2200.conf

2) Wrote: ```
options ipw2200 qos_enable=1
```

3) Used ```
sudo update-initramfs -u
```

4) Rebooted.

Is there a way to know why is this error happening? Is there something I can do to make the error stop? If a bug was created with some update, where I can get support, knowing that ipw2200 was abandoned by Intel?

Thank you.

---

### Post by jeremy31 on 2016-10-21
I would look at ```
iwconfig
```
If power management shows on, it can cause issues

---

### Post by leozinho29_eu on 2016-10-24
Thank you for your answer,

But I believe the error was being caused by a really unexpected thing to me: seahorse. From what looks like, after some time, the password of the WiFi would be requested again, but seahorse window wouldn't open, consequently the connection would be lost because no password was written.

It is important to say that the user could not connect to new networks (regardless if wired or wireless), but if the administrator connected to it once, the user could connect. The user couldn't create new connections, just access the ones created by the administrator. 

So looks like it was a combination of: too restrictive configuration + seahorse not requesting keys to reconnect + ipw2200 not well configured.

Things I've done:
-Configured the ipw2200 to activate QoS;
-Removed Seahorse password;
-Gave permission for user to create new connections.

I don't believe that giving such permissions to common users is good, but at least the connection became better to them and they can now reconnect if the WiFi signal is lost. 

I will make additional tests, and if the error stops, I will mark this topic as solved.

---

### Post by leozinho29_eu on 2016-10-28
> **jeremy31 said:**
> I would look at ```
iwconfig
```
If power management shows on, it can cause issues

And this is correct. Now I have found that NetworkManager decided to force on the powersave recently, while the wireless module had no direct option to turn on or off. The option which can change it was qos_enable, which I have activated, deactivating the powersave.

What was happening then? The notebook sensed the powersave was turned on, while the routers detected it as off. Consequently, the connection was terrible. The interface was all buggy too, I thought it was lxpanel issues, but it was NetworkManager too. 

Then I searched how to make NetworkManager to NOT control the wireless powersave. I have found [one useful link]("https://gist.github.com/jcberthon/ea8cfe278998968ba7c5a95344bc8b55"). Then I have changed the file at /etc/NetworkManager/conf.d, which was default-wifi-powersave-on.conf. I have changed from: ```
[connection]
wifi.powersave = 3
``` to ```
[connection]
wifi.powersave = ignore
```With this change, I have seen no more issues happening. However, only with more test to be sure. 

Thank you, I would never find the incompatible configurations by myself.

---

### Post by jeremy31 on 2016-10-28
That may need to be ```
[connection]
wifi.powersave = 2
```
But there is a chance that an invalid option disables it

---

### Post by leozinho29_eu on 2016-11-02
Hello

The invalid option did disabled the powersave, and by disabling it the Wi-Fi's stability was greatly improved. So random crashes from nowhere are no longer happening.

But I was not able to make the bug completely stops. In some extreme conditions, when the Wi-Fi quality is from terrible to catastrophic, when even smartphones have no internet, the ipw2200 crashes and the kworker using 100% CPU happens again. Gladly this is very rare, but it happens. 

About the problematic interface, it is fault of nm-applet. Just restarting nm-applet solves it. I have executed nm-applet from terminal to see if there would be any output that shown some sort of error, and I found this (I noticed the --verbose option did nothing...):

```
user@administrador-M2Ne:~$ nm-applet --verbose

(nm-applet:4208): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed


(nm-applet:4208): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed


(nm-applet:4208): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed


(nm-applet:4208): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed
^C
```

 I could revert too the changes to the permissions regarding the creation of new networks. 

A thing that would be nice would be a way to make the ipw2200 detects it has found a error and then it should restart automatically. Same to nm-applet.

Thank you.

---

