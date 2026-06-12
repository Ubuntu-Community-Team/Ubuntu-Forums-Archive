---
title: "how to define a run app command in terminal"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by thegoat001 on 2009-05-27
I have download eagle 5.6.0 an application for pcb layout.
This version is newer than that in the ubuntu repositories, which forced me to download it from the company's website.  I successfully installed the shell script and am able to run the program without any problems.

Issue: When I enter eagle into the terminal to run the app, I am told that the program is not installed and that I can use sudo apt to install it if I would like.  I am guessing this is because I did not download it through synaptic package manager.

How do I make it so that I can enter a command into the terminal which will then run a specific file/program for me.  The program runs fine, but appears to be installed with a different directory structure (everything is within one folder and there is no .eagle folder under the home user directory) than other programs I have installed with the package manager.

Specific Question:  Is there a file somewhere that would allow me to define a command to open a file rather than having to navigate to it every time.  I like the convenience of simply being able to type the application name to have it run and am also just curious about how ubuntu controls such commands.

Thanks in advance

---

### Post by kpkeerthi on 2009-05-27
You can search for the manually installed binary using
```

sudo updatedb && locate eagle

```

---

### Post by darthmob on 2009-05-27
you will find most executables (or rather links to executables) in the folder /usr/bin/ . if you want to start a program via terminal or alt+f2 launcher it will look in that folder.
personally, I would put a link to the executable in /usr/bin/ or create a shellscript in it which opens the program.

PS: I did not know you could do it like kpkeerthi says. sounds a bit easier!

---

### Post by Celauran on 2009-05-27
> **darthmob said:**
> 
PS: I did not know you could do it like kpkeerthi says. sounds a bit easier!

It's not a replacement for what you suggested, though. His code will tell you where the binary is located, you'll still need to either add a link to /usr/bin or add its directory to your $PATH.

---

### Post by thegoat001 on 2009-05-27
Thanks all, I moved the executable file into the filesystem/bin directory and everything seems to work now when I simply enter eagle into the terminal, thanks again for you help!  I also ran the updatedb and locate commands.

---

