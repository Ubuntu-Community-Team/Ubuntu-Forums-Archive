---
title: "How to transfer a binary file via minicom?"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by cuthbertkao on 2008-04-22
Hi folks,

I am trying to transfer a binary file via minicom but in its "send file" options only there are only five options: zmodem, xmodem, ymodem, kermit, and ascii. In Windows XP, I can use "File->Send file" in Tera Term Pro terminal software and check its "Binary" checkbox. 

    Is there any body who knows how to do it? Thanks in advance.


Cuthbert

---

### Post by russo.mic on 2008-04-22
> **cuthbertkao said:**
> Hi folks,

I am trying to transfer a binary file via minicom but in its "send file" options only there are only five options: zmodem, xmodem, ymodem, kermit, and ascii. In Windows XP, I can use "File->Send file" in Tera Term Pro terminal software and check its "Binary" checkbox. 

    Is there any body who knows how to do it? Thanks in advance.


Cuthbert

Could you just mount the device to a location on your HD, then cp it over?  I'm asking and suggesting at the same time!

Russo

---

### Post by osx424242 on 2012-01-05
> **cuthbertkao said:**
> I am trying to transfer a binary file via minicom but in its "send file" options only there are only five options: zmodem, xmodem, ymodem, kermit, and ascii. In Windows XP, I can use "File->Send file" in Tera Term Pro terminal software and check its "Binary" checkbox. 

I just had to do this: I ignored minicom and catted the file directly to the serial port:

```
cat binfile > /dev/ttyUSB0
```

(if your user doesn't have permissions to access the serial port (i.e. you can only access the serial port in minicom by running as root or with sudo), you'll probably get an error; try something like "cat binfile | sudo tee /dev/ttyUSB0")

You can test this before sending your binary file by echoing a command to the serial port that you expect will generate some sort of response in minicom.  So, for example, I needed to send the command 'update' in minicom before uploading the file.  Instead of typing "update" in minicom, I can "echo update > /dev/ttyUSB0" and the device on the serial port (seen through minicom) responded with the "send update file:" prompt that I expected to see.

---

