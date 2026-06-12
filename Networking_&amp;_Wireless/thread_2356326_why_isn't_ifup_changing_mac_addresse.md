---
title: "why isn't ifup changing mac addresse"
date: 2017-03-22
forum: Networking &amp; Wireless
---

### Post by jeff666 on 2017-03-22
/etc/network/interfaces looks like: 

```


manual wlp3s0 
iface wlp3s0 inet static 
address 192.168.1.251 
netmask 255.255.255.0 
gateway 192.168.1.1 
hwaddress ether mac-here 
wpa-ssid ssid-here 
wpa-psk password  


```

When I comment out the "hwaddress ether " line everything works fine, but when it is active 'sudo ifup wlp3s0' will return errors. I'm not actual using "mac-here", I'm replacing it with a real mac address. The mac address im using also will work fine like 'sudo ip link set wlp3s0 down && sudo ip link set wlp3s0 address mac-here ' (but that will not be persistent through a reboot). The errors look like this:  

```


RTNETLINK answers: File exists Failed to bring up wlp3s0.  

```

and i also got   

```

wpa_supplicant: /sbin/wpa_supplicant daemon failed to start run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1 Failed to bring up wlp3s0. 

```

What am i doing wrong? The man pages say this is ok for manual method.

---

### Post by jeff666 on 2017-03-22
no one has any ideas?
i could use machanger, ip or ifconfig but this way should be better and more automatic.

---

### Post by chili555 on 2017-03-24
> [COLOR="#FF0000"]manual [/COLOR]wlp3s0 
iface wlp3s0 inet static 
address 192.168.1.251 
netmask 255.255.255.0 
gateway 192.168.1.1 
hwaddress ether mac-here 
wpa-ssid ssid-here 
wpa-psk passwordThe stanza is malformed. Please try:```
auto wlp3s0 
iface wlp3s0 inet static 
address 192.168.1.251 
netmask 255.255.255.0 
gateway 192.168.1.1 
hwaddress ether mac-here 
wpa-ssid ssid-here 
wpa-psk password
```And follow with:```
sudo ifdown wlp2s0 && sudo ifup -v wlp3s0
```Better?

---

### Post by jeff666 on 2017-03-24
doesn't auto just bring it up when i restart, i need manual because manual is well manual (i don't want interfaces up unless i say so). I tried it anyway didn't work looks like its running 'ip link set dev wlp3s0 address <mac> up' after wpa_supplicant which mean interfaces is already up and interface must be down to change mac, so i guess that sums it up that. Im just going to stick with this for now 'pre-up macchanger -m mac-here wlp3s0' please share any other ideas i really do appreciate any help thanks a ton. i should mention i tried rearranging the stanza because i thought order may have something to do with order (nope)

```

manual wlp3s0 
iface wlp3s0 inet static
hwaddress ether mac-here 
address 192.168.1.251
netmask 255.255.255.0 
gateway 192.168.1.1 
wpa-ssid ssid-here 
wpa-psk password

```

---

### Post by chili555 on 2017-03-24
I hope I'm not being too blunt, but if manual wlp3s0 is malformed in post #1, then it's still malformed, that is, wrong, here.  

If you want:> i don't want interfaces up unless i say soThen the correct stanza is:```
iface wlp3s0 inet static 
address 192.168.1.251 
netmask 255.255.255.0 
gateway 192.168.1.1 
hwaddress ether mac-here 
wpa-ssid ssid-here 
wpa-psk password
```In other words, omit any reference to how and when the interface comes up. After you boot, you can bring it up whenever you want with all the details specified in the file with:```
sudo ifup wlp3s0
```

---

### Post by jeff666 on 2017-03-25
ok yeah after reading the man pages again your right 'auto wlp3s0' is a different stanza then 'iface wlp3s0 inet static' and there is no 'manual wlp3s0' theres only iface wlp3s0 inet manual' how ever the man page does say the hwaddress should be ok with 'iface wlp3s0 inet static' i wonder why it still won't work?

---

### Post by chili555 on 2017-03-25
*blush* I flunked mac address many years ago at Torvalds U. 

The man page suggests that you might try:

```
iface wlp3s0 inet static 
address 192.168.1.251 
netmask 255.255.255.0 
gateway 192.168.1.1 
hwaddress mac-here 
wpa-ssid ssid-here 
wpa-psk password
```In other words, without ether. Please try it and let us know.> The manual Method
       This method may be used to define interfaces for which no configuration is done by default. Such interfaces can be configured manually by means of up
       and down commands or /etc/network/if-*.d scripts.

       Options

             ** hwaddress address**
                     Link local address or "random".

              mtu size
                     MTU size

   The dhcp Method
       This method may be used to obtain an address via DHCP with any of the tools: dhclient, pump, udhcpc, dhcpcd. (They have been listed in their order of
       precedence.)  If  you  have  a  complicated DHCP setup you should note that some of these clients use their own configuration files and do not obtain
       their configuration information via ifup.

       Options

              hostname hostname
                     Hostname to be requested (pump, dhcpcd, udhcpc)

              metric metric
                     Metric for added routes (dhclient)

              leasehours leasehours
                     Preferred lease time in hours (pump)

              leasetime leasetime
                     Preferred lease time in seconds (dhcpcd)

              vendor vendor
                     Vendor class identifier (dhcpcd)

              client client
                     Client identifier (dhcpcd)

              **hwaddress address**
                     Hardware address.


---

