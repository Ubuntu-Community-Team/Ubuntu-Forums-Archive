---
title: "Switched from DHCP to Static IP &amp; back to DHCP. Now getting keyring password prompt."
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by kpkeerthi on 2008-04-25
My wireless is WPA secured. Hardy defaulted to roaming mode/DHCP and there was absolutely no problem connecting to my access point. One thing I immediately noticed was that the network manager did not prompt for keyring password except for the time I initially set it up. It automatically connected to wireless on subsequent reboots. Pretty neat. 

I do torrents so I needed a static IP for portforwarding and stuff. I switched to static IP from System -> Admin -> Network. I unchecked roaming mode on my wireless device and specified IP address, subnet mask and gateway. Everything was fine and I was able to connect online. Rebooted and network manager auto connected without prompting for keyring password. I was online.

Today, I figured out how to reserve a fixed IP to my PC (based on MAC address) in my router's admin console. In Hardy, I switched back to roaming mode/DHCP from System -> Admin -> Network. I prefer to be in roaming as this is my laptop. My wireless works fine and DHCP gets me the IP I want, ports are getting forwarded.

But just one problem, everytime I reboot, network manager is now prompting for keyring password like it used to do in Gutsy. How do I fix this? Is this a bug?

---

### Post by kpkeerthi on 2008-04-25
Anyone?

---

### Post by anthonyp on 2008-04-25
i too am looking for an answer to this exact same scenario!
Only difference is I never got the prompt the first three reboots but now get it everytime... the onyl thing I have done to a fresh install of Hardy is apt-get compiz, other than that its all fresh.

---

### Post by anthonyp on 2008-04-25
I went into System -Preferences -Encryptions & Keyrings. Set the new password as blank and restarted. No prompt anymore!

---

### Post by kpkeerthi on 2008-04-25
OK. Here is a (rather lousy) fix:

1. Boot up and let network manager connect to wireless
2. Delete the password keyring from System -> Preference -> Encryption & Keyrings
3. Reinstall network manager
```
sudo aptitude reinstall network-manager network-manager-gnome
```
4. Reboot.

Everything should reset and network manager should connection with no keyring unlock password prompt.

---

