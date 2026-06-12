---
title: "After i got connection to internet..."
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by Johan Tam on 2007-06-09
After i boot into my Ubuntu, i tried ifconfig and i got 2 pppoe interfaces there ,ppp0 and ppp1,etc.
Both of them were using to receive and send packages,which was making my connection unstable 
and blocking.
Then i ran pstree -p to look at the process tree ,i found 3 pppd daemons , so i manually used
sudo killall -9 pppd to kill them all, after that i ran sudo pon dsl-provider ,and then the 'plog' 
shows everything seems fine ,i got connection to Internet. I use wget to download files ,it no more
automatically blocked at some point.
I've used pppoeconf several time to configure my ADSL connection , so i suspect i've made too 
many pppd to start on boot ,is that the keypoint ? How can i fix it ?
And there's one more question, before i entered Ubuntu , in the grub menu i saw 2 
Ubuntu 2.6.20.generic and recovery mode , the menu.lst is like:

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,7)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=f818bfce-a500-42c8-be3a-1cca12dfdccc ro quiet splash
initrd          /initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,7)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=f818bfce-a500-42c8-be3a-1cca12dfdccc ro single
initrd          /initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,7)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=f818bfce-a500-42c8-be3a-1cca12dfdccc ro quiet splash
initrd          /initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,7)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=f818bfce-a500-42c8-be3a-1cca12dfdccc ro single
initrd          /initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,7)
kernel          /memtest86+.bin
quiet

Can i easily remove one of them ?

---

