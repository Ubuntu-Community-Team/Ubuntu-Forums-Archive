---
title: "Ubuntu 9.04 screen resolution problem (SiS 760 Grfx Chip). Help required, urgently :("
date: 2010-01-02
forum: New to Ubuntu
---

### Post by maxzero on 2010-01-02
Hi, I am new to Linux & Ubuntu. I am having some trouble with my display resolution; I want 1152x870 or greater but it only allows 960x600 max, I have tried the **System>Preference>Display** option, the** sis_drv.so** method, & editing the** xorg.conf** file (that Ubuntu doesnt allow me to save) to no avail. So right now, I am absolutely out options, and any sort of help in this matter would be most appreciated. Thanks

System Config:
AMD 2800+
Asus K8S-MX
         >Using on-board graphics chip (SiS 760 @ 128MB)
LCD > NEC LCD1701

---

### Post by ikt on 2010-01-02
> **maxzero said:**
> editing the** xorg.conf** file (that Ubuntu doesnt allow me to save) to no avail.

When you edit the xorg.conf are you running as the root user?

As far as I'm aware SiS aren't the greatest when it comes to drivers, if you're able to acquire a $10 nvidia graphics card I would go for that.

---

### Post by 3rdalbum on 2010-01-02
> **maxzero said:**
> editing the** xorg.conf** file (that Ubuntu doesnt allow me to save)

For security and safety reasons, ordinary user accounts cannot modify files outside their home directories. Only the "root" (administrator) account can modify the system in this way. You can open files and file browser as root by installing the "nautilus-gksu" package from Synaptic Package Manager. When you next log in, you can right-click a file or folder and choose "Open as Administrator".

So, you'd right-click /etc/X11/xorg.conf and choose "Open as Administrator", and then you can edit the file.

If you wanted to do something on the command-line that involves system-wide access, you'd prefix it with the 'sudo' command. For instance, to copy a file with the 'cp' command:

```
sudo cp /home/chris/file.txt /usr/share/file.txt
```

To run a GUI program as root, you use the "gksudo" command:

```
gksudo nautilus
```

---

### Post by 3rdalbum on 2010-01-02
> **ikt said:**
> As far as I'm aware SiS aren't the greatest when it comes to drivers, if you're able to acquire a $10 nvidia graphics card I would go for that.

+1

SiS is pretty useless. If you can buy a cheap Nvidia card, you'll be much happier.

---

### Post by maxzero on 2010-01-02
> **3rdalbum said:**
> +1

SiS is pretty useless. If you can buy a cheap Nvidia card, you'll be much happier.

I would say +2, but if it were up to me I would get myself a Nvidia card, if I had the dough and was living in the US. :(

But, thanks for all the help guys. Ubuntu Rocks       :guitar:

---

### Post by ST3ALTHPSYCH0 on 2010-01-02
Dunno if it will help, you might try my 8.04 Live workaround (sig link.... mileage varies)

---

### Post by maxzero on 2010-01-02
[SIZE=7]DUDES! YOU GUYS ROCK, SO DOES UBUNTU! [/SIZE]:guitar:
I did everything as guys said and it was [SIZE=7]AWESOME
[SIZE=1]So here is my [SIZE=7]BIG THANKS to all you guys! ROCK ON & ROCK HARD![/SIZE][/SIZE]
[/SIZE]

---

### Post by sandyd on 2010-01-02
nvm

---

