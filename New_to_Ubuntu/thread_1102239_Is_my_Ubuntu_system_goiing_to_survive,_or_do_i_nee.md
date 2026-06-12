---
title: "Is my Ubuntu system goiing to survive, or do i need to reinstall?"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by james.harding on 2009-03-21
Hey guys,

So I just made a very stupid move.

I installed Utramatix, following the advice of a Ubuntu starter blog, and have since discovered that it is horrible for the OS, and that it is not at all supported. I removed the program itself, and removed the repositories that it added to my Software Sources.

What I am worried about is that it has done more harm to my Ubuntu? I installed songbird with it...should that be uninstalled too?

Any help is appreciated.

Cheers,
James

---

### Post by drs305 on 2009-03-21
No reinstall is necessary. You have taken the steps to "recover" from your experience. As far as reinstalling songbird, all you may have to do since you got rid of Ultamatix is find a repository which includes it songbird (if there is one) so you can get future updates as they come along.

---

### Post by 123456789123456789123456 on 2009-03-21
finding a repository that has it, would be the best way.  From my experience, if you tell it to install songbird alone, it would probably try to install everything else you already deleted along with it.

a way around that may be apt

in terminal
sudo apt-get install songbird

that if I understand how it works, should bypass the repositories, from ubuntu, since I have used apt command to get programs that are not even listed in the add programs aplet program.

---

### Post by drs305 on 2009-03-21
1234...
Apt uses the sources.list repositories and can also look in the system's package archives. The gui Add/Remove doesn't list all the packages available, which is why apt will work with (many) apps that you don't see listed in Add/Remove.

james: I didn't find songbird in the standard repositories but if you can find a repository and add it to your sources.list it would be easy to reinstall it should that become necessary, as well as keep it updated.

---

### Post by james.harding on 2009-03-21
Thank-you for the help guys :-)

Now my only problem is the fact that my new songbird installation (and any other program for the matter) refuses to play my MP3 files...

Any ideas?

Cheers,
James

---

