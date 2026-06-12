---
title: "Help editing /etc/default/grub/"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by MarkFrancis905 on 2011-05-10
Hello all,
 
I am trying to get my newly installed 11.04 to boot past an issue with a black screen and I am unable to follow some instructions, please could some one show me how.
 
The instructions are "**Finally, it looks like acpi is mucking things up with the latest kernel for me: The options "ro acpi=off nosplash text" can consistently get me booted to a terminal. Then from the terminal "sudo service start gdm" gets to the gdm logon screen. On the logon screen I must choose "classic (no effects)" and then I can get to gnome."  ([http://ubuntuforums.org/showpost.php?p=10751479&postcount=23](http://ubuntuforums.org/showpost.php?p=10751479&postcount=23))**
 
I am able to get to a tty terminal and the grub command line but that is it. Can you advice on how I can edit the /etc/default/grub which is aparenltly what I need to do.
 
Thanks in advanced.

---

### Post by nothingspecial on 2011-05-10
```
sudo nano /etc/default/grub
```

When you are done press Ctrl-O to save then Ctrl-X to exit.

Then ```
sudo update-grub
```

---

### Post by MarkFrancis905 on 2011-05-10
> **nothingspecial said:**
> ```
sudo nano /etc/default/grub
```
 
When you are done press Ctrl-O to save then Ctrl-X to exit.
 
Then ```
sudo update-grub
```
 
Thank you for the help but this has not seemed to fix my issue. If you could help me follow the specific instructions id apriceate it. Basicly I have added to the bottom of the grub file "ro acpi=off nosplash text" but nothing seems to have changed. Do you understand the instructions better than I do?

---

### Post by compmodder26 on 2011-05-10
My /etc/default/grub file has this line in it:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Look for that line.  It may not have "quiet splash" in it.  But either way replace "quiet splash" (or whatever yours says) with "ro acpi=off nosplash text"

---

### Post by MarkFrancis905 on 2011-05-10
> **compmodder26 said:**
> My /etc/default/grub file has this line in it:
 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
 
Look for that line. It may not have "quiet splash" in it. But either way replace "quiet splash" (or whatever yours says) with "ro acpi=off nosplash text"
 
Thanks for the help I made the changes above but get no diffrence when I boot. Should I expect to now boot into a terminal? I can access the recovery mode from the GRUB menu and can get into the option "root - Drop to a root shell prompt" is that what I need to be in to follow these instructions?
 
Would this be better asked in the above thread? That thread seems far too advanced for my level of linux expirence.

---

### Post by compmodder26 on 2011-05-10
After editing the file did you run the following?

```
sudo update-grub
```

---

### Post by mikewhatever on 2011-05-10
In your case, the line should look as follows after editing:
```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=off nosplash text"
```

Don't forget to save and exit with ctrl-o and ctrl-x.

When done, run **sudo update-grub**, and then **sudo reboot**.

---

### Post by MarkFrancis905 on 2011-05-10
> **compmodder26 said:**
> After editing the file did you run the following?
 
```
sudo update-grub
```
 
The following comes up when I try to run the above command: "/etc/default/grub : 36: nosplash: not found"

---

### Post by mikewhatever on 2011-05-11
Have you tried omitting nosplash?

---

### Post by MarkFrancis905 on 2011-05-11
> **mikewhatever said:**
> Have you tried omitting nosplash?
 
Yes with no luck. Seeing as how my latest error seems to be having little replys I have chossen to compleatly downgrade to 10.04 untill I can find a solution. Thank you for you help though.

---

