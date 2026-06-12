---
title: "where to look for installed applications?"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by amit_singh on 2009-02-04
I had setup file of Adobe Acrobat Reader (AAR)on my desktop and I did install it through Alien and Terminal; and it has been installed successfully. Now I am not sure how to open the AAR. I was under assumption that AAR will appear in Menu. So, please help me.
Note: The setup file was in .rpm format. I converted it in .deb format first and then I installed it.


I have faced similar problem with some softwares installation through Wine too, it doesn't appear in Wine menu.

---

### Post by binbash on 2009-02-04
why didnt you add medibuntu to your repos and install via sudo apt-get install acroread?

anyways type acroread and see if that is the command

---

### Post by cwill747 on 2009-02-04
> **amit_singh said:**
> I had setup file of Adobe Acrobat Reader (AAR)on my desktop and I did install it through Alien and Terminal; and it has been installed successfully. Now I am not sure how to open the AAR. I was under assumption that AAR will appear in Menu. So, please help me.
Note: The setup file was in .rpm format. I converted it in .deb format first and then I installed it.


I have faced similar problem with some softwares installation through Wine too, it doesn't appear in Wine menu.

If you know the name of the executable, type Alt-F2 and type in the name. otherwise you can use the locate or whereis command in the terminal to find the executable file

---

### Post by cariboo on 2009-02-04
Most executables are in /usr/bin, if they were installed as root. I usually put scripts I have created in /usr/local/bin.

Jim

---

### Post by oldos2er on 2009-02-04
Adobe Acrobat should be in Applications, Office.

---

### Post by amit_singh on 2009-02-04
well none of the suggestions seems to work for me. please help.

---

### Post by handydan918 on 2009-02-04
Post the output of ```
which <application_name>
```

---

