---
title: "wired internet connection help"
date: 2020-01-20
forum: Networking &amp; Wireless
---

### Post by garyed on 2020-01-20
I've been running Ubuntu 18.04 LTS on my desktop plugged into my router with an ethernet cable with no problems until I changed my wireless router to a TP-Link AC1750. 
I'm running a dual boot sysytem & I can connect to the internet fine if i boot into Windows but not if I boot into Ubuntu. I've been running this setup for a few years now & everything has been working fine until i changed the router that i plug into. I even tried another older dual boot desktop that does exactly the same thing. It connects to the internet fine through Windows but not with Ubuntu. I have plenty of other stuff plugged into the same router & everything else works fine. I've tried rebooting the router & the desktop several times with no success.  
Any ideas?

---

### Post by howefield on 2020-01-20
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by garyed on 2020-01-20
A little update;
I forgot that I had my /etc/network/interfaces file set up for static ip & the new router default gateway is 192.168.0.1 where the other one was 192.168.1.1 
I changed the name of my interfaces file & rebooted with no interfaces file & it connected fine to the internet. 
Now its a matter of how to edit the interface file & keep it static.  Here is the interfaces file that used to work with my old router:
```
auto eno1
iface eno1 inet static
address 192.168.1.133
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.4.4 8.8.8.8

```
I changed the ......1.133 to .0.133 &  .1.1 to .0.1 but it still doesn't work. The only way I can get internet on Ubuntu so far is by having no interfaces file.

---

### Post by pcfan1234 on 2020-01-22
18.04 uses Netplan, not the interfaces file with ifupdown.
You can disable Netplan to use the interfaces file with ifupdown.
I recommend using the NetworkManager or set up Netplan. I do not recommend disabling Netplan.
EDIT:
Show the output of 
```

cat /etc/default/grub
ls -la /etc/netplan

```

---

### Post by garyed on 2020-01-27
> **pcfan1234 said:**
> 18.04 uses Netplan, not the interfaces file with ifupdown.
You can disable Netplan to use the interfaces file with ifupdown.
I recommend using the NetworkManager or set up Netplan. I do not recommend disabling Netplan.
EDIT:
Show the output of 
```

cat /etc/default/grub
ls -la /etc/netplan

```

I'm sorry for not replying but I subscribed to this thread & never received a notice of your reply. I just did a double check & found your response.
Anyways here are the outputs of the commands:
> 
~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_BACKGROUND="/home/gary/Pictures/coco.png"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
****************************************************************
~$ ls -la /etc/netplan
total 16
drwxr-xr-x   2 root root  4096 Jul  5  2018 .
drwxr-xr-x 161 root root 12288 Jan 24 14:19 ..
 



---

### Post by garyed on 2020-01-28
I tried ```
sudo netplan generate
``` & still no files in the net plan directory. 
I tried  ```

sudo apt install netplan 
sudo netplan generate

```  & no change
I then tried I tried  ```

sudo apt install netplan.io
sudo netplan generate

```  & no change either, just an empty directory

---

