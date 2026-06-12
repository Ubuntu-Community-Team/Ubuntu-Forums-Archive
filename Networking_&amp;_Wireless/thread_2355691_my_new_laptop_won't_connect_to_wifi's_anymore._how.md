---
title: "my new laptop won't connect to wifi's anymore. how to act?"
date: 2017-03-15
forum: Networking &amp; Wireless
---

### Post by ronjjjg8885 on 2017-03-15
i've:
Lenovo Ideapad 510S-14 80TK00B3IV


today i could not connect to wifi's anymore

even after rebooting.

what should i do?

---

### Post by howefield on 2017-03-15
Thread moved to the "*Networking & Wireless*" forum for a better fit.

Might help if you follow the suggestions in this [sticky thread]("https://ubuntuforums.org/showthread.php?t=370108") and post the wireless script info which others can  use the info to help you.

---

### Post by ronjjjg8885 on 2017-03-15
later i will do it
the problem started after installing todat's updates with the update tool

is there an easy way to return to how it was before the updates

edit:
some other problem emerged too
the screen won't turn on after inactivity - but only after shutting down and powering up

edit:
the ethernet cable is not working too. there is no bluetooth too.

when i tried to unplug the cable it was really really hard to do it

anyone?

---

### Post by jeremy31 on 2017-03-15
It isn't easy to diagnose without some info, like results from terminal for ```
lspci -nnk | grep -iA2 net; rfkill list all
```
Since it is a Lenovo try ```
echo "blacklist ideapad-laptop" | sudo tee /etc/modprobe.d/blacklist-ideapad.conf
```
Reboot

---

### Post by ronjjjg8885 on 2017-03-15
> lspci -nnk | grep -iA2 net; rfkill list all01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:384f]
02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
	Subsystem: Lenovo Device [17aa:4035]
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)


the other command and reboot didn't help

---

### Post by jeremy31 on 2017-03-15
What version of Ubuntu?

---

### Post by ajgreeny on 2017-03-15
If this was in 16.04, there was a new kernel version, 4.4.0-67 arrived today in upgrades which could possibly be implicated.

Try booting to a different earlier kernel, eg, 4.4.0-66, from the grub menu to see if wifi still works with that version

---

### Post by ronjjjg8885 on 2017-03-16
it is the latest ubuntu

how do you go back to another kernel with grub?

edit:
i don't think i've the kernel you specified in the list

eidt:
i chose another kernel and now it is working.

what should i do from here?

why did it happened?

---

### Post by jeremy31 on 2017-03-16
Any results for ```
lsmod | egrep 'ath|816'
```

To get the Grub menu, press Shift key while booting, then scroll down to advanced options, press enter then select an older kernel from the list

---

### Post by ronjjjg8885 on 2017-03-16
jeremy31 
i did it but the shift key did not work
i used the esc but there were problems with that

enevtually i got the menu but there were other versions of kernel

what should i do to current the problem for good?
right now it is working with another kernel but i want to have an updated version of linux

edit:
do you want me to try
> [COLOR=#000000][FONT=&quot]lsmod | egrep 'ath|816'[/FONT][/COLOR]

?

---

### Post by jeremy31 on 2017-03-16
If it is working, just install updates.  Check ```
ls /lib/modules/
```
Copy the highest numbered folder name
```
sudo apt-get install --reinstall linux-image-extra-{folder name}
```

If I needed to do it on my system now the command would be
```
sudo apt-get install --reinstall linux-image-extra-4.4.0-66-generic
```

I had the same thing happen on my Dell with 16.04, my Lenovo hasn't had this issue

---

### Post by ronjjjg8885 on 2017-03-16
what should i type?

this?:
ls /lib/modules/

or this:?

sudo apt-get install --reinstall linux-image-extra-4.4.0-66-generic


i'm confused

this is my list:
[http://imgur.com/a/3gpiO](http://imgur.com/a/3gpiO)

---

### Post by jeremy31 on 2017-03-16
Just post results for ```
ls /lib/modules
```

---

### Post by ronjjjg8885 on 2017-03-16
[COLOR=#000000][FONT=Arial]4.8.0-41-generic  4.8.0-42-generic[/FONT][/COLOR][COLOR=#000000][FONT=Arial]

BTW
does everything looks right with my ubuntu with all of the info i've provided? i mean besides this problem with the kernel

also
again
why does all of that happened?
will my system be up to date?

edit:
[/FONT][/COLOR]should it be?

sudo apt-get install --reinstall linux-image-extra-4.8.0-42-generic?
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by jeremy31 on 2017-03-16
Everything looks fine, now run
```
sudo apt-get install --reinstall linux-image-extra-4.8.0-42-generic
```
And let it boot normally and see if it is fixed

---

### Post by ronjjjg8885 on 2017-03-16
booted successfully

i wish i knew if it will be ok to keep the system as it is right now


i mean
shouldn't i worry that i don't have the right kernel now and later with the alternations i've performed?

---

### Post by jeremy31 on 2017-03-16
You should be good to go.  I foresee no issues with what we have done in this thread.  And I would just install updates as usual as I doubt you will see this issue again

---

### Post by nunyadam_bizness on 2017-03-17
> **jeremy31 said:**
> Everything looks fine, now run
```
sudo apt-get install --reinstall linux-image-extra-4.8.0-42-generic
```
And let it boot normally and see if it is fixed

After an update 2 days ago, I lost both wireless and wired networking. Your suggestion worked and got me back in business. Thanks!:D

---

### Post by ronjjjg8885 on 2017-03-17
why  did we had this problem?

edit
now it is the bluetooth turn once again.
it stopped working
the wifi just fine

---

### Post by jeremy31 on 2017-03-17
You might have to shutdown the computer and do a cold boot to get the bluetooth working.  I think the Atheros bluetooth are having timing issues with the firmware load as mine only wants to function about every third boot.
You might find the reason for the wifi issue if you look through the term files in /var/log/apt some of them are compressed, search the files for extra and look for anything saying error or dependency

---

### Post by ronjjjg8885 on 2017-03-17
so currently there isn't a way to fix the bluetooth permanently?

will it work with lubuntu or is it the same?

---

### Post by jeremy31 on 2017-03-17
It is the same as the big issue is in the kernel.  Post results for ```
lsusb
```

It seems you weren't alone in having problems with that kernel update.  It seems that kernel was pushed to the stable repository by mistake and later moved back to proposed

---

### Post by ronjjjg8885 on 2017-03-20
ok/? 
so then, how to i switch the kernel back to how it was?
because you are saying that the problem had been fixed already

---

### Post by jeremy31 on 2017-03-20
You could use Grub to boot back into the 4.8.0-41 kernel and remove the -42 kernel with ```
sudo apt-get remove linux-image-4.8.0-42-generic linux-image-extra-4.8.0-42-generic linux-headers-4.8.0-42-generic
```
Reboot

---

