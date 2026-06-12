---
title: "how do you uninstall openvpn from network manager"
date: 2017-03-08
forum: Networking &amp; Wireless
---

### Post by stefan_bahrens on 2017-03-08
I'm using Ubuntu 16.04LTS. I'm using a VPN service that employs Openvpn and this can be done through a plug-in to Network Manager. It seemed to work fine. I assume after an update some settings became greyed-out or vanished for no obvious reason. Specifically the changes were these. Under normal circumstances if I go -
Network Manager>VPN Connections>(list of vpn servers)+"Configure VPN"+"Disconnect VPN"
then everything is fine and these last two commands (Configure and Disconnect) are available. What happens now is that "Configure VPN" is greyed-out and "Disconnect VPN" has vanished. I decided to uninstall and reinstall Openvpn. I purged **network-manager-openvpn-gnome** and **network-manager-openvpn** and rebooted. I assumed that this would remove the menu item "VPN Connections" from the Network Manager menu which sits between "Create New Wi-Fi Network" and "Enable Networking". It did not. So I couldn't uninstall and reinstall Openvpn because I couldn't tell if I'd removed it. I don't wish to remove Network Manager itself because this simply leaves you with no internet connections at all. I tried restarting Network Manager **sudo systemctl restart network-manager** but it didn't help. I googled "Configure VPN grayed out" and found this confirmed bug report -
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1640970](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1640970) 
So, even if I had been able to uninstall and reinstall Openvpn the two unusable VPN commands (Configure and Disconnect) would have remained unusable. However, I am baffled that I couldn't get rid of "VPN Connections" from the Network Manager menu. Does anyone know how to do this? Thanks for any assistance.

---

