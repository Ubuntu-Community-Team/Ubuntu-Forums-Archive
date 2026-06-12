---
title: "NetworkManager doen't save WPA-passphrase in keyring"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by PinkyMouse on 2006-10-28
Hello,

after connecting to my WPA-secured WLAN the network-manager does not save the passphrase in my keyring. When I start nm-applet manually from terminal, i get the following error:

** (nm-applet:12177): WARNING **: <WARN>  nmi_save_network_info(): Error saving secret for wireless network 'myWLAN' in keyring: 5

Reinstalling the network-manager did not work.

I don't have an idea what to do...

Thanks in advance,
PinkyMouse

---

### Post by PinkyMouse on 2006-10-31
hmm... nobody has an idea?

---

### Post by BlaY0 on 2006-11-14
Hmm, yes. I connect to corporate SSID with PEAP credentials and those credentials are never saved in my default keyring although NM asks keyring-daemon to open keyring (I'm asked to enter keyring password). But I found strange thing... PEAP credentials are saved in gconf (system/networking/wireless/networks/ssid)in cleartext which is absurd! Why for example WEP credentials are stored in keyring as we all know any 10 year old kid could break it but PEAP/WPA credentials are stored in gconf in cleartext?!?!?! Right now the only sane explanation about this matter would be that "WPA credentials save to keyring" feature is not implemented yet.

I'm poking around this problem for several days now and no luck... the only option left for me is to subscribe to NM mailing list and check its archive for the past year...

---

### Post by bartoknagyjanos on 2006-11-30
> **PinkyMouse said:**
> hmm... nobody has an idea?

Just in the same situation... Reinstall doesn't help either :-(

---

### Post by function1 on 2008-01-03
been a bug since feisty.
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/41134](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/41134)
big big security risk!

---

