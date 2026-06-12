---
title: "Boots into Recovery Menu"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by lbarnes on 2011-01-14
Ubuntu 10.10 64 is the only OS
Nvidia 9600M GT
Nvidia driver ver. 260.19.29

After updating to the latest 2.6.35.25 kernel my HP HDX-16 lapi boots into Recovery Menu only and I am forced to run startx to get to the graphical desktop. Any ideas??

---

### Post by garvinrick4 on 2011-01-14
What does 
```
gedit /etc/default/grub
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
##should look like above GRUB_DEFAULT=0
The 0 means first in line of menu entries, a 1 will mean second in line and so on and on.

To see your menuentries:
```
grep menuentry /boot/grub/grub.cfg
```

# to make changes:
```
gksudo gedit /etc/default/grub
```
make changes and save then:
```
sudo update-grub
```

---

### Post by lbarnes on 2011-01-14
Thanks for the tip, I had grub timed out so I never saw it. I uncommented the timeout and found that I only have 2.6.35.24 and 2.6.35.22 recovery modes and those 2 only.  However, this is my list in the terminal:
```
lennon@lennon-HP-HDX-16-Notebook-PC:~$ grep menuentry /boot/grub/grub.cfg
menuentry "Ubuntu, with Linux 2.6.35-24-generic" --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-22-generic" --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
lennon@lennon-HP-HDX-16-Notebook-PC:~$ 

```
I did update-grub, I don't know if this helps but here's the grub:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=>>1024x768-24<<,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=">>1024x768-24<<"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
Any ideas??

---

### Post by garvinrick4 on 2011-01-15
#Should be booting into 0 which is first in order:
2.6.35-24 is the default boot. 
#Are you booting into correct menu entry now?

---

### Post by trovador on 2011-01-16
Hi all, I've a similar problem, I can't boot my pc on graphic way only string or character (as you prefer).
So I can login by tty and after
> grep menuentry /boot/grub/grub.cfg

I don't have any file
What can I do ?
Thanks

---

