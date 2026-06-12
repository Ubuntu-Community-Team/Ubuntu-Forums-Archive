---
title: "Realtek 8168 issues.. help me understand DKMS, etc"
date: 2022-04-05
forum: Networking &amp; Wireless
---

### Post by zim2dive on 2022-04-05
I recently did a clean install of Ubuntu Mate 20.04.

I have an Asrock Z68 Pro3 mobo, and wired Ethernet was fine initially .. until some kernel updates were installed (and I'm starting to get in beyond my experience level as a decade-plus but non-guru Ubuntu user)

FWIW, this same mobo networking was working all the way back to 11.04(?).. so this isn't a NEW chipset issue (which most of the r8168 vs. r8169 articles seem to imply).  I've also update BIOS and enabled LAN boot as some articles suggest, but no improvement.

I have the following kernels installed

```
>grep menuentry /boot/grub/grub.cfg | grep -v recove | grep advanced
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-71da56a8-e85b-483a-9c18-bf21cbd0fc12' {
	menuentry 'Ubuntu, with Linux 5.13.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.13.0-39-generic-advanced-71da56a8-e85b-483a-9c18-bf21cbd0fc12' {
	menuentry 'Ubuntu, with Linux 5.13.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.13.0-37-generic-advanced-71da56a8-e85b-483a-9c18-bf21cbd0fc12' {
	menuentry 'Ubuntu, with Linux 5.4.0-107-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.4.0-107-generic-advanced-71da56a8-e85b-483a-9c18-bf21cbd0fc12' {
	menuentry 'Ubuntu, with Linux 5.4.0-105-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.4.0-105-generic-advanced-71da56a8-e85b-483a-9c18-bf21cbd0fc12' {
```

Networking is good with 5.4.x, but totally broken with 5.13, to the point that I can't even use a USB wireless dongle with 5.13, nor a PCIe-NIC.... ie. all of networking seems to get knocked out, not just the Mobo LAN.

Searching for this, it looks like one fixes this by installing/updating drivers.

I'm a total newb to DKMS... reading what I can find online, it seems that one installs r8168 only when the built-in(?) r8169 doesn't work... I did NOT install r8168, it seems to have come with my Ubuntu-Mate install ??

```
>dkms status
nvidia, 470.103.01, 5.4.0-105-generic, x86_64: installed
nvidia, 470.103.01, 5.4.0-107-generic, x86_64: installed
r8168, 8.048.00, 5.4.0-105-generic, x86_64: installed
r8168, 8.048.00, 5.4.0-107-generic, x86_64: installed
```

I've seen articles about updating that DKMS version to r8168-8.049.02 but before I touch anything I wanted to understand several things

a) how did I end up with r8168?  Did the 20.04 install auto-detect there would be an issue with r8169?
b) am I better off trying to install a newer DKMS which might survive in to the 5.13 kernels?
c) do I just remove r8168 and see if r8169 works? (ie. the fact that the 20.04 installed r8168 makes me worry it will not)

I've also seen articles about blacklisting/etc and un-installing various drivers, but not so much as how to re-install.   But when if fails ALL networking options seem to fail ... so that makes recovery a challenge.. I can't just easy apt-get install my way out of things.  (other than perhaps purchasing an USB based networking interface).  So I want to have a firm plan on how to recover.

FWIW, I am trying to learn here and I'm holding back on other questions until I understand these initial questions.  Appreciate any pointers so I can educate myself.

thanks
Mike

---

### Post by chili555 on 2022-04-11
> I did NOT install r8168, it seems to have come with my Ubuntu-Mate install ??

It does not, as far as I’m aware, come by default in any Ubuntu version. I suspect that, at installation, you were asked if you wanted driver updates or some such and answered by ticking a box and it was installed.

If you are running kernel version 5.13-xx and you only have r8168 installed on 5.4-xx as you said:

> >dkms status
nvidia, 470.103.01, 5.4.0-105-generic, x86_64: installed
nvidia, 470.103.01, 5.4.0-107-generic, x86_64: installed
r8168, 8.048.00, 5.4.0-105-generic, x86_64: installed
r8168, 8.048.00, 5.4.0-107-generic, x86_64: installed

...then removing it will do nothing for your currently running 5.13-xx kernel.

It seems fairly clear to me that if networking was working under 5.4-xx where r8168 is installed and is* not *working under 5.13-xx where r8168 is *not *installed, then the first thing I’d suggest is:

```
sudo apt update
sudo apt install r8168-dkms

```
Reboot.

---

### Post by kevdog on 2022-04-14
You have a few kernels right?  dkms basically places a kernel module inside the selected when building the initramfs.  I'm fairly certain if you keep a backup kernel with r8168 previously built in -- that removing a module will only effect the running kernel and not the backup kernel.  Perhaps I'm wrong about this fact.

---

### Post by chili555 on 2022-04-14
> **kevdog said:**
> You have a few kernels right?  dkms basically places a kernel module inside the selected when building the initramfs.  I'm fairly certain if you keep a backup kernel with r8168 previously built in -- that removing a module will only effect the running kernel and not the backup kernel.  Perhaps I'm wrong about this fact.It depends.

If the module was installed from the r8168-dkms package in the repositories, the uninstalling it will remove it from all installed kernels.

If, on the other hand, you downloaded the source code and installed it with sudo dkms install, then the module is built only for the running kernel and then for subsequent kernels as they are added, typically by Update Manager. After that, one may remove the module for any kernel only, including the running kernel, with:

```
sudo dkms remove <module/version> -k <kernel/arch>

```
Or for all kernels currently installed:

```
sudo dkms remove <module/version> --all
```So far, we haven't enough information to tell which is the case here.

So, it depends.

---

