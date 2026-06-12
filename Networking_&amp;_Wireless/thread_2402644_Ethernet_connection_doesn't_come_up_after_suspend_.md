---
title: "Ethernet connection doesn't come up after suspend (Bionic)"
date: 2018-10-02
forum: Networking &amp; Wireless
---

### Post by Qew on 2018-10-02
Today I received a kernel update for 18.04 (4.15.0-36). Since that update, whenever I come out of suspend, my wired connection is disconnected and refuses to come up. The odd thing is that putting the machine back into suspend again and then waking it, does then bring up the wired connection, and my Internet then works fine.

I've done some Googling and discovered that my type of Ethernet controller is a bit notorious for this kind of thing after a suspend. However, most of the discussion about this is for kernel versions prior to the one I have or at least some months prior to today. As I said, it was working fine till today's kernel update, and I update daily (previous kernel was 4.15.0-34, which worked fine). 

This is a Dell Inspiron 5548 laptop, which has a Realtek Ethernet controller. **lspci | grep Ethernet** gives the result below:

```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
```

This uses the kernel module r8169.

Running the below will also bring up my wired network connection when disconnected after a suspend.

```
modprobe -r r8169 && modprobe r8169
```

Seeing that this works, I've added a file containing a script to /lib/systemd/system-sleep passing the code below. This workaround works for me, but I really shouldn't need to do this.

```
#!/bin/sh

case $1 in
  post)
        modprobe -r r8169
   sleep 3
   modprobe r8169
    ;;
esac

```

Anyone else facing this now? It's odd that I've been immune until today. The other oddity is that suspending it a second time and waking it brings up a working connection. I find that very odd that one suspend doesn't bring up my connection but a second one will.

---

