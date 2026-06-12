---
title: "Finding the Kismet Conf file"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by Conc3pt Art on 2008-02-15
Hi, I just installed kismet via the available .deb package from the official ubuntu repositories.Installation went fine and when I went to run kismet it said I needed to edit the configuration file to what suits my network and whatnot.

All good, except I cannot find the kismet configuration file, or any trace of kismet ANYWHERE. THe only way I know its even there is by running "sudo kismet" and seeing that. I can't find where the .deb has installed my files to, I've tried system searches and everything.

Please help, thanks in advance.

---

### Post by p_quarles on 2008-02-15
The vast majority of configuration files are located in the /etc directory. The kismet config may also be located in the /etc/networking sub-directory.

---

### Post by Conc3pt Art on 2008-02-17
ah thank you, directory was slightly different because im running from an sd card but same basic instructions.

---

### Post by atdhe on 2008-02-25
try this:  sudo gedit /etc/kismet/kismet.conf

---

