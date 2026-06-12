---
title: "Network Manager e220 3G Modem PPTP VPN's"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by jmead on 2008-10-22
Hey Guys,

Outline:
I am using Network Manager to manage my network configs as I am constantly moving around so it appears to be the best package to use. However it doesn't work in my favor when using the network manager with my 3G E220 USB modem, currently the only way to get the e220 modem is using the VODAFONE Mobile Connect Driver for linux which doesn't help me when i need to connect a VPN using the network manager. Once connected to the network using the VODAFONE Mobile Software the network manager still believes i am not connected using any interface and thus it disables the VPN options.

Solution:
Is there anyway to either connect the e220 modem via Network Manager or Trick Network Manager into thinking it is connected so as I can connect a VPN using it?

Thanks for your help in advance I know it might seem like a stupid question but honestly i have searched everywhere to find a GUI solution to connecting PPTP VPN's

---

### Post by wiebeest on 2009-02-02
> **jmead said:**
> 

Solution:
Is there anyway to either connect the e220 modem via Network Manager or Trick Network Manager into thinking it is connected so as I can connect a VPN using it?

Hi, maybe this tip from ToineM helps you to connect the e220 though Ibex's netwerk manager, as it did for me:
[http://ubuntuforums.org/showpost.php?p=6662938&postcount=3]("http://ubuntuforums.org/showpost.php?p=6662938&postcount=3")

Hope it helps!

Sincere greetings,

Wiebeest

---

### Post by claytronic on 2009-02-05
> **jmead said:**
> 
Thanks for your help in advance I know it might seem like a stupid question but honestly i have searched everywhere to find a GUI solution to connecting PPTP VPN's

Network-Manager supports three popular VPN plugins. 

 ```
sudo aptitude install network-manager-pptp network-manager-openvpn network-manager-vpnc
```

If you plan to connect to a M$ PPTP server you might also need to manually add the "refuse-eap" option via the gconf-editor.

[http://ubuntuforums.org/showthread.php?t=964255&highlight=refuse-eap]("http://ubuntuforums.org/showthread.php?t=964255&highlight=refuse-eap")

[https://bugs.launchpad.net/bugs/301593]("https://bugs.launchpad.net/bugs/301593")

---

