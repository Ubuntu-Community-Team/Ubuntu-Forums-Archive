---
title: "libusb vs. libusb-1.0-0"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by psi36 on 2010-10-30
I want to install some drivers for an eID card reader, which I need to compile myself.
I get this error message:
```
No package 'libusb' found
configure: error: install libusb 0.1.12 or later
```
There is are two packages in the repositories: libusb-0.1-4 and libusb-1.0-0, both are installed. The second one is clearly > 0.1.12, but it's not found/recognized i guess. Is this because the name of the package is libusb-1.0-0 in stead of libusb? And what can I do about it?

---

### Post by psi36 on 2010-11-02
OK, it was very simple: just needed to ```
sudo apt-get install libusb-dev
```

---

