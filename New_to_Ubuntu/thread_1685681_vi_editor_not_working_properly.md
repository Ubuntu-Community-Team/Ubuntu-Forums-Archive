---
title: "vi editor not working properly"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by jeeban37 on 2011-02-11
when i started writing c program in vi editor i saw my arrow keys are not working and when i tried to go to insert mode i pressed Esc and I but it doesnot work
if i write the c program in other textpad on compile it here it shows result correctly.
so i want to know how to write program in vi editor
PLZ reply

---

### Post by Brandon Williams on 2011-02-12
There are several different versions of vi available for install. Run this command -- 'update-alternatives --display vi' -- and post the results so that we know exactly what's being run as vi.

At the same time, do you have anything in .vimrc, .gvimrc, or .exrc that could be causing the behavior you describe? Or is it possible that some of these keys have been remapped? Use xev to figure out what code is being sent to X when you press those keys.

---

