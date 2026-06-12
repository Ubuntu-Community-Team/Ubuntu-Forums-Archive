---
title: "Is there any commmand to push the SWAP space into memory or vice-versa?"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by legolas_w on 2009-04-10
Hi
Thank you for reading my post.
Is there some command which let me push SWAP partition content into memory to speedup applications execution?
Also any command which let us force an specific application to move into SWAP space and free the memory for other applications?


Thanks.

---

### Post by spiderbatdad on 2009-04-10
you can tell the system to use more or less swap. For example to use swap only when no more ram is available or to use as much swap as possible. The setting is swappiness in /etc/sysctl.conf

```
vm.swappiness = 0
``` to 100 for maximum swap usage.

---

### Post by PukingPenguin on 2009-04-10
$free -m

$sudo sync; echo 3 >> /proc/sys/vm/drop_caches

$free -m

---

### Post by neu2buntu on 2009-04-10
are you sure this is the right file?....
```
you can tell the system to use more or less swap. For example to use swap only when no more ram is available or to use as much swap as possible. The setting is swappiness in /etc/sysctl.conf

     Code:
     vm.swappiness = 0 
 to 100 for maximum swap usage.
                                                                                               __________________
                :-({|= :guitar:
```


i can see you have a lot of knowledge ie num of posts,its just when i look at this file i see wifi settings...(using ubuntu 8.10)  its because im interested in how the whole swap thing works ,im not dissing anyone ... and i would like to know how to increase swap size also as i have upgraded ram on my acer aspire one....oooops i have stolen the post again,will have to stop doing this:lolflag::lolflag::lolflag:

---

### Post by spiderbatdad on 2009-04-10
Hi. well post count proves no great knowledge really, only that I have hung around awhile. Actually there are folks on here with very few posts, who can code circles around me, and know Ubuntu through and through.

 You can see all I know about swap here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
If you scroll down to performance tuning and how to change swappiness value...you'll see where I got my info.

---

### Post by neu2buntu on 2009-04-10
as i say dont get me wrong!!!,... and i know you know your stuff... im still a noob big time!! this is just what i see in your file. do remember that im using 8.10 and maybe the file structure is slightly different to yours... im just kind of hijacking this post (will stop having to do this...lol..)
   i could never code unless back in the 80's when i owned my amstrad ,that was different i was hacking into us military...lol...  but i do think that large num of posts shows knowledge,as im sure you have helped lots of people with ubuntu "stuff".... i do remember seeing a file on my comp about swappiness but cant rem where, seriously have a look at my file

```
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# This disables TCP Window Scaling ([http://lkml.org/lkml/2008/2/5/167](http://lkml.org/lkml/2008/2/5/167)),
# and is not recommended.
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net.ipv4.icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net.ipv4.icmp_ignore_bogus_error_responses = 1
# 
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#
# The contents of /proc/<pid>/maps and smaps files are only visible to 
# readers that are allowed to ptrace() the process
# sys.kernel.maps_protect = 1
```    this is where im coming from...????  what dist are you running ...jaunty??   i remember looking at the "swappiness" file in the past on 8.04 but cant rem where at!!!???:lolflag::confused:

---

### Post by neu2buntu on 2009-04-10
now im on a mission to find my "swappiness" as my ram is now equal to my swap and the recommended is double your ram (after my own ram upgrade on my aa1...took about an hour)...not really sure if swap matters so much but i like to stick to the rules...lol...actually what i should do is use "gparted" to increase my swap.....

---

### Post by lloyd_b on 2009-04-10
> **neu2buntu said:**
> now im on a mission to find my "swappiness" as my ram is now equal to my swap and the recommended is double your ram (after my own ram upgrade on my aa1...took about an hour)...not really sure if swap matters so much but i like to stick to the rules...lol...actually what i should do is use "gparted" to increase my swap.....
That "swap should be twice your RAM" rule is ancient and obsolete, as machines tend to have a lot more RAM than they used to.  For many modern systems, you can run completely without swap space and never notice the difference.

If yo're using a machine that you suspend to disk, then that old rule still applies.  Otherwise, swap = RAM is a pretty good rule to follow.

Lloyd B.

---

