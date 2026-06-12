---
title: "Older non-ACPI system"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by djenner on 2008-12-03
I want to test ubuntu for a possible after-school program computer lab project.  The box I have in my study for this test is an old Intergraph TD225 with 256mb RAM and a 17gb hard disk available, running a PII processor.  This should be adequate hardware for the test, as I read the documentation, and I have installed linux (and earlier ubuntu variants) on that system without problems.

8.10, in both standard and alternative installation versions, seems to require ACPI by default; this mid-90s system does not have ACPI; I get the error 

[   0.044438] ACPI: Unable to load the system description tables

I have looked at the various option buttons, and I have searched for alternative (no acpi) installation instructions, and I cannot find them.  I need a cookbook solution (time is pressing, and this is a *pro bono* gig and it's end of semester and I am swamped).  Suggestions?

---

### Post by anewguy on 2008-12-03
> **djenner said:**
> I want to test ubuntu for a possible after-school program computer lab project.  The box I have in my study for this test is an old Intergraph TD225 with 256mb RAM and a 17gb hard disk available, running a PII processor.  This should be adequate hardware for the test, as I read the documentation, and I have installed linux (and earlier ubuntu variants) on that system without problems.

8.10, in both standard and alternative installation versions, seems to require ACPI by default; this mid-90s system does not have ACPI; I get the error 

[   0.044438] ACPI: Unable to load the system description tables

I have looked at the various option buttons, and I have searched for alternative (no acpi) installation instructions, and I cannot find them.  I need a cookbook solution (time is pressing, and this is a *pro bono* gig and it's end of semester and I am swamped).  Suggestions?

Just change your boot string to include the noapic option.  The following link details that:

[http://https://answers.launchpad.net/ubuntu/+question/1808]("http://https://answers.launchpad.net/ubuntu/+question/1808")


Dave ;)

---

### Post by djenner on 2008-12-03
> **anewguy said:**
> Just change your boot string to include the noapic option.  The following link details that:

[http://https://answers.launchpad.net/ubuntu/+question/1808]("http://https://answers.launchpad.net/ubuntu/+question/1808")


Dave ;)

Thanks, Dave.  I looked at that site [as given, with the initial "http://" dropped].  That appears to apply to a substantially earlier version of the software, when booting from a command line. It also natters on about editing boot files.  I am using a CD (inherently not editable). I am not connection to the command line. There is a process for invoking noapci or apci=off in the present (8.10) interface, but it is not clear.  

In short, this does not get me past that error message.  I really do mean it when I say I need the cookbook, push-this-then-that answer correct for this version.

---

### Post by jimrz on 2008-12-03
on the "live" cd when you get to the initial screen that it boots from hit "f6" (for boot options) then type in "noapic" (no quote marks). If it works out ok and you decide to install, you can then add "noapic" as a boot option to your /boot/grub/menu.lst and be good to go from then on.

---

### Post by djenner on 2008-12-04
> **jimrz said:**
> on the "live" cd when you get to the inital screen that it boots from hit "f6" (for boot options) then type in "noapic" (no quote marks). If it works out ok and you decide to install, you can then add "noapic" as a boot boot option to your /boot/grub/menu.lst and be good to go from then on.

Ah.  Yes, that worked.  I fiddled a bit more, found that hitting F6 twice actually gave me a list of options.  After a couple tries, it seems nolapci (I think that's it) is the required command.  Old system, indeed.  Thanks, that was exactly the needed guidance.

---

### Post by djenner on 2008-12-04
> **djenner said:**
> Ah.  Yes, that worked.  I fiddled a bit more, found that hitting F6 twice actually gave me a list of options.  After a couple tries, it seems nolapci (I think that's it) is the required command.  Old system, indeed.  Thanks, that was exactly the needed guidance.

Hmn. That did get the installation done. When going to boot, however, I am clearly not plugging in "nolacpi" in the right place. Following the guidance in the earlier note's ref'd URL, I ESC'd to get to the GRUB editor, edited the standard bootup option by hitting "e", then selecting the "kernel" line, added "nolacpi" to the end of that line.  The system stopped with the same "ACPI: unable to load message".  Tried inserting the command at other places; same result.  I get the starting up message, then the system halts.

I'll keep fiddling, because now I am a bit pissed off, and I really would appreciate further guidance.  [I know, the best guidance is, get a newer box; under consideration.]

---

### Post by anewguy on 2008-12-04
As I mentioned earlier, and others have givin you guidance on, you need to edit the /boot/grub/menu.lst file (if you're a noobie, don't be intimidated ;) ) :

in a terminal window:

cd /boot/grub

sudo gedit menu.lst (just enter your regular password)

find the line that is not commented out that is for the normal boot of your system and add the noapic or what ever string you determined worked.

save the file, close the editor, close your terminal window and reboot.

Dave ;)

---

### Post by djenner on 2008-12-05
> **anewguy said:**
> As I mentioned earlier, and others have givin you guidance on, you need to edit the /boot/grub/menu.lst file (if you're a noobie, don't be intimidated ;) ) :

in a terminal window:

cd /boot/grub

sudo gedit menu.lst (just enter your regular password)

find the line that is not commented out that is for the normal boot of your system and add the noapic or what ever string you determined worked.

save the file, close the editor, close your terminal window and reboot.

Dave ;)

Dave, perhaps you're not thinking clearly here?  

