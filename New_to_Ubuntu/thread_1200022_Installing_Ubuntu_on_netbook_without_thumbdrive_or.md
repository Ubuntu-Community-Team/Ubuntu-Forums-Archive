---
title: "Installing Ubuntu on netbook without thumbdrive or CD drive"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by Me887799 on 2009-06-29
I'd like to install Ubuntu's netbook remix but alas, I am without a thumbdrive or CD drive and I was wondering if there was anyway to install it through a network boot or something.  I have a separate computer on the same network.

I understand that Wubi is an option but I'd rather install it fully.

If it's any help, my netbook is an Acer Aspire one, with the 10.1 inch screen.  I think its the second generation of the aspire one, with the intel atom and 160gb HDD.

---

### Post by pytheas22 on 2009-06-29
There are several guides [here]("https://help.ubuntu.com/community/Installation#Server%20and%20network%20installations") explaining how to install over the network.  But just keep in mind that depending on how much experience you have with Ubuntu/how much time you're willing to invest in this, it could be difficult (on the other hand, you'll probably learn a lot).  If there's any way to just get a cheap USB drive and install from that, it would be the more user-friendly way to go.

If you have grub already installed on this computer, it might also work to follow [these instructions]("https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet") for downloading the initrd.gz and linux files and save them to somewhere on your Windows partition, then tell grub to boot to them.  But this probably wouldn't work if all you have is the Windows bootloader.

---

