---
title: "Sudden disconnection with Belkin router"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by jpjandrade on 2008-08-06
Hey guys,

I'm using an HP dv6000 notebook, wireless card Intel 3945ABG, with Hardy. And when I connect to my wireless network at home, using a Belkin N Router (F5D8233), it connects normally and after a while using, it suddenly stops receiving and sending data. The nm-applet on the top corner says it's still conected, but I must reconnect (clicking twice on my connection) to restore normal connection.
I'd like to know what can I do to solve it, or at least find out more about the problem. For example, is there anyway to acess the network manager through the terminal and find out at least what kind of error message it gives? I'm completely blind here. Vista, on this same notebook, connects fine.

Thanks for the help!

---

### Post by pytheas22 on 2008-08-06
A good place to start troubleshooting is to look at dmesg, which prints information about what your system is doing behind-the-scenes.  The next time your connection drops, immediately open a terminal and enter this command:
```

dmesg | tail
```

and please post the output here.  It should give some useful information about what's going on, and some strings that you can google for and hopefully find a solution.  The iwl3945 driver seems to have a lot of issues, but usually there are fixes once you find the appropriate bug reports.

---

### Post by jpjandrade on 2008-08-06
Ok, not so lucky with that command. Here's the output before and after it stops responding (it was exactly the same):
joaop@joaop-laptop:~$ dmesg | tail
[   61.144528] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[   61.144534] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[   61.144539] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[   61.144544] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[   61.146813] wlan0: association frame received from 00:1c:df:a8:63:b5, but not in associate state - ignored
[   61.148150] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   64.832537] wlan0: no IPv6 routers present
[  157.907245] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[  157.907259] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x02EA ser 0x0000004B
[  158.899623] iwl3945: Can't stop Rx DMA.

Now, the next few lines appear after I re-click my connection but before it connects and resets the whole thing:

[  224.472138] wlan0: deauthenticate(reason=3)
[  224.588245] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate

I doubt those are really helpful, but I posted them anyway. Any ideas?

Thanks!

---

### Post by pytheas22 on 2008-08-06
I think I've found some bug reports related to your issue, based on what gets dumped to dmesg.  These are the useful links that I discovered:

[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1534](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1534)
[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1650](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1650)
[https://bugs.launchpad.net/linux/+bug/185470](https://bugs.launchpad.net/linux/+bug/185470)

Please try running these commands and see if the problem still occurs thereafter, at least until the next time you reboot your computer:
```

sudo rmmod iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```

Does that solve the problem?  If so, we can apply the fix permanently (the commands above would only fix it until the next reboot of the computer, at which time they'd need to be run again to apply the fix for that session).

---

### Post by jpjandrade on 2008-08-07
Nope, nothing :(
After I ran those commands, it happened twice. Is there any other Intel driver I can try to see how it works?

Thanks!

---

### Post by pytheas22 on 2008-08-08
> After I ran those commands, it happened twice. Is there any other Intel driver I can try to see how it works?

Sorry that didn't help.  At this point I'd probably conclude that there's just a weird bug with the particular build of the iwl2945 driver that you're using.  It will probably be fixed in an update, but it seems to me that the iwl project has a tendency to keep breaking stuff more than it improves it, at least on Ubuntu (I don't know if it's the fault of the Ubuntu packagers or the iwl people).

There's an older version of the Intel driver called ipw3945.  There are instructions [here]("http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html") on compiling it for Hardy, but there's a lot of hacking that you need to do and parts of that tutorial are vague, I think, so don't expect it to be easy.

Another option is ndiswrapper, which allows you to drive your card using Windows drivers.  If you want to go that route and need instructions, please tell me the output of:
```

lspci -nn | grep -i intel
```

---

### Post by jpjandrade on 2008-08-13
It seems that updating the firmware for the router solved this issue. I didn't try it before because due to a typo in the firmware's filename, the router interface can't detect the new version, but it is available in their website, in case of anyone who's reading this and has the same problem. Worked for me! :)

Thanks for the help, man!

---

