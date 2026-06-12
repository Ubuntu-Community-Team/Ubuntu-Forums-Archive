---
title: "Set up Serial Console"
date: 2017-04-16
forum: Networking &amp; Wireless
---

### Post by lordgallen on 2017-04-16
I am trying to make a connection via serial console to a serial device from terminal.

[LIST]
[*]I have a DB9-M cable and a USB to serial cable.
[*]Current software is Ubuntu 17.04
[*]Terminal is Bash
[/LIST]
I downloaded the ‘screen’ program, but I believe I am missing something else.

The command I am using is:```
screen /dev/tty.usbserial 115200
```
However, it disconnects after a few seconds because it finds no device to connect to.

How do I find a list of connected devices to make sure that the device is not using a different name?

I tried:```
df
```…however, I was not able to find any serial cable or device.

---

### Post by DuckHook on 2017-04-16
Welcome to the forums, lordgallen.

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity and refrain from using odd formatting, highlights, etc, which make posts difficult to read.

Please follow these instructions: [https://www.cyberciti.biz/hardware/5-linux-unix-commands-for-connecting-to-the-serial-console/](https://www.cyberciti.biz/hardware/5-linux-unix-commands-for-connecting-to-the-serial-console/)

If you need to install setserial, then:```
sudo apt install setserial
```
However, you likely won't need this app and only need to find the proper serial port, which is probably not the one you've been using. To find what yours is really called, use the methodology contained in the above link that involves grepping dmesg.

---

### Post by lordgallen on 2017-04-16
Thank-you for your kind welcome, and your help. The link looks great. I am looking through it right now, and will report back.

---

### Post by lordgallen on 2017-04-18
I found the link you provided to be very useful. I am now able to connect to my serial device via terminal 

Thank-you

---

### Post by DuckHook on 2017-04-19
Glad you were able to solve it.

If you are satisfied with this solution, please mark thread "solved" using thread tools at the top of this thread, so that others can benefit from your solution.

---

