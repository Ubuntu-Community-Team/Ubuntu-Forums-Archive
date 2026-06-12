---
title: "start a second conky"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by EuropaCar on 2009-09-11
Hi guys

I've been running conky for a while now and I love it.  Recently I tried running 2 conkys.  I have both conkyrc files in the same directory saved as .conkyrc and .conkyrc2
the trouble is that when I start conky with the command 
conky -c ~/.conkyrc2
I actually get the conky for .conkyrc instead of .conkyrc2
This happens when I put this command in the 'Run Application' shortcut and in the startup apps preference

However, when I start the command in the terminal, it works perfectly.
Does anyone know why this is?  How to solve it?

Thanks

---

### Post by Diabolis on 2009-09-26
The 'Run application' window is not a whole shell, so it just executes binaries, in this case Conky. Conky will look by default for the ~/.conkyrc file, when no arguments are passed to it, so the 'Run window' ignores the arguments and falls to the default value.

You can start your Conky files from System / Preferences / Startup Applications

---

