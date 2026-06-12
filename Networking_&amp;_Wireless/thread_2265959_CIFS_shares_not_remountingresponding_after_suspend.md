---
title: "CIFS shares not remounting/responding after suspend, Xubuntu 14.10"
date: 2015-02-18
forum: Networking &amp; Wireless
---

### Post by MATilley on 2015-02-18
Hi All,

I recently updated from 14.04 to 14.10 on my laptop. After resuming from suspend, all works well but I cannot access these shares. If I attempt in the terminal, it is completely locked up and doesn't respond, requiring a kill.

I've looked in launchpad and didn't see anything for this issue. Below are both the wireless-info script, as requested, error trace from system logs, and my fstab file.

[ATTACH]260076[/ATTACH]

System logs:

```

[ 8405.153284] INFO: task xfce4-terminal:8367 blocked for more than 120 seconds.
[ 8405.153294]       Tainted: G           OE 3.16.0-30-generic #40-Ubuntu
[ 8405.153297] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8405.153301] xfce4-terminal  D ffff88021f2d3840     0  8367   2010 0x00000000
[ 8405.153310]  ffff8800a496f880 0000000000000082 ffff8800821d9e90 0000000000013840
[ 8405.153317]  ffff8800a496ffd8 0000000000013840 ffff8800821d9e90 ffff8800a7be9e20
[ 8405.153322]  ffff8800a7be9e24 ffff8800821d9e90 00000000ffffffff ffff8800a7be9e28
[ 8405.153328] Call Trace:
[ 8405.153343]  [<ffffffff81785a89>] schedule_preempt_disabled+0x29/0x70
[ 8405.153351]  [<ffffffff81788025>] __mutex_lock_slowpath+0xd5/0x1f0
[ 8405.153358]  [<ffffffff8178815f>] mutex_lock+0x1f/0x30
[ 8405.153372]  [<ffffffffc0a78399>] cifs_reconnect_tcon+0x169/0x2e0 [cifs]
[ 8405.153382]  [<ffffffffc0a785ca>] smb_init+0x2a/0x50 [cifs]
[ 8405.153395]  [<ffffffffc0a7e1ca>] CIFSSMBQPathInfo+0x5a/0x2b0 [cifs]
[ 8405.153414]  [<ffffffffc0aa29d7>] cifs_query_path_info+0x67/0x1a0 [cifs]
[ 8405.153423]  [<ffffffff81189e11>] ? zone_statistics+0x81/0xa0
[ 8405.153433]  [<ffffffff811c3419>] ? kmem_cache_alloc_trace+0x39/0x1e0
[ 8405.153450]  [<ffffffffc0a9489b>] ? cifs_get_inode_info+0x3cb/0x8a0 [cifs]
[ 8405.153465]  [<ffffffffc0a948f9>] cifs_get_inode_info+0x429/0x8a0 [cifs]
[ 8405.153473]  [<ffffffff811c3a29>] ? __kmalloc+0x169/0x260
[ 8405.153486]  [<ffffffffc0a89ae6>] ? build_path_from_dentry+0xb6/0x2c0 [cifs]
[ 8405.153499]  [<ffffffffc0a89b54>] ? build_path_from_dentry+0x124/0x2c0 [cifs]
[ 8405.153515]  [<ffffffffc0a968af>] cifs_revalidate_dentry_attr+0xef/0x1c0 [cifs]
[ 8405.153530]  [<ffffffffc0a969c3>] cifs_revalidate_dentry+0x13/0x30 [cifs]
[ 8405.153542]  [<ffffffffc0a89809>] cifs_d_revalidate+0x29/0xc0 [cifs]
[ 8405.153551]  [<ffffffff811ebcbe>] lookup_fast+0x25e/0x2e0
[ 8405.153557]  [<ffffffff811ef18d>] link_path_walk+0x1fd/0xf00
[ 8405.153564]  [<ffffffff81197793>] ? do_read_fault.isra.57+0xf3/0x300
[ 8405.153570]  [<ffffffff811efee7>] path_lookupat+0x57/0xd70
[ 8405.153577]  [<ffffffff811c2b05>] ? kmem_cache_alloc+0x35/0x1f0
[ 8405.153583]  [<ffffffff811f1bdb>] ? getname_flags+0x4b/0x180
[ 8405.153588]  [<ffffffff811f0c2a>] filename_lookup+0x2a/0xd0
[ 8405.153593]  [<ffffffff811f2ad4>] user_path_at_empty+0x54/0xb0
[ 8405.153601]  [<ffffffff81084893>] ? do_sigaction+0x73/0x230
[ 8405.153606]  [<ffffffff811f2b41>] user_path_at+0x11/0x20
[ 8405.153613]  [<ffffffff811df79f>] SyS_chdir+0x2f/0xc0
[ 8405.153622]  [<ffffffff8178c3e8>] ? page_fault+0x28/0x30
[ 8405.153629]  [<ffffffff8178a3ad>] system_call_fastpath+0x1a/0x1f

```

