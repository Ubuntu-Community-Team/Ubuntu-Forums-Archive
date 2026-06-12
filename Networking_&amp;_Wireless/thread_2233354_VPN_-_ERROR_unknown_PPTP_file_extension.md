---
title: "VPN - ERROR: unknown PPTP file extension"
date: 2014-07-08
forum: Networking &amp; Wireless
---

### Post by ddebny on 2014-07-08
When I try import .ovpn file
```
[COLOR=#2E8B57][FONT=Monaco]The file 'xxx.ovpn' could not be read or does nor contain recognized VPN connection information[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ERROR: unknown PPTP file extension"
[/FONT][/COLOR]
```

So I try:

```
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo apt-get install openvpn network-[/FONT][/COLOR][COLOR=#0000FF]**_manager_**[/COLOR][COLOR=#2E8B57][FONT=Monaco]-openvpn network-manager-openvpn-gnome[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Reading package lists... 90%[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Building dependency tree       [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Reading state information... Done[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Package network-manager-openvpn is not available, but is referred to by another package.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]This may mean that the package is missing, has been obsoleted, or[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]is only available from another source[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]Package network-manager-openvpn-gnome is not available, but is referred to by another package.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]This may mean that the package is missing, has been obsoleted, or[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]is only available from another source[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]E: Package 'network-manager-openvpn' has no installation candidate[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]E: Package 'network-manager-openvpn-gnome' has no installation candidate[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo apt-get install network-manager-vpnc[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Building dependency tree       [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Reading state information... Done[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Package network-manager-vpnc is not available, but is referred to by another package.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]This may mean that the package is missing, has been obsoleted, or[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]is only available from another source[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]E: Package 'network-manager-vpnc' has no installation candidate[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ clear[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo apt-get install openvpn network-manager-openvpn network-manager-openvpn-gnome[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Building dependency tree       [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Reading state information... Done[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Package network-manager-openvpn is not available, but is referred to by another package.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]This may mean that the package is missing, has been obsoleted, or[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]is only available from another source[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]Package network-manager-openvpn-gnome is not available, but is referred to by another package.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]This may mean that the package is missing, has been obsoleted, or[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]is only available from another source[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]E: Package 'network-manager-openvpn' has no installation candidate[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]E: Package 'network-manager-openvpn-gnome' has no installation candidate[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ sudo apt-get install network-manager-vpnc[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Building dependency tree       [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Reading state information... Done[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Package network-manager-vpnc is not available, but is referred to by another package.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]This may mean that the package is missing, has been obsoleted, or[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]is only available from another source[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]E: Package 'network-manager-vpnc' has no installation candidate[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$[/FONT][/COLOR]
```

And I try repair next problem([http://askubuntu.com/questions/246041/package-network-manager-openvpn-is-not-available-but-is-referred-to-by-another](http://askubuntu.com/questions/246041/package-network-manager-openvpn-is-not-available-but-is-referred-to-by-another))

```
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ deb http://archive.ubuntu.com/ubuntu quantal universe[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]No command 'deb' found, did you mean:[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Command 'dab' from package 'bsdgames' (universe)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Command 'deb3' from package 'quilt' (main)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Command 'derb' from package 'icu-devtools' (main)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Command 'xdeb' from package 'xdeb' (universe)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Command 'debi' from package 'devscripts' (main)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Command 'debc' from package 'devscripts' (main)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Command 'dwb' from package 'dwb' (universe)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]deb: command not found[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ubuntu@ubuntu:~$ [/FONT][/COLOR]
```

How can i fix it? :( I need import ovpn.

---

### Post by ddebny on 2014-07-08
Anybody know?

---

