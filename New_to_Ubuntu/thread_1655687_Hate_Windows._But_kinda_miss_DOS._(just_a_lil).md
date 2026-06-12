---
title: "Hate Windows. But kinda miss DOS. (just a lil)"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by jaronron10 on 2010-12-30
I was wondering if there is a command line app for linux, like edit.com was to DOS?

For those times i need to edit grub files or reading instructions when i boot to command prompt?

Thanks
Aaron

---

### Post by SuaSwe on 2010-12-30
Do you mean an in-terminal text editor? If so, there are loads: vi/vim (not for the faint of heart!), pico, nano, etc. I used pico for a long time until I got the hang of vim - nice and user-friendly! You'd open a document by typing e.g. 'pico /path/to/file.txt'. You can also simply view files without editing using 'cat /path/to/file.txt', or 'sudo cat /path/to/file.txt' if owned by root. :)

---

### Post by jaronron10 on 2010-12-30
Perfection.

Thank you soo much. Pico looks easy enough. And I'm installing vim as we speak to see how i like it.

Again Thank You

---

### Post by Idefix82 on 2010-12-30
I don't expect to ever see the day when somebody finds something that he could do in DOS that he cannot do easier and more efficiently in the linux shell :p

---

### Post by ppv on 2010-12-30
Emacs is also one such editor....

---

### Post by SuaSwe on 2010-12-30
Both vim and emacs are terrifying creatures though! Took me an absolute age to become familiar enough with vim to even be able to scroll through a document without accidentally deleting everything in it. :D

---

### Post by jaronron10 on 2010-12-30
> **Idefix82 said:**
> I don't expect to ever see the day when somebody finds something that he could do in DOS that he cannot do easier and more efficiently in the linux shell :p

Well I know of one thing i could do in Windows quiet easily that i haven't managed to do on Linux. That is turning the screen BLUE and hitting the <ctrl><alt><del> keys.

Honestly about 2 weeks of solid Ubuntu fully removed everything else. And so far I havent even tryed <ctrl><alt><del>!  :guitar:

---

### Post by SuaSwe on 2010-12-30
> **jaronron10 said:**
> Well I know of one thing i could do in Windows quiet easily that i haven't managed to do on Linux. That is turning the screen BLUE and hitting the <ctrl><alt><del> keys.

Honestly about 2 weeks of solid Ubuntu fully removed everything else. And so far I havent even tryed <ctrl><alt><del>!

Personally I've actually never had Ubuntu's GUI completely crash in such a way that a Ctrl+Alt+Del would be required - however, there are equivalents should such a time arrive (varying a bit depending on distro version). :) In my experience though it's enough to just kill the process that's hanging (Alt+F2 then "killall <process>", for example).

---

### Post by Idefix82 on 2010-12-30
> **jaronron10 said:**
> Well I know of one thing i could do in Windows quiet easily that i haven't managed to do on Linux. That is turning the screen BLUE...


You mean the blue screen of death? You are right. That one certainly is much harder to reproduce on Ubuntu than on Windows :lolflag:

---

### Post by ronnielsen1 on 2010-12-30
> That one certainly is much harder to reproduce on Ubuntu than on Windows


It's right [here]("http://linux.softpedia.com/get/Utilities/bsod-29186.shtml")

> bsod project will let you UNIX user experience the authentic [microsoft windows]("http://linux.softpedia.com/get/Utilities/bsod-29186.shtml#") experience.

Bsod displays the famous windows [xp]("http://linux.softpedia.com/get/Utilities/bsod-29186.shtml#") blue screen of death on the console. Errors and drivers causing the error are selected randomly from a large set of examples.

**Installation:**

Type:

make install
and that's it!

**Usage:**

Type:

bsod
on the commandline.

[IMG]http://www.softpedia.com/screenshots/thumbs/bsod-29186-thumb.png[/IMG]

---

### Post by Idefix82 on 2010-12-30
That's hilarious!

---

### Post by jaronron10 on 2010-12-30
Well there we have it. Even the Blue Screen Of Death is easier on linux than windows!!

---

### Post by rg4w on 2010-12-30
I'm certainly no expert in either DOS or the Linux shell, but I'm curious:  is there any command in DOS that has no functional equivalent in the shell?

Last time I recall looking through DOS references it seemed DOS covered a very tiny subset of what can be done in Linux.  I walked away from the experience with two thoughts:

1. How does anyone actually use DOS to get work done?
2. Why hasn't Microsoft updated their terminal app in the last decade? ;)

---

