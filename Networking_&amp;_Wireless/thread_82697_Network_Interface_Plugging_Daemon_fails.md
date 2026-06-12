---
title: "Network Interface Plugging Daemon fails"
date: 2005-10-27
forum: Networking &amp; Wireless
---

### Post by burningbed on 2005-10-27
During boot up on my HP Pavilion dv1000 laptop I get the message "Starting Network Interface Plugging Daemon failed" this message stays on for quite a while and boot up gets delayed considerably (I can press CTRL-C to skip this step to speed things up, but I'd rather not have to do that). Later during bootup the same message gets displayed again briefly and this time there's no further delay. Can anyone give me pointers on how to fix this? I'm not sure if this is relevant, but ifplugd is configured as follows (these are all the default settings): static interfaces to be watched by ifplugd: auto, hotplugged interfaces to be watched by ifplugd: all, arguments to ifplugd: -q -f -u0 -d10 -w -I, suspend behaviour: stop. I'm also attaching the output of dmesg. I've posted this problem before, but didn't get an answer and suspect this may be partly due to me not posting it in the correct forum (I posted in in "Laptop Support"). My original post can be found here: [http://ubuntuforums.org/showthread.php?p=410994#post410994]("http://ubuntuforums.org/showthread.php?p=410994#post410994"). I also provide my dmesg output: [http://ubuntuforums.org/attachment.php?attachmentid=2895&d=1129310024]("http://ubuntuforums.org/attachment.php?attachmentid=2895&d=1129310024")

Any help would be appreciated!

---

### Post by mlomker on 2005-10-27
I've been getting the failed error since switching to Breezy as well, but it doesn't induce a pause.  What other interfaces do you have in your machine?  Judging from the dmesg output it's just wireless and ethernet (looks like a laptop similar to my own).

If that's true then I recommend this for /etc/default/ifplugd:

```

INTERFACES="eth0"
HOTPLUG_INTERFACES=""
ARGS_eth0="-qfwI -u0 -d10"
SUSPEND_ACTION="stop"

```

I'd also disable hotplug networking since it interferes with ifplugd anyway:

```

sudo update-rc.d -f hotplug-net remove

```

---

### Post by burningbed on 2005-10-28
I only have a wired ethernet (eth0) and a wireless (eth1) network interface (there's also a modem which I never use). I haven't had the chance to try out your suggestions yet, but am reluctant to disable hotplug, as I'd like to be able to just plug in USB (and other) devices and have them configured automatically. Is there no way to have ifplugd and hotplug running simultaneously? Any ideas?

---

### Post by mlomker on 2005-10-28
> Is there no way to have ifplugd and hotplug running simultaneously? Any ideas?

You are confusing hotplug networking with hotplug in general.  The only people that need hotplug networking are those that use PCMCIA cards or USB network adapters.

---

### Post by burningbed on 2005-10-30
OK, thanks for clearing that up. I did what you suggested, but the behavior is unchanged. I still get the "failed" notice during boot-up and it still introduces a considerable delay unless I exit out with CTRL-C. Any other ideas?

---

### Post by mlomker on 2005-10-30
As I mentioned, I get the 'failed' message as well.  That is probably not the cause of your delay, however, it is probably whatever is running before or after ifplugd in the startup.

Have you already downloaded **bum** and disabled the things that you don't need for your machine?

---

### Post by burningbed on 2005-10-31
Thanks again for your help. I've used bum to disable anything that I didn't think I needed, but that didn't get rid of the delay. I'm not sure about some services and I could do a more thorough test by disabling everything that I don't know to be absolutely essential (although if I accidentially disabled something that's required to boot up, I'd have a hard time figuring out how to enable it again without bum). The reason I believe the problem is with ifplugd is that the delay occurs between the appearance of "Starting Network Interface Plugging Daemon" and the appearance of "failed". In other words, the message "Starting Network Interface Plugging Daemon" is displayed for a long time without any status report and only after a delay does the status "failed" appear and the boot is completed. Does everybody get a "failed" status report from ifplugd? Is that a bug in ifplugd or Ubuntu? Again, any help solving this issue is appreciated.

---

### Post by burningbed on 2005-11-21
I removed ifplugd and now the "failed" message disappears. however "Configuring Network interfaces" still takes a long time. So I guess the hold up was indeed not due to ifplugd. Is there any way to speed up the configuration of the network interfaces?

---

### Post by mlomker on 2005-11-21
[QUOTE=burningbed]I removed ifplugd and now the "failed" message disappears. however "Configuring Network interfaces" still takes a long time. So I guess the hold up was indeed not due to ifplugd. Is there any way to speed up the configuration of the network interfaces?[/QUOTE]

Did you disable hotplug networking or not?  It's probably waiting for DHCP to fail on an interface that isn't connected.

---

### Post by burningbed on 2005-11-22
I did sudo update-rc.d -f hotplug-net remove ... is there anything else I can do to give up dhcp sooner?

---

### Post by mlomker on 2005-11-22
[QUOTE=burningbed]I did sudo update-rc.d -f hotplug-net remove ... is there anything else I can do to give up dhcp sooner?[/QUOTE]

Are your interfaces set for 'auto' in /etc/network/interfaces?  You could try removing that line as a test (none of your network interfaces will come up automatically that way).

---

### Post by hw-tph on 2005-12-23
Just a quick note on how I solved it: Comment out the hotplug mapping in /etc/network/interfaces and add eth0 there without auto:

```
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#       script grep
#       map eth0

# The primary network interface
iface eth0 inet dhcp
```

Add ifplugd to the default runlevel and add INTERFACES="eth0" to /etc/default/ifplugd. That's all there was to it for me. The fail message went away and the network comes up when the cable is connected.


Håkan

---

