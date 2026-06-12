---
title: "Shutdown problems"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by flying_monkey on 2008-12-11
Forum members,

I'll apologize in advance if this has been answered already, but I looked in both the Mint and Ubuntu forums and tried everything I found there, with no results.  I had this posted on the Mint forums, but there are a lot fewer eyballs there, and you guys are a friendly bunch so maybe I'll get some response here.

I'm running Mint Felicia (based on Ubuntu 8.10, I think) with Xfce on an old IBM Thinkpad T20. It runs quite well, no complaints. The problem comes when I try to stop running. I see the same thing no matter which shutdown method I use. I can use the Menu and Quit, or I can open a terminal and type sudo shutdown -P now. In either case, the screen immediately goes black, and the system will stay in that situation longer than I have patience to wait. There is no text, no blinking cursor, and no progress bar, but I can see that the screen backlight is still on behind the black screen. Eventually, I have to hold down the power button for several seconds to get it to shutdown. And then, it's not really shut down. I can leave it in this state under my bed when I go to sleep, and I'll invariably find that it's powered itself back on, waiting for me to login when I wake up. Also, when it's trying to shutdown as described above, I've tried to get to a terminal by typing CtlAltF1and nothing happens.

On the shutdown, I see just a flash of the splash screen, and see the loading bar emptying, while my screen goes black within 2 seconds or less when I give the command or click the shutdown button.

I found something interesting, which may bear on the problem. I had the thought that maybe if I went to a text console and did the shutdown, I'd get to see where it was hanging. So, I hit ctl-alt-F1, and instantly the screen went black, just like at shutdown, and could not get it back. I know the computer was still alive, because the light on the PCMCIA wireless card was blinking. Does this give any clues? Where is this output stored so that I can go look at it the next time I start?

I also tried
ifconfig eth0 down
ifconfig eth1 down

before trying to shutdown, with no success. eth1 is where my wireless card shows up.  Also tried shutting down the alsa driver.  None of these fixes have worked.

Help!
Ed

---

### Post by albinootje on 2008-12-11
Check /var/log.kern.log or /var/log/kern.log.0 for info.
And try booting with the "noapic nolapic acpi=off" parameters, or a combination of those.

---

### Post by alon_lhv on 2008-12-11
Hi,

I have also ThinkPad T20, and I've just installed Ubuntu 8.10, and have **exactly** the same problem. When I checked the /var/log/kern.log, I got this result (and didn't understand it - i'm a new in the Linux world..):
```
Dec 11 21:33:32 alon-laptop kernel: [   52.149785] Bluetooth: SCO (Voice Link) ver 0.6
Dec 11 21:33:32 alon-laptop kernel: [   52.149811] Bluetooth: SCO socket layer initialized
Dec 11 21:33:32 alon-laptop kernel: [   52.220951] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Dec 11 21:33:32 alon-laptop kernel: [   52.220972] Bluetooth: BNEP filters: protocol multicast
Dec 11 21:33:32 alon-laptop kernel: [   52.352137] Bridge firewalling registered
Dec 11 21:33:32 alon-laptop kernel: [   52.356345] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
Dec 11 21:33:49 alon-laptop kernel: [   68.802175] NET: Registered protocol family 17
Dec 11 21:33:52 alon-laptop kernel: [   72.166584] wlan0: authenticate with AP 00:14:d1:55:bf:ee
Dec 11 21:33:52 alon-laptop kernel: [   72.169694] wlan0: authenticated
Dec 11 21:33:52 alon-laptop kernel: [   72.169717] wlan0: associate with AP 00:14:d1:55:bf:ee
Dec 11 21:33:52 alon-laptop kernel: [   72.172672] wlan0: RX AssocResp from 00:14:d1:55:bf:ee (capab=0x421 status=0 aid=3)
Dec 11 21:33:52 alon-laptop kernel: [   72.172694] wlan0: associated
Dec 11 21:33:52 alon-laptop kernel: [   72.175227] wlan0: disassociating by local choice (reason=3)
Dec 11 21:34:21 alon-laptop kernel: [  101.655640] wlan0: authenticate with AP 00:14:d1:55:bf:ee
Dec 11 21:34:21 alon-laptop kernel: [  101.658743] wlan0: authenticated
Dec 11 21:34:21 alon-laptop kernel: [  101.658766] wlan0: associate with AP 00:14:d1:55:bf:ee
Dec 11 21:34:21 alon-laptop kernel: [  101.663681] wlan0: RX ReassocResp from 00:14:d1:55:bf:ee (capab=0x421 status=0 aid=3)
Dec 11 21:34:21 alon-laptop kernel: [  101.663701] wlan0: associated
Dec 11 21:36:02 alon-laptop kernel: [  202.732761] ppdev0: registered pardevice
Dec 11 21:36:03 alon-laptop kernel: [  202.782552] ppdev0: unregistered pardevice
Dec 11 21:36:03 alon-laptop kernel: [  202.884934] ppdev0: registered pardevice
Dec 11 21:36:03 alon-laptop kernel: [  202.935073] ppdev0: unregistered pardevice
Dec 11 21:36:06 alon-laptop kernel: [  206.229651] ppdev0: registered pardevice
Dec 11 21:36:06 alon-laptop kernel: [  206.280429] ppdev0: unregistered pardevice

```

