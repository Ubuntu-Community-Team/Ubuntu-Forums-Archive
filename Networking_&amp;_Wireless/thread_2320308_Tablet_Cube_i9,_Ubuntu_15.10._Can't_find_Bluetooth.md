---
title: "Tablet Cube i9, Ubuntu 15.10. Can't find Bluetooth."
date: 2016-04-12
forum: Networking &amp; Wireless
---

### Post by Luddevig on 2016-04-12
When I go to Bluetooth settings it says "No Bluetooth adapters found". Wireless info script attached. 

At first the wifi wouldn't work, but I found a site that helped me a lot ( [https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8723AU-chipset-0bda:b720-](https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8723AU-chipset-0bda:b720-) ). 

The Cube i9 uses Realtek RTL8723BU chipset, but I can only see 0bda:b720 when I run the wireless info script, so I had two options, RTL8723**B**U and RTL8723**A**U. I tried A first, but B was the right one. But in the guide for A there is an addition:
> If you also want Bluetooth, execute the following commands one by one:
git clone [https://github.com/lwfinger/rtl8723au_bt.git](https://github.com/lwfinger/rtl8723au_bt.git)
cd rtl8723au_bt
make
sudo make install
sudo modprobe -v 8723au_bt

Of course that didn't work, and I also tried to change every A to a B in the files, but that didn't do the trick either. I get the error(s): 
> ludvig@ludvig-cube-i9:~$ cd rtl8723bu_bt
ludvig@ludvig-cube-i9:~/rtl8723bu_bt$ make
make -C /lib/modules/4.2.0-35-generic/build M=/home/ludvig/rtl8723bu_bt modules
make[1]: Entering directory '/usr/src/linux-headers-4.2.0-35-generic'
  CC [M]  /home/ludvig/rtl8723bu_bt/rtk_btusb.o
/home/ludvig/rtl8723bu_bt/rtk_btusb.c:41:2: error: #error "This repo is only for kernels older than 4.1.0. For kernel 4.1 or later, use the kernel branch."
 #error "This repo is only for kernels older than 4.1.0. For kernel 4.1 or later
    . ^
/home/ludvig/rtl8723bu_bt/rtk_btusb.c: In function &#8216;btusb_intr_complete&#8217;:
/home/ludvig/rtl8723bu_bt/rtk_btusb.c:168:7: error: implicit declaration of function &#8216;hci_recv_fragment&#8217; [-Werror=implicit-function-declaration]
   if (hci_recv_fragment(hdev, HCI_EVENT_PKT,
         . . .^
/home/ludvig/rtl8723bu_bt/rtk_btusb.c: In function &#8216;btusb_close&#8217;:
/home/ludvig/rtl8723bu_bt/rtk_btusb.c:575:18: error: &#8216;NUM_REASSEMBLY&#8217; undeclared (first use in this function)
  for (i = 0; i < NUM_REASSEMBLY; i++) {
                    . . . . . . . . . . . . ^
/home/ludvig/rtl8723bu_bt/rtk_btusb.c:575:18: note: each undeclared identifier is reported only once for each function it appears in
/home/ludvig/rtl8723bu_bt/rtk_btusb.c:576:10: error: &#8216;struct hci_dev&#8217; has no member named &#8216;reassembly&#8217;
   if(hdev->reassembly[i]) {
            . . . . . . . ^
/home/ludvig/rtl8723bu_bt/rtk_btusb.c:577:18: error: &#8216;struct hci_dev&#8217; has no member named &#8216;reassembly&#8217;
    kfree_skb(hdev->reassembly[i]);
                    . . . . . . . . . . . . . . . ^
/home/ludvig/rtl8723bu_bt/rtk_btusb.c:578:8: error: &#8216;struct hci_dev&#8217; has no member named &#8216;reassembly&#8217;
    hdev->reassembly[i] = NULL;
          . . . . . ^
cc1: some warnings being treated as errors
scripts/Makefile.build:264: recipe for target '/home/ludvig/rtl8723bu_bt/rtk_btusb.o' failed
make[2]: *** [/home/ludvig/rtl8723bu_bt/rtk_btusb.o] Error 1
Makefile:1398: recipe for target '_module_/home/ludvig/rtl8723bu_bt' failed
make[1]: *** [_module_/home/ludvig/rtl8723bu_bt] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.2.0-35-generic'
Makefile:15: recipe for target 'all' failed
make: *** [all] Error 2

Am I on the right track? Where do I go from here? Is there another fix?

I also found someone with Bluetooth problems for the 0bda:b720, but I can't understand what they where doing. ( [https://github.com/lwfinger/rtl8723bu/issues/2](https://github.com/lwfinger/rtl8723bu/issues/2) ).

---

### Post by chili555 on 2016-04-12
I am not very experienced with BT, but your error is here:> ludvig@ludvig-cube-i9:~$ cd rtl8723bu_bt
ludvig@ludvig-cube-i9:~/rtl8723bu_bt$ make
make -C /lib/modules/4.2.0-35-generic/build M=/home/ludvig/rtl8723bu_bt modules
make[1]: Entering directory '/usr/src/linux-headers-4.2.0-35-generic'
CC [M] /home/ludvig/rtl8723bu_bt/rtk_btusb.o
/home/ludvig/rtl8723bu_bt/rtk_btusb.c:41:2: error: #error "This repo is only for kernels older than 4.1.0. [COLOR="#FF0000"]For kernel 4.1 or later, use the kernel branch.[/COLOR]"I suggest you try:```
cd ~
rm -rf rtl8723au_bt
git clone https://github.com/lwfinger/rtl8723au_bt.git
cd rtl8723au_bt
git checkout kernel
make
sudo make install
```Reboot.

That's it! That's all I have! Outa talent right here!!!

---

### Post by Luddevig on 2016-04-13
That's awesome. Thanks :)

---

