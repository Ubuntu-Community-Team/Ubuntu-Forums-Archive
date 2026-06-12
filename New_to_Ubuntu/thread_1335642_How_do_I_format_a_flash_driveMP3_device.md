---
title: "How do I format a flash drive/MP3 device?"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by LinuxFox on 2009-11-23
I was thinking about formatting an MP3 player in Ubuntu.  It's just a flash stick with buttons, no Firmware.  I'd like to know how do I go about doing this.

I right-clicked it and there's no format option.  Any help please

---

### Post by marshmallow1304 on 2009-11-23
Use gparted.

```
sudo apt-get install gparted
```

---

### Post by LinuxFox on 2009-11-23
Thanks, I did this, and ran gparted under sudo, but I still don't see an option to format it.  I did find my disk under it though.

---

### Post by Madel on 2009-11-23
[How to Format a USB Flash Drive in Ubuntu]("http://www.ehow.com/how_4963426_format-usb-flash-drive-ubuntu.html")

You might want to try that guide. 
I haven't tested it myself, but from the looks of it, it should work.

---

### Post by LinuxFox on 2009-11-23
Thanks, the guide helped, but how do I safely remove the device now.  I know there's an option for it in Windows.

Edit: Nevermind, I figured out how to safely remove it myself.  Thanks a lot, I was able to format without problems.

---

### Post by SunnyRabbiera on 2009-11-23
For small flash drives I personally never reformat them, when you have up to 4GB of space on these drives FAT32 usually works fair enough.
Now when I have a large capacity drive its a different story, but for small drives I usually dont reformat.

---

