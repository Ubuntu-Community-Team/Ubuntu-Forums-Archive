---
title: "OpenVPN Connection Failing"
date: 2019-01-30
forum: Networking &amp; Wireless
---

### Post by dutchvanderlinde on 2019-01-30
Hi there, this question is about OpenVPN failing on the GUI.
It works perfectly fine in the terminal, but it appears to only be failing when I try to add the connection on Settings => Network => VPN.
I'll post the logs below for Network Manager.

```
Jan 30 12:26:23 matthew-linux nm-openvpn[28995]: OpenVPN 2.4.4 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] built on Sep  5 2018
Jan 30 12:26:23 matthew-linux nm-openvpn[28995]: library versions: OpenSSL 1.1.0g  2 Nov 2017, LZO 2.08
Jan 30 12:26:23 matthew-linux nm-openvpn[28995]: WARNING: --ns-cert-type is DEPRECATED.  Use --remote-cert-tls instead.
Jan 30 12:26:23 matthew-linux nm-openvpn[28995]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Jan 30 12:26:23 matthew-linux nm-openvpn[28995]: TCP/UDP: Preserving recently used remote address: [AF_INET]63.141.252.132:1194
Jan 30 12:26:23 matthew-linux nm-openvpn[28995]: UDP link local: (not bound)
Jan 30 12:26:23 matthew-linux nm-openvpn[28995]: UDP link remote: [AF_INET]63.141.252.132:1194
Jan 30 12:26:23 matthew-linux nm-openvpn[28995]: NOTE: chroot will be delayed because of --client, --pull, or --up-delay
Jan 30 12:26:23 matthew-linux nm-openvpn[28995]: NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Jan 30 12:26:27 matthew-linux gnome-shell[1488]: JS ERROR: Exception in callback for signal: activate: Error: Error invoking IBus.set_global_engine_async: Expected function for callback argument callback, got undefined#012setEngine@resource:///org/gnome/shell/misc/ibusManager.js:207:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012activateInputSource@resource:///org/gnome/shell/ui/status/keyboard.js:490:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_emit@resource:///org/gnome/gjs/modules/signals.js:128:27#012activate@resource:///org/gnome/shell/ui/status/keyboard.js:65:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_inputSourcesChanged@resource:///org/gnome/shell/ui/status/keyboard.js:620:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012reload@resource:///org/gnome/shell/ui/status/keyboard.js:369:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_ibusSetContentType@resource:///org/gnome/shell/ui/status/keyboard.js:691:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_emit@resource:///org/gnome/gjs/modules/signals.js:128:27#012_setContentType@resource:///org/gnome/shell/misc/ibusManager.js:183:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22
Jan 30 12:27:12 matthew-linux nm-openvpn[28932]: TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Jan 30 12:27:12 matthew-linux nm-openvpn[28932]: TLS Error: TLS handshake failed
Jan 30 12:27:12 matthew-linux nm-openvpn[28932]: SIGUSR1[soft,tls-error] received, process restarting

```

Any help would be appreciated.

---

