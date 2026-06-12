---
title: "reinstalling pia vpn problem"
date: 2016-08-11
forum: Networking &amp; Wireless
---

### Post by jgw on 2016-08-11
I have just reinstalled the pia vpn.  

I had problems, sent an email to pia and they told me to remove and reinstall.  I did that and, now, everything is dandy!

I am trying to figure out how to get the pia icon on the top bar.  I have tried the config button (on bottom of server list) but nothing happens when I press it.  

It seems that I also have a DNS leak.  I have, in theory followed the directions and fixed it but I still have the leak.  Here is the network info:
===============================================================================
                Connection profile details (Wired connection 1)
===============================================================================
connection.id:                          Wired connection 1
connection.uuid:                        6309560d-9cac-4104-a04f-1d5edcb9c3f7
connection.interface-name:              --
connection.type:                        802-3-ethernet
connection.autoconnect:                 yes
connection.autoconnect-priority:        0
connection.timestamp:                   1470938356
connection.read-only:                   no
connection.permissions:                 
connection.zone:                        --
connection.master:                      --
connection.slave-type:                  --
connection.autoconnect-slaves:          -1 (default)
connection.secondaries:                 4e5e6949-68ae-45a2-af19-cfd1d791379d
connection.gateway-ping-timeout:        0
connection.metered:                     unknown
connection.lldp:                        -1 (default)
-------------------------------------------------------------------------------
802-3-ethernet.port:                    --
802-3-ethernet.speed:                   0
802-3-ethernet.duplex:                  full
802-3-ethernet.auto-negotiate:          yes
802-3-ethernet.mac-address:             FC:AA:14:8C:6B:C7
802-3-ethernet.cloned-mac-address:      --
802-3-ethernet.mac-address-blacklist:   
802-3-ethernet.mtu:                     auto
802-3-ethernet.s390-subchannels:        
802-3-ethernet.s390-nettype:            --
802-3-ethernet.s390-options:            
802-3-ethernet.wake-on-lan:             1 (default)
802-3-ethernet.wake-on-lan-password:    --
-------------------------------------------------------------------------------
ipv4.method:                            auto                                              (this is actually: "automatic DHCP addresses only")
ipv4.dns:                               209.222.18.222,209.222.18.218     (addresses of pia servers)
ipv4.dns-search:                        
ipv4.dns-options:                       (default)
ipv4.addresses:                         
ipv4.gateway:                           --
ipv4.routes:                            
ipv4.route-metric:                      -1
ipv4.ignore-auto-routes:                no
ipv4.ignore-auto-dns:                   yes
ipv4.dhcp-client-id:                    --
ipv4.dhcp-timeout:                      0
ipv4.dhcp-send-hostname:                yes
ipv4.dhcp-hostname:                     --
ipv4.dhcp-fqdn:                         --
ipv4.never-default:                     no
ipv4.may-fail:                          no
ipv4.dad-timeout:                       -1 (default)
-------------------------------------------------------------------------------
ipv6.method:                            auto
ipv6.dns:                               
ipv6.dns-search:                        
ipv6.dns-options:                       (default)
ipv6.addresses:                         
ipv6.gateway:                           --
ipv6.routes:                            
ipv6.route-metric:                      -1
ipv6.ignore-auto-routes:                no
ipv6.ignore-auto-dns:                   no
ipv6.never-default:                     no
ipv6.may-fail:                          yes
ipv6.ip6-privacy:                       0 (disabled)
ipv6.addr-gen-mode:                     eui64
ipv6.dhcp-send-hostname:                yes
ipv6.dhcp-hostname:                     --
-------------------------------------------------------------------------------

===============================================================================
                  Connection profile details (PIA - US West)
===============================================================================
connection.id:                          PIA - US West
connection.uuid:                        4e5e6949-68ae-45a2-af19-cfd1d791379d
connection.interface-name:              --
connection.type:                        vpn
connection.autoconnect:                 no
connection.autoconnect-priority:        0
connection.timestamp:                   1470940456
connection.read-only:                   no
connection.permissions:                 
connection.zone:                        --
connection.master:                      --
connection.slave-type:                  --
connection.autoconnect-slaves:          -1 (default)
connection.secondaries:                 
connection.gateway-ping-timeout:        0
connection.metered:                     unknown
connection.lldp:                        -1 (default)
-------------------------------------------------------------------------------
ipv4.method:                            auto
ipv4.dns:                               209.222.18.222,209.222.18.218
ipv4.dns-search:                        
ipv4.dns-options:                       (default)
ipv4.addresses:                         
ipv4.gateway:                           --
ipv4.routes:                            
ipv4.route-metric:                      -1
ipv4.ignore-auto-routes:                no
ipv4.ignore-auto-dns:                   yes
ipv4.dhcp-client-id:                    --
ipv4.dhcp-timeout:                      0
ipv4.dhcp-send-hostname:                yes
ipv4.dhcp-hostname:                     --
ipv4.dhcp-fqdn:                         --
ipv4.never-default:                     no
ipv4.may-fail:                          yes
ipv4.dad-timeout:                       -1 (default)
-------------------------------------------------------------------------------
ipv6.method:                            auto
ipv6.dns:                               
ipv6.dns-search:                        
ipv6.dns-options:                       (default)
ipv6.addresses:                         
ipv6.gateway:                           --
ipv6.routes:                            
ipv6.route-metric:                      -1
ipv6.ignore-auto-routes:                no
ipv6.ignore-auto-dns:                   no
ipv6.never-default:                     no
ipv6.may-fail:                          yes
ipv6.ip6-privacy:                       0 (disabled)
ipv6.addr-gen-mode:                     stable-privacy
ipv6.dhcp-send-hostname:                yes
ipv6.dhcp-hostname:                     --
-------------------------------------------------------------------------------
vpn.service-type:                       org.freedesktop.NetworkManager.openvpn
vpn.user-name:                          --
vpn.data:                               ca = /etc/openvpn/ca.crt, password-flags = 1, connection-type = password, remote = us-west.privateinternetaccess.com, comp-lzo = yes, username = xxxxxxx
vpn.secrets:                            <hidden>
vpn.persistent:                         no
vpn.timeout:                            0
-------------------------------------------------------------------------------

---

