---
title: "Lexmark X75"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by hifly1231 on 2010-04-23
I have a computer at my mom's house in the suburbs with Ubuntu 9.10 installed on it.  I have a Lexmark X75 printer that I used to use when I had Windoze,  I only need this printer for printing, as this is a temporary thing and I'll be moving this computer to my high-rise apartment Downtown within the next few months. I've downloaded **print-drivers-linux-glibc2-x86.deb**, and have installed it.  I also ran **/usr/local/lexmark/setup.lexprint** in terminal, and it says that setup is complete, but I still can't print anything.  I have an HP Deskjet f4235 at my apartment, and I would really prefer not to have to switch the printers until I move this computer down there. Can anybody help me with this?  Thanks!

---

### Post by avtolle on 2010-04-23
Have you tried:

1) Checking whether your user name is a member of the lp group (Users and Groups under System>Administration, as I recall); 
2) Logging out and back in: or
3) Powering the printer down, then shutting the computer down, then powering up the printer and restarting the computer?

Try above in the order given, please let us know.

---

### Post by hifly1231 on 2010-04-23
> **avtolle said:**
> Have you tried:

1) Checking whether your user name is a member of the lp group (Users and Groups under System>Administration, as I recall); 
2) Logging out and back in: or
3) Powering the printer down, then shutting the computer down, then powering up the printer and restarting the computer?

Try above in the order given, please let us know.

That didn't seem to work.  Under System Tools, I'm finding Lexmark Print Drivers.  When the box opens up, there's a splash screen that says Lexmark Print Drivers for Unix and Linux.  When I click on the printer with a plus sign on it, another box pops us asking me to add a device.  I click on that, and another box pops up where I choose Locally Attached Printer & USB.  However, it's telling me that I need to know the device file name associated with my printer.  Then, when I click on next, it has 3 choices for me to pick from.  dev/usblp0, dev/usb/lp0, and other with a browse box.  I have no idea where to go from here.

---

### Post by cjazz on 2010-04-24
I'm not familiar with the driver you're trying to install. However, the Linux Foundation's OpenPrinting site recommends an experimental driver for your model, which is located [here]("http://www.openprinting.org/driver/lxx74").

It might be unfortunate that you're not ready to switch yet to your other printer. HP's support for Linux is unparalleled, while Lexmark's is among the worst. But I respect your choice.

---

### Post by hifly1231 on 2010-04-27
> **cjazz said:**
> I'm not familiar with the driver you're trying to install. However, the Linux Foundation's OpenPrinting site recommends an experimental driver for your model, which is located [here]("http://www.openprinting.org/driver/lxx74").

It might be unfortunate that you're not ready to switch yet to your other printer. HP's support for Linux is unparalleled, while Lexmark's is among the worst. But I respect your choice.

Thanks everyone for your input.  I've decided that the easiest thing to do is just switch out printers.  I'll use the HP printer while I still have a computer at my mom's house, and I'll take the Lexmark X75 down to my high-rise.  I feel that's the easiest fix to a temporary problem. :)

---

### Post by mockingbird on 2011-11-02
I'm at the same stage you are...

But after I add the printer and I press next, it gives me the error:
"Printer Name Already Exists".

Using Kubuntu 11.10 X64

---