### Post by ibuclaw on 2009-04-10
To **push** memory in swap to RAM
```
sudo swapoff -a
```
**NOTE:** if you don't have enough RAM to hold the combined allocated memory in Swap+RAM, you system will fail with an "Out of Memory" error.

then you can set the swapiness level to a reason value, as noted above, then turn the swap partition back on:
```
sudo swapon -a
```

------------------------------------------------------------------------
To **free** up any dirty memory, run:
```
sudo sync
```
Although, this is generally not needed, as all data is flushed in a timely manner by default.

If you have an application that is consuming alot of memory (ie: Firefox, Pidgin) due to excessive memory leak, then the best thing to do is to close and reload the application in order to free up memory.

------------------------------------------------------------------------

Also, to speed up the loading of applications, you could use **readahead** to load the files into RAM before you start the app.
To do so, follow this tutorial: [http://ubuntuforums.org/showthread.php?t=565651&highlight=halve](http://ubuntuforums.org/showthread.php?t=565651&highlight=halve)

But, instead of stopping after login, open up your most commonly used applications too, and **then** stop the 'readahead-watch' daemon.

Regards
Iain

---

### Post by neu2buntu on 2009-04-10
thanks lloyd_b for your kind advice.... then i wont worry about my ram and swap being equal (acer aspire1) and i think the most swap i have seen used ["top" command in terminal"] was always very low anyway.

---

### Post by qwertyuiop96 on 2009-04-10
Uh-- this is going to sond SO dumb... what is SWAP anyway? :mrgreen:

---

### Post by ibuclaw on 2009-04-10
> **qwertyuiop96 said:**
> Uh-- this is going to sond SO dumb... what is SWAP anyway? :mrgreen:

'**Swap**' is the equivalent of a Paging File/Hiberfil.sys in Windows.

It is virtual memory kept on the Hard Drive, rather than in '**Cache**' (your RAM) in order to:
1) allow more active programs to run in RAM (faster access) while sleeping ones are kept in Swap (slower access).
2) To allow you to hibernate of your machine.
3) To allow large applications to run where lack of RAM will prevent you otherwise.

How it differs from the Windows Paging File is that Linux Swap is kept exclusively on a **separate partition**. It is also generally regarded that because of this, is one of the key reasons why the Linux filesystem is not easily fragmented.

Regards
Iain

---

### Post by neu2buntu on 2009-04-10
> How it differs from the Windows Paging File is that Linux Swap is kept exclusively on a **separate partition**. It is also generally regarded that because of this, is one of the key reasons why the Linux filesystem is not easily fragmented. is this why we dont need to defragment like as in windoze?   have noticed that ubuntu is always faster than "vista" and "xp" and the way ubuntu (linux in general) works its file system seems neater!!!  i have even noticed using "wine" for windows progs can leave a mess behind when you try to uninstall a program, the registry still needs cleaned ie it still has elements of the deleted program in there,,,,........just like windows it still follows the same behaviour.....

---

### Post by ibuclaw on 2009-04-11
> **neu2buntu said:**
> . is this why we dont need to defragment like as in windoze?   have noticed that ubuntu is always faster than "vista" and "xp" and the way ubuntu (linux in general) works its file system seems neater!!!  i have even noticed using "wine" for windows progs can leave a mess behind when you try to uninstall a program, the registry still needs cleaned ie it still has elements of the deleted program in there,,,,........just like windows it still follows the same behaviour.....

Well, it certainly contributes to the effort. A good filesystem will also help prevent fragmentation, and a separate /home partition will help too. But that doesn't mean that you can prevent fragmentation from happening.

A fully used disk/partition where you constantly append/truncate files through updates/upgrades and downloading/deleting GBs of files will indeed gradually become more sluggish as it wears on, regardless of what OS you use.

One reason why Ubuntu may be perceived at being faster is because Linux prefers to use cache (RAM) over Swap. Whereas in Windows, you will likely see a good 200MBs of data in the paging file, even if you have 2GBs of RAM in your machine.


With WINE, it is a pseudo emulated software layer to run Windows binaries, and the way most software is built, they assume that you will install the program again at a later date, so software leaves quite a few of its stored settings in the registry. So yes, some programs will most likely leave alot of itself behind after installation.

Regards
Iain

---

