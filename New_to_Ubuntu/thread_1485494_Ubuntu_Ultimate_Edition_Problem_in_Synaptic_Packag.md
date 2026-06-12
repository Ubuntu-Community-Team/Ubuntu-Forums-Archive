---
title: "Ubuntu Ultimate Edition Problem in Synaptic Package Manager"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by nitin_ramachandran on 2010-05-16
Hi,
I recently installed the Ubuntu Ultimate edition on my system which has a core 2duo and 2 gb ram. The look and feel is awesome. but, while trying to update my softwares and other third party softwares, (eg: Nvidia graphic card softwares) I am not being able to open the synaptic package manager. instead, an error is being shown :
E: Syntax error /etc/apt/apt.conf.d/00trustcdrom:2: Extra junk at end of file

Can anyone please help me on the above issue..?

Thanks in advance:)

---

### Post by mac9416 on 2010-05-16
Hi there!

I belive you can safely remove that file without causing any trouble. Try these commands.

```
$ sudo cp /etc/apt/apt.conf.d/00trustcdrom:2 ~/00trustcdrom:2  # This backs the strange file up to your home directory.
$ sudo rm /etc/apt/apt.conf.d/00trustcdrom:2  # This deletes the file.
```

Then try opening Synaptic again.

The folks on the Ultimate Edition forum would have a better idea what that file is for, but my guess is tha if you aren't installing software off a CD, it isn't necessary.

---

### Post by nitin_ramachandran on 2010-05-17
Thank you very much mate. Its working just fine..!:)

---

