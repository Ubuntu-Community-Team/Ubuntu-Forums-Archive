---
title: "Hibernate/Resume Wifi Problem - Won't run resume scripts"
date: 2014-05-30
forum: Networking &amp; Wireless
---

### Post by peter-a on 2014-05-30
Hi all,

I'm running Ubuntu 14.04 on an Acer Travelmate 5720 laptop.

So I have the common problem of having no wifi following an otherwise successful hibernation.

I can easily solve the problem with either:

```
sudo service network-manager restart
```

or

```
sudo pkill wpa_supplicant
```

And I can run these either as-is in the terminal, or from inside a script in my home folder.

So the problem is this - I want to automatically run these commands when my laptop comes round from hibernation. I have placed variations on the following script within:

/etc/acpi/sleep.d
etc/pm/sleep.d
usr/lib/pm-utils/sleep.d
usr/lib/pm-utils/power.d

```
#!/bin/sh
case $1 in
suspend)
;;
resume)
sudo pkill wpa_supplicant
;;
hibernate)
;;
thaw)
sudo pkill wpa_supplicant
;;
esac

```

The scripts just won't run when my laptop resumes, and if I run them manually, all is fine.

The scripts are owned by root and executable.

Any ideas why these scripts won't run when my laptop wakes up?

---

### Post by djkmmo on 2014-08-10
Hi!

How have come to the conclusion that the script isn't being run during the resume process? Is it just a deduction from the fact that wifi doesn't work after resume, or have you gone through the logs?

Why are you using "sudo" within the script? The scripts that are run during resume are run by root.

You shouldn't be messing about with the scripts under usr/lib/pm-utils/sleep.d and usr/lib/pm-utils/power.d. These are system managed scripts and all your changes can be overwritten during e.g. updates.

---

