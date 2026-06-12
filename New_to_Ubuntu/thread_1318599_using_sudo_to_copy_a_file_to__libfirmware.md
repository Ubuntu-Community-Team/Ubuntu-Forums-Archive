---
title: "using sudo to copy a file to  /lib/firmware"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by woody1 on 2009-11-07
I am trying to get a usb Win TV NOVA-T tuner to work in 8.10. I am trying to load the firmware using "sudo cp dvb-usb-megasky-02.fw /lib/firmware" .
The prompt in terminal is "colin@colin-desktop:~$", and the file "dvb-usb-megasky-02.fw" is on the desktop, but it doesn't copy it. The file, dvb-usb-dib0700-1.10.fw that is in /lib/firmware does not seem to work with my unit, the /var/log/messages suggest different firmware is needed.

Any suggestions as to what I am doing wrong.

Thanks for your help


               Colin

---

### Post by nothingspecial on 2009-11-07
You need to do ```
cd Desktop
``` first.

---

### Post by nothingspecial on 2009-11-07
or 

```
sudo cp Desktop/dvb-usb-megasky-02.fw /lib/firmware
```

You`ve got to get to your Desktop first.

---

### Post by woody1 on 2009-11-08
Thanks for the help, I hadn't realised that there were desktops and Desktops

Regards 
      Colin

---

### Post by nothingspecial on 2009-11-08
desktop is the name of your computer.

Desktop is a directory within it

;)

---