My /etc/fstab file is as follows:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/xubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=f7334eda-8806-4edc-bf1f-c0d407eb6208 /boot           ext2    defaults        0       
2
/dev/mapper/xubuntu--vg-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
//WINTERMUTE/Miscellany /home/matilley/wintermute/miscellany cifs credentials=/home/matill
ey/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0 
//WINTERMUTE/Readables /home/matilley/wintermute/readables cifs credentials=/home/matilley
/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0 

```

Any thoughts or help would be appreciated.

Thanks!
-MATilley

---

### Post by MATilley on 2015-02-19
I should state that I removed network manager and am using WICD instead.

---

### Post by djgrant on 2015-05-28
I have similar problems... Although I the shares are remounted after I resume. I do see a similar stack trace though. My main problem is that sometimes when I try to suspend, it doesn't actually suspend (I can tell because my laptop will be all hot the next time I open the lid). Stack trace is:

[142496.707975] Call Trace:
[142496.707986]  [<ffffffff8150da55>] ? schedule_preempt_disabled+0x25/0x70
[142496.707992]  [<ffffffff8150f503>] ? __mutex_lock_slowpath+0xd3/0x1c0
[142496.707998]  [<ffffffff8113f6e3>] ? mempool_alloc+0x53/0x150
[142496.708008]  [<ffffffff8150f60b>] ? mutex_lock+0x1b/0x2a
[142496.708023]  [<ffffffffa08b0cf8>] ? SendReceive+0x88/0x310 [cifs]
[142496.708032]  [<ffffffffa088f286>] ? CIFSSMBNegotiate+0x116/0x6a0 [cifs]
[142496.708042]  [<ffffffffa08b841a>] ? cifs_negotiate+0x3a/0x50 [cifs]
[142496.708052]  [<ffffffffa089dfbf>] ? cifs_negotiate_protocol+0x6f/0xd0 [cifs]
[142496.708059]  [<ffffffffa088eddd>] ? cifs_reconnect_tcon+0x15d/0x2e0 [cifs]
[142496.708067]  [<ffffffff811b1a64>] ? generic_permission+0x154/0x1c0
[142496.708074]  [<ffffffffa088eff5>] ? smb_init+0x25/0x80 [cifs]
[142496.708082]  [<ffffffffa08952ec>] ? CIFSSMBUnixQPathInfo+0x6c/0x2c0 [cifs]
[142496.708093]  [<ffffffffa08a9fde>] ? cifs_get_inode_info_unix+0x6e/0x1a0 [cifs]
[142496.708097]  [<ffffffff811b3573>] ? path_lookupat+0x73/0x780
[142496.708102]  [<ffffffff8114a3c5>] ? release_pages+0x85/0x220
[142496.708111]  [<ffffffffa089fe3e>] ? build_path_from_dentry+0xae/0x290 [cifs]
[142496.708121]  [<ffffffffa08ac128>] ? cifs_revalidate_dentry_attr+0xa8/0x1c0 [cifs]
[142496.708128]  [<ffffffff810eb46e>] ? from_kgid_munged+0xe/0x20
[142496.708133]  [<ffffffff811accaa>] ? cp_new_stat+0x13a/0x160
[142496.708141]  [<ffffffffa08ac2ef>] ? cifs_getattr+0x4f/0x120 [cifs]
[142496.708146]  [<ffffffff811ac867>] ? vfs_fstatat+0x57/0x90
[142496.708151]  [<ffffffff811accea>] ? SYSC_newstat+0x1a/0x40
[142496.708157]  [<ffffffff81510e4d>] ? system_call_fast_compare_end+0x10/0x15

---

