---
title: "How to Use Mobile Broadband via Bluetooth ?"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by hunkgagan on 2010-05-19
Hello friends,

I can connect mobile broadband through data cable. But how to connect it with Bluetooth.

Thanks in advance.

---

### Post by ankit singh on 2010-05-19
**this will help**
[https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)
do all the stuff in the link and then
Whenever u boot up ur computer,

run command
```
sudo rfcomm bind ur-phone-mac-address
```(compulsory and have to called everytime u boot ur computer.)

and then u type 

```
pon BluetoothDialup
``` and then wait for 15-20sec

However when u run the first command u will see that under network manager "new gsm connection"will appear.



[URL="https://help.ubuntu.com/community/BluetoothDialup"]
[/URL]

---

### Post by themusicalduck on 2010-05-19
I connect with my Nokia phone using the blueman bluetooth manager. It's in the software centre and you can select a device and tell it to use dial up networking (under serial ports or something, if I remember right).

---

