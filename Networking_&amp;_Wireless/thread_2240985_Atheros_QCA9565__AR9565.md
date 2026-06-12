---
title: "Atheros QCA9565 / AR9565"
date: 2014-08-23
forum: Networking &amp; Wireless
---

### Post by ratheeshp on 2014-08-23
Hi I've entered in to ubuntu world by installing in to my laptop but sadly it's not picking my wifi driver.Could some please help me to fix this.

   *-network DISABLED
                description: Wireless interface
                product: QCA9565 / AR9565 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                logical name: wlan0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical wireless

I've tried this  sudo apt-get install linux-headers-generic build-essential but it didn't fix my issue.

my os details are

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

RA

---

### Post by jeremy31 on 2014-08-23
If you can connect through a wired connection open a terminal window with CTRL+ALT+t and paste this command in ```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
``` and attach the resulting wireless-info file in your post using code tags if it is a txt file

---

### Post by ratheeshp on 2014-08-23
[ATTACH]255775[/ATTACH]

Attached as you requested

Also my rfkill list too

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by jeremy31 on 2014-08-23
Try this ```
sudo modprobe -rv asus_nb_wmi
``` then ```
sudo modprobe asus_nb_wmi wapf=4
``` then see if your hotkey will toggle the hard block in rfkill

If it doesn't toggle redo the above commands but use wapf=1

---

### Post by ratheeshp on 2014-08-23
Thanks for the quick update but it didn't work.I've tried both wapf=4 then wapf=1 after removing it and it didn't resulted any change.

---

### Post by jeremy31 on 2014-08-23
What is the model number of the laptop?  Is there a switch for wifi, or another button near the keyboard?

---

### Post by ratheeshp on 2014-08-24
It's [ASUS X551CA-SX021D 15.6-inch Laptop ]("http://www.amazon.in/gp/product/B00H1QGLFE/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1")

I was using windows 8 and it was working fine thought of using ubuntu and everything worked fine except wifi :(
I dont see any switch/button available for wifi near keyboard.
I've done all the ubuntu updates too.

---

### Post by jeremy31 on 2014-08-24
Is the wifi light on?  You might be able to toggle it on during boot when the ASUS splash screen is displayed if it isn't on now.
It might be one of the odd machines that the common values for wapf(0, 1, 4) aren't going to work, it is said that 0-9 are valid for wapf so it may be a case where you have to ```
sudo modprobe -rv asus_nb_wmi
``` and ```
sudo modprobe asus_nb_wmi wapf=0
``` and try every number from 0-9 and then try the hotkey to enable until rfkill shows wifi if no longer blocked.  Another possibility is that you might be able to unblock the wifi with just the sudo modprobe -rv asus_nb_wmi without reinstalling it

---

### Post by ratheeshp on 2014-08-24
Again no luck :( !
I tried all the values[0-9] and without asus_nb_wmi also but no results.I cant see any wifi light anywhere.
If it possible I can get you remote access to check though not sure which is the best tool will work in ubuntu(same as teamviewer in windows).

---

### Post by ratheeshp on 2014-08-24
Hi I think a small change in your code fixed it!
Actually I was desperately trying to fix this issue parallelly and got this link [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)
When checking I couldn't find any asus_nb_wmi.conf file getting created with the command 'sudo modprobe asus_nb_wmi wapf=4'  and I tried 
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf

and rebooted which did the magic. Not sure why the file didn't get created with modprobe command(is that temporary one!) but creating a file and putting this line worked.

Thanks **[COLOR=#000000]jeremy31[/COLOR]**[COLOR=#000000][/COLOR][COLOR=#000000] for staying with me to fix my issue and you guys really rocks. Even I haven't seen such a amazing quick support[/COLOR]**[COLOR=#000000][/COLOR]**[B][COLOR=#000000] anywhere.

Ratheesh
 
[/COLOR][/B][COLOR=#000000][/COLOR]

---

### Post by jeremy31 on 2014-08-24
> **ratheeshp said:**
> Hi I think a small change in your code fixed it!
Actually I was desperately trying to fix this issue parallelly and got this link [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)
When checking I couldn't find any asus_nb_wmi.conf file getting created with the command 'sudo modprobe asus_nb_wmi wapf=4'  and I tried 
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf

and rebooted which did the magic. Not sure why the file didn't get created with modprobe command(is that temporary one!) but creating a file and putting this line worked.

Thanks **[COLOR=#000000]jeremy31[/COLOR]**[COLOR=#000000] for staying with me to fix my issue and you guys really rocks. Even I haven't seen such a amazing quick support[/COLOR][B][COLOR=#000000] anywhere.

Ratheesh
 
[/COLOR][/B]

The asus_nb_wmi.conf doesn't get created with the modprobe command.  I usually try to find what value works before making the .conf file with the options

A bit strange but it works now, can you edit the topic as solved and post on this thread [http://ubuntuforums.org/showthread.php?t=2181558&page=4](http://ubuntuforums.org/showthread.php?t=2181558&page=4)
and post that yours works with wapf=4 and the result of 

```
[COLOR=#000000]cat /sys/class/dmi/id/product_name
```
[/COLOR]One of the developers is making a quirk table so that the wapf=4 gets set automatically and sometime in the future Ubuntu might work without workarounds

---

### Post by ratheeshp on 2014-08-24
Thanks Jeremy31 again

It's X551cap

---

### Post by varunendra on 2014-08-25
> **jeremy31 said:**
> I usually try to find what value works before making the .conf file with the options

A bit strange but....

Actually, not strange at all. Some drivers, particularly most (probably ALL) of the ***wmi* drivers, acpi ones** etc. don't reflect the changes if re-loded with parameters on a running system. They need to be loaded with desired changes from the very beginning of the booting.

It is probably because they deal with the core parts of hardware which can't change their set of instructions once initialized - just a guess.

You may have seen posts where removing some of such drivers, like acer-wmi or hp-wmi, immediately shows the difference. While they may be proofs of contradictions to my assumption above, I believe such drivers don't handle the core part of any critical hardware and only work as 'middle-man', not conveying the messages properly or sometimes even preventing other parts to work properly.

Of course all of the above is just guess and assumptions, and given the curious type you are, I encourage you to think/research in your own ways if you have the time, and come up with your own conclusions or proofs if you find some. While such kind of research may seem waste of time to most, clarity/knowledge about fundamentals is the core-component of a strong foundation for bigger troubleshootings.


**@ratheeshp,**
The correct way to mark a thread as **[SOLVED]** is to use the "Thread Tools" link above the top post. You can find screenshots of it in the "[COLOR="#0000CD"]see how[/COLOR]" link in my signature below. :)

---

