---
title: "I cant initiate linux"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by prime_arch on 2009-10-07
A few days ago i had to reinstall vista because a few things weren't working properly.
when the computer started back up i didn't get the option to start either linux or vista it just booted vista. i haven't bin able to get back in to my linux partition. what should i do?

---

### Post by yanceypd on 2009-10-07
If you used a system DVD the Vista install probably erased Ubuntu.   Is this what you did?:confused:

---

### Post by prime_arch on 2009-10-07
the install shouldn't have done anything to the linux partition in fact when i put in my linux cd i can get in to the linux partition and everything is there. I just cant run linux from my hard drive.

---

### Post by Windows Nerd on 2009-10-07
Microsoft just doesn't like Grub, your bootloader. So if you did a complete reinstall of Vista, it likely reconfigured the MBR (Master Boot Record) that Grub had worked its way around. You will probably have to reinstall Grub.

For an easy to follow guide go here:
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes)


Scott

---

### Post by prime_arch on 2009-10-08
thanks for the help.:)

---

### Post by Windows Nerd on 2009-10-08
Welcome

---

