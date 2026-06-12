---
title: "PC won't switch off"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by Mike1962 on 2011-04-02
Hi,
After getting my sound card sorted yesterday I'm on a roll!!
My computer won't switch off when I want it to. It will suspend or hibernate but won't completely switch off.
It hangs on a page that seems to have a lot of commands on it. It did this under 10.04 and again now under 10.10
Any ideas?

Mike

---

### Post by bumanie on 2011-04-02
In terminal > sudo apt-get shutdown -h now

---

### Post by Mike1962 on 2011-04-04
> **bumanie said:**
>  In terminal  	Quote:
 	 	 		 			 				sudo apt-get shutdown -h now 			 	 	 	 

 		                   		  		  		 		 			
I tried that and got this on the terminal:

apt 0.8.3ubuntu7 for i386 compiled on Oct  5 2010 14:07:36
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   markauto - Mark the given packages as automatically installed
   unmarkauto - Mark the given packages as manually installed

Options:
  -h  This help text.
  -q  Log output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives can't be located
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.

---

### Post by matt_symes on 2011-04-04
Hi

I think there was a small typo i there. It should have been

```
sudo shutdown -h now
```

Kind regards

---

### Post by rosencrantz on 2011-04-04
Does that happen during regular shutdown, suspend/hibernate or all such operations?
Some recent hardware modules can cause trouble during suspend/hibernation, for example if you have USB3 support.
If you give us more details - when it happens and what's on your screen during shutdown (try either the output of 'dmesg' in a terminal or take a photo), we can maybe point you to some workarounds.
Cheers,
rosencrantz

---

### Post by Mike1962 on 2011-04-05
The computer hangs with this on the screen:

                                            [  576.15879] power down.ocessess
                                              _terminate
*All processess ended within 1 secons.....                                 [ok]
*Deconfiguring network interfaces.......                                     [ok]
*Deactivateing sway...........                                                     [ok]
*unmounting weak filesystems...............                                  [ok]


I've tried to lay it out on the screen as it looks. On the top line looks likep is missing from prosessess?
Also the underscore before the word terminate is flashing.


Thanks

---

### Post by Mike1962 on 2011-04-05
I forgot to mention.
It only does it on shutdown. Hibernate and Suspend are fine.

---

### Post by DaveMcC on 2011-04-05
> **Mike1962 said:**
> I forgot to mention.
It only does it on shutdown. Hibernate and Suspend are fine.

What happens when you pull the plug out?

Dave

---

### Post by matt_symes on 2011-04-05
Hi

Does this happen on reboot as well ?

```
sudo shutdown -r now
``` 

Kind regards

---

### Post by rosencrantz on 2011-04-05
There is not much literature concerning your particular problem, but I found one source ([http://askubuntu.com/questions/7114/why-cant-i-restart-shutdown](http://askubuntu.com/questions/7114/why-cant-i-restart-shutdown)) suggesting setting the reboot=b flag in grub. (You can also try other values)
> 
/* reboot=b[ios] | s[mp] | t[riple] | k[bd] | e[fi] [, [w]arm | [c]old] | p[ci]
   warm   Don't set the cold reboot flag
   cold   Set the cold reboot flag
   bios   Reboot by jumping through the BIOS (only for X86_32)
   smp    Reboot by executing reset on BSP or other CPU (only for X86_32)
   triple Force a triple fault (init)
   kbd    Use the keyboard controller. cold reset (default)
   acpi   Use the RESET_REG in the FADT
   efi    Use efi reset_system runtime service
   pci    Use the so-called "PCI reset register", CF9
   force  Avoid anything that could hang.
 */
You can set the flag with adding 'reboot=b' as described here:
> **sisco311 said:**
> Edit the /etc/default/grub file and add the kernel parameter to the **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** line, then run:
```
sudo update-grub
``` 
I have no idea whether this is going to work - if it messes up your grub, boot either into failsafe or edit your grub selection on the fly as described in the link below. After that, you can just reverse the changes to /etc/default/grub and update again.
[https://help.ubuntu.com/community/Grub2#Editing Menus During Boot](https://help.ubuntu.com/community/Grub2#Editing Menus During Boot)

---

### Post by matt_symes on 2011-04-06
Hi

Try this.

Press and hold the ALT and sysrq keys at the same time.  While these keys are pressed type

R E I S U O

Leave a couple of seconds between each keypress. This is known as the magic key combination.

Does that switch off your PC ?

Kind regards

---

### Post by Mike1962 on 2011-04-27
> **matt_symes said:**
> Hi

Try this.

Press and hold the ALT and sysrq keys at the same time.  While these keys are pressed type

R E I S U O

Leave a couple of seconds between each keypress. This is known as the magic key combination.

Does that switch off your PC ?

Kind regards

Sorry I've been away.
What is the sysrq key? (total novice!)

Thanks

---

### Post by wep940 on 2011-04-27
I would also suggest that you may want to edit the boot line temporarily and put ACPI=no and perhaps APIC=no (or is it NOAPIC).  For some hardware this was needed a few years ago to sort of bypass power options on shutdown and just force a power off on shutdown - without those the PC's used to just hang at shutdown like you have.  If it works, we can give you instructions for making it permanent.  This was common with some of the cheaper MB's and with older hardware.

---

### Post by diegoviola on 2011-06-07
it sounds like the same problem we have here:

[https://bugzilla.kernel.org/show_bug.cgi?id=33872](https://bugzilla.kernel.org/show_bug.cgi?id=33872)

please report problems there.

---

