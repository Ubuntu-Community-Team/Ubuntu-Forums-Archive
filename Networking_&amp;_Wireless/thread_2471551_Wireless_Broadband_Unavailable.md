---
title: "Wireless Broadband Unavailable"
date: 2022-02-02
forum: Networking &amp; Wireless
---

### Post by tbnrc on 2022-02-02
Hi,

I have a single board computer set up with a fresh dual boot of Win 10 and Ubuntu 20.04.3. In this setup I have a Telit LE910C4-NF modem/gps module connected through USB.

I have configured the APN in both OSes. I get a strong cellular connection in Win 10, but when booting in Ubuntu it does not work. The gps serial ports are available at ttyUSB1 & ttyUSB2, and I can send AT commands, but the network manager GUI indicates "Wireless Broadband Disabled". Mobile Broadband Settings page indicates that Mobile Broadband is Unavailable. The worst part is that I have another computer right next to it with the same version of Ubuntu and when I plug the modem into that one, it works perfectly! I'm pulling my hair out at this point. What am I missing?

```
> mmcli -L
     /org/freedesktop/ModemManager1/Modem/0 [Telit] LE910C4-NF
```

```
> nmcli dev status
DEVICE        TYPE     STATUS            CONNECTION
cdc-wdm0      gsm      unavailable       --
```

```
> nmcli con show
NAME             UUID                                     TYPE
MyConnection     cb9bc2dc-0f7e-41c0-aadf-febaa547c028     gsm
```

```
> nmcli con up MyConnection
Error: Connection activation failed: No suitable device found for this connection (device cdc-wdm0 not available because device is not available).
```

```
> nmcli dev connect cdc-wdm0
Error: Failed to add/activate new connection: Connection 'cdc-wdm0' is not available on device cdc-wdm0 because device is not available.
```

```
>nmcli con show 'MyConnection'
connection.id:                          MyConnection
connection.uuid:                        cb9bc2dc-0f7e-41c0-aadf-febaa547c028
connection.stable-id:                   --
connection.type:                        gsm
connection.interface-name:              cdc-wdm0
connection.autoconnect:                 yes
connection.autoconnect-priority:        0
connection.autoconnect-retries:         -1 (default)
connection.multi-connect:               0 (default)
connection.auth-retries:                -1
connection.timestamp:                   0
connection.read-only:                   no
connection.permissions:                 --
connection.zone:                        --
connection.master:                      --
connection.slave-type:                  --
connection.autoconnect-slaves:          -1 (default)
connection.secondaries:                 --
connection.gateway-ping-timeout:        0
connection.metered:                     unknown
connection.lldp:                        default
connection.mdns:                        -1 (default)
connection.llmnr:                       -1 (default)
connection.wait-device-timeout:         -1
ipv4.method:                            auto
ipv4.dns:                               --
ipv4.dns-search:                        --
ipv4.dns-options:                       --
ipv4.dns-priority:                      0
ipv4.addresses:                         --
ipv4.gateway:                           --
ipv4.routes:                            --
ipv4.route-metric:                      -1
ipv4.route-table:                       0 (unspec)
ipv4.routing-rules:                     --
ipv4.ignore-auto-routes:                no
ipv4.ignore-auto-dns:                   no
ipv4.dhcp-client-id:                    --
ipv4.dhcp-iaid:                         --
ipv4.dhcp-timeout:                      0 (default)
ipv4.dhcp-send-hostname:                yes
ipv4.dhcp-hostname:                     --
ipv4.dhcp-fqdn:                         --
ipv4.dhcp-hostname-flags:               0x0 (none)
ipv4.never-default:                     no
ipv4.may-fail:                          yes
ipv4.dad-timeout:                       -1 (default)
ipv6.method:                            auto
ipv6.dns:                               --
ipv6.dns-search:                        --
ipv6.dns-options:                       --
ipv6.dns-priority:                      0
ipv6.addresses:                         --
ipv6.gateway:                           --
ipv6.routes:                            --
ipv6.route-metric:                      -1
ipv6.route-table:                       0 (unspec)
ipv6.routing-rules:                     --
ipv6.ignore-auto-routes:                no
ipv6.ignore-auto-dns:                   no
ipv6.never-default:                     no
ipv6.may-fail:                          yes
ipv6.ip6-privacy:                       0 (disabled)
ipv6.addr-gen-mode:                     stable-privacy
ipv6.ra-timeout:                        0 (default)
ipv6.dhcp-duid:                         --
ipv6.dhcp-iaid:                         --
ipv6.dhcp-timeout:                      0 (default)
ipv6.dhcp-send-hostname:                yes
ipv6.dhcp-hostname:                     --
ipv6.dhcp-hostname-flags:               0x0 (none)
ipv6.token:                             --
ppp.noauth:                             yes
ppp.refuse-eap:                         no
ppp.refuse-pap:                         no
ppp.refuse-chap:                        no
ppp.refuse-mschap:                      no
ppp.refuse-mschapv2:                    no
ppp.nobsdcomp:                          no
ppp.nodeflate:                          no
ppp.no-vj-comp:                         no
ppp.require-mppe:                       no
ppp.require-mppe-128:                   no
ppp.mppe-stateful:                      no
ppp.crtscts:                            no
ppp.baud:                               0
ppp.mru:                                0
ppp.mtu:                                auto
ppp.lcp-echo-failure:                   0
ppp.lcp-echo-interval:                  0
gsm.auto-config:                        no
gsm.number:                             <hidden>
gsm.username:                           <hidden>
gsm.password:                           <hidden>
gsm.password-flags:                     0 (none)
gsm.apn:                                <hidden>
gsm.network-id:                         --
gsm.pin:                                <hidden>
gsm.pin-flags:                          0 (none)
gsm.home-only:                          no
gsm.device-id:                          --
gsm.sim-id:                             --
gsm.sim-operator-id:                    --
gsm.mtu:                                auto
proxy.method:                           none
proxy.browser-only:                     no
proxy.pac-url:                          --
proxy.pac-script:                       --

```

---

### Post by jeremy31 on 2022-02-03
What does this reveal? ```
sudo cat /var/lib/NetworkManager/NetworkManager.state; rfkill list
```

---

### Post by tbnrc on 2022-02-03
> **jeremy31 said:**
> What does this reveal? ```
sudo cat /var/lib/NetworkManager/NetworkManager.state; rfkill list
```

```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
```

/facedesk

Why? Why would Ubuntu install with WWAN enabled by default on one system, but disabled on another?

---

### Post by jeremy31 on 2022-02-03
You could try ```
sudo sed -i 's/false/true/' /var/lib/NetworkManager/NetworkManager.state
systemctl restart network-manager.service
```
See if that allows you to use it

---

