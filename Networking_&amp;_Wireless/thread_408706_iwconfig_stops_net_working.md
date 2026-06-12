---
title: "iwconfig stops net working"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by giambrone on 2007-04-13
OK guys, I followed the tutorial on [here]("http://ubuntuforums.org/showthread.php?t=340689") (changing the parts to relate to my device, drivers and kernel etc) and when I get to iwconfig (step 13 - 14) everything goes wrong. The kernel gives me this error/message (its uber long so I'll put it last) - following this I no longer have internet access, and no new programs will open (nor will the terminal execute)... Any Ideas??

Thanks,
Matt:KS 

Error:
> matt@matt-desktop:~$ sudo depmod -a
matt@matt-desktop:~$ sudo modprobe ndiswrapper
matt@matt-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Segmentation fault
matt@matt-desktop:~$ 
Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016086] Oops: 0000 [#1]

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016087] SMP 

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016143] CPU:    0

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016144] EIP:    0060:[__nla_put+33/64]    Tainted: P      VLI

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016145] EFLAGS: 00210216   (2.6.20-14-generic #2)

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016154] EIP is at __nla_put+0x21/0x40

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016156] eax: df8480fc   ebx: 00000014   ecx: 00000005   edx: 00000000

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016159] esi: 00000004   edi: df848100   ebp: f2172000   esp: f317fbb4

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016161] ds: 007b   es: 007b   ss: 0068

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016163] Process iwconfig (pid: 5927, ti=f317e000 task=f3170030 task.ti=f317e000)

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016165] Stack: f6377b40 00000014 0000000b c029996b 00000004 f2172434 00000000 f9c00000 

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016170]        c028adf2 00000004 f317fc98 f317fc94 00200082 00000000 00000004 f6377b40 

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016175]        df848000 f9c00000 00000000 f9c10000 00000000 00000000 00000000 00000011 

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016180] Call Trace:

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016192]  [nla_put+75/96] nla_put+0x4b/0x60

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016208]  [rtnl_fill_ifinfo+930/1200] rtnl_fill_ifinfo+0x3a2/0x4b0

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016276]  [rtnl_getlink+320/368] rtnl_getlink+0x140/0x170

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016370]  [rtnl_getlink+0/368] rtnl_getlink+0x0/0x170

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016380]  [rtnetlink_rcv_msg+363/592] rtnetlink_rcv_msg+0x16b/0x250

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016383]  [netlink_ack+224/432] netlink_ack+0xe0/0x1b0

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016408]  [rtnetlink_rcv_msg+0/592] rtnetlink_rcv_msg+0x0/0x250

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016415]  [netlink_run_queue+130/288] netlink_run_queue+0x82/0x120

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016440]  [rtnetlink_rcv+40/80] rtnetlink_rcv+0x28/0x50

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016453]  [netlink_data_ready+18/80] netlink_data_ready+0x12/0x50

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016462]  [netlink_sendskb+33/64] netlink_sendskb+0x21/0x40

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016472]  [netlink_sendmsg+547/768] netlink_sendmsg+0x223/0x300

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016532]  [sock_sendmsg+274/304] sock_sendmsg+0x112/0x130

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016586]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016600]  [__wake_up_common+57/96] __wake_up_common+0x39/0x60

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016631]  [__wake_up+56/80] __wake_up+0x38/0x50

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016678]  [copy_from_user+39/96] copy_from_user+0x27/0x60

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016685]  [copy_from_user+39/96] copy_from_user+0x27/0x60

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016711]  [sys_sendmsg+353/624] sys_sendmsg+0x161/0x270

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016805]  [find_get_page+32/96] find_get_page+0x20/0x60

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016822]  [sock_ioctl+0/528] sock_ioctl+0x0/0x210

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016834]  [dev_ifsioc+28/864] dev_ifsioc+0x1c/0x360

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016853]  [dev_ioctl+561/896] dev_ioctl+0x231/0x380

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016865]  [__switch_to+198/496] __switch_to+0xc6/0x1f0

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016891]  [schedule+765/2704] __sched_text_start+0x2fd/0xa90

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016954]  [sys_socketcall+591/640] sys_socketcall+0x24f/0x280

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.016999]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.017059]  =======================

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.017060] Code: 98 29 c0 e8 22 42 fe ff eb b7 83 ec 0c 89 1c 24 89 cb 89 74 24 04 8b 74 24 10 89 7c 24 08 e8 67 ff ff ff 89 d9 c1 e9 02 8d 78 04 <f3> a5 89 d9 83 e1 03 74 02 f3 a4 8b 1c 24 8b 74 24 04 8b 7c 24 

