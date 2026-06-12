---
title: "Copying Over Network Slows Down Host"
date: 2013-11-10
forum: Networking &amp; Wireless
---

### Post by anomie.t on 2013-11-10
I'm running Ubuntu 13.10 (though this problem persisted in 12.04 and 13.04). 

My server is runing Ubuntu 12.04.

When I copy large files (>1GB) from my server to my desktop running 13.10, access to the host slows down dramatically. Here's what I've used:

Using cp to copy to a local directory from a mounted samba share.
Using scp over ssh for the same thing
Using rsync over ssh and through samba mounts for the same thing

In all cases, when I ping my server, while copying it jumps from ~0.250ms(server idle) to ~150ms. The lag becomes incredibly noticeable when I try to just navigate through directories on the server. Just running ls in a directory can take several seconds to complete execution.

When I copy from the same samba shares on a windows install, the latency only jumps to about ~25ms so minimal server slow down is perceived.

This means when I copy files over to my ubuntu desktop enviroment, accessing the server in any way because pretty much impossible since everything slows down. Currently open ssh terminals become really slow, navigating mounted shares in a file manager is slow, etc...

Anyone know why this would happen?

Thank you,
-anomie

---

### Post by TheFu on 2013-11-10
What sort of storage?
How much excess RAM .. can be used for disk buffers?
Has anyone tweaked the network buffers/queues?

What sort of throughput does each method provide?  Can you put in a bandwidth limit so the storage runs as slowly as on Windows?
What sort of CPU?  An Atom will use more CPU with networking and storage than a Core i7.

---

### Post by anomie.t on 2013-11-10
They are just standard hard disk drives.

On both windows and ubuntu I get ~10MBps when copying over files from my server. I ran rsync with bandwidth limits and it did lessen the load, but then my download speeds were significantly less. I want to keep the speeds around 10MBps and still be able to use my server just like when I copy files in windows.

I have an i7 on my desktop and an old intel quad core (qx6700) on my server.

> How much excess RAM .. can be used for disk buffers?
I'm not really sure. How do I check? Do I check on my server or my client?

> Has anyone tweaked the network buffers/queues?
I don't think so... Not entirely sure what this means?

Thank you,
-anomie

---

### Post by anomie.t on 2013-11-12
So I've troubleshooted more and found some interesting things.

I ended up upgrading my server to 13.10 and now it doesn't bog down the entire server. Other devices can access the server without lag. When copying large files, I tried pinging again and it only raises to about 10ms instead of 150ms. So definitely an improvement. However, I still have a problem on  my ubuntu desktop install. While copying large files to my local desktop machine, I still get a ton of latency when trying to navigate through server mounts on the same client performing the copy. While copying, running ls on mounted samba shares hangs, simply traversing directories (either in the terminal or in a file manager) has tons of lag. Other processes (music players) reading from the server while copying will begin to stutter as if having a hard time reading the files.

So I kept investigating and found something odd. I shutdown x completely by running ```
sudo service lightdm stop
```. Started copying a large file then switched to a new terminal use Ctrl+Alt+Left Arrow. Navigating directories was fine. Running ls performed as expected without significant lag. Before restarting x, I cancelled the copy and ran a tmux session and started copying in there. No lag navigating when I detached from the tmux window. So I restarted x again and attempted to navigate the mounted network shares and they lagged like crazy like usuall. I'm wondering if X11 is the culprit here? Anyone have any ideas?

Edit:
Another thing I found is that when I navigate the shares while copying large files using:
```
smbclient //server/share -U user%password
```

there is no lag.

Thanks,
-anomie

---

### Post by TheFu on 2013-11-13
Unity or a pure WM environment?
Also, I assume you are on a 100base-t network, not GigE?

---

### Post by anomie.t on 2013-11-13
No unity, just awesome wm. Also, no gigabit ethernet at the moment. I've always gotten around 10MB/s when copying files. Though, I don't think the network is the issue at this point since it seems isolated to just my desktop running awesome. I haven't tested it outside of awesome, so can't say for sure if it's x or more specifically awesome.

Thanks,
-anomie

---

### Post by TheFu on 2013-11-13
I use openbox and haven't noticed any slowdowns until around 700Mbps.

The only other idea is that USB is involved.  I've seen queuing "issues" with USB storage (even USB3) if too many different processes wanted access concurrently.  From your description, that doesn't seem to be the issue.

Might look at the process table during the copy-slowdowns. What is eating all the CPU? The threaded view might be useful.

BTW, 10MB/s is 80 megabits/sec. Add in the overhead for TCP and you are near the max for a 100base-t connection. The best I've ever seen on a 100base-t network copy is 11MB/s.  Everything was GigE ... except the NAS drive being written.  The source was GigE with fast SATA drives.

---

