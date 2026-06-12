---
title: "Source code check box in Software Sources dialog"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by men28 on 2008-12-07
What does it mean?

When I choose from the System menu:
```
System->Administration->Software Sources
```

there is a check box named "Source code" in this dialog.
What is this?

Thank you for help.

---

### Post by lovelyvik293 on 2008-12-07
ASynaptic download the .deb files only without the software source option.But when you check this, synaptic download the software source code also.

---

### Post by men28 on 2008-12-07
Where I can find the source code? In which directory?

---

### Post by lovelyvik293 on 2008-12-07
All the downloaded packages are kept in
```
/var/cache/apt/archives
```

---

### Post by men28 on 2008-12-07
I see in this directory a lot of .deb package files.
And where is the source code?

---

### Post by b0b138 on 2008-12-07
The source is download seperatly. When that box is checked, you can download with "sudo apt-get source packagename" (notice source instead of install) I believe it saves to your home folder.

---

