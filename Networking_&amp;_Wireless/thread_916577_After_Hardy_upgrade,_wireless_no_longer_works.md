---
title: "After Hardy upgrade, wireless no longer works"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by michaelkeenan on 2008-09-11
Hi
I'm pretty new to Linux. I bought a Dell Inspiron 1420 last year. I recently upgraded to Hardy. Since the upgrade, the wireless networking icon that used to provide a dropdown list of available networks isn't there any more (it used to appear in the top right of the screen next to the time and date), and I can't connect to the internet any more. I'd really appreciate any help in fixing this!

Using iwconfig, I see that my laptop is not automatically connecting to available wireless networks. After starting the computer and running iwconfig, it says it is unassociated. I can actually connect to a network like this:
"sudo iwconfig eth1 essid the_network"
This seems to be successful, in that it finds the access point and everything. But Firefox still doesn't think the internet is connected.

Can anyone tell me how to restore the wireless networking icon and make Firefox able to use the internet again?

Thanks!
Michael

---

### Post by Crafty Kisses on 2008-09-11
I'm pretty sure that driver is in the repo's now. If you didn't install ndiswrapper then skip steps 2,3,4.

Update and upgrade using **update-manager/synaptic/adept etc**
```

sudo apt-get remove ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
```
Remove the```
ndiswrapper
``` Line from **/etc/modules**. Then disable Wireless from the network manager applet and then:
```
sudo modprobe -r ndiswrapper
```
If it says something about module being in use, it means you have not disabled your Wireless so, so restart if there were any kernel upgrades. Then after do the following **System->Administration->Hardware Drivers** You should see a wl driver there, it should say "In use" if it doesn't click "Install driver" and you should be on your way.

---

### Post by michaelkeenan on 2008-09-11
Thanks for your reply! But my terminal seems to have stopped in the middle of a command.

I tried the first line: sudo apt-get remove ndisgtk ndiswrapper-common ndiswrapper-utils-1.9

A lot of output followed. About 20 lines in, it says:
Installing new version of config file /etc/sysctl.conf ...
 * Setting kernel variables...
error: "vm.mmap_min_addr" is an unknown key
                       [fail]
...[a few lines about setting up openssl omitted here]...
Setting up locales (2.7.9-4) ...
Generating locales...
 ar_AE.UTF-8...

And there it has stopped for the last few minutes. I'm leaving it running but I'm not expecting any progress. Should I just stop it with Ctrl+C?

Thanks
Michael

---

### Post by Crafty Kisses on 2008-09-11
Try just installing the package:
```
sudo apt-get install ndisgtk
```

---

### Post by michaelkeenan on 2008-09-11
When I run this line: sudo apt-get install ndisgtk

It says:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

So I ran sudo dpkg --configure -a

Lines of output followed, getting stuck on:
Setting up locales (2.7.9-4) ...
Generating locales...
  ar_AE.UTF-8...

And there it has stopped. Any ideas?

---

### Post by michaelkeenan on 2008-09-11
Following a different lead, I've found that the command "sudo nm-applet --sm-disable" restores the missing networking icon. Now that it's there, I can see the list of available wireless networks, and I can select one to connect to. But it doesn't connect. It shows two grey circles, then the bottom one turns green, and finally it turns back into the image of two computer monitors with a red exclamation mark, indicating that I'm not connected to any networks.

So...is that relevant? It feels a bit like progress.

---

### Post by michaelkeenan on 2008-09-12
Solved! I found elsewhere that the problem where it freezes when generating locales can be fixed by booting with kernel 2.6.22-14 at the grub menu. So I did that, ran the dpkg configure command, and now I can run 'nm-applet --sm-disable', and it successfully connects to the wireless network and I can use Firefox. Thanks!

One last thing though: the wireless network icon doesn't appear on startup; I have to run 'nm-applet --sm-disable' to make it work. How can I make it appear on startup?

Thanks!
Michael

---

### Post by michaelkeenan on 2008-09-13
Updating everything in Synaptic seems to have solved this last problem. My computer is cured.

---