The problem is not editing the grub file -- yet.  The problem is booting.  This Linux variant assumes a manufacturer-provided (hence, one assumes burned into ROM) table listing the basic hardware system.  This table is apparently consulted at boot-up, and if the table isn't there, the system stops unless an alternative has been specified. We know this is so because there are a half-dozen boot-time switched available in the installer (at installation time, F6, F6), three of which have to do with bypassing that ACPI table.

That got the system installed.  To boot, that same alternative (in this case, "nolacpi") has to be passed to the kernel at boot-time.  That has to be done at least once manually.  _*Until one boots into the system, one cannot edit the grub file*_, as you rightly suggest should be one.

In short, Dave, you have set up a very nice Catch 22, without benefit of Kurt Vonnegut.  If you have had this problem, then you know where the "nolacpi" instruction goes; if not have not had the problem, then perhaps you need to think about the matter more carefully?

Anent "newbie": Absolutely.  I stopped mucking around with Unix about a quarter-century ago, when I realized (I had other things to do than putz around with user-hostile OS installations.  Linux has inherited both the user-hostile character and the successful-user/techie arrogance that killed Unix.  That is too bad; all the evidence suggests that a solid off-the-shelf, plug-and-play alternative to Windows would be a good thing.  I note in passing, this is a generally held sentiment; people buy Apples and even Vista-OS'd systems because they don't have to deal with manually turning on a switch that a little bit of conditional coding could fix.  It is something Microsoft well understands; do you think they cooperate with cheap-computers-for-kiddies programs because they like the idea of giving product away at a lower price?

---

### Post by niteshifter on 2008-12-05
> **djenner said:**
> Hmn. That did get the installation done. When going to boot, however, I am clearly not plugging in "nolacpi" in the right place. Following the guidance in the earlier note's ref'd URL, I ESC'd to get to the GRUB editor, edited the standard bootup option by hitting "e", then selecting the "kernel" line, added "nolacpi" to the end of that line.  The system stopped with the same "ACPI: unable to load message".  Tried inserting the command at other places; same result.  I get the starting up message, then the system halts.

I'll keep fiddling, because now I am a bit pissed off, and I really would appreciate further guidance.  [I know, the best guidance is, get a newer box; under consideration.]

Humor us, please. Try the above again with noacpi (on GRUB's kernel line). If that doesn't work try both noacpi and acpi=off.

---

### Post by djenner on 2008-12-05
> **niteshifter said:**
> Humor us, please. Try the above again with noacpi (on GRUB's kernel line). If that doesn't work try both noacpi and acpi=off.

I would be glad to muck with the ACPI, will in fact do so. The table thing is a pain.  But the issue, as I have just found out (more extensive googling...) is APIC, which is a different thing altogether.  Appending ***nolapic*** (no local advanced programmable interrupt controllers) to the kernel line got me booted.

What is annoying: I am old enough to remember when Intel developed APIC (as I recall, an improvement on the original IBM PIC specification).  I should have twigged to the problem sooner; in partial mitigation, the stop-message is ACPI, not APIC, so....

I suspect I will have to go looking at that system's ancient (documentation long lost) BIOS.  Ihe Intergraph boxes were really nice -- proverbial brick outhouse quality -- and I really would not replace it with a current commodity box.

---

### Post by anewguy on 2008-12-05
> **djenner said:**
> Dave, perhaps you're not thinking clearly here?  

The problem is not editing the grub file -- yet.  The problem is booting.  This Linux variant assumes a manufacturer-provided (hence, one assumes burned into ROM) table listing the basic hardware system.  This table is apparently consulted at boot-up, and if the table isn't there, the system stops unless an alternative has been specified. We know this is so because there are a half-dozen boot-time switched available in the installer (at installation time, F6, F6), three of which have to do with bypassing that ACPI table.

That got the system installed.  To boot, that same alternative (in this case, "nolacpi") has to be passed to the kernel at boot-time.  That has to be done at least once manually.  _*Until one boots into the system, one cannot edit the grub file*_, as you rightly suggest should be one.

In short, Dave, you have set up a very nice Catch 22, without benefit of Kurt Vonnegut.  If you have had this problem, then you know where the "nolacpi" instruction goes; if not have not had the problem, then perhaps you need to think about the matter more carefully?

Anent "newbie": Absolutely.  I stopped mucking around with Unix about a quarter-century ago, when I realized (I had other things to do than putz around with user-hostile OS installations.  Linux has inherited both the user-hostile character and the successful-user/techie arrogance that killed Unix.  That is too bad; all the evidence suggests that a solid off-the-shelf, plug-and-play alternative to Windows would be a good thing.  I note in passing, this is a generally held sentiment; people buy Apples and even Vista-OS'd systems because they don't have to deal with manually turning on a switch that a little bit of conditional coding could fix.  It is something Microsoft well understands; do you think they cooperate with cheap-computers-for-kiddies programs because they like the idea of giving product away at a lower price?

As an ex-systems programmer and ex-systems admin for 23+ years on large scale, medium, mini and micro computers, I understand quite well what you are going through - and yes, I *HAVE* been there.  I made my comments base on your original reply that stated you were able to boot using F6 and adding your parameter to the boot line.  Any fool knows if you can't boot you can't edit the file, so forgive me if I feel a little insulted.  I was trying to give you help based upon your response that you were able to boot using F6 - this would not change on the first boot of an installed system until you actually got in and could modify the file.

dave ;)

---

