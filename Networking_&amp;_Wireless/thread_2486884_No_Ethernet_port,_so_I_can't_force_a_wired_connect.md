---
title: "No Ethernet port, so I can't force a wired connection"
date: 2023-05-15
forum: Networking &amp; Wireless
---

### Post by taratears on 2023-05-15
The laptop I'm working with has no port to hardwire the net. Does anyone have an idea around this? Wireless support all seems to require a hardline first. Ubuntu 20.4

---

### Post by sudodus on 2023-05-15
You can get an **ethernet adapter connected via usb** (or an ethernet card if it is desktop computer).

In many but not all computers, there is a wifi chip/card, that works 'out of the box' with the built-in linux drivers, so if you are lucky, you don't need such an adapter. Intel wifi is usually working, Broadcom wifi usually needs a proprietary driver, that you should download/install via ethernet (wired internet).

Are you running Ubuntu now (or Windows or MacOS or some other Linux distro)? Can you check what wifi hardware there is in the computer?

---

### Post by taratears on 2023-05-15
The laptop runs Ubuntu, and I'll pull up the original specs.

---

### Post by taratears on 2023-05-15
[https://support.hp.com/us-en/document/c04490851](https://support.hp.com/us-en/document/c04490851)

---

### Post by ajgreeny on 2023-05-15
That seems to suggest there is an ethernet card in the machine with a standard RJ-45 socket.
Are you saying that is not available?

>  Network Card : 10/100BASE-T Ethernet LAN (RJ-45 connector)

---

### Post by taratears on 2023-05-15
It doesn't, checking the serial again

---

### Post by sudodus on 2023-05-15
Thanks for the hardware specifications. I agree with ajgreeny, that there seems to be an ethernet port. Did you test it?

On the other hand, the description of the wireless hardware does not tell us about the brand name and model.

When running your Ubuntu, please run the following command line in terminal window.
```

sudo lshw -C network

```

Then copy&paste from the terminal window to a reply window here. Please put the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

The output should contain important information about your network hardware.

---

