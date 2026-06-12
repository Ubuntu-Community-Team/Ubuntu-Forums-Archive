---
title: "need to move files from mac-formatted iPod to Ubuntu or WinPC"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by hanzj on 2010-12-18
Hello,

I need to move some files from a Mac-formatted iPod to either my Ubuntu computer or a WinPC. How can I do this? 



When I plug in the iPod to a WinPC, windows says I need to reformat the iPod for Windows, but that means that my files will be deleted.
When I plug in the iPod to Ubuntu, I don't see it in the "Computer" folder.

The iPod is a 6th gen iPod Classic.

I don't have access to a Mac computer.
Please help.

---

### Post by cariboo on 2010-12-18
What does dmesg tell you when you plug the device in? Open a terminal and type:

```
dmesg | tail -n15
```

after plugging the device in, and paste the output in your next post.

---

### Post by hanzj on 2010-12-18
:~$ dmesg | tail -n15
[ 6730.461302] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6730.461307] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 6730.461311] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 6730.461316] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 6730.461323] end_request: I/O error, dev sr0, sector 0
[ 6753.487437] usb 1-10: USB disconnect, address 7
[ 6880.429233] ndiswrapper (NdisMIndicateStatus:2084): unrecognized PMKID ignored
[ 6921.800039] usb 1-9: new high speed USB device using ehci_hcd and address 8
[ 6921.933271] usb 1-9: configuration #1 chosen from 1 choice
[ 6950.130401] usb 1-9: USB disconnect, address 8
[ 6952.540032] usb 1-10: new high speed USB device using ehci_hcd and address 9
[ 6952.673284] usb 1-10: configuration #1 chosen from 1 choice
[ 6987.659416] usb 1-10: USB disconnect, address 9
[ 6994.604046] usb 1-10: new high speed USB device using ehci_hcd and address 10
[ 6994.738039] usb 1-10: configuration #1 chosen from 2 choices

---

### Post by nothingspecial on 2010-12-18
This may be nonsense

(in that this is understanding rather than experience)

However, I shall continue......

..... if your ipod is mac formated, it is using the hfs+ file system. This can only be mounted on linux with journaling disabled.

Therefore, you have to disable journaling.

How you do that, I don`t know. Sorry.

---

