---
title: "GoogleEarth Install"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Joelbruce on 2009-02-15
I have the googleearth installer icon on my desktop. I have tried the sh googleearthlinux.bin command in a terminal box, and the reply is: sh: Can't open googleearthlinux.bin. Any ideas on how to get it to install?

---

### Post by supersonicdarky on 2009-02-15
in terminal
```
chmod +x *googleearth.bin*
./*googleearth.bin*
```
that should run the installer

---

### Post by dox_drum on 2009-02-15
> **supersonicdarky said:**
> in terminal
```
chmod +x *googleearth.bin*
./*googleearth.bin*
```
that should run the installer

I did it for install the 5th version of googleearth, but it works very badly... I don't know why. It's very slow and graphics are not configured.

Any idea how to repair it or unistall it?

Thank you.

---

### Post by MarblePanther on 2009-02-15
> **dox_drum said:**
> I did it for install the 5th version of googleearth, but it works very badly... I don't know why. It's very slow and graphics are not configured.

Any idea how to repair it or unistall it?

Thank you.

It is a beta after all, perhaps try 4th version and check your video drivers?

For future reference it may be easier to just right click on the file and go to permissions and set executable, then type sudo in terminal and drag the file into it next to sudo and press enter.

to uninstall it:  remove the google file in /opt with:   sudo -rm -rf /opt/putthenameofthegooglefolderhere

replace putthenameofthegooglefolderhere with the real folder name (i can't recall the exact name)

---

### Post by Joelbruce on 2009-02-15
I tried sudo with the drag and drop and got a dialog box as follows, Could not load 'googleearth-linux-plu-4.3.7284. And under that, in small light type, Unrecognized image file format.

---

### Post by Joelbruce on 2009-02-15
I then closed the dialog box, hit enter, and received back the file name followed by, No such file or directory.

---

### Post by MarblePanther on 2009-02-15
Have you set it to be executable?

Always works for me...

---

### Post by dox_drum on 2009-02-15
Thank you!

I'll remove the 5th version and install the previous one.

Regards.

---

### Post by Joelbruce on 2009-02-15
Dragging and dropping without sudo worked.

---

