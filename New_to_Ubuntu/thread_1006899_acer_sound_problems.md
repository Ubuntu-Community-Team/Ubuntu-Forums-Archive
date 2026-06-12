---
title: "acer sound problems"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by Sigsaucer647 on 2008-12-09
hi linux peoples
im in highschool and thought it would be cool to give ubuntu a try
so i partitioned the hardrives...etc
well, i have ubuntu 8.10 and have run into a problem
i no longer have sound...well, i never had sound to begin with
my computer is an acer 6920 i tried some stuff a while back because a lot of people were having problems with sound on this computer
i did something while following some instructions and now i think that i deleted what makes the sound and stuffs work(the drivers?) and i would really like to have sound back so i can listen to music on ubuntu ^.^
so, if you can help or anything, really, really appreciated :lol:

---

### Post by gettinoriginal on 2008-12-09
In terminal type alsamixer and see what readings you get, there should be none muted and all have volume settings (you can change them with arrow keys)

---

### Post by Sigsaucer647 on 2008-12-10
.

---

### Post by Sigsaucer647 on 2008-12-11
jason@Jason-laptop:~$ alsamixer
No mixer elems found

jason@Jason-laptop:~$

thats what i get, and when i try to change the volume using the icon in the task bar, i get a message saying " no volume control GStreamer plugins and/or devices found "

---

### Post by LowSky on 2008-12-11
In terminal could you please post what pops up when you use the following command
```
lspci 
```

---

### Post by albinootje on 2008-12-11
Here's a recommendation : [https://answers.launchpad.net/ubuntu/+question/42289](https://answers.launchpad.net/ubuntu/+question/42289)

And here : [http://ubuntuforums.org/showthread.php?t=820774](http://ubuntuforums.org/showthread.php?t=820774)

blankfile1 writes :
===============================================================
 Re: No sound: Acer Aspire 6920
I used the step-by-step instructions to install OSS4 found HERE.

And guess what? it WORKED! My precious sound is working now.

Thanks again for the help, greatly appreciated.
===============================================================

---

### Post by binbash on 2008-12-11
your problem's solution here : 

[http://ubuntuforums.org/showthread.php?t=1001803&highlight=6920](http://ubuntuforums.org/showthread.php?t=1001803&highlight=6920)

---

### Post by Sigsaucer647 on 2008-12-11
jason@Jason-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9500M GS (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
08:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
jason@Jason-laptop:~$ 

----------------------------
thats what i got lowsky

---

### Post by Sigsaucer647 on 2008-12-11
hey binbash, i got up to quote 14 on your post thing here:: [http://ubuntuforums.org/showthread.php?t=984081&page=2]("http://ubuntuforums.org/showthread.php?t=984081&page=2")
but when i go to download the file, i get:::::::: a scren with the words, name, size, and last modfiied, but no actual thing to click on to download =[

---

### Post by rab4567 on 2008-12-11
> **Sigsaucer647 said:**
> hey binbash, i got up to quote 14 on your post thing here:: [http://ubuntuforums.org/showthread.php?t=984081&page=2]("http://ubuntuforums.org/showthread.php?t=984081&page=2")
but when i go to download the file, i get:::::::: a scren with the words, name, size, and last modfiied, but no actual thing to click on to download =[


Dude I know your pain however Cjay554 has found the answer or at least most of it, if you scroll about halve way down the page you'll see that you must download the new alsa 1.0.18 package then 4 commands and your done.

It here.

[http://ubuntuforums.org/showthread.php?t=921637&highlight=acer+6920+sound&page=3](http://ubuntuforums.org/showthread.php?t=921637&highlight=acer+6920+sound&page=3)

Good luck let use know how you made out.

---

### Post by Sigsaucer647 on 2008-12-11
ok, thanks man, i tried it...but i only got up to the 2nd step where i downloaded all 3 files to my desktop, then i put this into the terminal :::::::::::

sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa1.0.9rc4 .
sudo tar xjf alsa-driver1.0.9rc4.bz2
sudo tar xjf alsa-lib1.0.9rc4.tar.bz2
sudo tar xjf alsa-utils1.0.9rc4.tar.bz2

and i got this:::::::::

jason@Jason-laptop:~$ sudo mkdir -p /usr/src/alsa
jason@Jason-laptop:~$ cd /usr/src/alsa
jason@Jason-laptop:/usr/src/alsa$ sudo cp ~/downloads/alsa1.0.9rc4 .
cp: cannot stat `/home/jason/downloads/alsa1.0.9rc4': No such file or directory
jason@Jason-laptop:/usr/src/alsa$ sudo tar xjf alsa-driver1.0.9rc4.bz2
tar: alsa-driver1.0.9rc4.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
jason@Jason-laptop:/usr/src/alsa$ sudo tar xjf alsa-lib1.0.9rc4.tar.bz2
tar: alsa-lib1.0.9rc4.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
jason@Jason-laptop:/usr/src/alsa$ sudo tar xjf alsa-utils1.0.9rc4.tar.bz2
tar: alsa-utils1.0.9rc4.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
jason@Jason-laptop:/usr/src/alsa$ 
jason@Jason-laptop:/usr/src/alsa$

---

### Post by Sigsaucer647 on 2008-12-11
oops,  i did the one before that, i triedthe one half way down the page, and on the first command i got this message::::::::

jason@Jason-laptop:~$ sudo chmod +x alsa_setup_1.0.18.sh
chmod: cannot access `alsa_setup_1.0.18.sh': No such file or directory
jason@Jason-laptop:~$

---

### Post by CJay554 on 2008-12-12
If you have a problem reply to my thread i made for troubleshooting the problem for more organization. 

In this case, did you download the file from the link i gave? download that file to your home direction /home/<your user name>

then run those commands

---

### Post by Sigsaucer647 on 2008-12-14
ugh!!! i did exactly wat you said, and it all installed fine
but, when i trie a different way from someone before, it messed up the sound, so when ever i try to unmute it, i get "no volume control GStreamer plugins and/or devices found"

why wont it work!?!?

---

### Post by CJay554 on 2009-01-14
the "no volume control GStreamer plugins and/or devices found" error comes up when you uninstall ALSA at the beginning, to install OSS4, now you will have to reconfigure and maybe re-install the original ALSA, howto is at the bottom of my post # 26 here:
[http://ubuntuforums.org/showthread.php?t=921637&highlight=cjay554&page=3#26](http://ubuntuforums.org/showthread.php?t=921637&highlight=cjay554&page=3#26)

after you reconfigure your default driver to ALSA then reinstall the package (or maybe you won't have to) and see what you get!

---

