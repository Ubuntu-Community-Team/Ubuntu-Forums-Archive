---
title: "hueristics.broken.executable"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by letsgomudkip! on 2010-06-16
I ran a scan using klamav and 2 threats were detected 

1 /usr/lib/virtualbox/VBoxEFI32.fb
2 /usr/lib/virtualbox/VboxEFI64.fb

both say Hueristics.Broken.Executable
it wont let me quarantine them or do anything with them.
Does anyone know what I should do?

---

### Post by ankspo71 on 2010-06-16
Hi,
I'm not a antivirus for Linux expert, so I decided to install klamav to see what I can find out.

What I did find out, is that if anyone plans to scan system directories, then the user should run klamav as root, so they will be able to quarantine files from system directories as root.

```
kdesudo klamav
```

If you run the above command in the terminal (Konsole) you should have no problem quarantining the files.
Hope this helps.

PS. If you plan to continue scanning system directories, you can change your shortcut (or start menu entry) to the command "kdesudo klamav".

---

### Post by 3rdalbum on 2010-06-16
> **letsgomudkip! said:**
> I ran a scan using klamav and 2 threats were detected 

1 /usr/lib/virtualbox/VBoxEFI32.fb
2 /usr/lib/virtualbox/VboxEFI64.fb

both say Hueristics.Broken.Executable
it wont let me quarantine them or do anything with them.
Does anyone know what I should do?

Don't bother running anti-virus programs on your Linux system itself. Those anti-virus programs only look for Windows viruses, and ancient Linux viruses that are impossible to catch anymore.

The VBoxEFI files are perfectly safe. Even if you got a hypothetical Linux virus, that virus would need to gain root access to write to those files, and I'm sure it would put itself into a more important location than a part of Virtualbox that is almost never used.

---

### Post by letsgomudkip! on 2010-06-17
Thank you!

---

