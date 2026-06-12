---
title: "No WiFi settings in the"
date: 2021-06-21
forum: Networking &amp; Wireless
---

### Post by dorpapst on 2021-06-21
My problem is a bit similar to the topic below mine, but I don't want to interfere with him/her.

I recently started an old (March 2021, well) Ubuntu installation on a MacBook. Everything works fine except for the fact that there is no WiFi at all. In the settings under network, WiFi does not even exist. It doesn't show up. Since its a MacBook and I don't have an ethernet adapter, I currently don't have Internet on it in any way.

I ran some commands to see what happened.
```
sudo systemctl restart network-manager 
``` does not do anything.

The output of the following command shows the existence of a WiFi card. 
```
lspci -nnk | grep -iA3 net; lsusb; dmesg | egrep -i 'blue|firm'
```

Sorry, I can only show it to you as a photo since I cannot send it anywhere:
[ATTACH=CONFIG]288710[/ATTACH]

```
sudo up link show 
```
tells me that there only is the loopback device.

Is there anything I can do to solve that without actually having Internet? It seems very weird to me, honestly.

---

### Post by chili555 on 2021-06-21
Please open a terminal and do:

```
sudo modprobe -r wl
sudo dmesg | grep brcm
```Post the result and I suspect we'll be very close to a solution.

---

### Post by dorpapst on 2021-06-22
The first outputs: "FATAL: Module wl not found" and the second one outputs nothing

Thank you for your answer. :)

---

### Post by chili555 on 2021-06-22
> **dorpapst said:**
> The first outputs: "FATAL: Module wl not found" and the second one outputs nothing

Thank you for your answer. :)Verrry interesting! Please run and post:

```
sudo modprobe brcmfmac
sudo dmesg | grep -e brcm -e 03:00

```

---

### Post by dorpapst on 2021-06-22
The first one is empty (it&#8217;s supposed to be the case?) and the second one full of outputs, see the attachment. Thank you :)[ATTACH=CONFIG]288713[/ATTACH]

I hope it&#8217;s readable

---

### Post by chili555 on 2021-06-22
Please download this file on another computer and transfer it with a USB key or similar to the desktop of your Ubuntu macine: [https://gist.githubusercontent.com/cristianmiranda/ba9d64b4324f0803d9422d765de62252/raw/fa8c3db4ece70e21b9619d918a5e5bfb6a28d72b/brcmfmac43602-pcie.txt](https://gist.githubusercontent.com/cristianmiranda/ba9d64b4324f0803d9422d765de62252/raw/fa8c3db4ece70e21b9619d918a5e5bfb6a28d72b/brcmfmac43602-pcie.txt)

Now move it to the correct location:

```
sudo cp ~/Desktop/brcmfmac43602-pcie.txt  /usr/lib/firmware/brcm/

```
Reboot and again show us:

```
sudo dmesg | grep brcm

```

---

### Post by dorpapst on 2021-06-25
Hey [**[COLOR=#DD4814][B]chili555**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=35909")
Sorry for the late response.
I actually found out that running the
sudo modprobe brcmfmac
command last time solved the problem. I wasn't aware of it since I was not expecting it to be solved by that. :)

Thank you so much for your answer!
Lukas

---

