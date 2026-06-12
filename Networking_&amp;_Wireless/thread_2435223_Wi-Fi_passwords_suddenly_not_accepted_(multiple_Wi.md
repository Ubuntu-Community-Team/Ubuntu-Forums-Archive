---
title: "Wi-Fi passwords suddenly not accepted (multiple Wi-Fi networks)"
date: 2020-01-17
forum: Networking &amp; Wireless
---

### Post by kent-3 on 2020-01-17
This is Kubuntu 18.04 on a Thinkpad X1 Carbon 6th Gen, Intel 8265 wireless card. I performed some updates earlier today which I believe included linux firmware updates, and a restart was required. Since I had to reboot, I also took the opportunity to boot into Windows and update it, which included a BIOS update (which I don't expect would cause this problem, but including this just in case).

After rebooting back into Kubuntu, I started getting Wi-Fi authentication errors for networks I was previously connected to: the pop-up window appears titled "Wi-Fi password dialog -- KDE Daemon" with the text "Authenticate (network name)", For accessing the wireless network (network name) you need to provide a password below:" 

Even when I enter in the correct password (again) and verify it is correct, the message continues to pop-up as if the password is incorrect. This occurs on 3 different networks (2 different routers), all of which I connected to before.

I tried rebooting. I tried deleting the network profiles for each network. I tried rebooting and reverting to the older kernel. 

I'm writing this on a different laptop running Ubuntu Studio and it connects to the same networks fine. No changes have been made on the routers. 

Seems like one of the updates hosed the Wi-Fi authentication.

---

### Post by SeijiSensei on 2020-01-17
I've encountered this myself. I found that rebooting the router helped.

---

### Post by kent-3 on 2020-01-17
I did more testing with all available kernels:

5.0.0-23-generic (oldest) works

5.0.0-37-generic (previous kernel) works although it doesn't work initially at boot with one router: it deactivates, then tries again and successfully connects

5.0.3-26-generic the one just installed doesn't work

Rebooting one of the routers (the more problematic one) did help it reconnect with the older kernel. I don't consider that a viable solution though since some users won't have access to the wireless router they use in order to reboot it. I consider this a bug in the 5.0.3-26 kernel and uninstalled it.

---

