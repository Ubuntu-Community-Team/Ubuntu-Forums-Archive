---
title: "After power down, must restart for some services to start"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by MajorTom00 on 2009-03-27
Every time I turn the computer off, I have to reboot it before DHCP will enable, why does this happen and how can I set it so I won't need to reboot after each power down?
Thanls.

---

### Post by ddrichardson on 2009-03-28
When you say "turn off" do you mean "stand by".

If so then you need to edit a file and tell it to restart the network daemon on resume:
```
sudo vi /etc/default/acpi-support
```

Change the line to read:
```
   STOP_SERVICES=&#8220;networking&#8221;
```

---

### Post by Eisenwinter on 2009-03-28
Note that to edit in vi, press the "a" key, then you can start typing.

When you finish editing, press ESC, and then type in :wq to save the file and quit (w - write, q - quit).

I wrote this just so you won't get confused, if you never used vi before.

---

### Post by ddrichardson on 2009-03-28
Fair one, if you don't care for vi, then```
gksudo gedit /etc/default/acpi-support
```

---

