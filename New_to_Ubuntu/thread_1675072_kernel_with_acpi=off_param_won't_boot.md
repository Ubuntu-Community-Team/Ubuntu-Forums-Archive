---
title: "kernel with acpi=off param won't boot"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by EntropyReduction on 2011-01-24
I'm a linux newbie.   I have a problem with intermittent freezes on 
a acer aspire 5101AWLMi, kernel 2.6.35-22 and 2.6.35-23.  

I'm working through possible causes.  I'll do a full report n freezes in another post: suffice to say now it's probably not an X-freeze or overheating.

I've found posts that suggest acpi could be culprit, so on grub boot menu I've edited kernel line, added "acpi=off noacpi" or "acpi=off".  For both above kernels, after hitting ctrl-X system pauses for a while, then comes back with 

"giving up waiting for root device" 
Alert 
/dev/disk/by-uuid 00ad768f-79cf-...... (the Hard Drive Number continues) 
does not exist. Dropping to shell

Any way to persuade system to boot without acpi (again, for testing purposes only, for now)?

---

### Post by dileepm on 2011-01-25
Sorry I little understood your problem may be this would help you

[> http://starksolutions.blogspot.com/2010/05/acer-touchpad-screen-brightness-issue.html]("http://starksolutions.blogspot.com/2010/05/acer-touchpad-screen-brightness-issue.html")

---

### Post by verymadpip on 2011-01-25
EntropyReduction;

I don't think 10.10 has a grub "menu.lst" file as it uses grub 2.

If acpi=off, etc. are not working you could try "nomodeset".  I've seen that recommended.
  
I'm a newb myself, so that's about the most help I can offer.

P.S. I've had some trouble installing & booting an OS myself recently (that's another story) &  acpi=off was the only thing that worked.  It wasn't much use though, as  it disabled my laptop battery charge indicator.

---

### Post by smudgy on 2011-01-25
> **verymadpip said:**
> EntropyReduction;

I don't think 10.10 has a grub "menu.lst" file as it uses grub 2.

If acpi=off, etc. are not working you could try "nomodeset".  I've seen that recommended.
  
I'm a newb myself, so that's about the most help I can offer.

P.S. I've had some trouble installing & booting an OS myself recently (that's another story) &  acpi=off was the only thing that worked.  It wasn't much use though, as  it disabled my laptop battery charge indicator.

Try nomodeset at the grub2 menu you have to edit. (I haven;t found out how to make it permanent yet..)

Also noacpi I have found more useful than acpi=off and I use noacpi in addition to pci=noacpi successfully.

Screen brightness in linux i don;t know if it is possible...

---

### Post by Bucky Ball on 2011-01-25
Make the changes permanent in /etc/default/grub. BUT, try editing the line at boot first to see if it works. You don't want to make it permanent if it doesn't, obviously, or you could find yourself in more of a world of s**t. ;)

Here's a bit of mine. The line I added is in bold:

```
GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="5"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
**GRUB_CMDLINE_LINUX="acpi=copy_dsdt"**
```In a fresh install that line would probably read:

```
GRUB_CMDLINE_LINUX=""
```Add your bit between the quotation marks. For instance, yours might look like this:

```
GRUB_CMDLINE_LINUX="nomodset"
```

You will need to run:

```
sudo update-grub
```

... once you make the changes to make it stick on reboot. Good luck.

---

### Post by smudgy on 2011-01-25
> **Bucky Ball said:**
> Make the changes permanent in /etc/default/grub. 

Here's a bit of mine. The line I added is in bold:

```
GRUB_CMDLINE_LINUX="nomodset"
```You will need to run:

```
sudo update-grub
```... once you make the changes to make it stick on reboot. Good luck.

Thanks Bucky, it worked a treat. Added parameters for nomodeset xdriver=radeon etc

Now all I have to figure out is how to use traditional ifup instead of  Network Manager... Until then I can't use suspend/hibernate without  rebooting Ubuntu ...  I know from openSUSE that using traditional ifup  works and all I have to do there is ifdown then ifup with a couple of  launchers and then my internet is back. But in Ubuntu its not obvious  how to do the same thing (suse have a yast tool with the same name as  network tools but with functionality to effect change to traditional  ifup and dismantle Network Managers grip on the network.

Any ideas welcome  ;)

(Then if I get there the icing on the cake would be to know how to add   similar hooks to the suspend and resume scripts to execute sudo   /sbin/ifdown eth0 and the reverse for resume).

.

---

