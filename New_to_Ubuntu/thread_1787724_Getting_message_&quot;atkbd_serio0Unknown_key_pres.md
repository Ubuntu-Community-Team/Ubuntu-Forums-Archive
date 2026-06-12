---
title: "Getting message &quot;atkbd serio0:Unknown key pressed&quot; when trying to install Ubuntu 11.4"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by LBert on 2011-06-21
I downloaded Ubuntu 11.04 and put it on a USB stick as was explained on the site. When I booted from that USB stick, and chose "try Ubuntu", it began to start normally, until it gave hundreds of messages like
[I]"atkbd serio0: Unknown key pressed (translatesat 2, code 0x8d on isa0060/serio0)
Use 'setkeycodes e00d <keycode>' to make it known"
[/I]After a few minutes, these error messages stopped and a screen with the logo of Ubuntu appeared (like it should when you start Ubuntu). This screen stayed for a few minutes and afterwards disappeared again. At that moment I got again a text screen, and tens of pages of letters and ciphers were written on the screen, but I couldn't follow it, because the new text came very quickly.
After 5 minutes, I put the computer off.

I also tried the option "install Ubuntu" when I booted from the USB stick, and similar problems occurred. First it began normally, afterwards I got the same error messages "Unknown key pressed", after a few minutes I saw the logo of Ubuntu, and a few minutes later this disappeared and I saw again many letters and ciphers, but this time it stopped after about 10 seconds, and I got again the error messages like before (Unknown key pressed). I decided to wait and to see what would happen, but after more than five minutes I still had the same errors with "unknown key pressed". So I can't try nor install Ubuntu.

I have a Dell Vostro 1000 (laptop) AMD Turion 64 X2 Mobile Technology TL-56 1.80 GHz, I still have Windows Vista, and I tried to install Ubuntu 11.04 i386.

I have found other similar topics on the internet, but they all had problems when they already installed Ubuntu, and the solutions suggested there can only be applied when you already have installed Ubuntu.

Thank you for your help!

---

### Post by cariboo on 2011-06-22
It looks like you have a graphics problem of some sort, it's hard to tell with so little information. Have you tried setting nomodeset? To do so when you see the little man and keyboard on the initial screen, press the any key to see the menu, press F6, select nomodeset, then press esc to get back to the menu screen, and press enter.

---

### Post by LBert on 2011-06-23
First of all, I didn't see something with a little man and a keyboard. When I boot from my USB stick, I get a menu where I can choose between "run Ubuntufrom this USB", "Install Ubuntu on a hard disk", "test memory", "boot from first hard disk", "advanced options" and "help". At the bottom of the screen was written "press ENTER to boot or TAB to edit a menu entry". I pressed tab, so that I could add options, and I added the option "nomodeset". After that, it started, but it still gave the same error message as before (with setkeycodes).
I also managed to read something of the tens of pages of text and letters about which I spoke: "sys/devices/cpi". So it is no random text.

I also found out that if I waited long enough, I got a command line (in the nomodeset option) (I think that this is the command line; at the beginning of the input line, there is written (initramfs), and if I type help, I get built-in commands like . : [ alias break cd chdir command and so on). However, the error messages continued. I managed to stop these error messages by typing "setkeycodes e00d 255" (like I found in other help topics about this problem). However, this only worked from the moment that the command line started up, which takes a while (I think that all those error messages slow down the computer enormeously).

I didn't manage yet to start the computer up without the option nomodeset (maybe I need more patience, so that I don't put the computer off after some time).

Edit: I also managed to start the computer up without the option nomodeset, but it still gives the command line, and no graphical interface. When I typed "setkeycodes e00d 255" the error messages stopped. When I typed afterwards "exit" it said the following thing:
/init: line 331: can't open /root/dev/console: no such file
[...] Kernel panic - not syncing : Attempted to kill init!
[...] Pid: 1, comm: init Not tainted 2.6.38-8-generic #42-Ubuntu
[...] Call Trace:
[...] [<c1507054>] ? panic+0x5c/0x157
[...] [<c10531e8>] ? forget_original_parent+0x1f8/0x200
[...] [<c10dbc0c>] ? perf_event_exit_task_context+0x2c/0x130
[...] [<c10b4582>] ? call_rcu_sched+0x12/0x20
[...] [<c1053203>] ? exit_notify+0x13/0x350
[...] [<c1053a50>] ? do_exit+0x180/0x350
[...] [<c1127200>] ? vfs_write+0x100/0x170
[...] [<c1053d7e>] ? do_group_exit+0x3e/0xa0
[...] [<c1053df8>] ? sys_exit_group+0x18/0x20
[...] [<c1509bf4>] ? syscall_call+0x7/0xb
[...] panic occured, switching back to text console

After this, everything freezed.

---

### Post by LBert on 2011-07-01
I managed now to install Ubuntu 10.04 (32 bit). It seemed that the problem was that I didn't format my USB stick before I put Ubuntu on it. Someone helped me, and put Ubuntu on my USB stick (and formatted it before he put Ubuntu on it), and then I perfectly managed to install Ubuntu.
I still have some problems, but maybe I am going to begin another thread about that. Anyway, those problems don't have to do anything with the problems I described here.

---

### Post by manit64 on 2012-01-09
Hi


i have a laptop vostro 1000, come to grips with ERROR: set keycode e00d
pleas lead to me for fix keyboard?

---

