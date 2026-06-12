---
title: "Atheros AR9485 / Asus K550C"
date: 2013-10-07
forum: Networking &amp; Wireless
---

### Post by Marco_Santos on 2013-10-07
Hi everyone.

I am new to ubuntu and i just installed Ubuntu 13.04 and I am experiencing some problems with the WIFI. When I start the laptop the WIFI isnot connected and i cannot enable it. That options simply is not there (it is grey out). But what is strage is if I suspend the OS by closing the laptop and openning again, the WIFI is get's enabled and connected.

Have someone run into a similar problem? Can anyone explain to me what is wrong and how can i fix it?

Thank you very much:

Laptop: Asus K550C Series
 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)

---

### Post by designer-a on 2013-10-08
> **Marco_Santos said:**
> Hi everyone.

I am new to ubuntu and i just installed Ubuntu 13.04 and I am experiencing some problems with the WIFI. When I start the laptop the WIFI isnot connected and i cannot enable it. That options simply is not there (it is grey out). But what is strage is if I suspend the OS by closing the laptop and openning again, the WIFI is get's enabled and connected.

Have someone run into a similar problem? Can anyone explain to me what is wrong and how can i fix it?

Thank you very much:

Laptop: Asus K550C Series
 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)

I have the same problem whit the same hardware

---

### Post by designer-a on 2013-10-09
i have a solution, the regular key fn+F2 don't work, but if you instead press fn+F1 the computer will suspend but wen you press power button the wireless is turned on ... is not a great solution but for the time been is better, than don  use wifi.

sorry the pour English ..

---

### Post by Marco_Santos on 2013-10-10
Basicaly is what i have been doing. :)

Thank you very much..

---

### Post by varunendra on 2013-10-11
> **designer-a said:**
> the regular key fn+F2 don't work, but if you instead press fn+F1 the computer will suspend but wen you press power button the wireless is turned on ... is not a great solution but for the time been is better, than don  use wifi.

> **Marco_Santos said:**
> Basicaly is what i have been doing. :)

Then how about this one - [http://ubuntuforums.org/showthread.php?t=2174901&p=12805891#post12805891](http://ubuntuforums.org/showthread.php?t=2174901&p=12805891#post12805891) (followed by the feedback post #32)

Please try and let me know if the Fn+F2 works for you. If not, but it changes to "Always on", you may try what I suggested in [s]post #33 there (the link in it)[/s]. [COLOR="#FF0000"]**EDIT :** A slightly better and smarter way to do the same thing :[/COLOR] [http://ubuntuforums.org/showthread.php?t=2181558&p=12819607#post12819607](http://ubuntuforums.org/showthread.php?t=2181558&p=12819607#post12819607)

---

### Post by designer-a on 2013-10-11
> **varunendra said:**
> Then how about this one - [http://ubuntuforums.org/showthread.php?t=2174901&p=12805891#post12805891](http://ubuntuforums.org/showthread.php?t=2174901&p=12805891#post12805891) (followed by the feedback post #32)

Please try and let me know if the Fn+F2 works for you. If not, but it changes to "Always on", you may try what I suggested in post #33 there (the link in it).

yes it works ... 
now i have the wireless always on ...


thanks

---

### Post by Marco_Santos on 2013-10-11
Thank you very much. it worked with me. I choose to follow the post 33 and configure the short cuts. I am using the F3 to enable WIFI and F4 to disable. But i had to a slightly different thing in the actions:

marco@marco-X550CC:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

On the actions they say to execute "rfkill unblock 1" and "rfkill block 1" but if i execute "rfkill block 1" i cannot unblock it with out putting the laptop in sleep mode and start it again. But if I use the "rfkill unblock/block 0" it works perfectly. 

Does anyone know why? What is the difference?

Thank you very much again.

Regards.

---

### Post by varunendra on 2013-10-11
> **Marco_Santos said:**
> On the actions they say to execute "rfkill unblock 1" and "rfkill block 1" but if i execute "rfkill block 1" i cannot unblock it with out putting the laptop in sleep mode and start it again. But if I use the "rfkill unblock/block 0" it works perfectly. 

Does anyone know why? What is the difference?

See [post=12786842]post #23[/post] (output of "rfkill list all") in the same thread whose post #25 you followed to configure above. The output for the OP there was -
```
**[COLOR="#FF0000"]1[/COLOR]: phy0: Wireless LAN**
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```
While in your case, it is -
```
**[COLOR="#FF0000"]0[/COLOR]: phy0: Wireless LAN**
    Soft blocked: yes
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```
So there's the difference which is normal. The index number for the wireless device can be different for different people, but most often it is either 0 or 1.

And I'm very pleased to see it is working without fail. I hope the driver gets mature in the next releases so we don't have to manually cook up these workarounds.

---

### Post by Marco_Santos on 2013-11-03
I there by mistake i said that what fixed the problem was setting F3 and  F4 as short-cut to turnning on and off the wifi, but it didn't fixed  the problem. I sitll had to put the laptop to sleep.

The the following fixed the problem. I followed the orientation of the post 31:

```
echo "options asus_nb_wmi wapf=0" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
```

Then remove the driver from blacklist -
          ```
sudo sed -i '/asus_nb_wmi/ d' /etc/modprobe.d/blacklist.conf
```

Reboot and check if it's loaded (lsmod | grep asus). It should, but is 
the hardblock back again too? If it is, change the parameter "wapf=0" to
 "wapf=1"

```
sudo sed -i 's/0/1/' /etc/modprobe.d/asus_nb_wmi.conf
```

So I fixed the problem doing this.

Thank's a lot

---

### Post by varunendra on 2013-11-04
> **Marco_Santos said:**
> ```
sudo sed -i 's/0/1/' /etc/modprobe.d/asus_nb_wmi.conf
```

So I fixed the problem doing this.

Thank's a lot

You're welcome !

I posted a complete and more comprehensive method to do all this here : [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)

It also contains a slightly better workaround to compensate the Fn+F2 key in post #2 there. You may try that.

I'd also request to add yourself as an "Affected User" at the bug report page : [https://bugs.launchpad.net/bugs/1173681](https://bugs.launchpad.net/bugs/1173681) . Currently there are only 11 users in the "Affected users" list, while I'm sure there are plenty more.

If you wish to help as well, you may read [this wiki]("https://help.ubuntu.com/community/ReportingBugs") to help providing useful info (at the bug report page) so that the bug is quickly and effectively fixed.

---

