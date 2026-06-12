---
title: "Help Translating Command Prompt to English"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by carrick149 on 2008-06-13
I finally found a way to get the wifi card on my acer to work, but I am not an experienced Linux user yet because the wifi card doesn't work.  So basically, I need these instructions [http://ubuntuforums.org/showthread.php?t=490800](http://ubuntuforums.org/showthread.php?t=490800)
translated into stupid people english

---

### Post by calraith on 2008-06-13
Hey, if your Acer is an Acer Aspire 4520, 5520 or 7520, ask me how to get a patched madwifi that'll make your wireless work natively, without Windows drivers.

Otherwise, go to the Applications menu --> Accessories --> Terminal.  Enter the following, or copy the following code one line at a time and paste into your Terminal window.  You can copy simply by dragging your mouse over text and highlighting it.  Paste either by middle-clicking (clicking the mouse wheel), or clicking the left and right mouse buttons at the exact same time.  It can take a little practice, but your new copy / paste ability will make the effort worthwhile.
     
```
sudo su
echo blacklist ath_pci >> /etc/modprobe.d/blacklist
sed -i -r -e '/^# defoptions/s/$/ pci=assign-busses/' /boot/grub/menu.lst
update-grub
grub-install /dev/sda
apt-get update
apt-get install -y ndiswrapper-common ndiswrapper-utils-1.9
echo ndiswrapper >>/etc/modules
exit
```Download the windows xp driver for the wireless card from the acer website ([www.acer.com]("http://www.acer.com/")) to your Desktop.

Unzip the driver by right-clicking it and choosing Extract Here.

Go back to your Terminal window.  Enter the following commands:

```
cd ~/Desktop
cd NameOfDirectoryContainingExtractedZipFile[FONT=monospace]
ls *.inf[/FONT]
```[FONT=monospace]

If the output of "ls *.inf" indicates that there are no files with an extension inf, you might have to explore your extracted zip file until you find a directory containing the Windows drivers (and not just the Windows setup program for those drivers).

When you find where the INF file is located, "cd directoryname" to change to the directory containing it.  Then enter the following command:

[/FONT]```
sudo ndiswrapper -i net5211.inf
```Restart your computer.  After it's restarted, wireless should work.

---

### Post by carrick149 on 2008-06-13
i got "permission denied" from the first command
and i guess i should have been specific.  I'm ok with computers, I'm just new to linux and I need help with terminal.

---

### Post by calraith on 2008-06-14
> **carrick149 said:**
> i got "permission denied" from the first command
and i guess i should have been specific.  I'm ok with computers, I'm just new to linux and I need help with terminal.

It sounds like you don't have root access on this machine.  With Ubuntu, normal operations are performed with limited system privileges.  That way, if something goes unexpectedly, that something usually doesn't have appropriate permission to do any real damage to your system.  Browsing the web, typing documents, viewing pictures, instant messaging, and most other things you do from day to day on your computer are performed with this limited system privilege.

The sudo command is a way to escalate whatever command follows, to be given root access -- basically like god mode.  For instance, try the following two commands, and note the difference in the output.

```
whoami
sudo whoami
```

Now, sudo should prompt you for your password.  Are you entering your password correctly?  Can you tell me exactly what gave you a permission denied error?

---

### Post by carrick149 on 2008-06-15
No, that's the thing, it didn't prompt me for a password like for instance sudo nautilus does
and i can run a sudo nautilus using my username

---

