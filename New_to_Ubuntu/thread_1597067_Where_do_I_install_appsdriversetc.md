---
title: "Where do I install apps/drivers/etc???"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by haciendadad on 2010-10-14
One thing that has always confused me is where to install apps?  Windows has "Program Files", Apple has "apps" but Linux has /var, /tmp, /etc, /usr, /opt, etc. 

Currently I have to install a Xerox printer driver and I have to specify the install directory yet which one do I choose?

I am using Ubuntu 10.04

---

### Post by oldos2er on 2010-10-14
Usually the package manager takes care of where all the various files are installed.

What's the name of the driver file you need to install?

---

### Post by wishyjr on 2010-10-15
Yeah, one of the more common things people new to ubuntu (or linux in general) is 'where things go' when installing software. 

in windows, things are generally installed into a single directory but in linux, files are created/modified all over the filesystem - sounds messy, but really its not when you get used to it. 

Using a package manager like Synaptic really, as oldos2er has mentioned, handles all this for the user.

Unfortunately, some packages (like a driver) aren't handled by the package manager. In these cases, it's wise to carefully read the instructions that should come with the driver). 

But as a hint, usually, you can create a folder in the home directory to get things moving.

---

### Post by haciendadad on 2010-10-15
> **oldos2er said:**
> Usually the package manager takes care of where all the various files are installed.

What's the name of the driver file you need to install?

I downloaded the driver from the Xerox web site.  The readme says this:
> 
run setup within the install directory as root to install the driver.

NOTE: setup will expand and install the compressed tar file in the install
      directory, generate script files and other files that are needed
      at run time. The following syntaxes are supported:
        1) setup                               <== menu driven install
        2) setup tmp_path                      <== menu driven install
        3) setup install install_path          <== no menu, just install
        4) setup install install_path tmp_path <== no menu, just install
                  install_path is the installation directory which will contain all
                       the Xerox software.
                  tmp_path is a temporary work area. /tmp is the default work area.


so I expanded this in the directory: /home/joey/Desktop/XeroxLinuxi686xpxxInstall

When I try to execute the setup file (using this syntax "sudo ./setup") I get this error:

> /usr/bin/lpq: Error - unknown destination "/tmp"!
................ERROR: Invalid argument


tmp exist and looks like this: drwxrwxrwt 15 root root 4096 2010-10-15 19:42 .

Any suggestions?

---