---

### Post by anewguy on 2008-12-12
What happens in terminal if you just do  sudo shutdown -h now ?


dave ;)

---

### Post by kerry_s on 2008-12-12
**acpi=force**
to the kernel boot line

---

### Post by alon_lhv on 2008-12-12
> **anewguy said:**
> What happens in terminal if you just do  sudo shutdown -h now ?


dave ;)

Same results as if I tried to shut down in the GUI way .. :(

---

### Post by alon_lhv on 2008-12-12
> **kerry_s said:**
> **acpi=force**
to the kernel boot line

Can you explain what do you mean? In what line, and in what file should I try this?

---

### Post by kerry_s on 2008-12-12
> **alon_lhv said:**
> Can you explain what do you mean? In what line, and in what file should I try this?

sorry, i assumed you have already been trying different boot options and was just looking for the right 1.

press> alt+f2
type> gksu gedit /boot/grub/menu.lst

scroll to the bottom, add it to the end of the line that starts with "kernel".

save and reboot
test it see if it works.

---

### Post by alon_lhv on 2008-12-14
Thanks for the help, but it didn't work. Nothing really changed.. :(

---

### Post by utnubuuser on 2008-12-14
I suppose Ctrl+Alt+Del doesn't help?

How about Ctrl+Alt+Bckspc, then shut-down from login-screen?

---

### Post by alon_lhv on 2008-12-14
Ctrl+Alt+Bckspc made the same results as ctl-alt-F1 (see the 1st message of "flying_monkey" abouve).

---

### Post by flying_monkey on 2008-12-17
C'mon, guys, a little help here.  None of these suggestions have changed anything, and I'm obviously not the only one with these problems.

Ed

---

### Post by godzillajjk on 2009-02-02
I have **Exactly** the same problem. I have 8.10 amd64 version dual booted with XP installed on a Asus Striker II formula mobo. When i do a shutdown, the screen turns black and computer becomes non responsive. ctrl+alt+F1,  sudo shutdown -h now, system>shutdown>shut down gives me the same result. Fan and all still functioning. I believe this symptom was not present when the OS was fresh installed. I think installing Nvidia drivers or updating the kernel started the issue.

Also I had problems installing ubuntu on my desktop initially. It will hang after the "checking battery state...". I added acpi=NOACPI when installing and it passed. It seems the striker II formula has issues with its ACPI for it has problems sometimes with BIOS hangs and windows XP unable to hibernate.

I have to resort to manually pressing the power button on my PC after the hangs. Its gonna trash my HD someday. Really would like some help as well.

---

