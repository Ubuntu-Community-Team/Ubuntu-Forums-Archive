---
title: "USB permissions"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by Yerushalmi on 2010-02-14
Every time I format a new USB drive, I only have read permissions - no write permissions except as root. This is quite irritating.

Two questions:

1) How do I open up write permissions on the drive afterwards?
2) How do I make write permissions the default?

---

### Post by chewearn on 2010-02-14
```
sudo chown user:user /path/to/usb
```

---

### Post by lyall on 2010-02-14
see the following links

for USB Introduction see
[https://help.ubuntu.com/community/Mount/USB]("https://help.ubuntu.com/community/Mount/USB")

for MountUSB see
[https://help.ubuntu.com/community/Mount/USB]("https://help.ubuntu.com/community/Mount/USB")

for renaming see
[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

good luck and have fun learning

---

