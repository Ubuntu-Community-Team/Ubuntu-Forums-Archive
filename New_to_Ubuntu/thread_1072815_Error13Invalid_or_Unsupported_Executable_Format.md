---
title: "Error13:Invalid or Unsupported Executable Format"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by B.E. on 2009-02-17
Good Day. 
My hard drive is partitioned into PCLinuxOS and Windows. When I boot up and it comes to the screen of the Linux and windows I scroll down to the windows and press enter and this is what I get:

Error 13: Invalid or unsupported Executable Format.

Press any key to continue.

When I press any key it goes to an Aqua colored screen with this:

Linux
Linux-nonfb
failsafe
windows

Windows is in a Yellow Colour.

I scroll down to windows and press it and it goes back the the Error 13 screen all over again.

I'm very new at all this, a buddy did the partioning and he's not around anymore.

If you could help me out I'd surely appreciate it because I have all my stuff in windows and on the desktop & Favorites and I don't know how or if I could transfer all of that to my linux?

Thanks,

B.E.

---

### Post by caljohnsmith on 2009-02-17
In order to get a clearer picture of your setup, how about booting your Live CD (can be your PCLinuxOS CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal/konsole and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by B.E. on 2009-02-18
My hard drive is split (partitioned) with PcLinuxOS and windows. I have all my work on windows and when I boot up and scroll down and click on windows I get this message:
Error13: Invalid or unsupported executable format
Press any key to continue

When I press any key it goes to an aqua coloured screen  with the options I have on my computer which are:

Linux
Linux-nonfb
failsafe
windows
and windows is coloured Yellow

I press windows and it goes back to same screen that I mentioned above.

A friend of mine did the partitioning and he's not around anymore and I don't have a CD or anything so, I'm relying on anyone that might be able to help me fix this so I can get back to my windows because I have ALL my work there.

I'm quite new to all this so be patient with me if I have to add new posts if I don't get it right the first time.

Thanks in advance

B.E.

---

### Post by oldos2er on 2009-02-18
You might get better help from the PCLinuxOS forums.

 Can you boot PCLinuxOS, and post the output of
```
sudo fdisk -l
```
?

---

### Post by overdrank on 2009-02-18
Threads merged

---

