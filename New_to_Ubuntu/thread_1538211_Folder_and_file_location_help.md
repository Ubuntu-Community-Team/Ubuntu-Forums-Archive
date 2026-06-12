---
title: "Folder and file location help"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by Newbie2910 on 2010-07-24
I am moving some .net code over from Windows to Mono.  When my app tries to read a file, I get a file not found exception.  The file name as shown in the debugger is:

"/home/me/.config\MSTS\main.xml"

Now, I used the file browser to navigate to "me", then enabled viewing hidden files so I could navigate to ".config".  I then created the MSTS folder inside .config, and copied the main.xml file there.  So it exists.

But I am confused about the differences between \ and /.  Is that why my app can't locate the file, even though it appears to be in the right place?  Or is it a permission issue (meaning the app can't open files in hidden folders?

---

### Post by DaithiF on 2010-07-24
> **Newbie2910 said:**
> But I am confused about the differences between \ and /.  Is that why my app can't locate the file
most likely, yes.  find where the path is specified and change the backslashes to forward slashes

> even though it appears to be in the right place?  Or is it a permission issue (meaning the app can't open files in hidden folders?
theres nothing special about hidden files or folder on linux, the 'hiding' of them is just a convenience display feature, it doesn't restrict the ability of applications to use those files.

---

### Post by Newbie2910 on 2010-07-24
Ok... that's good.  So I wonder why the app can't find the file.

---

### Post by DaithiF on 2010-07-25
as I said,
> **DaithiF said:**
> most likely, yes.  find where the path is specified and change the backslashes to forward slashes


---

