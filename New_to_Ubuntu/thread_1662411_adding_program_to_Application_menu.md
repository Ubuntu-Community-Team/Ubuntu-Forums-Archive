---
title: "adding program to Application menu"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by DavidG24 on 2011-01-08
Hi guys,

I just installed Matlab R2010a and am hoping to add a shortcut to the Application Menu. The matlab executable is located in the bin directory, so I thought it would be a simple command, i.e.

/home/david/matlab/bin/matlab

however this doesn't work - it opens the splash screen for matlab then dies, and the only way I can open the program is via the terminal by navigating to the previous directory and running using the standand:
./matlab
(or by right clicking on the file and choosing 'Run in terminal'

I thought I might have to make it executable to make it work using

chmod +x matlab

again, this doesn't solve the problem.

So, my question is, how can I run this via a command for the Applications menu? 

Cheers,

David

ps - sorry if my terminology isn't correct, I'm still fairly new to Ubuntu :P

---

### Post by philipballew on 2011-01-08
i always drag the file i want to make a launcher for into the terminal and paste what the terminal says into the command option for a launcher

---

### Post by DavidG24 on 2011-01-08
> **philipballew said:**
> i always drag the file i want to make a launcher for into the terminal and paste what the terminal says into the command option for a launcher

hey mate,

tried that, the only difference was it changed from

/home/david/matlab/bin/matlab
to
'/home/david/matlab/bin/matlab'

and unforunately it didn't work :-(

Cheers,

David

---

### Post by philipballew on 2011-01-08
the executable file launches by just clicking on it i assume?

---

### Post by DavidG24 on 2011-01-08
> **philipballew said:**
> the executable file launches by just clicking on it i assume?

No unfortunately, you have to 'Run in Terminal'

---

### Post by philipballew on 2011-01-08
there is always the option to make the program open in terminal under the make a launcher window

---

### Post by DavidG24 on 2011-01-08
> **philipballew said:**
> there is always the option to make the program open in terminal under the make a launcher window

Damn, don't I feel like an idiot :-)

Thanks, its working now!

---

