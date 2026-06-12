---
title: "wifi roaming not working..."
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by nicedog on 2008-08-24
i am using Xubuntu 8.04 on my EEE PC 900.

my sys used to prompt me for key-ring (my wifi is WPA protected) it will be able to connect to the wifi after a while.

yesterday i installed fluxbox...the wifi not working at the first place... i had to manually config to connect to the wifi (unlike in xfce no network connect icon at the top panel cuz no panel at all) and i worked...

logon back with xfce, wifi not working... i now have to manually connect to the wifi... checked the roaming enabled option for wifi config in network manager... clicked the network connection icon at the top panel and selected my wifi connection, the sys prompted for key-ring.. the sys kept trying to connect... mouseove the network connection icon, the tiptext said "waiting the key for the network"...


i checked ps -x and saw a line like "nm-applet --sm-disbaled" anything wrong?... the gnome-keyring daemon was not up before but somehow i could see it in ps -x


any idea?

---

### Post by nicedog on 2008-08-25
here below log of processes i am runnning... i am able to manually connect to wifi but roaming still not working....

  PID TTY      STAT   TIME COMMAND
 5031 ?        Ssl    0:01 x-session-manager
 5113 ?        S      0:00 /usr/bin/gcin
 5119 ?        Ss     0:00 /usr/bin/ssh-agent x-session-manager
 5123 ?        Ss     0:00 xfce-mcs-manager
 5126 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 4
 5130 ?        S      0:00 gnome-keyring-daemon
 5131 ?        S      0:01 xfwm4 --sm-client-id 117f000101000121751913500000051230000 --display :0.0
 5133 ?        S      0:00 Thunar --sm-client-id 117f000101000121844354900000051480000 --daemon
 5135 ?        S      0:00 /usr/lib/gamin/gam_server
 5139 ?        Ss     0:00 /usr/bin/dbus-daemon --fork --print-pid 6 --print-address 10 --session
 5140 ?        S      0:00 dbus-launch --autolaunch 9590262a0407de6a06b344e84891cf34 --binary-syntax
 5141 ?        S      0:00 Thunar --sm-client-id 117f000101000121876020900000050840000 --daemon
 5143 ?        Sl     0:00 Thunar --sm-client-id 117f000101000121881602000000050830000 --daemon
 5144 ?        S      0:01 /usr/bin/xfdesktop --sm-client-id 117f000101000121838625500000050780002 -
 5160 ?        S      0:04 xfce4-panel --sm-client-id 117f000101000121842678900000050810002 --displa
 5162 ?        S      0:01 /usr/lib/xfce4/panel-plugins/xfce4-menu-plugin socket_id 27263016 name xf
 5163 ?        S      0:00 /usr/lib/xfce4-places-plugin/xfce4/panel-plugins/xfce4-places-plugin sock
 5173 ?        Ss     0:00 gnome-power-manager --sm-config-prefix /gnome-power-manager-uoNFkA/ --sm-
 5182 ?        S      0:00 update-notifier --sm-config-prefix /update-notifier-XKXp8z/ --sm-client-i
 5196 ?        Ss     0:02 nm-applet --sm-disable
 5209 ?        Ss     0:00 python /usr/share/system-config-printer/applet.py
 5213 ?        Ssl    0:00 /usr/local/bin/asusosd
 5225 ?        S      1:05 /usr/lib/xfce4-systemload-plugin/xfce4/panel-plugins/xfce4-systemload-plu
 5228 ?        S      0:01 /usr/lib/xfce4/panel-plugins/xfce4-mixer-plugin socket_id 27263029 name x
 5265 ?        S      0:00 /usr/lib/thunar/xfce4/panel-plugins/thunar-tpa socket_id 27263050 name th
 5323 ?        S      0:00 xfce4-terminal --geometry=80x24 --display :0.0 --role=Terminal-0x80b4828-
 5386 ?        S      0:00 gnome-pty-helper
 5387 pts/0    Ss+    0:00 bash
 5400 pts/1    Rs     0:00 bash
 9600 ?        Rsl   19:32 /usr/lib/seamonkey/seamonkey-bin
 9635 ?        Ss     1:00 /usr/lib/opera/9.27-20080331.6/opera
 9652 ?        S      0:00 /usr/lib/opera/plugins/operaplugincleaner 9635
 9746 ?        SNl    0:00 /usr/lib/opera/plugins/operapluginwrapper 54 57 /usr/lib/flashplugin-nonf
 9753 pts/1    R+     0:00 ps -x


any idea ?

---

