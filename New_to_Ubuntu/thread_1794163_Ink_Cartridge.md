---
title: "Ink Cartridge"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by arno48 on 2011-06-30
I have an old Epson D78 printer.
Is there an utility informing me about ink cartridge level and helping me to change a ink cartridge?

---

### Post by wolfen69 on 2011-06-30
```
sudo apt-get install escputil
```

---

### Post by arno48 on 2011-06-30
> **wolfen69 said:**
> ```
sudo apt-get install escputil
```

Thanks, I installed escputil.
Could you please let me know how I can either test ink level and change cartridge.

---

### Post by wolfen69 on 2011-06-30
> **arno48 said:**
> Thanks, I installed escputil.
Could you please let me know how I can either test ink level and change cartridge.

I've never used that utility as I use HP. As far as changing the cartridge, just google your model number, and you should be able to find instructions.

---

### Post by jtarin on 2011-06-30
[Stylus Toolbox]("http://stylus-toolbox.sourceforge.net/")

[Download .deb]("http://sourceforge.net/projects/stylus-toolbox/files/stylus-toolbox/0.2.7/")

> Stylus Toolbox supports all of the functions of escputil, including:

    Displaying ink levels
    Printing a nozzle test
    Cleaning the print nozzles
    Performing head alignment
    Identifying the model name

Additionally, Stylus Toolbox also provides:

    A tray icon for displaying the model name and ink levels
    A context menu for the tray icon, with access to all options
    An optional toolbox showing the same information as the tray icon with a toolbar
    Automatic "Just Works" configuration of parameters such as the raw printer device through integration with HAL/DBus and CUPS
    Automatic "Just Works" configuration for and support of printers attached to remote CUPS servers over an SSH connection
    SSH support for remote printers works supports both password and key-based authentication, including support for 'remembering' authentication credentials (username/password)
    Convient access to the printer settings via a 'Properties' menu pick and toolbar icon
    All settings are stored in an automatically-generated plain-text, yet fully editable configuration file


---

### Post by arno48 on 2011-07-04
Thanks for your assistance.
Escputil  can clean the printer heads and print the nozzle check.
My printer can change the cartridge by pressing a button.
I can mark this thread as SOLVED now

---

