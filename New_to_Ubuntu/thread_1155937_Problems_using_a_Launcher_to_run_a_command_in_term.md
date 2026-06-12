---
title: "Problems using a Launcher to run a command in terminal..."
date: 2009-05-11
forum: New to Ubuntu
---

### Post by mrskill121 on 2009-05-11
Hey,

I'm relatively new to Linux to bear with me...

I have a slight problem with a command to open the application "maple" on my computer. I have it installed but when I try and open it I just get a grey screen, after a lot of Internet searching, i have found the command

export AWT_TOOLKIT=MToolkit && /root/maple11/bin/xmaple 

runs the application fine when I copy it into the terminal, however, I cannot seem to make a launcher that will run this command! I try and copy that command into the "command" box when creating a launcher and select "application in terminal" but an error message comes up saying...

"There was an error creating the child process for this terminal"

Anybody got any ideas?

It would be nice to not have to copy and paste this command into the terminal every time I want to run Maple! (I also have to keep the terminal open while using maple which is a bit of bummer if anybody can fix that)

Thanks
Shaun

---

### Post by ashmew2 on 2009-05-11
Open a terminal and do :

```
cd ~/Desktop
nano launcher.sh

```

In the editor that opens , just copy paste :
```

export AWT_TOOLKIT=MToolkit && /root/maple11/bin/xmaple 
```

Press Ctrl+X. Press Y to save.

After that :
```

chmod a+x launcher.sh
```

And finally :

```
sh launcher.sh
```

You'll even have a nice icon on your desktop :P

---

### Post by mrskill121 on 2009-05-11
Thank you very much! Much better then what I was doing!

---

### Post by ashmew2 on 2009-05-11
Glad i could be of help :)

---

