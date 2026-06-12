---
title: "frowny faces and squigglies made computer stop"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by uubuuntuu1 on 2011-03-07
hi
someone told me that if i put soms symbols in a hidden file called bash r c my computer would go faster but now it doesn't run

plz help

---

### Post by uubuuntuu1 on 2011-03-07
???????????????????????

---

### Post by migs73 on 2011-03-07
That person has had you enter a malicious command that will have destroyed your OS. I can't post the suspected code here as it (wisely) against forum rules. Just to check, by squiglees you mean {} and sad face :( also some : and ; and & in the code.

I'm not 100% sure what it does but I think your OS is toast. You will need to re-install. You might want to check you if your data is still there if possible.

---

### Post by xtremesupremacy3 on 2011-03-07
so you know how to create and run a bash script but dont know what a command is doing?

Strange

---

### Post by XAZero on 2011-03-07
Just boot a livecd and remove the line in the file.

Also, it probably was a malicious perl script.

BTW, it wasn't gksudo (kdesudo) r@m -@r@f @/ (remove at symbols)right?

---

### Post by Habeouscorpus on 2011-03-07
> **migs73 said:**
> That person has had you enter a malicious command that will have destroyed your OS. I can't post the suspected code here as it (wisely) against forum rules. Just to check, by squiglees you mean {} and sad face :( also some : and ; and & in the code.

I'm not 100% sure what it does but I think your OS is toast. You will need to re-install. You might want to check you if your data is still there if possible.


It's called a fork bomb, and it makes your computer crash. No, it is not toast. Boot to a live disk right now. Start backing up your data, then open the .bashrc on your drive (It should be labeled "Filesystem, and be on the Desktop in the live CD) and take that section out! Reboot, and your computer should be fine. If not, then you have your data, and can reinstall. But that's a very, very slim chance.

---

### Post by CharlesA on 2011-03-07
> **Habeouscorpus said:**
> It's called a fork bomb, and it makes your computer crash. No, it is not toast. Boot to a live disk right now. Start backing up your data, then open the .bashrc on your drive (It should be labeled "Filesystem, and be on the Desktop in the live CD) and take that section out! Reboot, and your computer should be fine. If not, then you have your data, and can reinstall. But that's a very, very slim chance.
This.

Remove the offending entry from .bashrc and it should be fine.

---

### Post by migs73 on 2011-03-07
Great, you're system can be sorted.

Isn't strange how I can find the malicious code on the internet, but there is no explanation of what it does or how to sort it!

Never mind, at least you have learned a valuable lesson, never run code that you don't know.

Mike :)

---

### Post by Joe of loath on 2011-03-07
If someone told you to install speed.exe on a Windows PC to make it faster, would you do it? :lol:

Just hope it's not wiped your hard drive, and is just stopping it boot :p

---

