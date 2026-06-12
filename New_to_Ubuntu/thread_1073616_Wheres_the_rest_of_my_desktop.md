---
title: "Wheres the rest of my desktop"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by noob101 on 2009-02-18
I've posted earlier but reading it again it made no sense so I will try once more. I've installed Ubuntu 8.10 from the live cd but have a problem when viewing the desktop. The icons on the right and the notification area are not visible, nor is the bottom taskbar. 

I've tryed changing the screen resolution but this just gives me an unreadable screen.

Can anyone help me with fixing this problem please.

---

### Post by SunnyRabbiera on 2009-02-18
Well there is a glitch with ibex when setting higher resolutions.
I suggest try your higher resolution one more time but hit control+alt+backspace or try logging out in the menu under system> log out (yournamehere)

---

### Post by hatten on 2009-02-18
make sure the settings for the monitor is correct and there is no black borders around the screen. These settings can mostly be found by pressing the buttons on the front of the monitor.

---

### Post by noob101 on 2009-02-18
The resolution is set to 1600x1200 (4:3) at the moment. Ive tryed changing it a couple of times to lower settings but whenever I have it makes the screen unreadable.

---

### Post by noob101 on 2009-02-18
> **hatten said:**
> make sure the settings for the monitor is correct and there is no black borders around the screen. These settings can mostly be found by pressing the buttons on the front of the monitor.

Sorry installed this on a lappy fujistu siemens 7320 so this doesnt apply. Should have posted more info in the beginning :(

---

### Post by SunnyRabbiera on 2009-02-18
Did you try what I suggested?

---

### Post by noob101 on 2009-02-18
> **SunnyRabbiera said:**
> Did you try what I suggested?

Yeah i've just tryed it and its made no difference. This has me a bit stumped so any help is being very gratefuly recieved .

---

### Post by SunnyRabbiera on 2009-02-18
got any information on your video card?

---

### Post by noob101 on 2009-02-18
Yeah its a UniChrome Pro integrated graphics, up to 64 MB shared memory.

---

### Post by noob101 on 2009-02-18
The display is listed as being 1280x800 but if I select that as the resolution it messes the desktop up ?

---

### Post by Therion on 2009-02-18
> **noob101 said:**
> Yeah its a UniChrome Pro integrated graphics, up to 64 MB shared memory.
Ouch... Those UniChrome drivers, or the lack thereof, really, are going to be a pain.   

This MIGHT help but I'm hesitant to suggest you try it:  ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by noob101 on 2009-02-18
> **Therion said:**
> Ouch... Those UniChrome drivers, or the lack thereof, really, are going to be a pain.   

This MIGHT help but I'm hesitant to suggest you try it:  ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

The hesitant to suggest could probably do with an explanation lol. Im willing to try anything but I will point out that the cd drive is broken so I have to boot from usb key.

---

### Post by noob101 on 2009-02-18
Can anyone suggest where I can get suitable drivers  ???

---

