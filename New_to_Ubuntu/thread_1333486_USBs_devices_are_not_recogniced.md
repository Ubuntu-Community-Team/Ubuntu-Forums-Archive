---
title: "USBs devices are not recogniced"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by somoconsultores on 2009-11-21
Hello to everybody. I'm new in this forum and I have no clue about Ubuntu.
I updated the version to 9.10 and since then I have a few problems. The main one: every time I connect a pendrive or an external hard disk, the laptop does not recognize them. 
I'm a bit desperate because I have all my work in these devices and I can not work.
Anybody can help me? If I must write something in the konsole please have in mind I'm a completely begginer.
Thank so much.

---

### Post by gradinaruvasile on 2009-11-21
Did you upgrade from the previous version (9.04)? I would suggest a coplete reinstallation. 
First, boot from a live cd (d/l the .iso image from ubuntu site, burn it on a cd). Are the USB devices working?
If yes, reboot normally.
After connecting the thumb drive (and wait 2-3 seconds), open a terminal and type:

dmesg

and press enter. Post here the content of the terminal.

---

### Post by emigrant on 2009-11-21
hi,
go to system>admin>synaptic package manager
in the search box type 'pciutils' and see whether its been installed, if not install it.

---

### Post by somoconsultores on 2009-11-21
Thank very much.
To Gradinaruvasile: yes, I updated from the previous version (9.04).
I typed "dsmeg" in the terminal but the administrator does not let me to show the whole message becuase it's too long, so I show the last part. 

To emigrant: yes, ipciutils is installed.

Somoconsultores

smedg:
[38733.172732] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38733.176100] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[38733.176114] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38733.234003] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[38733.234024] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38733.237500] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[38733.237520] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38733.312366] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[38733.312386] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38733.316141] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[38733.316160] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38733.401869] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[38733.401891] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38733.405252] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[38733.405269] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38733.481353] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[38733.481374] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38733.485091] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[38733.485109] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38733.561140] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[38733.561161] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38733.564719] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[38733.564737] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38733.650416] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[38733.650437] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38733.654164] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[38733.654183] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38766.741180] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 445
[38783.284432] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[38783.284452] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38783.288121] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[38783.288139] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38783.345342] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[38783.345363] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38783.349622] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[38783.349642] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[38783.444655] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[38783.444671] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[38783.448110] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[38783.448130] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[38783.525459] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[38783.525475] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[38783.529544] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[38783.529566] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[38783.603990] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[38783.604007] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[38783.607404] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[38783.607420] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[38783.693452] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[38783.693469] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[38783.697225] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[38783.697239] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[38783.764502] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[38783.764518] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[38783.768077] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[38783.768090] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[38886.741108] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 479
[39006.743386] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 568
[39126.736197] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 485
[39246.741200] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 362
[39366.742771] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 485
[39486.740187] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 377
[39606.741551] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 454
[39658.405058] __ratelimit: 3 callbacks suppressed
[39658.405070] type=1503 audit(1258830427.681:24): operation="open" pid=5717 parent=1 profile="/usr/bin/evince" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name=2F6D656469612F5175657369746F2F6C494E5558205562756E74752F434F4D414E444F532042C3815349434F53204445204C494E55582E646F63
[39658.407429] type=1503 audit(1258830427.681:25): operation="open" pid=5717 parent=1 profile="/usr/bin/evince" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name=2F6D656469612F5175657369746F2F6C494E5558205562756E74752F436F736173206120696E7374616C6172206465737075C3A973206465205562756E747520392D3034
[39658.410658] type=1503 audit(1258830427.685:26): operation="open" pid=5717 parent=1 profile="/usr/bin/evince" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name=2F6D656469612F5175657369746F2F6C494E5558205562756E74752F436F736173206120696E7374616C6172206465737075C3A97320656E205562756E747520392E30342E646F63
[39658.439971] type=1503 audit(1258830427.713:27): operation="open" pid=5717 parent=1 profile="/usr/bin/evince" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name=2F6D656469612F5175657369746F2F6C494E5558205562756E74752F506F6E657220612070756E746F205562756E747520392E30342E646F63
[39658.441398] type=1503 audit(1258830427.717:28): operation="open" pid=5717 parent=1 profile="/usr/bin/evince" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name=2F6D656469612F5175657369746F2F6C494E5558205562756E74752F5265706F7369746F72696F73207072696E636970616C6573205562756E747520392E30342E646F63
[39726.757664] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 254
[39846.744201] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 494
[39966.740222] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 254
[40086.740105] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 377
[40151.588170] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)
[40151.588192] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost
[40151.588207] EXT4-fs: mballoc: 0 generated and it took 0
[40151.588220] EXT4-fs: mballoc: 0 preallocated, 0 discarded
[40206.736194] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 420
belen@belen-laptop:~$

---

### Post by gradinaruvasile on 2009-11-21
And this is right after inserting a thumb drive? It doesnt even recognise it if the dmesg command was given a few seconds after inserting the drive.
Does the drive have a LED on it that should blink when inserted? And if so, does it blink?

---

### Post by somoconsultores on 2009-11-21
Thank yo for your prompt response.
No, it does not blink (I have tried with several thumb drives)
Another thing I have done its tito type: "sudo fsck /dev/sdb1" and it says the superblock is corrupted (it does not work).

(The problem is I have no idea. I typed the command above because I saw it in another web page but I do not understand the meaning at all)
Thank you

---

### Post by gradinaruvasile on 2009-11-21
Try booting from a live cd and see if that way it works.

The problem is that the kernel doesnt sense the devices that should trigger auto mounting by the GDM.
 You should see in dmesg output right after inserting a thumb drive something like sdd sdd1 sdd2, the device list.

I hear many people had problems with the upgrade fro 9.04 to 9.10, maybe you should reinstall too...

---

### Post by somoconsultores on 2009-11-21
Yes, you are right, perhaps I should reinstall 9.10 again. 
How I do it? First time it was easy to upgrade (the update manager did everything). But now the update manager do not say to upgrade anymore.
Thank you very much for your help
Somoconsultores

---

### Post by emigrant on 2009-11-22
> **somoconsultores said:**
> Yes, you are right, perhaps I should reinstall 9.10 again. 
How I do it? First time it was easy to upgrade (the update manager did everything). But now the update manager do not say to upgrade anymore.
Thank you very much for your help
Somoconsultores

download the suitable version:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)


[LIST=1]
[*]burn the iso into a cd.
[*]insert the cd into the rom and restart
[*]upon restarting go to BIOS setup (often by pressing DEL)
[*]set CDROM as the first boot device under boot device priority
[*]save setting and exit (F10) - machine will restart and will be booting from the cd
[*]follow the instruction on screen
[/LIST]

---

