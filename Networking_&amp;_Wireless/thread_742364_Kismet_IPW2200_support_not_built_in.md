---
title: "Kismet IPW2200 support not built in"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by AngryMallard on 2008-04-01
I have a Thinkpad T43 with Ubuntu 7.10 and I would like to run kismet. After a successful install I run "sudo kismet" and I get this output:

```
bryan@thinkpad-ubuntu:~$ sudo kismet
[sudo] password for bryan:
Server options:  none
Client options:  none
Starting server...
Will drop privs to bryan (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Support for capture source type 'ipw2200' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
Waiting for server to start before starting UI...

```

I am not sure what to do about that. I had kismet running flawlessly in Kubuntu 7.04 but that was before I Ubuntu 7.10. 

The solution I kept getting pointed to was this one:
[http://ubuntuforums.org/showthread.php?t=40875]("http://ubuntuforums.org/showthread.php?t=40875")
but this is extremely dated and doesn't really work. (His version of Ubuntu was 5.04.)

If anyone could just tell me how to build the IPW2200 drivers that would be awesome.

---

### Post by hugmenot on 2008-04-02
Hey are you aware that there's a special rtap device for monitor mode in ipw2200? The downside is that it cannot hop channels but it is used with a special mode. The upside is that you don't have to interrupt your normal association for this.

```
sudo kismet -c ipwlivetap,eth1,rtap
```

To use it you have to enable the rtap device with:

```
sudo sh -c 'echo 1 > /sys/class/net/eth1/device/rtap_iface'
```

If you want to do the full monitor mode with channel hopping you would use ethX though. I don't know about Gutsy but in Hardy this works well.
```
sudo -c ipw2200,eth1,IntelPro
```

Also, I found out that the 2.6.24 Kernel doesn't allow to bring up rtap0 unless you manually give it a fake MAC address.

---

### Post by hugmenot on 2008-04-02
Oh and you would build the modules with module-assistant.

Are you sure that Kismet doesn't talk about it's own ipw2200 support?

---

### Post by AngryMallard on 2008-04-02
When I ran the above code, I get the following:

```
bryan@thinkpad-ubuntu:~/Desktop$ sudo sh -c 'echo 1 > /sys/class/net/eth1/device/rtap_iface'
[sudo] password for bryan:
bryan@thinkpad-ubuntu:~/Desktop$ sudo kismet -c ipwlivetap,eth1,rtap
Server options:   -c ipwlivetap,eth1,rtap
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Will drop privs to bryan (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Support for capture source type 'ipwlivetap' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}


bryan@thinkpad-ubuntu:~/Desktop$ sudo -c ipw2200,eth1,IntelPro
sudo: illegal option `-c'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
bryan@thinkpad-ubuntu:~/Desktop$ 

```

I still get the "support for [something] was not built" message. I need to know how to build support for whatever I need at compile/install time.

Kismet's documentation tell you how to enable the IPW2200 in the config file but that's after it installs. After I configure the file after install, it tells me I should have enabled some unknown options before I compiled or installed.

---

### Post by hugmenot on 2008-04-02
The second error is due to me forgetting to type "kismet" after "sudo".

I distinctly remember that Kismet used to work for in Gutsy. But I had an ipw2100 back then. Two months ago I bought an ipw2200 to get G rates.

Sorry, I can't give more input.

---

