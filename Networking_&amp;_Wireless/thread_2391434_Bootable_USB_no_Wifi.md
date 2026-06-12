---
title: "Bootable USB no Wifi"
date: 2018-05-09
forum: Networking &amp; Wireless
---

### Post by ush2018 on 2018-05-09
I have made a bootabe Ubuntu USB but when I boot via USB, Ubuntu won't connect to the wifi. Before I install Ubuntu I need to know that it will connect to the internet.

So, when I boot Ubuntu I don't even see a list of wifi connections like I do with Windows and my phone.

I'd like to install Ubuntu on my PC as Windows is giving me too much trouble but it needs to connect to the internet. Maybe it will connect to the internet when I install it (as opposed to using a bootable USB)?

---

### Post by ank2 on 2018-05-09
> **ush2018 said:**
> I have made a bootabe Ubuntu USB but when I boot via USB, Ubuntu won't connect to the wifi. Before I install Ubuntu I need to know that it will connect to the internet.

So, when I boot Ubuntu I don't even see a list of wifi connections like I do with Windows and my phone.

I'd like to install Ubuntu on my PC as Windows is giving me too much trouble but it needs to connect to the internet. Maybe it will connect to the internet when I install it (as opposed to using a bootable USB)?

Suppose Ubuntu does not have a driver. You have figure out that chip in this this stick. When booted open a terminal (probably called gnome-terminal), and type **sudo lsusb** and see if there is anything listed corespondent to your stick. Use the other PC and so a web search for the chip name you found and *linux* to see if there a if there does a name of the driver module show up. If, do a **sudo** **lsmod** to see if it is listed. If not, try **sudo** **modprobe <DRIVERNAME>** (replace with with what you found in a web search. Failing all other people might have the same problem with that driver and a possible solution.

---

### Post by ush2018 on 2018-05-09
If it matters I'm using a HP Stream.

---

### Post by yancek on 2018-05-09
> I have made a bootabe Ubuntu USB but when I boot via USB, Ubuntu won't connect to the wifi

You will need your wifi passphrase so write that down before you begin.

What does "won't connect to the wifi" mean?  What exactly did you do/try?  When you boot the Ubuntu installer and get to the Desktop, click in the extreme upper right the lightning or down arrow icon.  You should get a pop-up window and it will show Wifi not connected.  Click on that and you will then see an option to select networ, click on that and you should see the various wifi connections locally.  Select yours and at the bottom of that windows, click connect and in the new window you will be prompted for your wifi passphrase which is usually on the back/bottom of the router so enter it and again, click connect.

---

### Post by jeremy31 on 2018-05-09
Moved to Networking

Can you post results from terminal for 
```
lspci -nnk | grep -iA3 net; rfkill list
```

---

### Post by ush2018 on 2018-05-10
> **yancek said:**
> You will need your wifi passphrase so write that down before you begin.

What does "won't connect to the wifi" mean?  What exactly did you do/try?

I mean there is working wifi but my computer, whilst running Ubuntu, won't connect to it. I see no list of wifi connections.

> When you boot the Ubuntu installer and get to the Desktop, click in the extreme upper right the lightning or down arrow icon.  You should get a pop-up window and it will show Wifi not connected.  Click on that and you will then see an option to select networ, click on that and you should see the various wifi connections locally.  Select yours and at the bottom of that windows, click connect and in the new window you will be prompted for your wifi passphrase which is usually on the back/bottom of the router so enter it and again, click connect.

I will try this.

---

### Post by ush2018 on 2018-05-10
> **yancek said:**
> ...get to the Desktop, click in the extreme upper right the lightning or down arrow icon.  You should get a pop-up window and it will show Wifi not connected.  Click on that and you will then see an option to select networ, click on that and you should see the various wifi connections locally.  Select yours and at the bottom of that windows, click connect and in the new window you will be prompted for your wifi passphrase which is usually on the back/bottom of the router so enter it and again, click connect.

What I see is the network icon which resembles a triangle with one curved side. I click thi and I get a drop-down menu with the following contents:


[LIST]
[*]No network devices available
[*]VPN Conections
[*]Enable networking
[*]Connection information
[*]Edit conections
[/LIST]

I'm thinking that since "No Network Devices Available" is there that Ubuntu isn't "seeing" the wifi (Windows connects just fine).

---

### Post by ush2018 on 2018-05-10
> **jeremy31 said:**
> Moved to Networking

Can you post results from terminal for 
```
lspci -nnk | grep -iA3 net; rfkill list
```

I ran this command and took a screenshot of the output but now Windows wont find the screenshot.

---

### Post by ush2018 on 2018-05-10
> **jeremy31 said:**
> Moved to Networking

Can you post results from terminal for 
```
lspci -nnk | grep -iA3 net; rfkill list
```


Here's a photo of the output.

---

### Post by jeremy31 on 2018-05-10
You are running the Live ISO, you can try ```
sudo apt install bcmwl-kernel-source
```
And see if it works

---

### Post by ush2018 on 2018-05-10
> **jeremy31 said:**
> You are running the Live ISO, you can try ```
sudo apt install bcmwl-kernel-source
```
And see if it works

I ran that command and it did it's thing. It still wouldn't connect to the WiFi so I rebooted and still no change.

Last time I switched to Ubuntu from Windows I didn't have this much trouble.

---

### Post by jeremy31 on 2018-05-10
Does ```
cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Show
```
[connection]
wifi.powersave = 3
```
If so do ```
 sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf && systemctl restart network-manager.service
```

---

### Post by ush2018 on 2018-05-10
[QUOTE=jeremy31;13765410]Does ```
cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

"No such file or directory" was the output.

---

### Post by jeremy31 on 2018-05-10
Does ```
iwconfig
```
Show power management on?

---

### Post by ush2018 on 2018-05-10
> **jeremy31 said:**
> Does ```
iwconfig
```
Show power management on?

Output is: lo no wireless extensions.

---

### Post by MrSchroeder13 on 2019-01-09
I'm encountering the same issue with an HP laptop.

iwconfig shows

lo no wireless extensions
no wireless extensions



It's basically like the driver simply doesn't exist in Ubuntu Live ISO.  any ideas?

---

