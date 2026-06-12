---
title: "NFS timeout crashing Gnome/ Unity"
date: 2016-05-09
forum: Networking &amp; Wireless
---

### Post by solitaire on 2016-05-09
Hi all

I'm having a problem with Ubuntu 16.04 and NFS shared folder on my D-Link -DNS-320L NAS. (it's cheap and cheerfull and it works!)

Every so often the NFS share times out causing the program accessing it to time out and also to cause nautilus hang, sometimes resulting in the window manager crashing. When the window manager comes back everything is blurred, except what's under the pointer (and gives me a bloooody huge headache if i have to look at it for longer than a few mins!)

Other times the program just hangs till it can reastablish a connection to the NFS shared folder and continues as normal.

I never noticed this happening under 15.10 but I only got the NAS box and set up NFS around the time I upgraded to 16.04 beta. 

I can still access the NAS box using another device (Using ssh, as well as accessing it via it's web interface!) so i'ts not an issue with the NAS (unles i'm missing something!)

Last time it happened i was moving files to the NFS shared folder. Here was the errors in the log : (this was repeated 6 or so times)

<code>
May  9 16:32:12 Zotac gnome-session[2162]: (nautilus:2317): Gtk-CRITICAL **: gtk_container_foreach: assertion 'GTK_IS_CONTAINER (container)' failed
May  9 16:32:18 Zotac kernel: [  840.167513] INFO: task pool:2910 blocked for more than 120 seconds.
May  9 16:32:18 Zotac kernel: [  840.167534]       Tainted: P           OE   4.4.0-22-generic #39-Ubuntu
May  9 16:32:18 Zotac kernel: [  840.167540] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
May  9 16:32:18 Zotac kernel: [  840.167547] pool            D ffff880077403b28     0  2910   2162 0x00000000
May  9 16:32:18 Zotac kernel: [  840.167562]  ffff880077403b28 000000000001c6c4 ffffffff81e11500 ffff880241017080
May  9 16:32:18 Zotac kernel: [  840.167573]  ffff880077404000 ffff88024ec16d00 7fffffffffffffff ffffffff818219f0
May  9 16:32:18 Zotac kernel: [  840.167582]  ffff880077403c88 ffff880077403b40 ffffffff818211f5 0000000000000000
May  9 16:32:18 Zotac kernel: [  840.167592] Call Trace:
May  9 16:32:18 Zotac kernel: [  840.167614]  [<ffffffff818219f0>] ? bit_wait+0x60/0x60
May  9 16:32:18 Zotac kernel: [  840.167625]  [<ffffffff818211f5>] schedule+0x35/0x80
May  9 16:32:18 Zotac kernel: [  840.167635]  [<ffffffff81824315>] schedule_timeout+0x1b5/0x270
May  9 16:32:18 Zotac kernel: [  840.167645]  [<ffffffff810b4b83>] ? update_curr+0xe3/0x160
May  9 16:32:18 Zotac kernel: [  840.167654]  [<ffffffff818219f0>] ? bit_wait+0x60/0x60
May  9 16:32:18 Zotac kernel: [  840.167663]  [<ffffffff818219f0>] ? bit_wait+0x60/0x60
May  9 16:32:18 Zotac kernel: [  840.167673]  [<ffffffff810f574c>] ? ktime_get+0x3c/0xb0
May  9 16:32:18 Zotac kernel: [  840.167682]  [<ffffffff818219f0>] ? bit_wait+0x60/0x60
May  9 16:32:18 Zotac kernel: [  840.167691]  [<ffffffff81820744>] io_schedule_timeout+0xa4/0x110
May  9 16:32:18 Zotac kernel: [  840.167699]  [<ffffffff81821a0b>] bit_wait_io+0x1b/0x70
May  9 16:32:18 Zotac kernel: [  840.167708]  [<ffffffff8182159d>] __wait_on_bit+0x5d/0x90
May  9 16:32:18 Zotac kernel: [  840.167719]  [<ffffffff8118cadb>] wait_on_page_bit+0xcb/0xf0
May  9 16:32:18 Zotac kernel: [  840.167730]  [<ffffffff810c3ab0>] ? autoremove_wake_function+0x40/0x40
May  9 16:32:18 Zotac kernel: [  840.167739]  [<ffffffff8118cbf3>] __filemap_fdatawait_range+0xf3/0x160
May  9 16:32:18 Zotac kernel: [  840.167750]  [<ffffffff8118cc74>] filemap_fdatawait_range+0x14/0x30
May  9 16:32:18 Zotac kernel: [  840.167761]  [<ffffffff8118eaea>] filemap_write_and_wait+0x6a/0x70
May  9 16:32:18 Zotac kernel: [  840.167816]  [<ffffffffc131c500>] nfs_wb_all+0x20/0x110 [nfs]
May  9 16:32:18 Zotac kernel: [  840.167855]  [<ffffffffc13105cd>] nfs_getattr+0x11d/0x240 [nfs]
May  9 16:32:18 Zotac kernel: [  840.167865]  [<ffffffff8121146c>] vfs_getattr_nosec+0x2c/0x40
May  9 16:32:18 Zotac kernel: [  840.167873]  [<ffffffff81211686>] vfs_getattr+0x26/0x30
May  9 16:32:18 Zotac kernel: [  840.167880]  [<ffffffff812116c3>] vfs_fstat+0x33/0x60
May  9 16:32:18 Zotac kernel: [  840.167888]  [<ffffffff81211dc4>] SYSC_newfstat+0x24/0x60
May  9 16:32:18 Zotac kernel: [  840.167898]  [<ffffffff8106b554>] ? __do_page_fault+0x1b4/0x400
May  9 16:32:18 Zotac kernel: [  840.167907]  [<ffffffff81211e6e>] SyS_newfstat+0xe/0x10
May  9 16:32:18 Zotac kernel: [  840.167918]  [<ffffffff818252f2>] entry_SYSCALL_64_fastpath+0x16/0x71
May  9 16:32:12 Zotac gnome-session[2162]: message repeated 5 times: [ (nautilus:2317): Gtk-CRITICAL **: gtk_container_foreach: assertion 'GTK_IS_CONTAINER (container)' failed]
May  9 16:33:37 Zotac systemd[1]: Starting Cleanup of Temporary Directories...
May  9 16:33:37 Zotac systemd-tmpfiles[3819]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
May  9 16:33:37 Zotac systemd[1]: Started Cleanup of Temporary Directories.
May  9 16:34:28 Zotac kernel: [  970.541138] nfs: server 192.168.1.150 not responding, still trying
May  9 16:34:28 Zotac kernel: [  970.544158] nfs: server 192.168.1.150 OK
May  9 16:34:30 Zotac dbus[738]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
May  9 16:34:30 Zotac systemd[1]: Starting Hostname Service...
May  9 16:34:30 Zotac dbus[738]: [system] Successfully activated service 'org.freedesktop.hostname1'
May  9 16:34:30 Zotac systemd[1]: Started Hostname Service.
May  9 16:34:36 Zotac sm-notify[1375]: Unable to notify 192.168.1.150, giving up</code>

Just in case Ive messed things up here's is how the folder is being mounted in fstab : 
<code>
# mount ~/Plex folder from NAS box "Monolith" on to Zotac box
192.168.1.150:/mnt/HD/HD_a2/Plex                        /home/bill/Plex nfs     rw,hard,intr,user       0       0
</code>

<code>
bill@Zotac:~$ uname -a
Linux Zotac 4.4.0-22-generic #39-Ubuntu SMP Thu May 5 16:53:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
</code>

---

