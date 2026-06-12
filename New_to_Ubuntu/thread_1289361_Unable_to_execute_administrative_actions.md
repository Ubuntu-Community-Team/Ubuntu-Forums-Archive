---
title: "Unable to execute administrative actions"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by therudnick on 2009-10-12
Hi all,

I'm very new at Ubuntu, but I've been having trouble running Synaptic (or any other administrative program, for that matter).

I've also been unable to enter the GRUB menu to edit the Sudoers file.

Just a little extra info, I'm running Ubuntu 9.04 on PPC.

Any help would be greatly appreciated.

---

### Post by HarrisonNapper on 2009-10-12
First of all, make sure you read up on running Ubuntu on a PPC, as it will be a bit different.

Other than that, boot into recovery mode and adduser username admin and that should get you set up with a fresh admin user. That's generally the easiest way to go about it.

---

### Post by therudnick on 2009-10-12
I've booted into Rescue mode, and on the Ubuntu installer main menu I selected "Set up users and passwords"

When I enter "admin" as the username for the new account, it tells me "The username you entered (admin) is reserved for use by the system. Please select a different one."

Where should I go from here?

---

### Post by therudnick on 2009-10-12
Also, my first user doesn't have root privelages. The error message shows up that "spencer isn't in the sudoers file"

---

### Post by nothingspecial on 2009-10-12
You need to boot into the recovery root shell and issue the command

```
adduser *[COLOR="Red"]username[/COLOR]* admin
```

change username to your real username.

---

### Post by therudnick on 2009-10-12
Sorry, I'm very new at this and I don't exactly know what I'm doing. Could you provide steps please? I'm unsure of how to boot into recovery mode...

---

