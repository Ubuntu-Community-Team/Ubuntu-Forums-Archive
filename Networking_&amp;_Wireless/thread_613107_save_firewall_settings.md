---
title: "save firewall settings"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by kedmond on 2007-11-14
Hello,
    I'm relatively new to Debian/Ubuntu.  I'm using Ubuntu 7.10.

    My computer is connected to a network of CentOS 5 machines.  The network manager has a script that he runs on all the machines that uses iptables to configure the firewall settings of each machine.  He then goes on to save these settings in /etc/init.d/iptables, so they are restored at startup.

    Of course, Debian does not have this any longer.  If I type in "iptables -L" after running the script, the correct firewall settings are displayed.  I can run iptables-save to save these results to a file.

    How do I take these results, from iptables-save, and reinstate them at startup?  NetworkManager is running on my machine.  Do I have to do something with that?

    I already followed the directions here: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) 

    But it doesn't work.  Thanks for any help!

-kedmond

---

### Post by kedmond on 2007-11-15
Nevermind.  I found help at [http://ubuntuforums.org/showthread.php?t=159661&highlight=save+iptables](http://ubuntuforums.org/showthread.php?t=159661&highlight=save+iptables)

Sorry for the redundancy!

-kedmond

---