Message from syslogd@matt-desktop at Fri Apr 13 22:18:06 2007 ...
matt-desktop kernel: [  331.017081] EIP: [__nla_put+33/64] __nla_put+0x21/0x40 SS:ESP 0068:f317fbb4


---

### Post by giambrone on 2007-04-14
***bump***

---

### Post by huygens on 2007-04-14
Hi Matt,

First of all, there is a much recent release of ndiswrapper than the one mentioned in the guide. Simply go here: [http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148)
And download the latest release.

I do not know if it will solve your problem, but hepofully yes ;-)

---

### Post by giambrone on 2007-04-15
Okay, It would appear that I now have the latest version of ndiswrapper, although checking dmesg after modprobe suggests that I have version 1.38 installed, not version 1.41 :o. - In synaptic it doesn't say that I have ndiswrapper installed at all!

It still comes up with the segfault and that bunch of messages after, although I haven't checked that they're the same.

Matt :KS:KS

---

### Post by huygens on 2007-04-15
Could you do a 
```
slocate ndiswrapper.ko
```
You might found that you have more than one version... In this case, unload ndiswrapper from memory (rmmod ndiswrapper) and remove (or rename) the ndiswrapper.ko that you did not install.
Now you should do again:
```
sudo depmod -a
sudo modprobe ndiswrapper
```

Verify in dmesg that you have now the latest version.

---

### Post by giambrone on 2007-04-16
Still a noob at this end, I'm not sure which ones to delete - I'll post the output of "slocate ndiswrapper.ko" and could you tell me which ones to do - Or how to completely remove ndiswrapper?

> matt@matt-desktop:~$ slocate ndiswrapper.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.20-14-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.20-14-generic/misc/ndiswrapper.ko
/lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko


Thanks :)

Matt :KS

---

### Post by huygens on 2007-04-17
Reading your entry I would guess the following. You are now running Ubuntu Feisty Fawn on an upgraded Edgy Eft.
I would be pretty confident that you system picks-up the one "2.6.20-15" but as it is the Ubuntu installed one, I would not remove it.
I think that also there is a strange thing. Your custom ndiswrapper (the one you compiled using the tutorial) was done against the kernel 2.6.20-14, whereas your latest kernel is 2.6.20-15... So I would make sure that I have the latest linux-header.
In your case the command:
```
sudo apt-get install linux-headers-2.6.20-15
```should do the trick.
Now your recompile (step C. 8. from at least 'make distclean') and perform all the step up to C. 12. included.
Before continuing, you should do this:
```
cd /lib/modules/2.6.20-14-generic/misc/
sudo mv ndiswrapper.ko ndiscustom.ko
echo 'blacklist ndiswrapper' | sudo tee -a /etc/modprobe.d/blacklist
sudo depmod -a
sudo modprobe ndiscustom
```Now you can start again with step D. 14. (so skipping the 13th step).
The only step that should be different should be the 17th, where you have to make sure the line is:
```
alias wlan0 ndiscustom
```I have tested it in a virtual machine, it should work. I have used ndiswrapper 1.42 (was out 2 days ago). It installed ndiswrapper.ko in /lib/modules/2.6.20-14-generic/misc/ and /usr/sbin/ndiswrapper (amongst many other things).
If I check the versions:
```
huygens@huygens-desktop:~$ strings /lib/modules/2.6.20-14-generic/misc/ndiscustom.ko | grep ^version
version=1.42
huygens@huygens-desktop:~$ ndiswrapper -v
utils version: 1.9
driver version:        1.38
vermagic:      2.6.20-15-generic <blah blah>
```

---

### Post by giambrone on 2007-04-18
Okay I got it up to "iwconfig again" - The same segfault occurs with no wireless card being found.
I'm really stumped now.

Thanks for trying so far - I think I have bigger problems though!! I'm considering a reinstall when feisty is released ...tomorrow?

Matt:KS

---

### Post by giambrone on 2007-04-21
Hooray problem solved...Ish

Reinstalled feisty, and the problem no longer exists - Cowards way out :P

Even have my wireless card working ;D

Thanks guys

Matt:KS

---

