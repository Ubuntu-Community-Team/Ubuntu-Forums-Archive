---
title: "network-manager won't remember settings?"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by Mighty_Ferguson on 2006-08-03
Hello,
I searched for any threads with a similar issue, but didn't see any. If I missed one, please let me know.

I am using network-manager and ndiswrapper with a Linksys/Broadcom wireless card. When I manually enter my network name and WPA password, it connects right away and works great. However, after a reboot all the settings are gone. Is there a way to get network-manager to remember these settings? 

I should mention that I also have the problem where network-manager asks for the password for the gnome-keyring every time (described [here]("http://ubuntuforums.org/showthread.php?t=187874"), unfortunately I can't get the fix described in the linked thread to work). Are the two problems related or seperate? It seems like most people who have the keyring issue still don't need to enter their settings into network-manager every time.

Thanks for any help,
-Mighty

---

### Post by cantormath on 2006-08-03
> **Mighty_Ferguson said:**
> Hello,
I searched for any threads with a similar issue, but didn't see any. If I missed one, please let me know.

I am using network-manager and ndiswrapper with a Linksys/Broadcom wireless card. When I manually enter my network name and WPA password, it connects right away and works great. However, after a reboot all the settings are gone. Is there a way to get network-manager to remember these settings? 

I should mention that I also have the problem where network-manager asks for the password for the gnome-keyring every time (described [here]("http://ubuntuforums.org/showthread.php?t=187874"), unfortunately I can't get the fix described in the linked thread to work). Are the two problems related or seperate? It seems like most people who have the keyring issue still don't need to enter their settings into network-manager every time.

Thanks for any help,
-Mighty

With wireless, I have installed wifi-manager, waproamd, and Network Manager from add/remove or synaptic.

Wifi-manager just seems to work better.

---

### Post by Mighty_Ferguson on 2006-08-03
> **cantormath said:**
> With wireless, I have installed wifi-manager, waproamd, and Network Manager from add/remove or synaptic.

Wifi-manager just seems to work better.

I just searched within synaptic and I don't see anything called wifi-manager. I see wifi-radar, is that what you mean?

-Mighty

---

### Post by cantormath on 2006-08-03
> **Mighty_Ferguson said:**
> I just searched within synaptic and I don't see anything called wifi-manager. I see wifi-radar, is that what you mean?

-Mighty

sorry Im a dumbass, I have been up to long. Yes, I mean wifi-radar.

I appologize.

---

### Post by Mighty_Ferguson on 2006-08-07
> **cantormath said:**
> sorry Im a dumbass, I have been up to long. Yes, I mean wifi-radar.

I appologize.

Not a problem. Sorry for the delay in replying, but I haven't had a chance to work on this much since your post. I've removed network-manager and installed wifi-radar, both through the add/remove applications menu. I'm having trouble getting wifi-radar to work at all though. I found a couple of examples on how to configure it in various threads and none of them seem to work for me. I need WPA to work, so in the WPA Driver field I've tried "wext", "ipw", "ndiswrapper". None of them seem to work. Can you offer any suggestions?

Also, I can't remove "nm-applet --sm-disable from the startup programs list in System Preferences. I can disable it, but the option to delete it is grayed out. Is there a config file that can be deleted from?

Thanks,
-Mighty

---

### Post by Mighty_Ferguson on 2006-08-08
Well, I've tried to get wifi-radar to work, and I can't figure it out. After some searching, I found [this thread]("http://ubuntuforums.org/showthread.php?t=198924&highlight=wifi-radar") which seems to indicate that wifi-radar won't work at all with Broadcom cards (someone please let me know if that's incorrect). So I'm basically left going back to network-manager and begging for someone to help me fix it so I don't have to enter in my network info and unlock the keyring every time. Can anyone help me? I'm a new transfer from Windows, and I'm about ready to chuck this laptop out the real window.

-Mighty

---

