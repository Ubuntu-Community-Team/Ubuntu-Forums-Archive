---
title: "software location on disk"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by avneravner on 2010-12-23
hello,

i've installed a new software on my ubuntu, i can use it and access it but i can't find where it is located on the disk. i want to check its size and location but even th search option doesn't show anything but the shortcuts which size is only a few kb.

please help/

avner

---

### Post by cariboo on 2010-12-23
In most cases the executable itself is located in /usr/bin, this doesn't include any libraries also installed. I found a good way to find out what is installed with a program, is to go to System-> Administration-> Synaptic Package Manager, search for the package, click the properties button, and then the installed files tab, to get a listing of what is installed where.

---

### Post by JRV on 2010-12-24
> **avneravner said:**
> hello,

i've installed a new software on my ubuntu, i can use it and access it but i can't find where it is located on the disk. i want to check its size and location but even th search option doesn't show anything but the shortcuts which size is only a few kb.

please help/

avner

Open a terminal and use the which command.

Example; to find firefox:
```

jim@test:~$ which firefox
/usr/bin/firefox
jim@test:~$ 

```

---

### Post by avneravner on 2010-12-25
cool, thanks!

---

### Post by kgarbutt on 2010-12-25
You can also use locate to find it. Open the terminal and type:

locate firefox

---

### Post by gmargo on 2010-12-25
Use the **dpkg** command with the **-L** option to get the list from the package name:
```

dpkg -L firefox

```Then get fancy to run **ls** on the list:
```

ls -ld $(dpkg -L firefox | sort)

```

---

### Post by avneravner on 2010-12-26
ok, i tried some of the options and it worked but how all i got are lists of files that are not longer than hundreds of kb's? is that the size softwares occupy on ubuntu? even firefox appeared as being the size of few kb's. possible?

---

### Post by karthick87 on 2010-12-26
```
whereis <packagename>
```

---

