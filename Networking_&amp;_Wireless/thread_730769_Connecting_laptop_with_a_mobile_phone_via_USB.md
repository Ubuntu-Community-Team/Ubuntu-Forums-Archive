---
title: "Connecting laptop with a mobile phone via USB"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by HuBaghdadi on 2008-03-21
Hi.
I got a Sony Ericsson K810i (yes, I can hear you congrats me :))
It is possible to connect my Ubuntu laptop with SE via Bluetooth but I want to connect them via USB.
What do I need on Ubuntu to do this?
(My laptop is blessed by Gutsy)
Thanks.

---

### Post by dannystaple on 2008-03-21
I am not sure (I do not own said phone) but this page may be of help: 

[Transfering files to the Sony Ericsson K610i from GNU/Linux through USB + OBEX]("http://www.olivierberger.com/weblog/index.php/2006/11/12/66-transfering-files-to-the-sony-ericsson-k610i-from-gnu-linux-through-usb-obex")

It is aimed at Debian, but since Debian is in the Ubuntu heritage, it should be handy. It also depends how similar the k610i and k810i are. It suggests OpenOBEX which may be in the ubuntu repos.
Try "aptitude install OpenOBEX fuse", then the stuff in that guide.

Hope it helps.

---

