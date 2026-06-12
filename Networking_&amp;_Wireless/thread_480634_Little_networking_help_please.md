---
title: "Little networking help please"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by swoll1980 on 2007-06-21
I have a ubuntu desktop and a windows laptop trying to set up file sharing. They can both ping each other, double checked firewall configs, neither pc can see the other on there respective browsers . My windows work group is mshome how do I chose a workgroup for the ubuntu pc ? Is there any advice anyone could offer. Also when I choose a static ip for desktop it will not connect to the network. I have to leave it on dchp.

---

### Post by spd106 on 2007-06-21
I usually access windows shares by opening nautilus (Places), then press Ctrl+L to switch to text based location bar and enter smb://hostname/ (swap hostname for the windows PC name). This relies on you already having setup the shares on the windows PC.

You can configure the workgroup name in System -> Admin -> Network, under the General tab and add the workgroup name to the Search Domain box under the DNS tab.

For a more in depth guide with troubleshooting help from dbott67 see this thread [http://ubuntuforums.org/showthread.php?t=437080](http://ubuntuforums.org/showthread.php?t=437080)

---

