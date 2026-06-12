---
title: "Mounted network share - 'jerky' file transfer"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by element42 on 2008-06-12
I've got a share on a NAS that I mount in ubuntu (hardy) from the terminal with one of
```
sudo mount -t nfs NAS:/share /share/
```
```
sudo mount -t cifs cifs //NAS/share /share/ -o username=user,password=pass,iocharset=utf8,uid=1000
```
```
 sudo smbmount //NAS/share /share -o username=user,password=pass,uid=1000,iocharset=utf8
```
(where NAS and share are substitude with the real thing!) and it all works okay. But when I transfer a large file (anything over 20ish MB - and I'm usually transferring gbs of music) it does it very jerkily: flying along for a second then pausing and doing nothing. This is judged from the Nautilus progress bar. 

Strangely, when I use Nautilus to browse my network and get into my share that way (using smb), the files transfer smoothly!

I'm sure that when I mount it from the command line, the transfers would be quicker, because when the progress bar is actually moving, it moves very fast! Am I just being deceived by the progress bar? Or is there an issue here?

---

