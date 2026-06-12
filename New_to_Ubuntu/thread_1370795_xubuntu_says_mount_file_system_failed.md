---
title: "xubuntu says mount file system failed?"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by kapi on 2010-01-02
Not too sure what to do next, I've installed xubuntu three times and am ready to admit defeat.

If anyone can help  . . .please

the installation went well but upon rebooting I get the mount filesystem failed 

that's it

---

### Post by Max_Mackie on 2010-01-02
I'm not sure if there would be another way of fixing it in Xubuntu (instead of Ubuntu) but you can try a couple of things. First try typing "fsck" (without quotes), the press CTRL+D. You might have to enter it again.

Hope that helps!

---

### Post by RodGer GR on 2010-01-02
While your computer is still booting, press esc to bring up the GRUB menu. Move (using the up-down arrows keys) to the recovery option and press enter. When the recovery menu shows up choose the option that will give you a command line (netroot or root or something like this). When the command line prompt appears, give the command
```
sudo fsck
```

If this doesn't work try to use a live cd, open a terminal (Applications->Accessories->terminal), type sudo fsck ank press enter.

If you try the live cd option, check also if you can mount the partition where you installed xubuntu (meaning if you can open the partition from the Places menu and read the files in it).

After trying the above take some time to post again providing feedback.

I hope your problem gets solved. Good luck!

Have a happy new year :P !

---

### Post by vvfrn on 2010-01-02
The easiest way to fix this is just to use the ubuntu live CD disk then install xubuntu desktop and deleted the ubuntu desktop

---

### Post by RodGer GR on 2010-01-02
vvfrn, why do you think that the Ubuntu installation won't give the same error?

---

### Post by tilixibr on 2010-01-02
Did you install using Wubi?
I had this problem when I installed Ubuntu using Wubi. Every time I  turned off the computer and turned it back again it would give me the same message and put me into an emergency shell. I solved the problem by burning the .iso file (that is used on wubi) and installed using the CD.

---

### Post by kapi on 2010-01-03
Morning all, thankyou for the replies and a happy new year to you all.

First, I ran the live cd then via the terminal input "sudo fsck". I got nothing! just a response saying: 

fsck from unbuntu-linux 2.16 
ubuntu@ubuntu

I also tried installing karmic (I know it is too large for my system because it freezes)

Wubi is for windows and as I've been using ubuntu for the last year it's not relevant, but thanks.

so whats next?

---

