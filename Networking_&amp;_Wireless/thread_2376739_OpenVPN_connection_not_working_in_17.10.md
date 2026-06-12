---
title: "OpenVPN connection not working in 17.10"
date: 2017-11-05
forum: Networking &amp; Wireless
---

### Post by Chesslover on 2017-11-05
I had working OpenVPN connection on my ubuntu 17.04. After upgrade (reinstall) to 17.10, I made another (the same) OpenVPn connection, but it does not establish connection.  Result of the command sudo openvpn vpnbook-euro2-tcp443.ovpn:
```
Sun Nov  5 22:56:20 2017 OpenVPN 2.4.3 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] built on Jul  3 2017
Sun Nov  5 22:56:20 2017 library versions: OpenSSL 1.0.2g  1 Mar 2016, LZO 2.08
Enter Auth Username: vpnbook
Enter Auth Password: *******
Sun Nov  5 22:56:48 2017 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Sun Nov  5 22:56:48 2017 NOTE: --fast-io is disabled since we are not using UDP
Sun Nov  5 22:56:48 2017 TCP/UDP: Preserving recently used remote address: [AF_INET]176.126.237.214:443
Sun Nov  5 22:56:48 2017 Socket Buffers: R=[87380->87380] S=[16384->16384]
Sun Nov  5 22:56:48 2017 Attempting to establish TCP connection with [AF_INET]176.126.237.214:443 [nonblock]
Sun Nov  5 22:56:49 2017 TCP: connect to [AF_INET]176.126.237.214:443 failed: Connection refused
Sun Nov  5 22:56:49 2017 SIGUSR1[connection failed(soft),init_instance] received, process restarting
Sun Nov  5 22:56:49 2017 Restart pause, 5 second(s)
```

Here is my syslog file content regarding unsuccessfull attempt of connecting through Network Manager (after 1 minute I'm timed out):
```
Nov  5 23:00:07 matej-GA-MA770-UD3 NetworkManager[554]: <info>  [1509919207.5789] audit: op="connection-activate" uuid="fda1f388-a8e8-42ee-ae9a-861ba62645da" name="book2" pid=12881 uid=1000 result="success"
Nov  5 23:00:07 matej-GA-MA770-UD3 NetworkManager[554]: <info>  [1509919207.5891] vpn-connection[0x55febea8f4b0,fda1f388-a8e8-42ee-ae9a-861ba62645da,"book2",0]: Started the VPN service, PID 13357
Nov  5 23:00:07 matej-GA-MA770-UD3 nm-applet[12881]: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed
Nov  5 23:00:07 matej-GA-MA770-UD3 nm-applet[12881]: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed
Nov  5 23:00:07 matej-GA-MA770-UD3 nm-applet[12881]: Can't set a parent on widget which has a parent
Nov  5 23:00:07 matej-GA-MA770-UD3 NetworkManager[554]: <info>  [1509919207.6086] vpn-connection[0x55febea8f4b0,fda1f388-a8e8-42ee-ae9a-861ba62645da,"book2",0]: Saw the service appear; activating connection
Nov  5 23:00:07 matej-GA-MA770-UD3 nm-applet[12881]: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed
Nov  5 23:00:07 matej-GA-MA770-UD3 nm-applet[12881]: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed
Nov  5 23:00:07 matej-GA-MA770-UD3 nm-applet[12881]: Can't set a parent on widget which has a parent
Nov  5 23:00:07 matej-GA-MA770-UD3 nm-applet[12881]: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed
Nov  5 23:00:07 matej-GA-MA770-UD3 nm-applet[12881]: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed
Nov  5 23:00:07 matej-GA-MA770-UD3 nm-applet[12881]: Can't set a parent on widget which has a parent
Nov  5 23:00:07 matej-GA-MA770-UD3 nm-openvpn[13363]: WARNING: file '/home/matej/Videos/key.key' is group or others accessible
Nov  5 23:00:07 matej-GA-MA770-UD3 nm-openvpn[13363]: OpenVPN 2.4.3 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] built on Jul  3 2017
Nov  5 23:00:07 matej-GA-MA770-UD3 nm-openvpn[13363]: library versions: OpenSSL 1.0.2g  1 Mar 2016, LZO 2.08
Nov  5 23:00:07 matej-GA-MA770-UD3 NetworkManager[554]: <info>  [1509919207.7707] vpn-connection[0x55febea8f4b0,fda1f388-a8e8-42ee-ae9a-861ba62645da,"book2",0]: VPN plugin: state changed: starting (3)
Nov  5 23:00:07 matej-GA-MA770-UD3 NetworkManager[554]: <info>  [1509919207.7707] vpn-connection[0x55febea8f4b0,fda1f388-a8e8-42ee-ae9a-861ba62645da,"book2",0]: VPN connection: (ConnectInteractive) reply received
Nov  5 23:00:07 matej-GA-MA770-UD3 nm-openvpn[13363]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Nov  5 23:00:07 matej-GA-MA770-UD3 nm-openvpn[13363]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Nov  5 23:00:07 matej-GA-MA770-UD3 nm-openvpn[13363]: TCP/UDP: Preserving recently used remote address: [AF_INET]176.126.237.214:443
Nov  5 23:00:07 matej-GA-MA770-UD3 nm-openvpn[13363]: Attempting to establish TCP connection with [AF_INET]176.126.237.214:443 [nonblock]
Nov  5 23:00:08 matej-GA-MA770-UD3 nm-openvpn[13363]: TCP: connect to [AF_INET]176.126.237.214:443 failed: Connection refused
Nov  5 23:00:08 matej-GA-MA770-UD3 nm-openvpn[13363]: NOTE: chroot will be delayed because of --client, --pull, or --up-delay
Nov  5 23:00:08 matej-GA-MA770-UD3 nm-openvpn[13363]: NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Nov  5 23:00:08 matej-GA-MA770-UD3 nm-openvpn[13363]: SIGUSR1[connection failed(soft),init_instance] received, process restarting
Nov  5 23:00:13 matej-GA-MA770-UD3 nm-openvpn[13363]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Nov  5 23:00:13 matej-GA-MA770-UD3 nm-openvpn[13363]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Nov  5 23:00:13 matej-GA-MA770-UD3 nm-openvpn[13363]: TCP/UDP: Preserving recently used remote address: [AF_INET]176.126.237.214:443
Nov  5 23:00:13 matej-GA-MA770-UD3 nm-openvpn[13363]: Attempting to establish TCP connection with [AF_INET]176.126.237.214:443 [nonblock]
Nov  5 23:00:14 matej-GA-MA770-UD3 nm-openvpn[13363]: TCP: connect to [AF_INET]176.126.237.214:443 failed: Connection refused
```

---

### Post by #&amp;thj^% on 2017-11-05
This jumps out for me:
```
No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
```
Are you sure you have the right** "ca.crt file."** associated with the connection and the right password? 
A good place to start: [http://ubuntuhandbook.org/index.php/2014/05/establish-openvpn-connection-ubuntu-1404/](http://ubuntuhandbook.org/index.php/2014/05/establish-openvpn-connection-ubuntu-1404/)

---

### Post by Chesslover on 2017-11-05
I'm 99% sure I have the right file...

---

### Post by #&amp;thj^% on 2017-11-06
> **Chesslover said:**
> I'm 99% sure I have the right file...

I can now confirm with what you are seeing...Ubuntu Gnome 17.10
Tried opening a Ticket with vpnbook, But no response yet.
I will pass along any information if I hear from them at all.
Regards

---

### Post by Chesslover on 2017-11-07
I managed to connect to euro2 tcp80 server...

---

