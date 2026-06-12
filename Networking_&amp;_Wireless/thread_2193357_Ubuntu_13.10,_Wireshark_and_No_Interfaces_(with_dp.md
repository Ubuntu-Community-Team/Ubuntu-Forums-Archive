---
title: "Ubuntu 13.10, Wireshark and No Interfaces (with dpkg reconfigure)"
date: 2013-12-12
forum: Networking &amp; Wireless
---

### Post by noloader on 2013-12-12
I installed Wireshark on Ubuntu 13.10 (x64). I ran `[FONT=courier new]sudo dpkg-reconfigure wireshark-common` and selected YES. I also added myself to the 'wireshark' group. Finally, I rebooted.

I get no interfaces when I launch Wireshark. The UI displays, "Couldn't run /usr/bin/dumpcap in child process: Permission denied". I checked [FONT=courier new]/usr/bin/dumpcap, and its owned by 'root' with group 'wireshark'.[/FONT]

Any ideas?
[/FONT]

---

### Post by Azrael84 on 2014-01-31
If you've not done so already you could try the series of steps here: [http://www.dickson.me.uk/2012/09/17/installing-wireshark-on-ubuntu-12-04-lts/](http://www.dickson.me.uk/2012/09/17/installing-wireshark-on-ubuntu-12-04-lts/)

In particular make sure you have done:

    sudo chmod 750 /usr/bin/dumpcap

       
    sudo setcap cap_net_raw,cap_net_admin=eip /usr/bin/dumpcap

then restart for good measure. Check the capabilities are set correctly:

    sudo getcap /usr/bin/dumpcap

This got me past your problem, but on 13.10 (but not on 12.04) it left me with another problem: [http://askubuntu.com/questions/413449/ubuntu-13-10-wireshark-crashes-at-start-of-capture-with-segfault-unless-ran-as-r](http://askubuntu.com/questions/413449/ubuntu-13-10-wireshark-crashes-at-start-of-capture-with-segfault-unless-ran-as-r)

---

