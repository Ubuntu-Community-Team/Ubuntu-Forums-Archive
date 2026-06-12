---
title: "wine install problems"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by mjnaik2 on 2009-03-20
hey guys,
i just tried to install wine in ubuntu 7.10 from "add/remove..." and it gives me an error:
The application cannot be installed as it conflicts with other software. first remove the conflicting software. switch to synaptic package manager to fix the problem.

I couldn't find anything in synaptic so i went to the terminal and tried:
sudo apt-get install wine

but it gives me the following error:
The following packages have unmet dependencies:
  wine: Depends: libaudio2 but it is not installable
E: Broken packages

any help will be appreciated

---

### Post by MaindotC on 2009-03-20
Did you add the wine repository?

---

### Post by mjnaik2 on 2009-03-20
im a real noob and iv only been using ubuntu for about 2 months...so, how do i get these resporitories?

---

### Post by mjnaik2 on 2009-03-20
ok, i got the resporitories but it says:
dependancy is not satisfyable: libaudio2
what do i do now?

---

### Post by mjnaik2 on 2009-03-20
omg, i got it!! i went online and downloaded the "libaudio2.deb" for i386 and installed it and then installed the resporitory and wine intalled!!! thanks for all your help

---

### Post by MaindotC on 2009-03-20
Np - typically you shouldn't have to do that and the dependencies will automatically resolve themselves so you may have some type of configuration problem.  Just anticipate dealing with these issues in the future and having some thick skin to get through them.  I've had problems w/ "Broken Packages" before and had a LOT of difficulty fixing them :(  But good luck.

---

