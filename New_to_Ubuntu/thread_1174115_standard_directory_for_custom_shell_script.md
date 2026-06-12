---
title: "standard directory for custom shell script?"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by finkston on 2009-05-30
Hi,

I just made my first shell script and will want to use it random directories. What is the standard place to put custom scripts. I currently put it in /usr/bin/ but that seems ... I don't know wrong.

In other random news, New to linux/ubuntu but so far very pleased, especially with the community support. Everyone please give themselves a hearty pat on the back from me.

---

### Post by brian_p on 2009-05-30
> **finkston said:**
> Hi,

I just made my first shell script and will want to use it random directories. What is the standard place to put custom scripts. I currently put it in /usr/bin/ but that seems ... I don't know wrong.

/usr/local/bin

/usr/bin is for executables which are installed by the packaging system.

---

### Post by dunkar70 on 2009-05-30
If I understand your intent, you want to be able to call the script from any location without typing the full path. You just want to type the name of the script. Is this accurate?

If so, then the problem may not be the location. Did you make the file executable?

After you save a file, you need to execute a command to make it executable. If your file name is SomeFile.sh, execute > chmod +x SomeFile.sh This will make the file executable to anyone who has access to the folder where the file is located.

---

### Post by mcduck on 2009-05-30
If you want to have it available system-wide (as in for all users on the machine) out it into /usr/local/bin.

If it's only for your user, create a bin directory in your home (~/bin) and put it there.

Both these locations are included in your path by default so you can run the script just like any other program, simply with it's name (instead of having to type the full path).

---

