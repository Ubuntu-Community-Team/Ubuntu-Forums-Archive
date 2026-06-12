---
title: "OpenVPN/PPTP Queries Greyed Out"
date: 2014-09-30
forum: Networking &amp; Wireless
---

### Post by griff3 on 2014-09-30
I recently discovered one of my old netbooks in a cardboard box, so I installed Lubuntu (32bit) on to it. I've been using it for SSH, FTP, and I run TightVNC on it. I've searched around google, and I haven't found a solution for my current problem:

Whenever I try to configure a VPN the setting are greyed out. I followed all the steps on two places and neither have worked; [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN) and somewhere else I installed this; network-manager-openvpn network-manager-pptp network-manager-pptp-gnome network-manager-vpnc
EXAMPLE OF WHAT'S HAPPENING:
  

[IMG]https://i.imgur.com/tfbHNqm.png[/IMG][IMG]http://i.imgur.com/3n2e1YY.png[/IMG]

---

### Post by griff3 on 2014-10-02
I still haven't gotten a reply, and I haven't solved the problem.

---

### Post by aaron_surabhi on 2014-10-03
I think you must read this: [https://www.bestvpnservicemag.com/vpn-protocols-pptp-l2tp-openvpn-sstp/](https://www.bestvpnservicemag.com/vpn-protocols-pptp-l2tp-openvpn-sstp/) it's all about [COLOR=#63656A][FONT=Open Sans]VPN Tunnelling Protocols. Hope this helps![/FONT][/COLOR]

---

### Post by griff3 on 2014-10-03
Unfortunately that doesn't really help my case, this more of an OS specific problem.

---

### Post by weatherman2 on 2014-10-03
I have used OpenVPN successfully in Ubuntu (both clients and servers) for years, but I have very little experience with Lubuntu - sorry!

---

### Post by griff3 on 2014-10-03
Yeah this is annoying. I'm considering installing Xubuntu or something equally as light, considering it's a netbook, but I don't want to risk losing my files. The most I do right now is connect to a Tor node, and it's unfortunate that I can't pair that with a VPN.

---

### Post by weatherman2 on 2014-10-03
You can always try connecting to your VPN via command line openvpn.  You'll have to go into the manpage for openvpn and figure out the command-line options, though.  If you get error messages, they may help you figure out original the issue.

---

