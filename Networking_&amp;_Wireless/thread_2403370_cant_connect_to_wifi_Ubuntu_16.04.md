---
title: "cant connect to wifi Ubuntu 16.04"
date: 2018-10-10
forum: Networking &amp; Wireless
---

### Post by nimrod0901 on 2018-10-10
```

~ uname -a
Linux nimrod-thinkpad-x220 4.15.0-34-generic #37~16.04.1-Ubuntu SMP Tue Aug 28 10:44:06 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
~ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 6 Series/C200 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)
0d:00.0 System peripheral: Ricoh Co Ltd PCIe SDXC/MMC Host Controller (rev 07)
~ ifconfig
enp0s25   Link encap:&#20197;&#22826;&#32593;  &#30828;&#20214;&#22320;&#22336; f0:de:f1:ac:7f:0c  
          UP BROADCAST MULTICAST  MTU:1500  &#36291;&#28857;&#25968;:1
          &#25509;&#25910;&#25968;&#25454;&#21253;:0 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#24103;&#25968;:0
          &#21457;&#36865;&#25968;&#25454;&#21253;:0 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#36733;&#27874;:0
          &#30896;&#25758;:0 &#21457;&#36865;&#38431;&#21015;&#38271;&#24230;:1000 
          &#25509;&#25910;&#23383;&#33410;:0 (0.0 B)  &#21457;&#36865;&#23383;&#33410;:0 (0.0 B)
          &#20013;&#26029;:20 Memory:f2500000-f2520000 


lo        Link encap:&#26412;&#22320;&#29615;&#22238;  
          inet &#22320;&#22336;:127.0.0.1  &#25513;&#30721;:255.0.0.0
          inet6 &#22320;&#22336;: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  &#36291;&#28857;&#25968;:1
          &#25509;&#25910;&#25968;&#25454;&#21253;:7465 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#24103;&#25968;:0
          &#21457;&#36865;&#25968;&#25454;&#21253;:7465 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#36733;&#27874;:0
          &#30896;&#25758;:0 &#21457;&#36865;&#38431;&#21015;&#38271;&#24230;:1000 
          &#25509;&#25910;&#23383;&#33410;:1044674 (1.0 MB)  &#21457;&#36865;&#23383;&#33410;:1044674 (1.0 MB)


wlp3s0    Link encap:&#20197;&#22826;&#32593;  &#30828;&#20214;&#22320;&#22336; 08:11:96:f4:15:d4  
          inet6 &#22320;&#22336;: fe80::5043:b1a1:5b63:762b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  &#36291;&#28857;&#25968;:1
          &#25509;&#25910;&#25968;&#25454;&#21253;:385 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#24103;&#25968;:0
          &#21457;&#36865;&#25968;&#25454;&#21253;:168 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#36733;&#27874;:0
          &#30896;&#25758;:0 &#21457;&#36865;&#38431;&#21015;&#38271;&#24230;:1000 
          &#25509;&#25910;&#23383;&#33410;:78572 (78.5 KB)  &#21457;&#36865;&#23383;&#33410;:28426 (28.4 KB)
~ ping 192.168.1.1 -c 4
connect: Network is unreachable
~ tail /var/log/syslog -n 20
Oct 10 22:49:27 Nimrod-ThinkPad-X220 avahi-daemon[941]: Joining mDNS multicast group on interface wlp3s0.IPv6 with address fe80::5043:b1a1:5b63:762b.
Oct 10 22:49:27 Nimrod-ThinkPad-X220 avahi-daemon[941]: New relevant interface wlp3s0.IPv6 for mDNS.
Oct 10 22:49:27 Nimrod-ThinkPad-X220 avahi-daemon[941]: Registering new address record for fe80::5043:b1a1:5b63:762b on wlp3s0.*.
Oct 10 22:49:29 Nimrod-ThinkPad-X220 systemd[1]: Failed to start MySQL Community Server.
Oct 10 22:49:29 Nimrod-ThinkPad-X220 systemd[1]: mysql.service: Unit entered failed state.
Oct 10 22:49:29 Nimrod-ThinkPad-X220 systemd[1]: mysql.service: Failed with result 'exit-code'.
Oct 10 22:49:29 Nimrod-ThinkPad-X220 systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Oct 10 22:49:29 Nimrod-ThinkPad-X220 systemd[1]: Stopped MySQL Community Server.
Oct 10 22:49:29 Nimrod-ThinkPad-X220 systemd[1]: Starting MySQL Community Server...
Oct 10 22:49:29 Nimrod-ThinkPad-X220 mysqld[8611]: /usr/sbin/mysqld: error while loading shared libraries: libz.so.1: cannot open shared object file: Error 20
Oct 10 22:49:29 Nimrod-ThinkPad-X220 systemd[1]: mysql.service: Main process exited, code=exited, status=127/n/a
Oct 10 22:49:29 Nimrod-ThinkPad-X220 kernel: [  894.920825] audit: type=1400 audit(1539182969.423:78): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/usr/local/lib/libz.so.1.2.9" pid=8611 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=127 ouid=0
Oct 10 22:49:29 Nimrod-ThinkPad-X220 gnome-session[2772]: [4202:4220:1010/224929.745068:ERROR:connection_factory_impl.cc(396)] Failed to connect to MCS endpoint with error -130
Oct 10 22:49:29 Nimrod-ThinkPad-X220 gnome-session[2772]: (gnome-shell:3864): Gjs-WARNING **: JS ERROR: Gio.ResolverError: &#35299;&#26512;“openweathermap.org”&#20986;&#38169;&#65306;&#22495;&#21517;&#35299;&#26512;&#26242;&#26102;&#22833;&#36133;
Oct 10 22:49:29 Nimrod-ThinkPad-X220 gnome-session[2772]: OpenweatherMenuButton<._asyncReadyCallback@/home/nimrod/.local/share/gnome-shell/extensions/openweather-extension@jenslody.de/extension.js:544
Oct 10 22:49:29 Nimrod-ThinkPad-X220 gnome-session[2772]: wrapper@resource:///org/gnome/gjs/modules/lang.js:178
Oct 10 22:49:30 Nimrod-ThinkPad-X220 gnome-session[2772]: [4202:4202:1010/224930.708514:ERROR:gcm_channel_status_request.cc(151)] GCM channel request failed.
Oct 10 22:49:34 Nimrod-ThinkPad-X220 systemd[1]: Starting Cleanup of Temporary Directories...
Oct 10 22:49:34 Nimrod-ThinkPad-X220 systemd-tmpfiles[8645]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Oct 10 22:49:34 Nimrod-ThinkPad-X220 systemd[1]: Started Cleanup of Temporary Directories.
~ sudo ls -al /etc/resolv.conf
lrwxrwxrwx 1 root root 29 7&#26376;   2 16:18 /etc/resolv.conf -> ../run/resolvconf/resolv.conf
~ sudo cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN



```
sorry some output is Chinese, but it may not affect

---

### Post by nimrod0901 on 2018-10-10
I guess it may be affected by the following instructions
I downloaded libz.so.1.2.9
```

~cd zlib-1.2.9
~./configure
~make
~sudo make install
~cd /lib/x86_64-linux-gnu
~sudo ln -s -f /usr/local/lib/libz.so.1.2.9/lib libz.so.1

```
I use these instructions to solve some problems about Python

---

