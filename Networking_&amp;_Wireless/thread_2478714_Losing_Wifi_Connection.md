---
title: "Losing Wifi Connection"
date: 2022-09-02
forum: Networking &amp; Wireless
---

### Post by master-55555 on 2022-09-02
Please help me

---

### Post by master-55555 on 2022-09-02
Please help me

I post share please see

---

### Post by QIII on 2022-09-02
master-55555

Please do not intrude on the threads of other users.  And when you ask for help, please describe what it is you need.

Also please bear in mind that all of us here, including the Staff, are volunteers with real lives.  Please do not continue to ask for help repeatedly as you have.  You will not speed things up.

If after 12 hours you have not gotten a new response, you may feel free to bump your post.

---

### Post by mIk3_08 on 2022-09-03
> **master-55555 said:**
> Please help me
Please run the command below in your terminal and paste the result here in thread. To open terminal in your desktop just press ctrl + alt + t or just find it in your Ubuntu installed apps. Regard and cheers.
```
sudo lshw -C network
```

---

### Post by master-55555 on 2022-09-03
```

*-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 15
       serial: f0:2f:74:4c:ec:7b
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.048.00-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:33 ioport:e000(size=256) memory:fc904000-fc904fff memory:fc900000-fc903fff
  *-network
       description: Wireless interface
       product: RTL8822CE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 00
       serial: 94:08:53:64:fa:c9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtw_8822ce driverversion=5.15.0-46-generic firmware=N/A ip=192.168.1.82 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:86 ioport:d000(size=256) memory:fc800000-fc80ffff
```

---

### Post by master-55555 on 2022-09-03
```
AME             UUID                                  TYPE      DEVICE          
ALHN-E738 2      ee6e758a-570b-4c32-ae65-59c8c473f509  wifi      wlp3s0          
br-1540dc100ab8  f470c91d-f95e-4b77-90ea-8eabd4f18782  bridge    br-1540dc100ab8 
br-1e89040960f2  6d6fd2bc-bc52-4f0d-945c-cb5fe0b348c2  bridge    br-1e89040960f2 
br-4c35e4c03d42  b00dccb5-6944-4ea1-8bf3-2e16974f1b36  bridge    br-4c35e4c03d42 
br-59a597e6774c  97207d02-3d2e-4006-a22f-887f3954d5f3  bridge    br-59a597e6774c 
br-5c510e51036f  f6b6d82a-e5dc-4866-82a7-a8f8e4c0860d  bridge    br-5c510e51036f 
br-62b05783c88f  0fe7a5ca-afce-4692-b5dd-c67da39b9f06  bridge    br-62b05783c88f 
br-73d3fbdf14aa  b0751c7c-6ddb-47d5-a172-61b4175019f2  bridge    br-73d3fbdf14aa 
br-84d990d5c139  6dc5ef1b-7ab1-4f44-8d5a-a0116d2ef59c  bridge    br-84d990d5c139 
br-8aeca049bbe8  d6fcdc01-a694-46e5-9920-16586b5cdc95  bridge    br-8aeca049bbe8 
br-8c826c1d8a39  d50c850f-eddf-4d57-a720-2ca6291b72a3  bridge    br-8c826c1d8a39 
br-b7f109fbdb17  80574a18-70ba-4780-9fe2-03e76e937980  bridge    br-b7f109fbdb17 
br-bf66b1604eee  1c5aa742-f6d7-4e27-9145-359aabec50eb  bridge    br-bf66b1604eee 
br-d747d2a926cc  3f24ca76-6f33-4a13-a389-82c63a94d86b  bridge    br-d747d2a926cc 
br-e79031311dbc  4ba722bc-fa18-48e4-b0cf-6f5c6af39898  bridge    br-e79031311dbc 
br-ef3ed8ecda41  18f9fb95-bac7-4669-908d-ee5b3819474b  bridge    br-ef3ed8ecda41 
br-f8a9ad1573d9  500b185e-8105-4fdd-ac28-83d665c0d168  bridge    br-f8a9ad1573d9 
docker0          4e6bd54c-67b8-4100-836e-9e4954f60393  bridge    docker0         
70mai_d02_1f33   d6144797-7ed1-4c0b-9d22-de6b6495ff2d  wifi      --              
ALHN-C967        3f72db28-5ae0-4d3e-929d-5dd83eaccf53  wifi      --              
ALHN-E738        cc90ba03-3641-410d-849a-4f30d8bdb25c  wifi      --              
ALHN-E738 1      e445e4ae-d1b1-475e-b487-8a3a290b1286  wifi      --
Mobile           72739b02-f64f-4d2e-a4c4-cec29ac57b79  wifi      --              
netplan-enp2s0   7ea6f90b-3495-3533-948a-ef0035687c34  ethernet  --              
Profile 1        b94e0f90-b1c6-401e-9925-90002638a77e  ethernet  --              
Receb            c1b0d7ed-a231-4dd8-bf5b-2dffcda72905  wifi      -- 

```


netplan yaml

```

network:
  version: 2
  renderer: NetworkManager
  ethernets:
    enp2s0:
      dhcp4: no
      addresses: [192.168.1.82/24]
      gateway4:  192.168.1.255
      
```

---

### Post by QIII on 2022-09-03
Hi!

Code tags will preserve the formatting.  YAML is particularly sensitive to formatting and it would be helpful to be able to see that.  I've edited your posts accordingly.

To use code tags:

1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

