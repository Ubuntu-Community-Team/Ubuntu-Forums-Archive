---
title: "Too many boot loaders after using wubi (Ubuntu installer for Windows)"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by Colin Keenan on 2010-02-11
I just installed Ubuntu Linux for the first time a couple of days ago. I think it was Feb 9, 2010.  I installed the latest - Ubuntu 9.10 - the Karmic Koala - released in October 2009.  This is the first time I'm seriously trying Linux since I tried Red Hat back in the 90's.

Very impressed and surprised that I like it better than both Windows XP and Mac OS X.  I really did not expect to like it much at all.

Because I wasn't sure about it, I chose the easiest install method - wubi.exe or the "Ubuntu installer for Windows" option.  It worked great except for one annoyance: both Windows and Linux put up a boot loader screen.  If you don't press any buttons, the Windows boot loader goes on for 30 seconds, and then boots into Windows.  If you choose Ubuntu on the Windows boot loader, you then get Grub2 (not Grub) for another 10 seconds before finally booting into Ubuntu.

Since I'm so impressed with Ubuntu, I just wanted the computer to go into Ubuntu right away without giving any options unless I pressed some sort of key.  I'm posting this because the solution doesn't seem to be anywhere else since things have changed with grub2.

1) MAKE THE WINDOWS BOOT LOADER DEFAULT TO UBUNTU
from Command Prompt in Windows, type:

bootcfg /default /ID 2

Obviously, that works if Ubuntu is the operating system with ID 2, which it probably will be if you just only had Windows installed before.  If not, use bootcfg /? to find out how to figure out what ID Ubuntu is.

2) MAKE THE WINDOWS BOOT LOADER NOT SHOW ITSELF ON BOOTUP
from Command Prompt in Windows, type:

bootcfg /timeout 1

This is supposed to make the boot loader show for 1 second, but it actually makes it not show at all, which is what I wanted.

3) MAKE GRUB2 NOT SHOW ITSELF ON BOOTUP
from Terminal, type:

cd /etc/default
sudo gedit grub (after hitting enter, it will ask for password, so type it in)

in gedit, change "GRUB_TIMEOUT="10" to GRUB_TIMEOUT="1", save and exit gedit.

still in Terminal,  /etc/default, type:

sudo update-grub


These 3 steps above will prevent any boot load screens from showing and it will boot into the newest build of Ubuntu without having to press any keys.  

If you want to use Windows, just tap the **down-arrow** **key** immediately after the bios boots up, and choose Windows when the Windows boot loader shows up.  You can also press esc to get the Windows boot loader, but not a good way because see below.

If you want to use an earlier build of Ubuntu, just tap the **down-arrow key** immediately after the bios boots up, choose Ubuntu from the Windows boot loader and immediately tap **down-arrow key again** to make Grub2 show up.  If you try to press esc key after choosing Ubuntu from the Windows boot loader, instead of getting the Grub2 boot loader menu, you will get a command prompt, which is why I don't think pressing the esc key is a good way to get these boot loader menus.


Finally, I did try setting the timeout to "0" instead of "1" but that generated an error message about not finding a file during the boot process into Ubuntu.  Everything still seemed to work, but I don't like error messages.  When I set the timeout to "1", everything worked without any error messages, but the menu still never shows itself, exactly as I wanted.

---

