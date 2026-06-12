---
title: "all of my network devices &quot;unclaimed&quot;"
date: 2016-04-13
forum: Networking &amp; Wireless
---

### Post by alex531 on 2016-04-13
Hello all,

I would greatly appreciate any help with this issue. My computer was acting up today, so I rebooted it, and when it came back, all of my network devices are unclaimed. From what I understand this is because there is no driver for it, which I really don't understand how that can happen all of a sudden. The thing is that I don't know how to go about acquiring the driver and how to install it again. I obviously have no internet, so I can't use apt. I also don't know which driver to use anymore. I've attached a screen shot of the output for lshw -C network. Please let me know if there is anything else you need to see. I'm using ubuntu 14.04.1

Thanks for any help

Screen shot is here: [http://imgur.com/U3Epi4T](http://imgur.com/U3Epi4T) if you can't see it below[IMG]http://i.imgur.com/U3Epi4T.jpg[/IMG]

---

### Post by chili555 on 2016-04-14
What is the result of:```
sudo modprobe iwlwifi
dmesg | grep iwl
```

---

### Post by alex531 on 2016-04-14
The output to that command is below:

[http://imgur.com/8cRc3XJ](http://imgur.com/8cRc3XJ)
[IMG]http://i.imgur.com/8cRc3XJ.jpg[/IMG]

Not entirely sure what this means, but it doesn't look good. :(

---

### Post by chili555 on 2016-04-14
How about:```
sudo updatedb
locate iwlwifi.ko
uname -r
```*updatedb* will take a few moments; please be patient.>  but it doesn't look good. Not very good at all, but let's see what we can do with what we have. Fingers crossed!

---

### Post by alex531 on 2016-04-14
Here is the output:

[http://imgur.com/vicu85X](http://imgur.com/vicu85X)
[IMG]http://i.imgur.com/vicu85X.jpg[/IMG]

Fingers and toes crossed!

---

### Post by chili555 on 2016-04-14
Please notice that the driver exists in kernel versions -33 through -37 but not, for some reason, in -70, which is your currently running version (uname -r[COLOR="#FF0000"]unning[/COLOR]). That's not precicely what -r means, but that's it's common meaning.

I think you can reboot and get to the GRUB menu to reboot into an earlier kernel version, -37 for example, and your devices will be working. [http://www.howtogeek.com/wp-content/uploads/2014/09/640x480xgnu-grub2-boot-loader-menu.png.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.gh1Zn0zLtS.png](http://www.howtogeek.com/wp-content/uploads/2014/09/640x480xgnu-grub2-boot-loader-menu.png.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.gh1Zn0zLtS.png) Highlight and select 'Advanced Options' and the earlier kernels will be available. Select one, press Enter and boot.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)> On a new installation of Ubuntu 9.10 or later with no other installed operating systems, GRUB 2 will boot directly to the login prompt or Desktop. No menu will be displayed.

Hold down (right) SHIFT to display the menu during boot. In certain cases, pressing the ESC key may also display the menu. Then we will purge and reinstall -70. Post back when you are ready.

---

### Post by alex531 on 2016-04-14
I did reboot into an earlier kernel version, -37, the devices are now there, but it doesn't seem to want to connect to the internet. Going to try to boot into an earlier version still and see if that changes things.

---

### Post by alex531 on 2016-04-14
That seemed to have done the trick, booted into -36. I can connect to the internet now. Ready for next step I believe.

---

### Post by chili555 on 2016-04-14
Please do:

```
ls /var/cache/apt/archives | grep 3.16.0-70

```
You will get a list of packages that are installed, and probably mis-installed, associated with your -70 kernel. We will purge them all:

```
sudo apt-get purge linux-image-3.16.0-70-generic
sudo apt-get purge linux-headers-3.16.0-70-generic
sudo apt-get purge linux-image-extra-3.16.0-70-generic

```
These are my best guesses as to what you may find there. If there are other packages, stop and ask before you proceed.

Once you are finished, reboot and we will reinstall the latest kernel version.

I will be away for a couple of hours. We at least have your computer operating correctly for now.

---

### Post by alex531 on 2016-04-14
Purged the files and rebooted. Things are working normally as far as I can tell.

---

### Post by chili555 on 2016-04-14
You might get the kernel updated, properly this time, with:```
sudo apt-get update && sudo apt-get dist-upgrade
```Let's see if you get offered and then can accept -70.

---

