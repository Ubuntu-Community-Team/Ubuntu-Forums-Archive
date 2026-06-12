---
title: "hello"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by zero_cool05 on 2008-11-16
Hello everyone, just managed to partition my hdd to have vista and ubuntu on the same machine. i'm a total newbi to ubuntu and was wondering what i need to get my wireless usb key working? it detects my wireless network, but when i select it and enter the key it just  won't connect. i just get the same window again asking me to input the key again. :( the wireless key is from netopia and so is the router. I know that my wep key is correct as the same key is working in vista, and i also tried to use it without any wepkey setted on the router and i cant connect. even changed the usb port of the wifi key didn't make a difference.

If anyone could help me out would be great as i wanna see how good ubuntu is.

regards

p.s hope this is the right prefix  :lolflag:

---

### Post by zero_cool05 on 2008-11-16
anyone????

---

### Post by gnusci on 2008-11-16
You should give more details, please read the sticky:

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Post the output of the commands described in [COLOR="Red"]HOWTO post a Wireless issue[/COLOR].

---

### Post by zero_cool05 on 2008-11-16
looked at that alredy, but don't understand it. checked the list for the wifi usb sticks, but mine wasn't on it

---

### Post by gnusci on 2008-11-16
Please post the output of this command

**$ lsusb**

Open a terminal (**Applications**->**Accessories**->**Terminal**), write the command above and post the output.

---

### Post by zero_cool05 on 2008-11-16
ok will try that. just need to reboot into ubuntu, and will the format of that be compatible with vista? as i can only use vista to go online???!!!

---

### Post by gnusci on 2008-11-16
> **zero_cool05 said:**
> ok will try that. just need to reboot into ubuntu, and will the format of that be compatible with vista? as i can only use vista to go online???!!!

Yeah, no problem, it just a text output, actually use this command to get the output in a text file on your desktop

```
$ lsusb > /home/$USER/Desktop/lsusb.log
```

Then post the content of the file **lsusb.log**, you can open with any text editor you like.

---

### Post by jnorthr on 2008-11-16
Please keep in mind that WEP and WPA keys may need to be entered as hexidecimal characters in some systems and/or as ascii characters in other systems. So just do a bit of home-work to make sure you are using the correct key PLUS the correct character coding, otherwise you will be using the correct key but still not satisfying the input requirements.

---

