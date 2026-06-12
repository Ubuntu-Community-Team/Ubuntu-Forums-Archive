---
title: "Killing Xserver Turns the Screen Black"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by bluepete59 on 2009-05-28
Hi,
 
Sorry if this question is a repeat, but I've just installed Xubuntu 8.04 on a Dell 5000e. Video card is ATI Moblity 128 AGP 2X. I want to kill X server and just show a command prompt. When I do Ctrl->Alt-backspace or /etc/init.d/gdm stop in a terminal, the screen behaves very strangely, as if its doing some sort of wierd special effects fade out to black. Nothing appears at all after a moment. I have to reboot in order to recover.
 
How do I kill X server and get a command line? Also, what file do I modify so that I get a command line on bootup.
 
Thanks in advance.
 
bluepete59

---

### Post by pytheas22 on 2009-05-28
Control-alt-backspace won't stop X in modern versions of Ubuntu; it will just log you out, and GDM will automatically start X again.  The only way to drop to the command line is to type:
```

sudo /etc/init.d/gdm stop
```

I'm not sure why you experience strange behavior after typing that command.  Are you typing the command inside a Gnome terminal, or are you doing it from a virtual terminal (which you access by pressing control-alt-F1...)?  You should do it from a virtual terminal, not from within Gnome.

Also, after you type the command, is gdm still listed as running if you type:

```

ps -e | grep gdm
```

To prevent GDM and X from starting automatically, type this command to remove GDM from the startup scripts:
```

sudo update-rc.d gdm remove
```

---

### Post by bluepete59 on 2009-05-28
Thanks for the response. I tried Ctrl->Alt-F1 and get the same behavior. The screen just fades slowly to black. I can make the change to the startup script, but I would like the option to call up a terminal.
 
bluepete59

---

### Post by pytheas22 on 2009-05-28
> Thanks for the response. I tried Ctrl->Alt-F1 and get the same behavior. 

That's strange.  What happens if you press control-alt-F2 or control-alt-F3?  These should also bring you to a virtual terminal.

I'm wondering if something weird might be going on with your monitor--perhaps you are dropping down to the terminal successfully, but for some reason your monitor is not displaying it correctly, and is just showing you the weird black screen instead.  Is there any way for you to connect to an external VGA monitor and see what happens there?

---

### Post by bluepete59 on 2009-05-28
Tried F1 through F6, same result. Unfortunately, I don't have a spare monitor to try out your suggestion. However, I can SSH into the machine from another box and killing gdm remotely has the same effect on the host machine (funky display behavior), though I get a prompt through the terminal client.
 
This has to be a display or video card issue? Again, I've got a ATI Mobility 128 AGP 2X on a Dell Inspiron 5000e.
 
bluepete59

---

### Post by pytheas22 on 2009-05-29
In that case, it does sound like an issue with your video card or driver.  Could you please post the output of:
```

lspci -nn | grep -i ati
```

so we'll know the exact device ID of your video card?  I tried googling based on 'ATI Mobility 128 AGP 2X' but nothing useful came up.

---

### Post by bluepete59 on 2009-05-29
Here you go:
 

00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
00:10.0 Communication controller [0780]: Agere Systems WinModem 56k [11c1:0448] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage Mobility M3 AGP 2x [1002:4c46] (rev 02)
06:00.0 Ethernet controller [0200]: 3Com Corporation 3cCFE575CT CardBus [Cyclone] [10b7:5257] (rev 10)
 
> **pytheas22 said:**
> In that case, it does sound like an issue with your video card or driver. Could you please post the output of:
```

lspci -nn | grep -i ati
```
 
so we'll know the exact device ID of your video card? I tried googling based on 'ATI Mobility 128 AGP 2X' but nothing useful came up.

---

### Post by pytheas22 on 2009-05-29
Thanks for the information.  Unfortunately Google is still not turning up anything very useful, which makes me think even more that the problem likely lies with your monitor.

If you stop gdm from autostarting ('sudo /etc/init.d/gdm remove') and [disable the splash screen]("http://ubuntuforums.org/showthread.php?t=542082"), do you still have problems?  With splash disabled, how much of the boot process do you see before the screen turns gray?  Does playing with the settings of your display (if possible) change anything?

---

### Post by bluepete59 on 2009-05-29
OK. So I can report a little progress. First, I disabled the splash screen and disabled "quiet" bootup. Then I installed rrconf and unchecked gdm. On reboot, I got the login prompt and everything's peachy.
 
However, the display problem is still there. I discovered that stopping gdm appears to be crashing the entire system. Hard to believe, but when I stopped gdm via PuTTY on my other laptop, sshd died. No response from the keyboard on the Ubuntu box. The system's just dead. How can that be?
 
Would like to solve this problem, if only because it's so wierd. ;)
 
> **pytheas22 said:**
> Thanks for the information. Unfortunately Google is still not turning up anything very useful, which makes me think even more that the problem likely lies with your monitor.
 
If you stop gdm from autostarting ('sudo /etc/init.d/gdm remove') and [disable the splash screen]("http://ubuntuforums.org/showthread.php?t=542082"), do you still have problems? With splash disabled, how much of the boot process do you see before the screen turns gray? Does playing with the settings of your display (if possible) change anything?

---

### Post by pytheas22 on 2009-05-29
> However, the display problem is still there. I discovered that stopping gdm appears to be crashing the entire system. Hard to believe, but when I stopped gdm via PuTTY on my other laptop, sshd died. No response from the keyboard on the Ubuntu box. The system's just dead. How can that be?

That's interesting.  Does the system log mention anything that might explain why starting gdm causes a crash?  Can you start an X session by typing just 'startx', without starting gdm first?

---

