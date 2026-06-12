---
title: "[Solved]ethernet card not active after reboot"
date: 2022-10-11
forum: Networking &amp; Wireless
---

### Post by diplo95 on 2022-10-11
Hi all,

I've got a problem every time I reboot my PC. The card switch to inactive. If I do this command, it resolves my problem :
```
greg@greg-nuc:~$ sudo ip link set enp88s0 down 
greg@greg-nuc:~$ sudo ip link set enp88s0 up 
greg@greg-nuc:~$ sudo dhclient enp88s0
```

My install is quite new. My problem appeared when I tried to set up a VM using KVM. I followed this tuto :
[https://linuxhint.com/install-kvm-ubuntu-22-04/](https://linuxhint.com/install-kvm-ubuntu-22-04/)

I'm a beginner in linux, but I wonder if my problem doesn't come with 6th item of the tuto.

As I said, I'm a beginner in linux after more than 20 years with Microsoft. If someone could help me sort this out, it would be appreciated.

Thx

---

### Post by diplo95 on 2022-10-12
Hi,

I finally sorted out my problem. It came from a bad netplan conf file. I rewrote it and it did the job.

---

### Post by TheFu on 2022-10-12
This was very much a virtualization question.  If you'd have posted to the correct subforum with a different title, we virtualization people would have jumped onto it within a few hours.  All we see is the title and forum when deciding which posts to spend effort helping.  Based on those, I'd assumed you had a realtek NIC and a bad driver that didn't reinitialize the NIC registers correctly.  This was a common problem about 5 yrs ago with realtek drivers.  I stopped using realtek hardware around 2015 for that and other reasons. The $20 extra to get intel has been well worth it to me. That assumption (which could easily be false) - especially if I'd opened the actual post to see the NIC device, enp88s0, which is typically an Intel NIC using the igb driver.  But all I had was the title and subforum.

MS-Windows isn't Linux, as you are learning.  Things that appear to be similar aren't.  Underneath, there are huge differences in the overall security model and in how the different OSes are meant to behave.  Unix will do what we ask whether it is stupid or genius. It cannot tell which, so it tries.  It isn't there to stop us from doing anything. If we want to shot ourselves in the foot, leg, chest or head and the command is valid, it will do it .... and if is works, it will be silent.  Philosophical differences in the OS.  If you see any "Are your sure?" prompts, those were added because so many people with MSFT backgrounds were doing bad things with the command.

Anyway, glad you figured this out.  Also, please use the "thread tools" button to mark the thread as solved. This toggles a flag in the DBMS, so people searching for answers will find it.  Changing the title to have the words is good for human readers, but not as good as toggling the flag in the DBMS. Definitely appreciate the attempt to convey that it is solved, there's just a better way in these forums.

---

