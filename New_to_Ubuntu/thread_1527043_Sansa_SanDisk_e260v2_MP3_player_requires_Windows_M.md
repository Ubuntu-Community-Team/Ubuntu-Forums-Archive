---
title: "Sansa SanDisk e260v2 MP3 player requires Windows Media Player"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by Binjali on 2010-07-08
So I recently switched over to Ubuntu and am thrilled with it. There's just one small problem...my MP3 player (Sansa SanDisk e260v2, which has been discontinued) is a bit fussy. On my old Windows machine, I had to download Windows Media Player 10 or higher before the computer could even see that there was a data storage device connected to it. I never had to use WMP directly, just had to have it installed, and then I could drag and drop files as I pleased.

The same thing is happening now, only I can't just go and download WMP and go on my merry way. Any suggestions on how to get Windows Media Player to work on Ubuntu 9.10 (normal install) or how to get around the WMP requirement? I can open terminal, but my knowledge ends shortly after that.

---

### Post by oldos2er on 2010-07-08
If it's in MTP mode, try switching it to MSC. Or vice versa.

---

### Post by mgranet on 2010-07-08
SanDisk is known to push out firmware updates with actual new features. Unfortunately, Linux is not supported to to the flashing. If you have access to a Windows computer, you can update to the latest firmware (which may correct your problem, in addition to what **oldos2er** said) here:

[http://kb.sandisk.com/app/answers/detail/a_id/156/kw/firmware/r_id/101834]("http://kb.sandisk.com/app/answers/detail/a_id/156/kw/firmware/r_id/101834")

---

### Post by Merovius on 2010-07-08
I have an older e250 and it has worked with the last several versions of Ubuntu. If set to MSC mode it opens as a flash storage drive in Nautilus. If in MTP mode it opens in Rhythmbox with the MTP plugin enabled. (Edit, Plugins)

Just choose the USB mode in the settings menu of the Sansa. Should work.

---

