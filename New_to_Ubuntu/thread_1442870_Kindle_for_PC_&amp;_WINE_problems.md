---
title: "Kindle for PC &amp; WINE problems"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by nuwave on 2010-03-30
Hello, 
I was having problems with Kindle PC under WINE. It seems to have installed fine but when I click to open it nothing happens. I tried opening it in Terminal and I had this output
```

ed@ed-laptop:~/.wine/dosdevices/c:/Program Files/Amazon/Kindle For PC$ wine KindleForPC.exe
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
fixme:system:SystemParametersInfoW Unimplemented action: 8204 (SPI_GETFONTSMOOTHINGCONTRAST)
fixme:crypt:CertGetNameStringW unimplemented for type 2
ed@ed-laptop:~/.wine/dosdevices/c:/Program Files/Amazon/Kindle For PC$ 

```

Please help I really need to have this app running.
Thanks

---

### Post by nuwave on 2010-03-30
Ok I got things fixed basicly I found this post that had a run-down of what was going on. To summarize the post Amazon changed something in the download but if you download the previous version it works. I have it working just fine and I'm very happy. Thanks to everyone on the other post and I suggest anyone having problems with this app to check this post.

[http://ubuntuforums.org/showthread.php?t=1326044&highlight=kindle+wine+linux](http://ubuntuforums.org/showthread.php?t=1326044&highlight=kindle+wine+linux)

---

### Post by nick3499 on 2012-10-05
I think right now there are two main tricky tips for getting that pesky Kindoze for PC running on an Ubuntu system.
1. finally settle with a previous version. :KS
2. cut away the "deadbeef" :KS

I was able to push the Kindle for PC version up to 1.9.0 using the "deadbeef" trick. when I tried 1.9.3, I received an "you have an obsolete version":( error message.

---

