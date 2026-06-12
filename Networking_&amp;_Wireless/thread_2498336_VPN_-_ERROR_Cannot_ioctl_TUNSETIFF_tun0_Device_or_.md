---
title: "VPN - ERROR: Cannot ioctl TUNSETIFF tun0: Device or resource busy (errno=16)"
date: 2024-06-09
forum: Networking &amp; Wireless
---

### Post by gebbione on 2024-06-09
I am trying to connect to TunnelBear VPN, this uses certificates and user and password. After importing the configuration i try to run it from the UX but in syslog i see

```
[INDENT]Jun  7 09:10:06 bizmate-i7 NetworkManager[1735]: &lt;info&gt;  [1717737006.9673] vpn[0x55c1f3a78230,38417925-e00b-4cab-bc9c-9d741c81a2fc,&quot;TunnelBear_Italy&quot;]: starting openvpn
Jun  7 09:10:07 bizmate-i7 nm-openvpn[41760]: WARNING: --keysize is DEPRECATED and will be removed in OpenVPN 2.6
Jun  7 09:10:07 bizmate-i7 nm-openvpn[41760]: OpenVPN 2.5.9 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] built on Sep 29 2023
Jun  7 09:10:07 bizmate-i7 nm-openvpn[41760]: library versions: OpenSSL 3.0.2 15 Mar 2022, LZO 2.10
Jun  7 09:10:07 bizmate-i7 nm-openvpn[41760]: WARNING: --ns-cert-type is DEPRECATED.  Use --remote-cert-tls instead.
Jun  7 09:10:07 bizmate-i7 nm-openvpn[41760]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Jun  7 09:10:07 bizmate-i7 nm-openvpn[41760]: TCP/UDP: Preserving recently used remote address: [AF_INET]98.98.148.148:443
Jun  7 09:10:07 bizmate-i7 nm-openvpn[41760]: UDP link local: (not bound)
Jun  7 09:10:07 bizmate-i7 nm-openvpn[41760]: UDP link remote: [AF_INET]98.98.148.148:443
Jun  7 09:10:07 bizmate-i7 nm-openvpn[41760]: NOTE: chroot will be delayed because of --client, --pull, or --up-delay
Jun  7 09:10:07 bizmate-i7 nm-openvpn[41760]: NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Jun  7 09:10:09 bizmate-i7 nm-openvpn[41760]: WARNING: 'link-mtu' is used inconsistently, local='link-mtu 1549', remote='link-mtu 1570'
Jun  7 09:10:09 bizmate-i7 nm-openvpn[41760]: WARNING: 'auth' is used inconsistently, local='auth [null-digest]', remote='auth SHA256'
Jun  7 09:10:09 bizmate-i7 nm-openvpn[41760]: WARNING: 'comp-lzo' is present in remote config but missing in local config, remote='comp-lzo'
Jun  7 09:10:09 bizmate-i7 nm-openvpn[41760]: [5469/server] Peer Connection Initiated with [AF_INET]98.98.148.148:443
Jun  7 09:10:10 bizmate-i7 nm-openvpn[41760]: sitnl_send: rtnl: generic error (-101): Network is unreachable
Jun  7 09:10:10 bizmate-i7 nm-openvpn[41760]: ERROR: Cannot ioctl TUNSETIFF tun0: Device or resource busy (errno=16)
Jun  7 09:10:10 bizmate-i7 nm-openvpn[41760]: Exiting due to fatal error
Jun  7 09:10:10 bizmate-i7 NetworkManager[1735]: &lt;warn&gt;  [1717737010.3175] vpn[0x55c1f3a78230,38417925-e00b-4cab-bc9c-9d741c81a2fc,&quot;TunnelBear_Italy&quot;]: dbus: failure: connect-failed (1)[/INDENT]

```

I have looked around and some [non strictly ubuntu posts]("https://serverfault.com/questions/911317/cannot-ioctl-tunsetiff-tap0-device-or-resource-busy-errno-16") suggest that openvpn might need to be restarted and ensure the service is not blocking the port before starting it again and connecting. But this did not work. Also the network unreachable seems to be suggesting that i cannot connect to the VPN server but i doubt that is the actual error.

If you have any suggestions please let me know . Also if you want to try it the linux configuration page is a bit outdated, you will need:
- config file (I am trying to connect to the italian server) [https://tunnelbear.s3.amazonaws.com/support/linux/openvpn.zip](https://tunnelbear.s3.amazonaws.com/support/linux/openvpn.zip)
- [COLOR=#2B2E2F][FONT=&amp]Add a line break after [/FONT][/COLOR]**cert UserCertificate.crt**[COLOR=#2B2E2F][FONT=&amp] and enter [/FONT][/COLOR]**key PrivateKey.key**[COLOR=#2B2E2F][FONT=&amp] . Save the file.[/FONT][/COLOR]
[COLOR=#2B2E2F][FONT=&amp]- [/FONT][/COLOR][Download the Private Key here]("https://tunnelbear.s3.amazonaws.com/support/linux/PrivateKey.key.zip")[COLOR=#2B2E2F][FONT=&amp], unzip and add it to the openvpn folder.[/FONT][/COLOR]
[COLOR=#2B2E2F][FONT=&amp]- Try setting the configuration up once more [/FONT][/COLOR][following the guide]("https://www.tunnelbear.com/blog/linux_support/")[COLOR=#2B2E2F][FONT=&amp], and see if things work now.[/FONT][/COLOR]

---

### Post by currentshaft on 2024-06-09
I would probably start by addressing the warning messages and align configurations between server and client.

Check to see for other services bound to utun0 - do you have multiple VPN processes trying to start?

Take a packet capture with tcpdump locally and see if the server is responding as expected.

Just some ideas of things to try.

---

### Post by gebbione on 2024-06-10
Hi, thank you for the suggestion

I made another attempt but instead of restarting openvpn i simply killed it. Once done i was able to connect to the VPN, I assume the openvpn is only needed if i actually run a gateway from my machine and not needed if i want to connect as a client.

Anyhow it is working now

---

