---
title: "grub fails"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Artanis.ro on 2011-01-31
This morning I had a problem with my grub, a problem that costed me 1 week of data and files.
So, I have dual boot on my computer, Vista (which is encrypted) and ubuntu 10.10.
I started the PC, and I remembered that I had to go, and I reseted it by holding down the power button. The thing is that when I reached my destination and I started the laptop, there was no Windows Vista what so ever. 
So actually, what it had happened is that the Vista installation dissapeared from grub. I googled a little this issue and I found out that I am not the only one who got this dissapearance act from grub.
My Vista installation being encrypted, I understand why not even in ubuntu I could see or access its partitions.

Now, I have only a couple of questions:

1)Is there a file in ubuntu 10.10, that acts like a grub start configuration and tells it what to boot and where from? 
Because if I could had somehow get that file restored than I wouldn't have lost everything (I guess).

2)The GRUB boot menu has several "ubuntu...........", "ubuntu recovery" and "memory test........" categories. Is there any way to edit this list? I am not interested in the memory test and in 10 lines of "start ubuntu". Also, to edit the "start ubuntu" stuff would be nice, maybe I could call it just "ubuntu". So how I edit these lines?

Thank you, your help is much apreciated

---

### Post by Rubi1200 on 2011-01-31
Resetting using the power button is never really a good idea.

If there is a problem with Windows it is most likely a Windows issue and nothing to do with Ubuntu.

For almost all the other questions there is Grub Customizer:
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Also, this excellent guide by Cavsfan:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

As far as the main problem is concerned, I suggest the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

The results will hopefully help us figure out what happened.

---

### Post by stoogiebuncho on 2011-01-31
As you've no doubt learned now, it's not the best idea to force a shutdown while your computer is booting up.  If you can avoid that in the future you'll save yourself a lot of headaches.

The first thing I would try is boot into Ubuntu, open up a terminal window, and run ```
sudo update-grub
```
Reboot to see if that puts Windows back on your menu.

If you want a cleaner boot up page, I'd recommend checking out BURG.  You can learn more about it here: [http://www.omgubuntu.co.uk/tag/burg/]("http://www.omgubuntu.co.uk/tag/burg/")


It is possible to edit the Ubuntu entries on your GRUB menu, but it's not easy.  I wouldn't recommend even attempting it unless you are very confident in your scripting skills.

If you still want to try, the file you would need to edit is /etc/grub.d/10_linux

BEFORE YOU EDIT IT, make a backup copy and save it somewhere, but DON'T save it in the /etc/grub.d folder, or else it will still be run at boot time and you'll get two versions of every entry.

And just keep in mind before you try this that if you mess it up it could make it very difficult to boot your computer.

After you've made your edits, run sudo update-grub again to make your changes take effect.

---

