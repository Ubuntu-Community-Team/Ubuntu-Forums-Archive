---
title: "Ubuntu 10.04 Problems (screen black out)"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by facemelter12 on 2010-06-26
I tried upgrading to Ubuntu 10.04 and I got a black screen once prompted to restart. Everytime I start my computer now it does the same thing: It goes through the normal Toshiba intro, then it starts the Ubuntu intro and then goes black right when it should start up and show my desktop. I tried burning it to a CD and booting from the CD but no dice. Any suggestions?
I have an older laptop, this could be the cause of my problems but I'm not sure why.
My computer:
Toshiba Tecra A1 (canadian laptop)
Pentium 4 2.2 GHz
RAM 1 GB

Its runs Ubuntu 9.10 just fine...

Whats the difference between Linux Lucid 10.04 and Ubuntu 10.04? Sorry I'm a newly converted alternate OS user...

---

### Post by anewguy on 2010-06-26
At the boot menu, follow the prompts so you can edit the boot information.  Add this in the line by the "quiet":

i915.modeset=1

Then follow the prompts on the screen to boot (F6?).

If this works, let us know.  It won't be permanent yet, but not knowing at this time what video adapter you have, just try this and see what happens.

Dave ;)

---

### Post by cuberts on 2010-06-27
> **facemelter12 said:**
> I tried upgrading to Ubuntu 10.04 and I got a black screen once prompted to restart. Everytime I start my computer now it does the same thing: It goes through the normal Toshiba intro, then it starts the Ubuntu intro and then goes black right when it should start up and show my desktop. I tried burning it to a CD and booting from the CD but no dice. Any suggestions?
I have an older laptop, this could be the cause of my problems but I'm not sure why.
My computer:
Toshiba Tecra A1 (canadian laptop)
Pentium 4 2.2 GHz
RAM 1 GB

Its runs Ubuntu 9.10 just fine...

Whats the difference between Linux Lucid 10.04 and Ubuntu 10.04? Sorry I'm a newly converted alternate OS user...During the boot up try accessing the CLI by doing Ctrl Alt F1. Can you access it?

---

### Post by facemelter12 on 2010-06-27
> **anewguy said:**
> At the boot menu, follow the prompts so you can edit the boot information.  Add this in the line by the "quiet":

i915.modeset=1

Then follow the prompts on the screen to boot (F6?).

If this works, let us know.  It won't be permanent yet, but not knowing at this time what video adapter you have, just try this and see what happens.

Dave ;)

Doing this allowed me to get to my desktop threw my disk, so then i tried reinstalling it from the disk but it still didn't work. I can get to my desktop everytime now but only if I put in your code and boot from a disk....

---

### Post by facemelter12 on 2010-06-27
> **cuberts said:**
> During the boot up try accessing the CLI by doing Ctrl Alt F1. Can you access it?

no, wouldn't let me

---

### Post by facemelter12 on 2010-06-27
Still having no luck, should I just go back to my ubuntu 9.10? or try Linux lucid? Is it any different from ubuntu 10.04??

---

### Post by shihkster1015 on 2010-06-27
did you do a clean install?

---

### Post by facemelter12 on 2010-06-28
> **shihkster1015 said:**
> did you do a clean install?

Yes, many times.

---

### Post by anewguy on 2010-06-30
If it works when you edit the boot line from the grub menu as I mentioned, then it's a matter of making the change permanent.  Right now it is only an on-the-fly change for a single boot.  I can't remember off the top of my head how to do it with grub 2, so I'll look for the instructions and post back.  Don't give up!

EDIT:  Okay, here's what I found:

- open a terminal window (applications/accessories/terminal)

- type:

cd /etc/default <press enter>

ls <press enter>  You should see a file called "grub" in the listing.

sudo gedit grub <press enter>

This will call up a text editor with the "grub" file opened.  Search for the boot string like you have been editing, and add the information I had you add at boot time.

Save the file and exit the editor.

sudo update-grub <press enter>

Now try rebooting and see how it goes.

Dave

---

### Post by facemelter12 on 2010-07-02
> **anewguy said:**
> If it works when you edit the boot line from the grub menu as I mentioned, then it's a matter of making the change permanent.  Right now it is only an on-the-fly change for a single boot.  I can't remember off the top of my head how to do it with grub 2, so I'll look for the instructions and post back.  Don't give up!

EDIT:  Okay, here's what I found:

- open a terminal window (applications/accessories/terminal)

- type:

cd /etc/default <press enter>

ls <press enter>  You should see a file called "grub" in the listing.

sudo gedit grub <press enter>

This will call up a text editor with the "grub" file opened.  Search for the boot string like you have been editing, and add the information I had you add at boot time.

Save the file and exit the editor.

sudo update-grub <press enter>

Now try rebooting and see how it goes.

Dave

When I tried to update the grub it responded with:
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

I have no idea what that means but I'm assuming it didn't work

---

### Post by facemelter12 on 2010-07-10
I haven't been able to fix the problem. So, I just switched back to Ubuntu 9.10. Running smoothly. I'll try again once a newer version comes out and hope for the best.

---

### Post by Baziboune on 2011-09-28
Hi, did you finally got more chance with a newer version of ubuntu?  I am also running and old version on a good old Tecra A1 and I am unable to install a newer version :(

Thank you

---

