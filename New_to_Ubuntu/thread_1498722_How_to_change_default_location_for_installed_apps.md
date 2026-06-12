---
title: "How to change default location for installed apps"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by Julia A on 2010-06-01
Hi

I'm struggling to find how I can change the location of applications that I download. I've got Ubuntu 10.04 loaded onto an EEE 900. As it has two ssds, I'd rather put any apps on the larger drive, and leave the smaller (4gb) drive just for Ubuntu and updates. Update Manager doesn't provide an option to change directory. 

I've been through all the settings for Ubunto (Gnome and netook remix) but can't find anything.I've also tried downloading various apps from Update Manager in the hope that one of them would provide for changing defaults. I can't believe its not possible!

If you can help please provide step by step instructions, as I'm very new to Linux

Thanks

---

### Post by -humanaut- on 2010-06-01
sudo apt-get -o=dir::forpackage install foo

---

### Post by Julia A on 2010-06-01
Thanks for this. I pasted it into a terminal, and had the message:

E: Option -o=dir::forpackage: Configuration item specification must have an =<val>.

Is this what you would expect? Can you advise what I need to do next?

---

### Post by formaldehyde_spoon on 2010-06-01
Perhaps this problem would be better solved by a line in fstab, if someone could tell Julia what mount point she should use for her second drive....

---

### Post by philinux on 2010-06-01
> **Julia A said:**
> Hi

I'm struggling to find how I can change the location of applications that I download. I've got Ubuntu 10.04 loaded onto an EEE 900. As it has two ssds, I'd rather put any apps on the larger drive, and leave the smaller (4gb) drive just for Ubuntu and updates. Update Manager doesn't provide an option to change directory. 

I've been through all the settings for Ubunto (Gnome and netook remix) but can't find anything.I've also tried downloading various apps from Update Manager in the hope that one of them would provide for changing defaults. I can't believe its not possible!

If you can help please provide step by step instructions, as I'm very new to Linux

Thanks

What's the size of the other ssd?

---

### Post by Julia A on 2010-06-01
The second ssd is 16GB. I guess I could put Ubuntu onto that drive; its just that when I bought the EEE the OS was on the smaller (4gb) drive, with the larger one for apps and files. Also I'm not sure whether the 16gb drive is slower than the other one.

---

