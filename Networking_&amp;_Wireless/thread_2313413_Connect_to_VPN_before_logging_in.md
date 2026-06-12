---
title: "Connect to VPN before logging in"
date: 2016-02-12
forum: Networking &amp; Wireless
---

### Post by fnadde42 on 2016-02-12
I have a VPN connection in my Network Manager which automatically connect at the same time i plug in a network cable into my computer. The problem is that a lot of times I use non-encrypted WiFi where I can connect but must do so without my VPN connection. After I have established connection I can connect my VPN. However, there are a lot of applications on my computer and I do not want any of those to try automatically connect on an unencrypted connection, hence I want to connect to WiFI AND VPN before I log in and all my applications starts screaming out secrets unencrypted. Is this possible?

---

### Post by alexandari on 2016-02-12
Hey there! Here is something you might try out, see if it works for you. Open up root's crontab **sudo crontab -e** and add the following:

@startup /usr/bin/nmcli con up id "yourwifiname"; openvpn --config /path/to/your/openvpn.conf

that means,that at reboot your machine will connect up to your wifi and after that will connect to openvpn. Keep in mind that you need to have your VPN username and password included in the file or it will prompt you for them. I don't know if that's the most efficient method but, try it out

---

